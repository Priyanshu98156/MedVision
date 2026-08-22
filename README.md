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
```

---

## 🧰 Tech Stack

- **Primary Language:** Python
- **Deep Learning Framework:** TensorFlow / Keras
- **Computer Vision & Image Processing:** OpenCV, PIL (Pillow)
- **Data Manipulation & Scientific Computing:** NumPy, Pandas
- **Visualization:** Matplotlib, Seaborn, Plotly
- **Web Application Framework:** Streamlit
- **Evaluation & Metrics:** Scikit-learn

---

## 📂 Project Directory Structure

```text
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
```

---

## 🔬 Data Preprocessing & Augmentation

Raw MRI scans often contain non-brain artifacts (skull regions, background black space, labels). MedVision applies a standardized preprocessing pipeline:

- **Extreme Contour Cropping:** Finds the largest continuous contour in the thresholded grayscale image to isolate the brain region.
- **Resizing:** Converts input scans to a uniform dimension ($224 \times 224 \times 3$).
- **Normalization:** Scales pixel values from $[0, 255]$ to $[0, 1]$.
- **Data Augmentation:** Applies random rotations, horizontal/vertical flips, and zoom variations during training to generalize across scan orientations.

---

## 📊 Model Performance & Evaluation

The network was trained and evaluated on benchmark Brain Tumor MRI classification datasets:

- **Overall Accuracy:** >90% on validation and holdout test splits
- **Loss Function:** Categorical Cross-Entropy
- **Optimizer:** Adam (Adaptive Moment Estimation)
- **Diagnostic Metrics Tracked:** Precision, Recall, and F1-Score per class, alongside Confusion Matrix analysis for false negative minimization.

---

## 🚀 Getting Started

### Prerequisites
- Python 3.9 or higher
- Git
- Virtual environment manager (`venv` or `conda`)

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Priyanshu98156/MedVision.git
   cd MedVision
   ```

2. **Create and activate a virtual environment:**
   - **Linux / macOS:**
     ```bash
     python3 -m venv venv
     source venv/bin/activate
     ```
   - **Windows:**
     ```bash
     python -m venv venv
     venv\Scripts\activate
     ```

3. **Install dependencies:**
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```

### Running the Application

Launch the Streamlit web dashboard locally:
```bash
streamlit run app.py
```
Once started, navigate to `http://localhost:8501` in your browser.

---

## 🌐 Deployment

To deploy MedVision to Streamlit Community Cloud:

1. Push your code to your GitHub repository.
2. Sign in to Streamlit Community Cloud.
3. Select your repository (`Priyanshu98156/MedVision`), main branch, and specify `app.py` as the entry file.
4. Click **Deploy**.

---

## 🗺️ Roadmap

- [ ] Add Grad-CAM (Gradient-weighted Class Activation Mapping) heatmaps for visual explainability.
- [ ] Integrate multi-planar MRI scan support (Axial, Coronal, Sagittal).
- [ ] Implement DICOM (`.dcm`) image reading support for hospital PACS integration.
- [ ] Add PDF export functionality for generated diagnostic summaries.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the project.
2. Create your feature branch (`git checkout -b feature/NewFeature`).
3. Commit your changes (`git commit -m 'Add new feature'`).
4. Push to the branch (`git push origin feature/NewFeature`).
5. Open a Pull Request.

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 📬 Contact & Author

**Priyanshu Gupta**

- GitHub: [@Priyanshu98156](https://github.com/Priyanshu98156)
- LinkedIn: [Priyanshu Gupta](https://linkedin.com/in/priyanshu98156)
- Email: pgupta98156@gmail.com
