# 🤖 Fall Detection using YOLOv8 Pose + SVM (Google Colab Project)

This repository presents a human **fall detection system** built using **YOLOv8 pose estimation** and a **Support Vector Machine (SVM)** classifier. The model is trained and tested using **Google Colab**, with pose keypoints extracted from a labeled image dataset of humans in fall and non-fall scenarios.

---

## 📌 Project Overview

- 🧍 Extracts human keypoints from images using **YOLOv8-pose**
- 🧠 Trains an **SVM classifier** on normalized keypoints to detect:
  - `Fall` (label: `0`)
  - `Not Fall` (label: `1`)
- 🖼️ Predicts on new images/videos
- 📊 Visualizes the output and saves processed results

---

## 📁 Repository Structure

```text
fall-detection-colab/
├── notebook/
│   └── fall_detection_colab.ipynb       ← Colab notebook (full pipeline)
├── models/
│   └── fall_detector_classifier.pkl      ← Trained SVM classifier
├── samples/
│   ├── sample_input_1.mp4                ← Input test video
│   ├── output_1.mp4                      ← Video with fall prediction overlays
│   ├── sample_input_2.mp4                ← Input test video
│   └── output_2.mp4                      ← Video with fall prediction overlays
├── dataset/
│   └── README.md                         ← Instructions to download training dataset
└── README.md                             ← This file
```

### 🏷️ Labeling Convention

- Images with `fall` in their filenames are treated as class `0`
- Images with `notfall` in their filenames are treated as class `1`

Keypoint extraction and labeling logic is implemented inside the notebook.

👉 See [`dataset/README.md`](dataset/README.md) for details of dataset used for training the classifier.

---

## 🔍 How It Works

### 🔹 1. Keypoint Extraction

- The YOLOv8 pose model (`yolov8n-pose.pt`) is used to extract 17 body keypoints (x, y) for each person in the image.

### 🔹 2. Feature Normalization

- Extracted keypoints are normalized to account for person size and position.

### 🔹 3. Classification

- A **Support Vector Machine (SVM)** is trained using the normalized keypoints to classify each pose as a `Fall` or `Not Fall`.

### 🔹 4. Inference

- Predictions are run on test images/videos using the trained classifier.
- Fall and Not Fall cases are highlighted visually.

---

## 📸 Sample Results

### 🖼️ Image Output  
Shown in the colab notebook

### 🎥 Video Output  
🧍 Fall detected in video frame-by-frame  
📁 [`output_1.mp4`](samples/output_1.mp4)

### 🎥 Video Output  
🧍 Fall detected in video frame-by-frame  
📷 [`output_2.jpg`](samples/output_2.jpg)
