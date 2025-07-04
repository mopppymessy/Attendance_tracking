# Real-Time Face Detection, Recognition & Age Prediction Attendance System

This is a Python-based real-time face recognition and age prediction attendance system that detects faces through your webcam, identifies known individuals using DeepFace (Facenet model), predicts age for unknown faces using a trained regression model, and logs attendance with timestamps and saved images into a CSV file.


## Features

- Real-time face detection using OpenCV (Haar cascades)
- Face recognition using DeepFace with Facenet embeddings
- Age prediction using a trained regression model (`MLAssignment2.pk1`)
- Attendance logging with:
  - Name
  - Timestamp
  - Captured face image path
- Daily folder (YYYY-MM-DD) with:
  - Attendance.csv
  - Saved cropped face images
-  Attendance logged only once every 3 seconds per recognized face to avoid spam
- Works with custom image folders for each person


## Setup Instructions

### 1. Install Requirements

Make sure you have Python 3 and install dependencies:
pip install opencv-python pandas joblib deepface numpy


### 2. Prepare Your Dataset

Create a folder named 'ImagesAttendance/', with a separate subfolder for each person. Add multiple clear, front-facing '.jpg' or '.jpeg' images in each.

Example:
ImagesAttendance/
├── Alice/
│   ├── img1.jpg
│   ├── img2.jpg
└── Bob/
    ├── img1.jpg
    └── img2.jpg


It should accept input of shape (1, 224, 224, 3) and output a numerical age.

## Run the Program
python main.py

## How It Works

1. Face Detection: Uses Haar cascade to detect faces from webcam input.
2. Face Recognition:
   - Encodes known faces using DeepFace Facenet
   - Compares detected faces in real-time to known embeddings
   - If a match is found logs the name
   - If no match predicts age using regression model
3. Attendance Logging:

   - Saves cropped face image to `YYYY-MM-DD/` folder
   - Adds a row in `Attendance.csv` with:

     - Name
     - Timestamp
     - Image path
   - Waits 3 seconds before logging the same face again

## Example Output

Console:
Number of faces detected: 1
Logging attendance: Name: Alina, Time: 14:32:10, Image Path: 2025-07-03/Alina_143210.jpg
Attendance logged for Alina

CSV (Attendance.csv):

Name,Time,Image Path
Alina,14:32:10,2025-07-03/Alina_143210.jpg

## Tips for Better Accuracy

- Use 3–5 high-quality, front-facing photos per person.
- Ensure faces are well-lit and not blurred.
- Match input size and preprocessing for your trained age model 224x224, normalized.
- Use consistent naming conventions in the image folders.



## Exit

Press the 's' key in the OpenCV window to stop the program safely.

