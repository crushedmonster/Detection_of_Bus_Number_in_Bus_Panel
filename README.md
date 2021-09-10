# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Capstone Project: Detection of Bus Number in Bus Panel

## Capstone Project: Detection of Bus Number in Bus Panel

### Details
Name: Wenna Loo Yan Ying

Class: DSIF-SG-1

## Problem Statement
Mobility and orientation are the biggest challenges for people with visual impairments. This includes walking, taking public transportation, or even getting a ride on buses. Developing assistive technologies to help them navigate outdoor environments could potentially improve their quality of life. Since public transportation, such as buses, is a main tool for people with visual impairments to navigate outdoor, this project aims to create a proof of concept (POC) that can help people with visual impairment to determine if it’s the right bus they need through Optical Character Recognition (OCR) for the text on the bus.


## Executive Summary
To assist the visually impaired passengers to travel more independently, a POC has been created to detect and recognise bus number of public buses arriving at a bus stop in Singapore. The design made use of a combination of Object Detection (using YOLOv5) and Optical Character Recognition (OCR), to extract bus numbers from the bus panel and convert the extracted text for audio notification.

Starting with data acquisition, we downloaded YouTube videos of public buses arriving at a bus stop in Singapore. Individual frames were extracted from the video every 1 second and saved as images. The collection of images were labelled using [CVAT](https://cvat.org/). Bounding boxes were specified around each bus panel only from the perspective of buses arriving at the bus stop. A manual review of the annotations was done to ensure that the bus panels in the images were properly labelled. The saved annotations were exported to YOLO format. The custom dataset was then formated and split into train, validation, and test set.

Following the data preparation process, we trained YOLOv5 on our custom object (bus panel) using the model’s pre-trained weights for transfer learning. The model's performance was evaluated using the mean Average Precision (mAP) metric. Our model performed pretty well as the mAP score converges close to 100%. Using this model we were able to detect and localise the bounding box coordinates of the bus panel contained in an image. We consider the model to be performing relatively well given that it is successful in generating predictions on new images. Finally, we incorporated the custom object detection model into the OCR pipeline to transform the bus number into raw text data with Tesseract OCR. The project deployment can be found on [Streamlit](https://share.streamlit.io/crushedmonster/streamlit_bus_number_detector).

### Additional Information
There are a total of three notebooks in this project, namely:
* [01_Data_Preparation.ipynb](https://github.com/crushedmonster/Detection_of_Bus_Number_in_Bus_Panel/blob/master/codes/01_Data_Preparation.ipynb)
* [02_Custom_YOLOv5_Training.ipynb](https://github.com/crushedmonster/Detection_of_Bus_Number_in_Bus_Panel/blob/master/codes/02_Custom_YOLOv5_Training.ipynb)
* [03_OCR_Pipeline.ipynb](https://github.com/crushedmonster/Detection_of_Bus_Number_in_Bus_Panel/blob/master/codes/03_OCR_Pipeline.ipynb)

*Note: The custom YOLOv5 training is done entirely on Google Colab. Google Colab is a free cloud service that supports free GPU*

The description and walkthrough for the entire project is available in the notebooks. The datasets for this project are accessible on [Google Drive](https://drive.google.com/drive/folders/1RBHFOXFMMLCXX0rdxxigoxZa4Ax1GGOz?usp=sharing).


## Conclusion
With the problem statement in mind to help people with visual impairment to determine if it’s the right bus they need, we have successfully created a POC for deployment and tested that it is indeed tangible to make use of computer vision-based system to solve our problem. We were able to train YOLOv5 on our custom dataset and found that YOLOv5 trains quickly, inferences quickly, and performs really well in detecting the bus panel contained in an image. But, OCR is not without its challenges. There were some limitations found within the pipeline which will be explained below.


### Limitations
* The OCR capabilities 
* Improving the OCR capabilities
* Better ways of preprocessing the images before feeding into the OCR software

### Future Exploration
* Collect more images of buses at night
* Test it on videos or on a live camera
