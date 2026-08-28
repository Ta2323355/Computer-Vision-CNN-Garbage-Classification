 CNN-Based Garbage Image Classification

A custom Convolutional Neural Network (CNN) built from scratch using PyTorch for multi-class garbage image classification. Two CNN architectures — plain and regularized — are designed, trained, compared, and evaluated on a real-world garbage dataset.

##  Objective

Design, train, and evaluate a custom CNN for **6-class garbage image classification**, covering the full deep learning pipeline from data loading to final model saving.

## 🗂️ Dataset

- **Dataset:** Garbage Classification Dataset
- **Classes (6):** `cardboard`, `glass`, `metal`, `paper`, `plastic`, `trash`
- **Split:** 70% Train | 15% Validation | 15% Test
- **Image Size:** 128 × 128

---

## 🔄 Pipeline Overview

Dataset Loading → EDA → Preprocessing & Augmentation
→ Model Design (Model A & B) → Training → Comparison
→ Evaluation → Confusion Matrix → Model Saving

## 🧠 Models

### Model A — Plain CNN
A baseline CNN with 4 convolutional blocks (no regularization):
```
Conv2d(3→32) → ReLU → MaxPool
Conv2d(32→64) → ReLU → MaxPool
Conv2d(64→128) → ReLU → MaxPool
Conv2d(128→256) → ReLU → MaxPool
Flatten → Linear(512) → ReLU → Linear(6)
```

### Model B — Regularized CNN
Same architecture as Model A but with **Batch Normalization** and **Dropout** added after each conv block to reduce overfitting.
## ⚙️ Training Configuration

| Hyperparameter | Value |
|---|---|
| Optimizer | Adam |
| Learning Rate | 0.001 |
| Weight Decay | 1e-4 |
| Loss Function | CrossEntropyLoss |
| Epochs | 15 |
| Batch Size | 32 |
| LR Scheduler | StepLR (step=5, γ=0.5) 

## 📊 Data Augmentation (Training Only)

- Random Horizontal Flip (p=0.5)
- Random Rotation (±15°)
- Color Jitter (brightness, contrast, saturation)
- Normalization: mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225]

## 📈 Results

| Model | Best Val Accuracy |
|---|---|
| Model A: Plain CNN | **71.24%** ✅ Selected |
| Model B: Regularized CNN | 62.80% |

### Final Test Performance (Model A — Plain CNN)

| Metric | Score |
|---|---|
| Test Accuracy | **73.95%** |
| Weighted Precision | 74.44% |
| Weighted Recall | 73.95% |
| Weighted F1-score | 73.73% |

---

## 🔍 Analysis

- **Model A outperformed Model B** on validation accuracy (71.24% vs 62.80%), suggesting that for this dataset size and training duration, the plain CNN generalized better.
- The regularized model may have required more epochs or different dropout rates to benefit from regularization.
- The confusion matrix showed strongest performance on **cardboard** and **metal**, while **trash** and **glass** had more misclassifications due to visual similarity with other categories.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python | Core language |
| PyTorch | Model building & training |
| torchvision | Dataset loading & transforms |
| torchinfo | Model summary |
| scikit-learn | Evaluation metrics |
| matplotlib / seaborn | Visualization |
| Google Colab | Training environment |

---

## 📁 Files

| File | Description |
|---|---|
| `CNN_22_49208_3.ipynb` | Full Jupyter Notebook |
| `best_garbage_classifier.pth` | Saved best model weights |


    
