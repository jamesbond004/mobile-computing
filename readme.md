## Title
Multimodal Human Activity Recognition using Sensor Fusion on UTD-MHAD Dataset
## Problem Statement
Human Activity Recognition (HAR) is a foundational problem in mobile and ubiquitous computing, enabling intelligent applications such as health monitoring, gesture control, and smart environments. Traditional HAR systems rely primarily on inertial sensors (e.g., accelerometer, gyroscope) embedded in smartphones or wearables. However, unimodal sensor approaches face significant challenges in real-world variability, including sensor noise, body placement differences, and lack of contextual information.
Recent advances in multimodal fusion—combining inertial, visual, and depth information—have demonstrated significant performance improvements. However, integrating and learning effectively from heterogeneous data sources remains a challenge due to synchronization issues, modality imbalance, and computational limitations on mobile platforms.
This project aims to design and evaluate a multimodal deep learning model that integrates motion sensor and visual data for human activity recognition using the UTD-MHAD dataset. The system will explore early vs. late fusion strategies for combining modalities and analyze trade-offs between accuracy and computational efficiency.
## Specific and Measurable Objectives:
- Develop and train a multimodal HAR model on UTD-MHAD combining inertial and RGB data.
- Achieve ≥90% accuracy on test activities.
- Compare fusion strategies (early vs. late) and evaluate robustness to missing or noisy modalities.
## Why It Matters for Mobile Computing:
- Multimodal HAR directly supports context-aware mobile systems, enabling adaptive interfaces and assistive applications.
- Improved fusion methods can make on-device sensing more robust, reducing reliance on cloud-based inference and preserving user privacy.
## Technical Challenges:
- Aligning asynchronous sensor and visual data streams.
- Designing fusion layers that effectively capture cross-modal correlations without excessive computation.
- Handling modality dropout or corruption (common in mobile settings).
## Technical Approach
#### Dataset

The UTD-MHAD dataset(https://personal.utdallas.edu/~kehtar/UTD-MHAD.html) contains Multimodal dataset with IMU + skeleton + RGB video:
- 27 human actions performed by 8 subjects (e.g., jogging, waving, clapping).
- RGB + depth videos from Kinect sensors.
- Inertial sensor data (3-axis accelerometer and 3-axis gyroscope) captured from a wearable device on the subject’s wrist and pocket.

This dataset provides the ideal multimodal testbed for HAR research since it integrates wearable and visual sensing modalities relevant to mobile systems.
#### Methodology

##### 1. Data Preprocessing:
- Extract synchronized sensor and video samples.
- Normalize accelerometer and gyroscope signals.
- Sample RGB frames (or extract features using pretrained CNNs such as ResNet18).
- Segment activities into fixed-length sequences.

##### 2. Model Architecture:
- Sensor Branch: 1D CNN + LSTM for temporal feature learning.
- Vision Branch: CNN (pretrained ResNet or MobileNet) for spatial feature extraction.
- Fusion Layer:
  - Early Fusion: Concatenate features before classification.
  - Late Fusion: Combine decision outputs using weighted averaging or attention.
- Classifier: Fully connected layers with softmax output over activity classes.

##### 3. Training Strategy:
- Train unimodal branches separately first, then jointly fine-tune fusion network.
- Use Adam optimizer with early stopping.
- Perform k-fold cross-validation across subjects.

##### 4. Tools and Environment:
- Framework: PyTorch (or TensorFlow).
- Environment: Jupyter Notebook (Colab GPU recommended).
- Libraries: NumPy, OpenCV, SciPy, scikit-learn.
