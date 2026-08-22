# MedVision — AI-Powered Brain Tumor Detection & MRI Classification

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg?logo=python&logoColor=white)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg?logo=tensorflow&logoColor=white)](https://www.tensorflow.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-App-FF4B4B.svg?logo=streamlit&logoColor=white)](https://streamlit.io/)
[![OpenCV](https://img.shields.io/badge/OpenCV-Computer%20Vision-5C3EE8.svg?logo=opencv&logoColor=white)](https://opencv.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

MedVision is a medical computer vision platform that detects and classifies brain tumors from magnetic resonance imaging (MRI) scans using Convolutional Neural Networks (CNNs). It provides a web-based diagnostic support interface built with Streamlit, enabling fast inference, confidence scoring, and visual verification for healthcare workflows.

---

## 📌 Table of Contents
- [Overview](#overview)
- [Key Features](#key-features)
- [Tumor Classification Classes](#tumor-classification-classes)
- [System Architecture](#system-architecture)
- [Tech Stack](#tech-stack)
- [Project Directory Structure](#project-directory-structure)
- [Data Preprocessing & Augmentation](#data-preprocessing--augmentation)
- [Model Performance & Evaluation](#model-performance--evaluation)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Running the Application](#running-the-application)
- [Deployment](#deployment)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## 🔍 Overview

Early diagnosis of brain tumors is essential for effective treatment planning. Interpreting MRI scans manually can be time-consuming and requires specialized radiological expertise. **MedVision** automates the preliminary screening process by preprocessing MRI inputs, running deep feature extraction via a trained CNN model, and outputting classification results with probabilistic confidence levels in real time.

---

## ✨ Key Features

- **Automated MRI Preprocessing:** Utilizes OpenCV for contour detection, brain tissue cropping, noise reduction, and intensity normalization.
- **Deep Feature Classification:** Employs a multi-layer Convolutional Neural Network with Dropout and Batch Normalization to mitigate overfitting.
- **Interactive Web Interface:** Streamlit-powered dashboard supporting drag-and-drop file uploads (JPG, PNG, JPEG).
- **Confidence Scoring & Diagnostics:** Displays class probabilities, predictions, and visualization diagnostics for clinical clarity.
- **Modular Codebase:** Clean separation between model definition, preprocessing utilities, and web interface logic.

---

## 🧠 Tumor Classification Classes

The model identifies and classifies brain MRI scans into four distinct categories:

| Class | Description |
| :--- | :--- |
| **Glioma** | Tumors originating in the glial cells of the brain and spinal cord. |
| **Meningioma** | Tumors arising from the meninges (membranes surrounding brain/spinal cord). |
| **Pituitary Tumor** | Abnormal growths that develop in the pituitary gland. |
| **No Tumor** | Normal brain MRI scans without detected abnormalities. |

---

## 🏗️ System Architecture

```text
[MRI Scan Input]
       │
       ▼
[Image Preprocessing Pipeline] (OpenCV: Extreme contour crop, Resize 224x224, Normalize [0, 1])
       │
       ▼
[CNN Feature Extractor] (Conv2D + MaxPooling + Batch Normalization + ReLU)
       │
       ▼
[Classification Head] (Flatten + Dense Layers + Dropout Regularization)
       │
       ▼
[Softmax Output] ──► [Predicted Class & Probability Distribution]
       │
       ▼
[Streamlit Interface] ──► [Real-Time Visual Diagnostics & Report]

🧰 Tech Stack
Primary Language: Python

Deep Learning Framework: TensorFlow / Keras

Computer Vision & Image Processing: OpenCV, PIL (Pillow)

Data Manipulation & Scientific Computing: NumPy, Pandas

Visualization: Matplotlib, Seaborn, Plotly

Web Application Framework: Streamlit

Evaluation & Metrics: Scikit-learn

📂 Project Directory Structure

MedVision/
├── data/
│   ├── raw/                   # Raw MRI image datasets
│   └── processed/             # Preprocessed & augmented image arrays
├── models/
│   ├── cnn_tumor_model.h5     # Serialized trained model weights
│   └── model_architecture.json# Model configuration details
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_data_preprocessing.ipynb
│   └── 03_model_training_evaluation.ipynb
├── src/
│   ├── __init__.py
│   ├── preprocess.py          # OpenCV cropping & scaling utilities
│   ├── predict.py             # Model inference & prediction logic
│   └── utils.py               # Helper functions & visualization tools
├── app.py                     # Streamlit web application entry point
├── requirements.txt           # Python package dependencies
├── .gitignore                 # Git ignore configuration
├── LICENSE                    # Project license (MIT)
└── README.md                  # Project documentation
