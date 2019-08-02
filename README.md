# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 5: Using Satellite Images to Identify Damage

### Project Overview

During a disaster the immediate needs are the search and rescue of survivors.  Following a disaster, assessing the level of damage caused and the area that has been affected is critical to timely distribution of needed resources.

This project seeks to distinguish affected disaster areas from satellite images using image selection, transformation and object detection.


### Team


- [Chris Birch](https://www.linkedin.com/in/chris-birch/) 

- [Angela Kunanbaeva](https://www.linkedin.com/in/aqqu/)

- [Drannen Love](https://www.linkedin.com/in/drannenlove/) 

- [Tricia Wells](https://www.linkedin.com/in/triciawells731/)


### Requirements
- Python 
- scikit-image
- scikit-learn
- pandas
- numpy
- matplotlib
- OpenCV
- glob
- os
- keras
- plaidml
- imutils
- PIL



### Image Selection


   Image selection was a manual process and consisted of searching for images, modifying them, and evaluating them. The goal was to find satellite images before and after a natural disaster. For our purposes satellite images provide the best view for damage assessement. The challenge with satellite images made available to the public is they don't have specific date range filters to search on related to natural disasters. We resorted to taking snapshots of images that were made available to the public via news channels as well as google images. They were then saved in Jpeg format for image preprocessing and then resized using OpenCV image visualization library. We used the structural Similarity Index(SSIM) score to compare before and after satellite images. These scores are a measure on a range from (0,1) for structural similarity, with 0, having no structural similarity and 1, having complete structural similarity.




### Image Transformation

       
   In order for the images to be processed via machine learning algorithms not only do they have to be converted into matrices of numbers but also it is essential to scale them. This is really important since we have to compare the images in pairs, and they have to be the same size. Most of our images were collected manually using computer screenshots and thus they come in bunch of different size. Scaling/resizing scales the images to a certain size, but the difference in scale will remain. It is better to crop this kind of images, but in order to keep majority of information the cropping should be in accordance with the image size. To see the code how the resizing is performed and the files are written [click here](code/cropping_images.ipynb) to go to *Cropping Images Notebook*. The SSIM score is also calculated in the notebook above.
    
    
   The next part is to actually transform images so we can compare the differences in the images, and apply techniques that will enable us to create the contours for object detection purposes, and essentially help us asses the damaged areas of the buildings or areas.
       
       
   The worklfow for two images comparison usually follows the steps below, and two libraries required for this OpenCV and scikit-image. 
    

1. Reading in the images using OpenCV

2. The images should be grayscaled first for further image processing techniques

3. It is important to threshold the images in order to binarize the images into black and white output. This essentially creates a mask where further computer vision algorithms can detect the significant parts of the image and ingore the insignificant parts. In our case the black will be ignored and the white should be considered significant

4. Another method to create mask is edge detection, which can also be used as a mask.

5. Lastly we have to create the contours in order to outline the buildings on the images before disaster and after disaster, and essentially detect the building and as the end result calculate the difference between undamaged building and damaged building or area


      In order to streamline the image comparison process it is essential to define functions [click here](code/Disaster_images_processing.ipynb) to see the notebook containing these functions. Using the functions we can read in the images, display them using Matplotlib, covert to grayscale and threshold images. Moreover, one can determine absolute difference between the images and calculate the SSIM score, in order to determine how those images differ. The commented out section in functions explain what function does and what it returns, as well as what the inputs are.
      Also in the same notebook you can see how before and after disaster images compare to each other, these include Hurricane Harvey, Hurricane Michael, Tornado Joplin and Widlfire California.
      
      
      After the inital processing part the object detection algorithm is required to determine where the buildings are, and calculate the SSIM scores on how they differ, so that initial damage assesment can be determined.




### Object Detection: Training a Network


This section consists of different methods to accomplish the same classification goal.  All of our models are trying to classify what is a building and what is background.
All of the images for this section are located in the `images/training/` folder, along with a script to create the positive and negative images from the originals and binary mask.
- Upon further review, this seems to be a useless step and is not the proper way to accomplish this task.
- Using Histogram of Gradients (HOG) supplies the 'hot spots' to build the bounding boxes / contours, but this has not been fully accomplished at this point.

Each notebook that has the structure `010_<notebook_name>` is an attempt at a model to classify the buildings.

> *The main points of this section are as follows:*
> - Classifying, segmenting, creating bounding boxes, annotating, and training on images from scratch is **hard!**
> - This section was a great lesson on research and working around current solutions and adapting others to fit our needs.
> - Further work or restructuring of this section is needed to get the segmentation of the buildings correct.
> - Convolutional Neural Network(s) (CNN) are the way to go for the future, because of their ability to detect higher order and more complex features, based on the structure of the network.
> - SVM, SGDClassifier, and the more manual method are quicker to implement, and much less computationally taxing, however the tradeoff is their complexity limitations.

#### Future of this section:
 - Restructure the order of creating HOG and finding bounding box points.
 - Find out how to create (accurate) binary masks from original images.
 - Use binary masks to find contours and corners.
 - Annotate, and programatically annotate, the binary masks.
 - Pass the coordinates and annotations to train a basic model.
 - Use the model to detect buildings, and find the SSIM score of the boxed regions.
 - Use the trained network to more accurately identify buildings and create binary masks from them in order to annotate them and improve the model upon itself.
 
 

