# 📘 CIFAR-10 Image Classification Learning Project
## Comparing Deep Learning Architectures: ANN vs. CNN

This project features a hands-on Jupyter Notebook (`week4_Mehar_Bhanwra.ipynb`) designed as an educational deep learning pipeline. It provides students and beginners with a clear blueprint for building, tuning, and comparing **Artificial Neural Networks (ANN)** and **Convolutional Neural Networks (CNN)** using the classic **CIFAR-10** dataset.

## 🎯 Learning Goals
* Understand the complete deep learning lifecycle: from data preprocessing and augmentation to model evaluation.
* Understand the structural limitations of fully connected layers (MLPs/ANNs) when handling raw image arrays.
* Grasp the mathematical advantages of CNNs (local connectivity, weight sharing, and spatial invariance).
* Learn how advanced tuning strategies (Batch Normalization, Dropout, Data Augmentation, and Early Stopping) prevent overfitting and stabilize training.

---

## 📦 Dataset: CIFAR-10
The CIFAR-10 dataset consists of **60,000 32x32 color images** split across 10 classes (50,000 for training, 10,000 for testing):
* Airplane, Automobile, Bird, Cat, Deer, Dog, Frog, Horse, Ship, Truck

---

## 🚀 Project Workflow & Notebook Highlights

### 1. Preprocessing & Normalization
* Scales pixel values from `0–255` down to a unified `0–1` float range to prevent exploding/vanishing gradients and speed up optimizer convergence.
* Flattens 3D color images into 1D vectors ($32 \times 32 \times 3 = 3,072$ inputs) strictly for the ANN baseline architectures.

### 2. Base & Deep ANN Baseline Models
* Explores fully connected layers to establish a performance benchmark.
* Demonstrates why flattening images destroys critical localized structural information (spatial coherence), leading to low model accuracy (~41%).

### 3. Base & Feature-Tuned CNNs
* Feeds raw 3D spatial grids directly into the network.
* Uses `Conv2D` layers to extract structural primitives (edges, shapes) and `MaxPooling2D` to downsample feature representations while slashing parameter overhead.
* Scales filter channel stacks ($32 \rightarrow 64 \rightarrow 128$) to establish a deep hierarchical feature extractor, boosting testing accuracy dramatically to ~71%.

### 4. Advanced Regularization & Strategies
* **Data Augmentation:** Implements random horizontal flips, rotations, and zooms to enforce transformation invariance and stop the model from memorizing fixed pixel alignments.
* **Batch Normalization (BN):** Stabilizes internal covariate shifts across batches, dramatically improving training speeds.
* **Early Stopping Callback:** Dynamically tracks validation trajectories, automatically halting execution when performance plateaus and rolling back weights to the optimal checkpoint.
* **Confusion Matrix:** Provides deep error diagnostics to visually map out inter-class confusion (e.g., *cats vs. dogs*).

---

## 📊 Summary of Results

| Architecture | Model Configuration / Training Strategy | Test Accuracy | Learning Characteristics |
| :--- | :--- | :---: | :--- |
| **ANN** | Base Flattened Vector Input ($3,072$ inputs) | **~41.4%** | Stalls early; expanding model depth causes an parameter explosion without resolving accuracy limitations. |
| **CNN** | Base 3-Layer Spatial Convolution ($32 \rightarrow 64 \rightarrow 128$) | **~71.1%** | Rapidly climbs; preserves geometric shapes, but shows a severe tendency to overfit past epoch 15. |
| **CNN** | Advanced Architecture with Data Augmentation & Batch Norm | **~70.8%** | Highly stable convergence; training and validation curves stay tightly locked, indicating excellent generalization. |

---

## 🛠️ Prerequisites & Installation

To run this notebook locally, ensure you have Python 3 installed along with the required deep learning dependencies.

1. **Clone the repository:**
```bash
   git clone https://github.com/meharbhanwra/celebal-excellence-internship-program-2026-mehar-bhanwra.git
   cd celebal-excellence-internship-program-2026-mehar-bhanwra/week-4
```
2. **Install the dependencies:**
```bash
   pip install tensorflow keras matplotlib numpy pandas jupyter
```
3. **Launch the Jupyter Notebook:**
```bash
   jupyter notebook week4_Mehar_Bhanwra.ipynb
```
