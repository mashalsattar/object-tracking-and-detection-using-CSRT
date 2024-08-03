# Project Title: YOLOv8 Object Tracking with CSRT

# Description:

This project implements a real-time object tracking system using YOLOv8 for object detection and the CSRT (Correlation-based Tracker) algorithm for tracking the detected object. It utilizes the ultralytics library for a streamlined YOLOv8 experience. The project is designed to be adaptable to different object tracking scenarios by replacing the pre-trained "bottle.pt" model with one trained on your specific dataset.

# System Requirements:

Operating System: Windows, macOS, or Linux (x86-64)

Python 3.6 or later

OpenCV (cv2)

ultralytics ([invalid URL removed])
(Optional) CUDA and compatible NVIDIA GPU for faster training (if applicable)
**Installation:**

# Create a virtual environment:
```
python -m venv env
source env/bin/activate
```
**Use code with caution.**

# Install Required Libraries:
```
pip install opencv-python ultralytics
```
**Use code with caution.**

**(If using a GPU for training, install torch with CUDA support:pip install torch==1.x.0+cu117 torch-vision==0.x.0+cu117 Replace x.x.0 and cu117 with appropriate versions based on your GPU)**

# Project Structure:

your_project_name/

├── README.md (this file)

├── tracking.py (main script)

└── model/ (directory for your trained YOLOv8 model)

    └── bottle.pt (example pre-trained model, replace with yours)

# Project Setup:

Place your trained YOLOv8 model file (e.g., "bottle.pt") in the model/ directory.

(Optional) Update the video path in tracking.py to the location of your video file.

Training YOLOv8 (if applicable):

**Prepare your dataset:** You'll need a labeled dataset in the COCO format. Tools like VGG Image Annotator (VIA) or LabelImg can be used for labeling.

**Train the model:** Refer to the YOLOv8 documentation (https://github.com/computervisioneng/train-yolov8-custom-dataset-step-by-step-guide) for detailed training instructions. The general steps involve creating a YAML configuration file, preparing your dataset, and running the training script.

# Running the Script:

Open a terminal in your project directory.

Execute the script:
```
python tracking.py
```
**Use code with caution.**

# Explanation of the Script:

Imports necessary libraries cv2, YOLO from ultralytics, and defines variables.

Loads the pre-trained YOLOv8 model from model/bottle.pt.

Initializes video capture using cv2.VideoCapture. Checks for successful opening.

Initializes tracking variables: tracker_initialized, tracker, roi (region of interest), class_name, conf (confidence score).

**Enters a loop to process video frames:**

Reads a new frame from the video capture.

If no tracker is initialized (not tracker_initialized):

Performs object detection using the YOLOv8 model.

Extracts bounding boxes and confidence scores.

If an object is detected with confidence greater than 0.5:

Creates an ROI from the bounding box coordinates.

Maps the class index to a class name (assuming you have a mapping mechanism).

Initializes the CSRT tracker with the ROI.

Sets tracker_initialized to True.

**Otherwise:**

Updates the tracker to track the object in the new frame.

Draws bounding boxes, confidence scores, and class names on the frame (if tracking is successful) or a "Tracking failure detected" message (if tracking fails).

Displays the video frame with tracking results.

Exits the loop when the 'q' key is pressed.

Releases the video capture and destroys OpenCV windows.

# Additional Notes:

**Customizing Object Classes:** The provided script assumes a pre-trained YOLOv8 model for bottle detection. You can adapt it to different object classes by replacing the model and potentially modifying the class name mapping logic.

Error Handling: Consider adding more comprehensive error handling for common issues like invalid video paths or model loading failures
