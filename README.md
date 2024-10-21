# Real-Time Face Recognition Attendance System

## Overview
This project implements a face recognition attendance system using OpenCV and the face_recognition library. It captures video from a camera, recognizes faces, and records attendance in an Excel file.

## Features
- Load known faces from a specified directory.
- Cache face encodings for faster access.
- Record attendance in an Excel file.
- Display recognized faces with bounding boxes and labels in real time.

## Requirements
- Python 3.x
- OpenCV
- face_recognition
- NumPy
- pandas
- logging
- argparse
- Pickle
- Hashlib
- Datetime

## Installation
1. Clone this repository or download the source code.
2. Install the required libraries:
   ```bash
   pip install opencv-python face_recognition numpy pandas
   ```

## Directory Structure
```
/YourProjectDirectory
│
├── KnownFaces/                # Directory to store known face images
│   ├── Person1/               # Subdirectory for Person1
│   │   ├── image1.jpg         # Image files of Person1
│   │   └── image2.jpg
│   └── Person2/               # Subdirectory for Person2
│       ├── image1.jpg
│       └── image2.jpg
│
├── cache/                     # Directory for caching encodings
│   ├── encodings_<date>.pkl   # Cached face encodings
│   └── encodings_hash_<date>.txt # Hash for cache validation
│
└── attendance_<date>.xlsx     # Attendance record file
```

## Usage
1. Place known face images in the `KnownFaces` directory. Each person's images should be in a separate subdirectory named after the person.
2. Run the script:
   ```bash
   python face_recognition_attendance.py
   ```
3. The program will open a window displaying the video feed. Press `q` or `Esc` to exit.

### Command-Line Arguments
- `--clear-cache`: Clear the cached face encodings and reprocess known faces.

## Code Explanation

### Logging Configuration
- Logs are configured to display info-level messages and above. Attendance records are saved in an Excel file named with the current date.

### Loading Known Faces
- The program loads known faces from a specified directory. It uses hashing to check if the contents of the directory have changed since the last run. If changes are detected, it processes the images again to update the encodings.

### Attendance Recording
- The attendance of recognized individuals is recorded in an Excel file, which includes their name and a timestamp.

### Video Processing
- The program captures video frames from a webcam or IP camera. Each frame is processed to detect and recognize faces. Detected faces are annotated with bounding boxes and labels. Attendance is recorded for recognized individuals.

### Main Function
- The `main()` function initializes video capture, processes video frames in a loop, and displays the annotated frames in real-time.

## Error Handling
- The code includes error handling for file I/O operations and video capture, with appropriate logging messages.

## Conclusion
This system provides a straightforward way to manage attendance using face recognition. 
By leveraging caching and efficient processing, it can be adapted for various applications such as classrooms, events, and offices.
