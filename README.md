# Real-Time Driver Drowsiness Alert System

## Overview

This project implements a **real-time driver drowsiness detection system** using **OpenCV, Keras (CNN), and Pygame**. The system monitors the driver’s eye status via webcam and triggers an alarm if drowsiness is detected, helping prevent accidents caused by microsleep while driving.


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


## Requirements

- Python 3.x
- OpenCV
- Keras
- TensorFlow
- Numpy
- Pygame
- Matplotlib

Install dependencies using:

```bash
pip install opencv-python keras tensorflow numpy pygame matplotlib
```
## How It Works

### Model Training (`model.py`)

- Trains a **Convolutional Neural Network (CNN)** on **grayscale eye images (24x24)**.
- Classifies eyes as **Open** or **Closed**.
- Saves the trained model (`cnn.h5`).

### Real-Time Detection (`drowsiness detection.py`)

- Captures video using the **webcam**.
- Detects **face and eyes** using Haar cascades.
- Predicts **eye status** using the trained CNN.
- Increases the **drowsiness score** when eyes are closed.
- Triggers a **red flashing border and alarm** when the score exceeds the threshold (`score > 15`).

---

## Usage

Ensure you have:

✅ Trained the CNN model (`model.py`) or placed your `cnn.h5` in the `models` folder.  
✅ Haar cascade XML files in the `haar cascade files` folder.  
✅ `alarm.wav` in your project directory.

**Files**

* **haar cascade files**: XML files for detecting faces and eyes (located in "haar cascade files" folder)
* `cnn.h5`: Trained CNN model for eye classification
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
Press q to exit the detection window.

## Results

If the driver closes their eyes for a prolonged period:

-  **An alarm sound is triggered.**
-  **A red flashing border appears on the video feed.**
-  **Helps in alerting the driver in case of microsleep or drowsiness.**

