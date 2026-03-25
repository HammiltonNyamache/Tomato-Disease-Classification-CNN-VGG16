# Automated Tomato Plant Disease Classification: Custom CNN vs. VGG16 Transfer Learning

## Project Overview
[cite_start]Tomato cultivation is a vital component of Kenya's agricultural sector, yet yields are threatened by diseases that cause significant economic losses[cite: 9, 74]. [cite_start]This project addresses this challenge by developing deep learning models for automated disease classification from leaf images[cite: 11]. 

[cite_start]The goal is to provide a proof-of-concept for a low-cost, scalable diagnostic tool that empowers small-scale farmers to protect their crops[cite: 80, 103].

## Key Features
* [cite_start]**Dataset**: Utilizes a comprehensive collection of over 20,000 images, including data from the Plant Village repository[cite: 108, 112].
* [cite_start]**Classification**: Categorized into 11 distinct classes, including 10 common diseases and one healthy category[cite: 114, 135].
* [cite_start]**Comparative Analysis**: Evaluates a custom-built **Convolutional Neural Network (CNN)** against a **VGG16 Transfer Learning** model[cite: 12].
* [cite_start]**Impact**: Focuses on creating lightweight models suitable for future deployment on mobile applications for Kenyan farmers[cite: 149, 150].

## Methodology
[cite_start]The experiments were conducted in a **Google Colab** environment utilizing an **NVIDIA T4 GPU**.

### 1. Data Preprocessing & Augmentation
* [cite_start]Images were resized to a uniform dimension of **224x224 pixels**[cite: 155].
* [cite_start]Pixel values were normalized to a floating-point range of **0 to 1**[cite: 156].
* [cite_start]**Data Augmentation** techniques (rotation, width/height shifts, shear, zoom, and horizontal flips) were used to mitigate class imbalance and prevent overfitting[cite: 157, 159].

### 2. Model Architectures
* [cite_start]**Model 1 (Custom CNN)**: A sequential model with three main convolutional blocks (64, 128, and 256 filters)[cite: 171, 172]. [cite_start]It contained a total of 44 million trainable parameters[cite: 176].
* [cite_start]**Model 2 (VGG16 Transfer Learning)**: Leveraged the pre-trained VGG16 architecture (ImageNet weights) with a frozen convolutional base[cite: 179, 181]. [cite_start]Only the 25 million parameters in the newly added custom classifier head were trainable[cite: 184].

## Results & Evaluation
[cite_start]The study conclusively demonstrated that the transfer learning approach is superior for this specialized agricultural task[cite: 17, 276].

| Metric | Model 1 (Custom CNN) | Model 2 (VGG16) |
| :--- | :---: | :---: |
| **Validation Accuracy** | 84.65% (unstable) | 77.15% (stable) |
| **Weighted Avg. Precision** | 90.00% | 88.50% |
| **Weighted Avg. Recall** | 80.00% | 68.39% |
| **Weighted Avg. F1-Score** | 83.00% | 77.00% |

[cite_start]*Data sourced from project performance summary.*

> [cite_start]**Analysis**: While Model 1 showed high peak accuracy, its learning curves exhibited classic signs of instability and overfitting[cite: 15, 201]. [cite_start]Model 2 showed a much healthier, stable learning process and achieved higher confidence in qualitative tests[cite: 206, 242].

## How to Run

### Prerequisites
* A Google Account to access **Google Colab**.
* Python 3.x environment.
* Libraries: `tensorflow`, `keras`, `numpy`, `matplotlib`.

### Steps
1. **Clone the Repository**:
   ```bash
   git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
