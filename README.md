# 🧍 Human Activity Analyzer Using Deep Learning

A computer vision project that analyzes human movement in video using **MediaPipe Pose Estimation, OpenCV, and Python**. The system detects body landmarks, processes video frames, and applies rule-based logic to identify basic activities such as sitting and standing/walking.

## 📌 Project Overview

Human activity analysis is an important application of computer vision, with potential uses in fitness monitoring, movement analysis, and human-computer interaction.

The **Human Activity Analyzer** processes an input video frame by frame to detect human body landmarks. Using the detected pose information, the system estimates basic activities based on the vertical distance between selected body landmarks.

The processed video displays the detected pose skeleton and the predicted activity label, allowing users to visualize the analysis.

## 🎯 Objectives

- Detect human body landmarks from video frames.
- Apply pose estimation using MediaPipe.
- Analyze body posture using landmark coordinates.
- Classify basic activities using rule-based conditions.
- Visualize detected body landmarks and activity labels.
- Generate a processed video containing the analysis results.

## ✨ Key Features

- 🎥 **Video Input:** Process an uploaded video for human movement analysis.
- 🧍 **Human Pose Estimation:** Detect body landmarks using MediaPipe Pose.
- 📍 **Landmark Visualization:** Draw pose landmarks and skeletal connections on video frames.
- 🧠 **Activity Classification:** Identify basic activities using landmark-based rules.
- 🪑 **Sitting Detection:** Estimate sitting posture using the vertical distance between selected landmarks.
- 🚶 **Standing/Walking Classification:** Identify frames that satisfy the configured distance threshold.
- 🎬 **Video Processing:** Process and save the annotated output video.
- 📥 **Output Download:** Download the processed video for further viewing and analysis.

## 🛠️ Technology Stack

| Component               | Technology                |
| ----------------------- | ------------------------- |
| Programming Language    | Python                    |
| Pose Estimation         | MediaPipe Pose            |
| Computer Vision         | OpenCV                    |
| Numerical Processing    | NumPy                     |
| Development Environment | Google Colab              |
| Input/Output            | Video Processing with MP4 |

## 🏗️ System Architecture

The project follows a video-processing pipeline.

1. **Video Upload:** Upload the input video to Google Colab.
2. **Frame Extraction:** OpenCV reads the video frame by frame.
3. **Pose Estimation:** MediaPipe detects human body landmarks in each frame.
4. **Landmark Analysis:** The system examines the coordinates of selected body landmarks.
5. **Activity Classification:** Rule-based conditions assign an activity label.
6. **Visualization:** The detected pose and activity label are drawn on the frame.
7. **Video Generation:** OpenCV saves the processed frames into an output video.
8. **Output Display:** The generated video is displayed and made available for download.

## 🔄 Workflow

```text
       Input Video
            |
            v
     Video Frame Reading
          (OpenCV)
            |
            v
    MediaPipe Pose Estimation
            |
            v
     Detect Body Landmarks
            |
            v
    Calculate Landmark Distance
            |
            v
     Rule-Based Classification
            |
      +-----+------+
      |            |
      v            v
   Sitting    Standing/Walking
      |            |
      +-----+------+
            |
            v
  Draw Pose and Activity Label
            |
            v
     Generate Output Video
            |
            v
     Display and Download
```

## 🧠 Activity Classification Logic

The current implementation uses the vertical distance between the left hip and left ankle landmarks.

```python
vertical_distance = abs(left_hip.y - left_ankle.y)

if vertical_distance < 0.3:
    return "Sitting"
elif vertical_distance > 0.5:
    return "Standing/Walking"
else:
    return "Unknown"
```

The classification thresholds are:

| Condition                       | Predicted Activity |
| ------------------------------- | ------------------ |
| Distance below `0.3`            | Sitting            |
| Distance above `0.5`            | Standing/Walking   |
| Distance between the thresholds | Unknown            |

These are heuristic thresholds, not learned classification boundaries. The predictions depend on the detected pose, camera angle, body position, and video framing.

## 📂 Project Structure

The following structure is suitable for organizing the project on GitHub.

```text
Human-Activity-Analyzer/
├── notebooks/
│   └── human_activity_analyzer.ipynb
├── sample_videos/
│   └── sample.mp4
├── outputs/
│   └── output.mp4
├── requirements.txt
└── README.md
```

*Note: The folders shown above are a suggested organization. Your actual files may differ. Avoid uploading large video files unless necessary.*

## ⚙️ Installation

### Prerequisites

- Python
- Google Colab or a compatible Python environment
- A video file supported by OpenCV

### Install Dependencies

Run the following command in Google Colab:

```python
!pip install mediapipe==0.10.20 opencv-python numpy
```

### Upload the Input Video

```python
from google.colab import files

uploaded = files.upload()
```

Select your video file when prompted.

### Configure the Input Filename

Use the exact filename of the uploaded video:

```python
input_video = "sample.mp4"
output_video = "output.mp4"
```

Replace `sample.mp4` with the actual uploaded filename if it differs.

### Run the Analysis

Execute the video-processing code to detect pose landmarks, classify activities, and generate the annotated video.

### Display and Download the Output

```python
from IPython.display import Video, display
from google.colab import files

display(Video("output.mp4", embed=True))
files.download("output.mp4")
```

## 📊 Expected Output

The output is an annotated video containing:

- Detected human pose landmarks.
- Skeletal connections between body landmarks.
- An activity label, such as `Sitting`, `Standing/Walking`, or `Unknown`, when a pose is detected.
- The processed video saved as `output.mp4`.

## ⚠️ Current Limitations

- Activity classification relies on fixed, manually selected thresholds.
- Sitting and standing/walking may be confused in certain poses or camera angles.
- The current logic does not independently distinguish walking from standing.
- The analysis depends on successful pose detection and visible body landmarks.
- The system does not currently train a separate activity-classification model.

## 🔮 Future Enhancements

- Develop a deep learning activity classifier using labeled pose landmarks.
- Distinguish walking, standing, sitting, running, and other activities.
- Use multiple body landmarks and joint angles for more reliable posture analysis.
- Analyze landmark sequences across multiple video frames.
- Improve classification under different camera angles and lighting conditions.
- Build a web interface for uploading videos and viewing analysis results.
- Evaluate classification performance using accuracy, precision, recall, and F1-score.

## 🎓 Learning Outcomes

Through this project, I explored:

- Computer vision using OpenCV.
- Human pose estimation using MediaPipe.
- Body landmark extraction and coordinate analysis.
- Rule-based activity classification.
- Frame-by-frame video processing.
- Visualization of pose landmarks.
- Generating and downloading processed video outputs.

## Outcome 

1. Sitting Analysis
<img width="681" height="1015" alt="Screenshot 2025-10-27 095201" src="https://github.com/user-attachments/assets/bfe2109f-999e-4fde-b8b8-e5e1549f6da0" />

2. Exception Analysis
![Uploading Screenshot 2025-10-27 095137.png…]()


## 👩‍💻 Author

Shanmugapriya S
B.Tech – Artificial Intelligence and Data Science

