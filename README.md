# Automated Tomato Plant Disease Classification: Custom CNN vs. VGG16 Transfer Learning

## Project Overview
Tomato cultivation is a vital component of Kenya's agricultural sector, yet crop yields are consistently threatened by plant diseases that cause significant economic losses. Traditional visual inspection for disease diagnosis is often slow, subjective, and requires expertise. 

This project addresses this challenge by developing and evaluating deep learning models for automated disease classification from leaf images. The goal is to provide a proof-of-concept for a low-cost, scalable, and readily available diagnostic tool that empowers small-scale farmers to make informed decisions about disease control measures.

## Key Features
* **Dataset**: Utilizes the "Tomato Disease Multiple Sources" dataset, a diverse collection of over 20,000 images, including data from laboratory settings and real-world field conditions.
* **Classification Scope**: Categorizes images into 11 distinct classes, covering 10 common diseases (e.g., Early Blight, Late Blight, Tomato Yellow Leaf Curl Virus) and one healthy category.
* **Comparative Analysis**: Establishes a performance baseline using a custom-built **Convolutional Neural Network (CNN)** and compares it against a more advanced **VGG16 Transfer Learning** model.
* **Agricultural Impact**: Lays the groundwork for deploying lightweight, offline models on mobile applications to support Kenyan farmers in precision agriculture.

## Methodology
The experiments were built using the **TensorFlow** framework with the **Keras API** and conducted in a **Google Colab** environment utilizing an **NVIDIA T4 GPU**.

### 1. Data Preprocessing & Augmentation
* All images were resized to a uniform dimension of **224x224 pixels**.
* Pixel values were normalized to a floating-point range of **0 to 1**.
* To prevent overfitting and mitigate class imbalance, **Data Augmentation** (up to 40° rotation, 20% width/height shifts, 0.2 shear intensity, 20% zoom, and horizontal flips) was applied to the training set.

### 2. Model Architectures
* **Model 1 (Custom CNN)**: A sequential model comprising three main convolutional blocks (64, 128, and 256 filters) followed by a dense classifier head. This model contained a total of 44 million trainable parameters.
* **Model 2 (VGG16 Transfer Learning)**: Leveraged the pre-trained VGG16 architecture (ImageNet weights). The convolutional base was frozen, and a new custom classifier head (1024 units) was added. This reduced the trainable parameters to 25 million, significantly improving computational efficiency.

## Results & Evaluation
The experimental results demonstrated a stark performance difference, conclusively showing that the transfer learning approach is highly effective and efficient for this agricultural computer vision task.

| Metric | Model 1 (Custom CNN) | Model 2 (VGG16) |
| :--- | :---: | :---: |
| **Validation Accuracy** | 84.65% (unstable) | 77.15% (stable) |
| **Weighted Avg. Precision** | 90.00% | 88.50% |
| **Weighted Avg. Recall** | 80.00% | 68.39% |
| **Weighted Avg. F1-Score** | 83.00% | 77.00% |

> **Analysis**: While the Custom CNN exhibited higher peak accuracy metrics, its learning curves showed significant instability and signs of overfitting—essentially memorizing the training images. In contrast, the VGG16 model showed a stable and consistent learning progression, achieving a superior validation accuracy of ~78% even with a limited training duration of only 15 epochs. 

## How to Run

### Prerequisites
* A Google Account to access **Google Colab**.
* Python 3.x environment.
* Required Libraries: `tensorflow`, `keras`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`.

### Steps
1. **Clone the Repository**:
   ```bash
   git clone [https://github.com/your-username/agri-vision-tomato-health.git](https://github.com/your-username/agri-vision-tomato-health.git)
1. **Open in Colab**:
Navigate to the notebooks/ directory and upload the .ipynb file to your Google Colab environment.

2. **Dataset Setup**:
Download the Tomato Disease Multiple Sources Dataset from Kaggle. Upload the dataset to your Google Drive and mount your drive within the Colab notebook.

3. **Configure GPU**:
In Colab, navigate to Runtime > Change runtime type and select T4 GPU as the hardware accelerator.

4. **Execute**:
Run the notebook cells sequentially to execute data preprocessing, model training (set to 15 epochs), and performance evaluation.

## Future Work
Extended Training & Early Stopping: Retrain the VGG16 model for 50-100 epochs with an Early Stopping callback to reach peak convergence.

1. **Fine-Tuning**: Unfreeze the final convolutional layers of the pre-trained VGG16 base and retrain with a very low learning rate to adapt the feature detectors specifically to tomato leaves.

2. **Mobile Deployment**: Convert the optimized model into a lightweight format (e.g., TensorFlow Lite) and deploy it into a mobile application for real-time, offline diagnoses.

3. **Dataset Enhancement**: Expand the dataset with images captured directly on local Kenyan farms to expose the model to real-world variables like variable lighting, shadows, and different soil types.

Author: Hammilton Nyamache

Department: Electrical and Electronic Engineering

Institution: Dedan Kimathi University of Technology
