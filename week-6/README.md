# 🖼️ Image Denoising using CNN Autoencoders

### Understanding Image Reconstruction, Feature Learning, and Deep Denoising Networks

This project features a comprehensive Jupyter Notebook focused on designing, training, and evaluating multiple convolutional autoencoder architectures for image denoising using the MNIST handwritten digit dataset.

The notebook explores how neural networks learn compact latent representations of images and reconstruct clean images from noisy inputs. Multiple architectural improvements including Batch Normalization, Deep CNNs, Residual Connections, and Bottleneck Representations are investigated and compared using quantitative image-quality metrics.

The project serves as a practical introduction to image restoration, representation learning, and deep autoencoder architectures used in modern computer vision systems.

---

# 🎯 Learning Goals

* Understand the complete image denoising pipeline using deep learning.
* Learn how autoencoders compress and reconstruct visual information.
* Explore the effect of latent-space representations on reconstruction quality.
* Compare shallow and deep convolutional autoencoder architectures.
* Understand the role of Batch Normalization in stabilizing training.
* Learn how residual connections improve gradient flow and feature preservation.
* Investigate the impact of bottleneck compression on reconstruction performance.
* Evaluate image quality using MSE, PSNR, and SSIM metrics.
* Perform hyperparameter tuning to identify optimal model configurations.

---

# 📦 Dataset & Data Preparation

The project uses the MNIST handwritten digit dataset.

### Dataset Characteristics

* Training Images: 60,000
* Testing Images: 10,000
* Image Resolution: 28 × 28
* Grayscale Images
* Pixel Range Normalized to [0,1]

### Noise Generation

To simulate corrupted images, Gaussian noise is added during training and evaluation.

Noise Levels Explored:

* 0.1
* 0.2
* 0.3

The model receives noisy images as input and learns to reconstruct the original clean images.

---

# 🚀 Project Workflow & Notebook Highlights

## 1. Data Loading & Visualization

The notebook begins by:

* Loading the MNIST dataset
* Applying normalization
* Creating training, validation, and testing splits
* Visualizing clean and noisy images

This provides an understanding of the denoising task before model training.

---

## 2. Baseline CNN Autoencoder

A simple convolutional autoencoder is implemented as the initial benchmark model.

### Architecture

Encoder:

* Convolution Layer
* ReLU Activation
* Max Pooling

Decoder:

* Transposed Convolution Layers
* Sigmoid Output Layer

### Purpose

Establish a performance baseline against which all future architectural improvements can be measured.

---

## 3. CNN Autoencoder with Batch Normalization

Batch Normalization layers are introduced after convolution operations.

### Benefits

* Faster convergence
* Improved gradient flow
* More stable training
* Reduced internal covariate shift

### Observation

The addition of Batch Normalization significantly reduced reconstruction error compared to the baseline architecture.

---

## 4. Deep CNN + BatchNorm Autoencoder

The network depth is increased by introducing additional convolutional feature extraction layers.

### Features

* More convolutional filters
* Larger feature hierarchy
* Deeper latent representation

### Purpose

Evaluate whether increased model capacity improves image reconstruction quality.

---

## 5. Residual Autoencoder

Residual learning is incorporated using skip connections inspired by ResNet architectures.

### Residual Block

Each residual block learns:

F(x) + x

instead of learning the full mapping directly.

### Advantages

* Improved gradient propagation
* Easier optimization of deep networks
* Better feature preservation
* Reduced degradation problem

### Outcome

The Residual Autoencoder achieved the best overall denoising performance among all tested architectures.

---

## 6. True Bottleneck Autoencoder

A fully connected bottleneck is introduced between encoder and decoder.

### Workflow

Feature Maps

→ Flatten

→ Dense Bottleneck Layer

→ Dense Expansion Layer

→ Decoder

### Purpose

Force the network to learn a highly compressed latent representation.

### Observation

Although compression was achieved successfully, excessive information reduction negatively impacted reconstruction quality compared to the Residual Autoencoder.

---

## 7. Hyperparameter Tuning

After identifying the Residual Autoencoder as the strongest architecture, extensive hyperparameter tuning was performed.

### Learning Rates Tested

* 0.0001
* 0.0005
* 0.001

### Weight Decay Values Tested

* 0
* 1e-5
* 1e-4

### Noise Levels Tested

