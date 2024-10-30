# Real-Time Driver Drowsiness Alert System

## Overview

This project is a **Real-Time Driver Drowsiness Alert System** that monitors a driver’s eye status through a webcam and alerts them when signs of drowsiness are detected. Utilizing **OpenCV** for image capture and preprocessing, a **Convolutional Neural Network (CNN)** model classifies the driver’s eyes as 'Open' or 'Closed.' If the eyes remain closed for an extended period, an alarm is triggered to keep the driver alert.

## System Workflow

### Key Steps in Drowsiness Detection

1. **Image Capture**: Capture frames in real-time from a webcam.
2. **Face Detection**: Detect the driver’s face in the frame and set it as the Region of Interest (ROI).
3. **Eye Detection**: Detect eyes within the ROI and pass these to the classifier.
4. **Eye Classification**: Classify eye state as 'Open' or 'Closed' using the CNN model.
5. **Drowsiness Evaluation**: Monitor and calculate a score based on the duration of eye closure to detect drowsiness.

## CNN Model Architecture

The **Convolutional Neural Network (CNN)** used for classification has the following layers:

- **Convolutional Layers**:
  - Layer 1: 32 filters, kernel size 3
  - Layer 2: 32 filters, kernel size 3
  - Layer 3: 64 filters, kernel size 3
- **Fully Connected Layers**:
  - Dense Layer: 128 nodes
  - Output Layer: 2 nodes with Softmax activation (to classify eyes as 'Open' or 'Closed').

### Activation Functions
- **ReLU**: Applied to all layers except the output layer.
- **Softmax**: Applied to the output layer for classification.

## Project Requirements

### Hardware
- Webcam for image capture.

### Libraries
Ensure Python (version 3.6 recommended) is installed, then install the following libraries:

```bash
pip install opencv-python
pip install tensorflow
pip install keras
pip install pygame
```

# Real-Time Driver Drowsiness Alert System

**Files**

* **haar cascade files**: XML files for detecting faces and eyes (located in "haar cascade files" folder)
* **models**:
    * `cnnCat2.h5`: Trained CNN model for eye classification
* **alarm.wav**: Audio file played if drowsiness is detected (located in root directory)
* **Python Scripts**:
    * `Model.py`: Script for building and training the CNN model
    * `drowsiness_detection.py`: Main script that executes the real-time detection and alert system

**Running the System**

1. Open a command prompt and navigate to the directory containing `drowsiness_detection.py`.
2. Run the following command:

```bash
python drowsiness_detection.py
```
