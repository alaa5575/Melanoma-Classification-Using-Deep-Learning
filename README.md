# Melanoma Classification Using Deep Learning

## Project Overview

This project investigates binary skin lesion classification using deep learning, aiming to distinguish between **Melanoma and Nevus** using dermoscopic images.

Two convolutional neural network architectures, **ResNet-50** and **EfficientNet-B0**, were implemented and compared using transfer learning and fine-tuning. The project also includes model evaluation, computational efficiency analysis, error analysis, and **Grad-CAM explainability** to visualize image regions contributing to model predictions.

---

## Dataset

**Dataset:** HAM10000 – Human Against Machine with 10000 training images

The dataset contains dermoscopic images of skin lesions. For this project, the dataset was filtered to include two diagnostic categories:

- **Nevus (nv)** — Label 0
- **Melanoma (mel)** — Label 1

Images were linked to their corresponding metadata using image IDs, and lesion IDs were used to group related images.

---

## Project Workflow

### 1. Data Preparation & Exploratory Data Analysis

- Dataset exploration and metadata analysis
- Image path mapping and data cleaning
- Filtering the dataset to Nevus and Melanoma categories
- Class distribution analysis
- Identification of class imbalance

### 2. Data Splitting

The dataset was divided into:

- Training set: 70%
- Validation set: 15%
- Test set: 15%

**Group-based splitting using `lesion_id`** was implemented to prevent images belonging to the same lesion from appearing in different subsets, helping reduce data leakage.

### 3. Preprocessing & Data Augmentation

- Image resizing to 224 × 224 pixels
- Image normalization using ImageNet statistics
- Random horizontal and vertical flipping
- Random rotation
- Random resized cropping
- Brightness and contrast augmentation

### 4. Class Imbalance Handling

- Analysis of class distribution
- Class weighting
- Weighted Cross-Entropy Loss

### 5. Model Development

Two pretrained deep learning architectures were implemented:

#### ResNet-50

- Transfer learning using pretrained ImageNet weights
- Initial training of the classification head
- Fine-tuning of the deeper feature extraction layers
- Model evaluation on the test set

#### EfficientNet-B0

- Transfer learning using pretrained ImageNet weights
- Training and fine-tuning
- Model evaluation on the test set

### 6. Model Evaluation & Comparison

Models were evaluated using:

- Accuracy
- Precision
- Sensitivity (Recall)
- Specificity
- F1-score
- ROC-AUC
- Confusion Matrix
- ROC Curve

Additional computational comparisons included:

- Number of model parameters
- Model size
- Training time
- Inference time
- Images processed per second

### 7. Error Analysis

The project includes analysis and visualization of:

- False positive predictions
- False negative predictions
- Correctly classified examples
- Prediction confidence

This helps examine model behavior beyond aggregate performance metrics.

### 8. Explainable AI — Grad-CAM

Grad-CAM (Gradient-weighted Class Activation Mapping) was implemented using ResNet-50 to visualize image regions contributing to the model's predictions.

The explainability analysis includes:

- Target layer selection
- Grad-CAM heatmap generation
- Heatmap overlay on the original image
- Visualization of predictions on selected test images

This provides a visual perspective on the regions influencing model predictions.

---

## Results

### Test Set Performance

| Metric | ResNet-50 | EfficientNet-B0 |
|---|---:|---:|
| Accuracy | 88.41% | 79.53% |
| Precision | 52.58% | 36.00% |
| Sensitivity (Recall) | 77.78% | 81.25% |
| Specificity | 89.94% | 79.28% |
| F1-score | 62.75% | 49.89% |
| ROC-AUC | 92.53% | 89.17% |

### Computational Comparison

| Metric | ResNet-50 | EfficientNet-B0 |
|---|---:|---:|
| Total Parameters | 23.51M | 4.01M |
| Model Size | 90.00 MB | 15.58 MB |
| Average Inference Time | 5.29 ms/image | 5.19 ms/image |
| Throughput | 188.89 images/sec | 192.70 images/sec |

ResNet-50 achieved higher overall classification performance across most evaluation metrics, while EfficientNet-B0 demonstrated a substantially smaller model size and slightly faster inference performance in the recorded evaluation.

---

## Technologies & Libraries

- Python
- PyTorch
- Torchvision
- Scikit-learn
- Pandas
- NumPy
- Matplotlib
- OpenCV
- PIL
- Grad-CAM

---

## Repository Contents

- `Melanoma_Classification.ipynb` — Main notebook containing data preprocessing, model development, training, fine-tuning, evaluation, model comparison, error analysis, and Grad-CAM explainability.

---

## Disclaimer

This project was developed for educational and research purposes. It is not intended to replace professional dermatological evaluation, clinical diagnosis, or medical decision-making.

---

**Author:** Alaa Nasr  
Dentist | MSc Student in Artificial Intelligence in Healthcare
