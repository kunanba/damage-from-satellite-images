# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 5: Using Satellite Images to Identify Damage

### Project Overview

We've organized for you to complete a client project. This is a great opportunity for you to be exposed to a **real organization** doing **real work** with **real data**.



During the recovery phase immediately following a disaster, FEMA performs damage assessment “on the ground” to assess the level of damage caused to residential parcels and to critical infrastructure. To assure an accurate estimation of the damage, it is important to understand the condition of the structures prior to the event. To help and guide the damage assessment efforts following a disaster, and to assist the surveyors in identification of the structures of interest, SightVisit. It will retrieve screen shots of the structures from Google Street View. A damage assessment form, which, in addition to relevant information





### Team

<<<<<<< HEAD
- [Chris Birch](linkedin link?)
=======
- [Chris Birch](https://www.linkedin.com/in/chris-birch/) 
>>>>>>> b5305101b7447431dd9a09b0f9a980aa021e656a

- [Angela Kunanbaeva](https://www.linkedin.com/in/aqqu/)

<<<<<<< HEAD
- [Drannon Love](https://newlighttechnologies.com/)
=======
- [Drannen Love](https://www.linkedin.com/in/drannenlove/) 
>>>>>>> b5305101b7447431dd9a09b0f9a980aa021e656a

- [Tricia Wells](https://www.linkedin.com/in/triciawells731/)


### The Work

The repository includes:

- Source code of Mask R-CNN built on FPN and ResNet101.
- Training code for MS COCO
- Pre-trained weights for MS COCO
- Jupyter notebooks to crop the image and visualize the image comparison
- ParallelModel class for multi-GPU training



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
the image selection was a manual process and consisted of searching for images, modifying them, and evaluating them. The goal was to find satellite images before and after a natural disaster. For our purposes satellite images provide the best view for damage assessement. The challenge with satellite images made available to the public is they don't have specific date range filters to search on related to natural disasters. We resorted to taking snapshots of images that were made available to the public via news channels as well as google images. They were then saved in Jpeg format for image preprocessing and then resized using OpenCV image visualization library. We used the structural Similarity Index(SSIM) score to compare before and after satellite images. These score are measure on a range from (0,1) for structural similarity.0, having no structural similarity and 1, having complete structural similarity.




### Image Transformation

       
   In order for the images to be processed via machine learning algorithms not only do they have to be converted into matrices of numbers but also it is essential to scale them. This is really important since we have to compare the images in pairs, and they have to be the same size. Most of our images were collected manually using computer screenshots and thus they come in bunch of different size. Scaling/resizing scales the images to a certain size, but the difference in scale will remain. It is better to crop this kind of images, but in order to keep majority of information the cropping should be in accordance with the image size. To see the code how the resizing is performed and the files are written [click here](./cropping_images.ipynb) to go to *Cropping Images Notebook*. The SSIM score is also calculated in the notebook above.
    
    
   The next part is to actually transform images so we can compare the differences in the images, and apply techniques that will enable us to create the contours for object detection purposes, and essentially help us asses the damaged areas of the buildings or areas.
       
       
   The worklfow for two images comparison usually follows the steps below, and two libraries required for this OpenCV and scikit-image. 
    

1. Reading in the images using OpenCV

2. The images should be grayscaled first for further image processing techniques

3. It is important to threshold the images in order to binarize the images into black and white output. This essentially creates a mask where further computer vision algorithms can detect the significant parts of the image and ingore the insignificant parts. In our case the black will be ignored and the white should be considered significant

4. Another method to create mask is edge detection, which can also be used as a mask.

5. Lastly we have to create the contours in order to outline the buildings on the images before disaster and after disaster, and essentially detect the building and as the end result calculate the difference between undamaged building and damaged building or area


      In order to streamline the image comparison process it is essential to define functions [click here](./disaster_images_processing.ipynb) to see the notebook containing these functions. Using the functions we can read in the images, display them using Matplotlib, covert to grayscale and threshold images. Moreover, one can determine absolute difference between the images and calculate the SSIM score, in order to determine how those images differ. The commented out section in functions explain what function does and what it returns, as well as what the inputs are.
      Also in the same notebook you can see how before and after disaster images compare to each other, these include Hurricane Harvey, Hurricane Michael, Tornado Joplin and Widlfire California.
      
      
      After the inital processing part the object detection algorithm is required to determine where the buildings are, and calculate the SSIM scores on how they differ, so that initial damage assesment can be determined.




### Object Detection
<<<<<<< HEAD
=======

### Next Steps
- Access to additional images from satellite sources
- Automation of image capture, scoring, and selection
- Incorporating Object detection before contouring
- Training a neural network to detect bounding boxes
- Annotation of images
>>>>>>> b5305101b7447431dd9a09b0f9a980aa021e656a
