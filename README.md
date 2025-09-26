# MCD: Generalized Deepfake Detection Using Multi-Scale and Cross-Domain Fusion

If there is something wrong or you have any questions, please feel free to tell me.

Email: isslimeng@gmail.com

---

## Introduction

This study addresses the challenge of generalized deepfake detection by proposing the **Multi-scale and Cross-domain Fusion (MCD) framework**. Our framework is designed to be robust and adaptable to various forgery types by integrating features from both spatial and frequency domains across multiple scales.

---

## Key Contributions

* **Multi-scale Strategy:** Captures local inconsistencies in forged images at different scales.
* **Multi-domain Fusion:** Integrates information from both spatial and frequency domains at the channel level for richer feature representations.
* **Frequency-aware Domain Features:** Used as auxiliary inputs to improve model performance on images with diverse compression techniques.
* **Data Augmentation:** Employs both in-domain and cross-domain strategies to enhance robustness and prevent overfitting.
* **Cross-domain Attention Mechanism:** Emphasizes regions with forgery traces for improved detection accuracy.
* **Spatial Frequency Domain Fusion (SFDF):** A novel module that combines spatial and frequency information for superior feature representation.

<img width="3913" height="2206" alt="fig2" src="https://github.com/user-attachments/assets/a49ead00-47bc-4757-8cc6-5f04ea078cc2" />

---

## Training Details

Our experiments were conducted using the **PyTorch framework** on **Nvidia 3090 GPUs**. All images were cropped using Dlib, scaled to $224 \times 224$ pixels, and augmented with in-domain and cross-domain strategies.

### Model and Configuration

* **Feature Extractor:** We used an **EViT-based framework** with an **EfficientNet-B0** as the local feature extractor and a pre-trained **ViT-B/16** for the Vision Transformer component. Each branch of the MCD architecture operates independently.
* **Training Configuration:** We trained the model for up to **150 epochs** with a **batch size of 32**. We used an early stopping strategy, the **AdaBelief optimizer** (learning rate: $0.0001$), and a weight decay of $1 \times 10^{-8}$.
* **Loss Function:** The weighting factors for our loss function were empirically set to $\alpha=8$, $\beta=2$, and the channel reduction ratio $r=4$. For each video, 32 frames were extracted for training and testing.
```eof
