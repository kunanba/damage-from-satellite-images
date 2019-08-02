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
