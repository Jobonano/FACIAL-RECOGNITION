# Face Recognition Attendance System (With Speech Intro)

## Overview

This project implements a real-time face recognition attendance system using OpenCV, `face_recognition`, and the Ultraytics YOLO model. It captures video from a webcam, recognizes faces, and records attendance in an Excel file. The system is designed to work with a directory of known faces and employs caching for efficiency.

## Requirements

To run this project, you need to install the following Python packages:

- OpenCV
- face_recognition
- numpy
- pandas
- pyttsx3
- ultralytics
- scikit-learn (optional, for distance calculations)

You can install these packages using pip:

```bash
pip install opencv-python face_recognition numpy pandas pyttsx3 ultralytics
```

## Project Structure

- **KnownFaces/**: Directory containing subdirectories for each known person, with images of their faces.
- **cache/**: Directory for storing cached encodings and hash files (auto-created).
- **attendance_*.xlsx**: Excel file for storing attendance records.

## Code Explanation

### 1. Import Libraries

The script imports necessary libraries, including OpenCV for image processing, `face_recognition` for facial encoding, and logging utilities.

### 2. Configuration

The script sets up logging to record system events and defines the file paths for storing attendance records and cached face encodings.

### 3. Face Encoding Loading

- The `load_known_faces_with_cache` function loads face encodings from the specified directory. It uses a hash of the directory contents to determine if the cache is valid or if it needs to reprocess the images.

### 4. Attendance Recording

The `record_attendance` function appends recognized individuals' names and timestamps to an Excel file.

### 5. Frame Processing

The `process_frame` function detects faces in each video frame, recognizes them using the loaded encodings, and draws bounding boxes around recognized faces.

### 6. Main Function

The `main` function orchestrates video capture, processing frames in real time, and managing attendance records.

### 7. Voice Interaction

The `welcome_speech` function uses the `pyttsx3` library to provide audio feedback to users.

## Usage

1. **Setup Known Faces**:
   - Create a directory named `KnownFaces`.
   - Inside `KnownFaces`, create subdirectories for each person, naming them appropriately (e.g., `Alice`, `Bob`).
   - Add face images in the respective subdirectories.

2. **Run the Script**:
   - Execute the script in your terminal or an IDE. Ensure your webcam is connected.
   - The system will greet users and start capturing video.

3. **Attendance Recording**:
   - As recognized faces are detected, their names and timestamps will be recorded in the attendance Excel file.

4. **Stop the Program**:
   - Press 'q', 'Q', or 'Esc' to exit the application.

## Notes

- Ensure the `KnownFaces` directory and its structure is set up correctly for the system to recognize individuals.
- Adjust the `distance_threshold` in the `process_frame` function if necessary, to balance recognition accuracy and false positives.
- To clear the cache of face encodings, run the script with the `--clear-cache` option.

## Conclusion

This Face Recognition Attendance System provides an efficient and interactive way to track attendance using facial recognition technology. It can be further enhanced with additional features such as real-time alerts, integration with other systems, or improvements in user interaction.
