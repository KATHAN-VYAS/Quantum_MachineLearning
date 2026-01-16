# Adversarially Robust Hybrid Quantum Malware Detection

This repository contains the implementation of **QNI-CCP (Quantum Noise Injection Class Center Perturbation)**, a hybrid Classical-Quantum framework designed for robust image-based malware detection. This was a collaborative work done during my internship at IIT Gandhinagar.

The project demonstrates how injecting specific, sensitivity-weighted perturbations into the quantum latent space can harden Hybrid Quantum Neural Networks (HQNNs) against adversarial attacks and quantum noise.

## 📂 Repository Structure

The project is divided into three progressive stages of implementation. Here is what each file contains:

| File Name | Description | Key Features |
| :--- | :--- | :--- |
| **`basics_QML_circuit`** | **The Baseline Model** | • Standard Hybrid Architecture (CNN + QNN)<br>• **No** QNI-CCP defense<br>• **No** Adversarial Training<br>• Used to establish baseline accuracy and vulnerability. |
| **`QML_QNI-CCP`** | **Robustness via Perturbation** | • Integrates the **QNI-CCP** mechanism<br>• Injects class-aware, sensitivity-weighted noise into the latent feature space<br>• Improves generalization and clean-data accuracy. |
| **`QML_QNI-CCP_adv`** | **Full Adversarial Defense** | • Combines **QNI-CCP** with **Adversarial Training**<br>• Trains against active PGD (Projected Gradient Descent) and FGSM threats<br>• Delivers state-of-the-art robustness against adversarial attacks. |

#### Note: Other files are used for experimenting with different parameters. The results in those files may not be important.
---

## 🚀 Architecture Overview

The framework operates in a 4-stage pipeline designed for Noisy Intermediate-Scale Quantum (NISQ) devices:

1.  **Classical Feature Extractor (CNN):** Reduces high-dimensional malware images (e.g., Malimg/MalVis) into a compact latent feature vector.
2.  **QNI-CCP Mechanism:** * Calculates **Class Centroids** in feature space.
    * Computes **Sensitivity Gradients** (which features affect the loss most?).
    * Injects **Quantum-Informed Noise** to push features toward incorrect class centers during training, forcing the model to learn robust decision boundaries.
3.  **Quantum Circuit (QNN):** A 6-qubit Parameterized Quantum Circuit (PQC) using Angle Encoding and Variational Ansatz (Rotations + Entanglement).
4.  **Classifier Head:** A classical MLP that outputs the final malware family prediction.

---

## 🛠️ Installation & Requirements

Ensure you have the following dependencies installed. This project relies on **PyTorch** for classical processing and **PennyLane** for quantum simulation.

```bash
pip install torch torchvision pennylane matplotlib scikit-learn tqdm numpy
