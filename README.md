# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Capstone Project: Detection of Bus Number in Bus Panel

## Capstone Project: Detection of Bus Number in Bus Panel

### Details
Name: Wenna Loo Yan Ying

Class: DSIF-SG-1

## Problem Statement
Mobility and orientation are the biggest challenges for people with visual impairments. This includes walking, taking public transportation, or even getting a ride on buses. Developing assistive technologies to help them navigate outdoor environments could potentially improve their quality of life. Since public transportation, such as buses, is a main tool for people with visual impairments to navigate outdoor, this project aims to create a proof of concept (POC) that can help people with visual impairment to determine if it’s the right bus they need through Optical Character Recognition (OCR) for the text on the bus.


## Executive Summary
To assist the visually impaired passengers to travel more independently, a POC has been created to detect and recognise bus number of public buses arriving at a bus stop in Singapore. The design made use of a combination of Object Detection (using YOLOv5) and Optical Character Recognition (OCR), to extract bus numbers from the bus panel and convert the extracted text for audio notification.

Starting with data acquisition, we downloaded YouTube videos of public buses arriving at a bus stop in Singapore. Individual frames are extracted from the video every 1 second and saved as images. The collection of images were labelled using [CVAT](https://cvat.org/). Bounding boxes were specified around each bus panel only for buses arriving at the bus stop. A manual review of the annotations was done to ensure that the bus panels are properly labelled. The saved annotations were exported to YOLO format. The custom dataset was then formated and split into train, validation, and test set.

Following the data preparation process, we trained YOLOv5 on our custom object (Bus Panel) using the model’s pre-trained weights for transfer learning. The model's performance was evaluated using the mean Average Precision (mAP) metric. 

* What were your findings?
* What risks/limitations/assumptions affect these findings?

