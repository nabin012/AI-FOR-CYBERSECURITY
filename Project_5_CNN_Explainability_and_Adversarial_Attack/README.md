# 🧠 Project 5: CNN Detector, Explainability & Adversarial Attack

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![TensorFlow](https://img.shields.io/badge/TensorFlow-Keras-orange?logo=tensorflow)
![Trustee](https://img.shields.io/badge/Explainability-Trustee-purple)

## 📘 Overview

This project builds a **deep learning detector** for malicious DoH traffic, **explains** what the neural network learned, and then **attacks** it to test how robust it is.

## 🔍 What I Did

### 1. 1D CNN Detector (`CNN_Model.ipynb`)
- Built a custom Keras `SequentialNN` with **Conv1D → MaxPooling1D → Flatten → Dense (sigmoid)** on 16 flow features.
- Balanced the data by sampling the same number of malicious and benign flows.
- Trained a baseline (5 epochs, batch 32), then improved training (20 epochs, batch 16), then designed a **deeper CNN** (32-filter Conv1D and more layers).
- Saved training histories and plotted training vs. validation loss.

### 2. Explainability with Trustee (`Explainability_and_Adversarial_Attack.ipynb`)
- Used **Trustee** to train a **decision-tree surrogate** that imitates the CNN.
- Visualized the full and **pruned** decision trees with Graphviz to see which features the CNN relies on.

### 3. Adversarial Attack
- Selected 100 malicious flows the CNN correctly flagged.
- Replaced one feature (`median_in`) with the **average benign value**.
- Measured how many malicious flows then slipped through as "benign", and compared ROC curves before and after the attack.

## 📊 Results

| Experiment | Result |
|---|---|
| Baseline CNN | val accuracy 99.79% |
| Improved training | val accuracy 99.79%, val loss 0.053 → 0.010 |
| Deeper CNN | **val accuracy 99.89%** |
| Trustee surrogate tree | 100% fidelity to the CNN |
| Adversarial attack (1 feature changed) | **30% of malicious flows misclassified as benign** |

## ✅ Key Takeaways

- High accuracy does not mean the model is secure: changing a **single feature** evaded the detector 30% of the time.
- Trustee showed that a simple tree fully explains the CNN, which reveals the few features an attacker would target.

## ⚠️ Not Done Yet

- No defense yet (e.g., adversarial training or feature randomization).
- The attack changed one feature only; multi-feature attacks were not tested.

## ▶️ How to Run

`pip install tensorflow pandas scikit-learn matplotlib trustee pydot graphviz`, then run `CNN_Model.ipynb` first (it saves the model and train/test splits) and then `Explainability_and_Adversarial_Attack.ipynb`.
