﻿# ANN2DL-Polimi

This repository contains code and notebooks for the Artificial Neural Networks and Deep Learning (ANN2DL) course at Polimi.

## Project Structure

### Project 1: Blood Cell Classification with Deep Learning

#### Introduction

This project focuses on classifying blood cells into one of eight distinct classes using 96x96 RGB images. The dataset included labeled blood cell images provided as NumPy arrays. The primary goal was to build a robust deep-learning model capable of accurate classification while addressing challenges such as overfitting, data imbalance, and generalization to unseen data.

#### Dataset Overview

- **Total Images:** 13,759
- **Image Dimensions:** 96x96x3 (RGB)
- **Classes:** 8 blood cell types
- **Key Challenges:**
  - Imbalanced classes
  - Significant overfitting during early experiments
  - Generalization due to dataset distribution differences

#### Methodology

##### Data Preprocessing

- Outlier detection and removal using the Isolation Forest algorithm.
- Addressed class imbalance via data augmentation and upsampling techniques.

##### Model Architectures Explored

- **EfficientNetB7:** Final choice due to robust augmentation capabilities.
- ResNet, MobileNetV2, and custom CNNs for baseline comparisons.

##### Optimization Techniques

- Advanced data augmentations (CutMix, MixUp, and RandomAug).
- Test-time augmentation (TTA) improved predictions by averaging results from augmented inputs.

##### Training Details

- **Loss Functions:** Categorical Cross-Entropy and Focal Loss.
- **Optimizers:** Adam and RMSProp.
- Callbacks for early stopping and learning rate adjustment.

#### Results

- **Final Model:** EfficientNetB7
- **Competition Performance:** Ranked 110/516 on [Codabench](https://www.codabench.org/competitions/4430/#/results-tab)
- **Key Metrics:**
  - Local Accuracy: 98.28%
  - Test Accuracy: 90%
- Recognized limitations in handling the immature granulocytes class due to biological and dataset constraints.

#### Conclusion

This project achieved high accuracy on unseen data by leveraging data augmentation and advanced architectures. Future work could explore ensembling negatively correlated models, use autoencoders features for classification or fine-tuning other architectures.

---

### Project 2: Semantic Segmentation of Martian Terrain

#### Introduction

This project tackled the semantic segmentation of 64x128 grayscale images of Martian terrain. The objective was to classify each pixel into one of several terrain classes. Pretrained models were disallowed, necessitating custom model designs.

#### Dataset Overview

- **Training Data:** 2,615 labeled images
- **Testing Data:** 10,022 images
- **Challenges:**
  - Small dataset size and limited resolution.
  - Highly imbalanced classes, with the background dominating.

#### Methodology

##### Data Preprocessing

- Removal of corrupted or irrelevant data.
- Data augmentation using Albumentations and CutMix for better class balance.

##### Model Architectures

- **Attention ResUNet:** Introduced attention gates and residual connections.
- **MultiResUNet:** Employed multi-scale feature extraction with residual paths.
- **MultiResUNet with Attention:** Combined both enhancements for superior results.

##### Training Details

- **Loss Function:** Sparse Categorical Cross-Entropy (excluding the background class).
- **Optimizer:** Adam with exponential decay learning rate.
- **Evaluation Metric:** Mean Intersection over Union (MIoU).

#### Results

- **Best-performing Model:** MultiResUNet with Attention
- **Competition Performance:** Ranked 50/197 on [Kaggle](https://www.kaggle.com/competitions/an-2-dl-2024-2025-homework-2)
- **Key Metrics:**
  - Kaggle MIoU: 68.344%
  - Local MIoU: 69.12%
- Ablation studies revealed significant improvements from attention mechanisms and class-wise augmentation.

## Conclusion
The project demonstrated the efficacy of advanced UNet architectures enhanced with attention mechanisms for pixel-wise classification. Future improvements could include super-resolution techniques and transformer-based architectures for better segmentation.

The final grade for these projects was **10/10**.

