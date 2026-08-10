readme_content = """# 👁️ Ocular Disease Detection using Computer Vision & Deep Learning

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)](https://pytorch.org/)
[![Roboflow](https://img.shields.io/badge/Roboflow-Dataset-purple)](https://roboflow.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

An automated deep learning framework for early detection and multi-class classification of ocular diseases from retinal fundus imagery. Built with **PyTorch** and transfer learning architectures, this system provides fast, accurate diagnostic assistance for clinical and remote healthcare settings.

---

## 💡 Overview & Motivation

Early detection of retinal pathologies is critical to preventing irreversible vision loss. Traditional diagnostic procedures often require specialized medical equipment and expert ophthalmologists, making screening expensive and inaccessible in remote or underserved areas.

This project implements a computer vision pipeline that automatically analyzes retinal images to classify ocular conditions. Developed in collaboration with clinical ophthalmology expertise for dataset annotation and validation, the system serves as a reliable decision-support tool for healthcare professionals and clinics.

---

## ✨ Key Features

- **Multi-Class Classification**: Identifies 5 distinct ocular conditions with high precision.
- **Expert-Validated Dataset**: Data manually reviewed and re-annotated alongside a specialist ophthalmologist.
- **Transfer Learning**: Evaluated multiple state-of-the-art CNN architectures (**ResNet-50**, **VGG16**, **MobileNet**).
- **Comprehensive Evaluation**: Metrics tailored for medical diagnostics (**Precision**, **Recall**, **F1-Score**, and **Confusion Matrices**).
- **User-Friendly Interface**: Desktop/web demo allowing doctors and users to upload retinal scans (`.jpg`, `.png`) for instant prediction.

---

## 🩺 Supported Pathologies

1. **Normal Eye**: Healthy retinal structure without lesions or optic nerve degradation.
2. **Cataract**: Opacification of the eye lens affecting visual clarity.
3. **Glaucoma**: Optic nerve damage often linked to increased intraocular pressure.
4. **Diabetic Retinopathy**: Vascular damage caused by diabetes (hemorrhages, aneurysms, cotton wool spots).
5. **Retinal Disease**: Other generalized pathological manifestations across the retina.

---

## 📊 Dataset & Preprocessing

The dataset was sourced from high-quality retinal repositories (including **Kaggle / EyePACS**) and curated using **Roboflow**.

### Data Splits
- **Raw Dataset (7,291 images)**:
  - **Train Set**: 5,102 images (70%)
  - **Validation Set**: 1,459 images (20%)
  - **Test Set**: 730 images (10%)

- **Augmented Dataset (17,469 images)**:
  - Preprocessing: Resize to $128 \\times 128$
  - Augmentations: Grayscale conversion (15%), Hue shift ($-81^\\circ$ to $+81^\\circ$), 3x training multiplier.
  - *Note*: Comparative experiments revealed that aggressive color augmentations (e.g., hue/grayscale) decreased diagnostic performance (94.1% vs 96.6% raw accuracy) due to the importance of natural color cues in retinal lesions.

---

## ⚙️ Model Architectures & Experiments

Several pre-trained deep learning architectures were trained using **PyTorch** with fine-tuning strategies:

| Model Architecture | Strengths | Validation Accuracy | Test Accuracy | Selected |
| :--- | :--- | :---: | :---: | :---: |
| **ResNet-50** | Deep residual connections, best generalization, balanced precision/recall | **91.5%** | **91.5%** | ✅ **Selected** |
| **VGG16** | Feature extraction depth, simple sequential structure | 90.5% | 90.1% | ❌ |
| **MobileNet** | Lightweight & fast, ideal for edge/mobile devices | 88.3% | — | ❌ |

### Training Hyperparameters (Selected ResNet-50 Model)
- **Framework**: PyTorch
- **Strategy**: Transfer Learning (Feature Extractor frozen, custom Fully Connected head)
- **Loss Function**: Cross-Entropy Loss
- **Optimizer**: Adam (Learning rate = $1 \\times 10^{-4}$)
- **Batch Size**: 32
- **Epochs**: 25 - 100

---

## 📈 Performance & Results

For medical applications, high **Recall** is critical to avoid missing pathological cases (false negatives), while **Precision** reduces unnecessary referrals.

- **ResNet-50 Test Set Evaluation**:
  - **Overall Accuracy**: **~91.5%**
  - **Diabetic Retinopathy**: Precision **0.99**, Recall **0.97**, F1-Score **0.98**
  - **Cataract**: Precision **0.92**, Recall **0.94**, F1-Score **0.93**
  - **Retina Disease**: Precision **0.95**, Recall **0.99**, F1-Score **0.97**
  - **Normal Eye**: Precision **0.87**, Recall **0.95**, F1-Score **0.91**

---

## 🛠️ Installation & Usage

### Prerequisites
- Python 3.8+
- PyTorch & Torchvision
- NumPy, Pandas, Matplotlib, Scikit-learn, OpenCV, Pillow

### 1. Clone the Repository
```bash
git clone [https://github.com/your-username/ocular-disease-detection.git](https://github.com/your-username/ocular-disease-detection.git)
cd ocular-disease-detection
