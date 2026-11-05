# 🛡️ AI for Cybersecurity: Detecting Malicious DNS-over-HTTPS (DoH) Traffic

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange?logo=scikit-learn)
![TensorFlow](https://img.shields.io/badge/TensorFlow-CNN-orange?logo=tensorflow)
![Security](https://img.shields.io/badge/Domain-Network%20Security-darkgreen)

---

## 📘 Overview

**DNS-over-HTTPS (DoH)** encrypts DNS lookups for privacy, but attackers can abuse it to hide **DNS tunneling** (data exfiltration and command-and-control with tools like `dnscat2`) inside normal-looking HTTPS traffic.

This repository is a series of 5 projects that build a complete detection pipeline, from raw packet captures to machine learning and deep learning detectors, and finally explaining and attacking those detectors.

---

## 📂 Projects

| # | Project | What it covers | Result |
|---|---|---|---|
| 1 | [DoH Traffic Feature Extraction](./Project_1_DoH_Traffic_Feature_Extraction) | pcap → flow features with NFStream, benign vs. malicious exploration | 14 engineered flow features |
| 2 | [Linear Regression Traffic Analysis](./Project_2_Linear_Regression_Traffic_Analysis) | Simple, multiple, Lasso and NNLS regression between traffic features | Lasso R² = 0.994 with 2 features |
| 3 | [Logistic Regression Classifier](./Project_3_Logistic_Regression_Classifier) | Benign vs. malicious classifier + permutation feature importance | 99.88% accuracy |
| 4 | [Decision Tree & Random Forest](./Project_4_Decision_Tree_and_Random_Forest) | Interpretable trees at several depths, Random Forest | 99.9% → 100% accuracy |
| 5 | [CNN, Explainability & Adversarial Attack](./Project_5_CNN_Explainability_and_Adversarial_Attack) | 1D CNN, Trustee decision-tree explanations, single-feature evasion attack | 99.89% accuracy; attack evaded it 30% of the time |

---

## 🛠️ Tech Stack

Python · pandas · NumPy · **NFStream** · scikit-learn · TensorFlow/Keras · **Trustee** · Graphviz · matplotlib · seaborn · Google Colab

---

## ✅ Key Takeaways

- Simple flow statistics (byte ratio, delays, packet sizes) reveal DoH tunneling even though the traffic is encrypted.
- Every model scored ~99.9%+, but a one-feature adversarial change fooled the CNN 30% of the time. **Accuracy ≠ robustness.**
- Explainability tools show which few features a detector relies on, which is exactly what an attacker would target.

## ⚠️ Limitations / Future Work

- Data covers one tunneling tool (dnscat2) and one resolver (Cloudflare).
- The full benign/malicious CSV datasets are not included (only a sample pcap and extracted features).
- Next steps: adversarial training, multi-feature attacks, and testing on other tunneling tools (e.g., iodine, dns2tcp).

---

## ▶️ How to Run

Each project folder has its own README with setup steps. Notebooks were built in **Google Colab**; run them in project order.
