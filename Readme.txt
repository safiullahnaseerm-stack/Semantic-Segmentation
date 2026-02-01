Real-Time Domain Adaptation for Semantic Segmentation
Overview

This project investigates domain adaptation for real-time semantic segmentation in urban driving scenarios, focusing on the domain gap between synthetic (GTA5) and real-world (Cityscapes) datasets. Models trained on synthetic data often experience a significant performance drop when applied to real-world data due to domain shift. To address this, the project primarily uses BiSeNet, a lightweight real-time segmentation network, together with domain adaptation strategies such as Fourier Domain Adaptation (FDA) and Domain Adaptation via Cross-domain Mixing (DACS). A hybrid loss function combining Cross-Entropy Loss and Dice Loss is also introduced to handle class imbalance and improve segmentation for underrepresented classes.

Objectives

The main goals of this project are:

To study the impact of domain shift in semantic segmentation

To evaluate BiSeNet for real-time segmentation

To apply and compare FDA and DACS domain adaptation methods

To improve segmentation of rare classes using a hybrid loss

To maintain real-time inference performance while improving accuracy

Datasets

The project uses the GTA5 dataset as the synthetic source domain and the Cityscapes dataset as the real target domain. The datasets are not included in the repository and should be downloaded from their official sources.

Methodology

First, an upper-bound performance reference is established by training and evaluating DeepLabV2 on Cityscapes, representing a high-capacity, non–real-time segmentation model. BiSeNet is then trained and evaluated on Cityscapes to obtain a real-time baseline.

Next, domain shift is analyzed by training BiSeNet on GTA5 and evaluating it on Cityscapes, revealing a significant performance drop due to the synthetic-to-real domain gap. Data augmentation techniques such as horizontal flipping, color jittering, and their combination are applied to improve generalization.

Domain adaptation is subsequently performed using FDA, which aligns low-frequency appearance statistics between domains in Fourier space, and DACS, which leverages pseudo-labels and ClassMix to combine source and target information during training. Finally, a hybrid loss function combining Cross-Entropy and Dice Loss is employed to better address class imbalance and improve segmentation performance on small or rare classes.

Key Results

DeepLabV2 trained and tested on Cityscapes achieves a mean IoU of 57.42%, serving as an upper-bound reference for segmentation performance without real-time constraints.

BiSeNet trained and tested on Cityscapes achieves a mean IoU of 54.08%, demonstrating competitive accuracy while maintaining real-time inference.

BiSeNet trained on GTA5 and tested on Cityscapes (no adaptation) achieves 15.41% mean IoU, confirming severe domain shift.

Data augmentation improves performance to approximately 30% mean IoU.

FDA achieves 26.98% mean IoU, while DACS reaches 24.83% mean IoU.

The final model with hybrid loss achieves 28.23% mean IoU, with noticeable improvements for several minority classes while preserving real-time capability.

Overall, the results demonstrate that while a gap remains between synthetic and real-world performance, combining data augmentation, domain adaptation techniques, and improved loss design can significantly mitigate domain shift in real-time semantic segmentation.