* 0.1
* 0.2
* 0.3

The best configuration was selected based on reconstruction quality metrics.

---

## 8. Model Evaluation

Three complementary metrics were used to evaluate reconstruction performance.

### Mean Squared Error (MSE)

Measures pixel-wise reconstruction error.

Lower values indicate better reconstruction.

### Peak Signal-to-Noise Ratio (PSNR)

Measures reconstruction quality in decibels.

Higher values indicate better image quality.

### Structural Similarity Index (SSIM)

Measures perceptual similarity between original and reconstructed images.

Values closer to 1 indicate better structural preservation.

---

# 📊 Summary of Results

| Experiment         | Architecture                | Parameters | Noise Level | Learning Rate | MSE      | PSNR  | SSIM   |
| ------------------ | --------------------------- | ---------- | ----------- | ------------- | -------- | ----- | ------ |
| Baseline CNN AE    | CNN Autoencoder             | 27,169     | 0.2         | 0.001         | 0.003983 | 24.21 | 0.9593 |
| BatchNorm CNN AE   | CNN + BatchNorm             | 27,425     | 0.2         | 0.001         | 0.003031 | 25.49 | 0.9531 |
| Deep CNN BN AE     | Deep CNN + BatchNorm        | 282,497    | 0.2         | 0.0005        | 0.003033 | 25.52 | 0.9568 |
| Residual AE        | Residual Autoencoder        | 1,059,329  | 0.2         | 0.0005        | 0.002671 | 26.03 | 0.9631 |
| True Bottleneck AE | True Bottleneck Autoencoder | 578,689    | 0.2         | 0.0005        | 0.003336 | 25.15 | 0.9550 |

---

# 🔍 Key Observations

### Architectural Comparison

* Batch Normalization significantly improved performance over the baseline model.
* Increasing network depth alone produced only marginal improvements.
* Residual learning delivered the strongest reconstruction quality.
* The bottleneck architecture demonstrated that aggressive compression can lead to information loss.
* Residual connections proved more effective than simply increasing depth or adding latent compression.

### Hyperparameter Tuning

* Learning Rate = 0.001 achieved the best convergence.
* Weight Decay provided no measurable benefit for this task.
* Higher noise levels increased reconstruction difficulty and reduced PSNR and SSIM.
* Noise Level 0.2 provided a balanced denoising challenge while maintaining realistic reconstruction performance.

### Overall Conclusion

The Residual Autoencoder emerged as the most effective architecture, achieving the lowest reconstruction error and highest perceptual image quality. The results demonstrate that residual learning significantly improves denoising performance by enabling deeper feature extraction while preserving important image structures.

---

# 🧠 Mathematical Concepts Covered

## Autoencoder Objective

The network learns a mapping:

x → Encoder → Latent Space → Decoder → x̂

where:

* x = Original image
* x̂ = Reconstructed image

Training minimizes reconstruction loss.

---

## Mean Squared Error

MSE = (1/N) Σ(x − x̂)²

Measures pixel-wise reconstruction error.

---

## Peak Signal-to-Noise Ratio

PSNR = 10 log₁₀(MAX² / MSE)

Higher PSNR indicates better reconstruction quality.

---

## Structural Similarity Index

SSIM evaluates:

* Luminance similarity
* Contrast similarity
* Structural similarity

It correlates better with human visual perception than MSE alone.

---

# 🛠️ Technologies Used

* Python
* PyTorch
* NumPy
* Pandas
* Matplotlib
* Scikit-Image
* TorchInfo
* Jupyter Notebook

---

# 🛠️ Prerequisites & Installation

Clone the repository:

```bash
git clone <repository-url>
cd <project-folder>
```

Install dependencies:

```bash
pip install torch torchvision numpy pandas matplotlib scikit-image torchinfo
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open the notebook and run all cells sequentially.

---

# ✅ Conclusion

This project demonstrates how convolutional autoencoders can learn meaningful latent representations for image denoising. Through systematic experimentation with Batch Normalization, deeper networks, residual learning, bottleneck compression, and hyperparameter tuning, the study highlights the importance of architectural design choices in reconstruction-based computer vision tasks. Among all evaluated models, the Residual Autoencoder consistently achieved the best balance between reconstruction accuracy, perceptual quality, and training stability, making it the strongest solution for the MNIST denoising task.
