# 🧮 Project 3: Logistic Regression Classifier for Malicious DoH Traffic

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Classification-orange?logo=scikit-learn)

## 📘 Overview

The first true **detector** in this series: a logistic regression model that classifies each traffic flow as **benign DoH** or **malicious DoH tunneling**, plus an analysis of which features drive its decisions.

## 🔍 What I Did

- Used 8 input features: `bytes_in`, `bytes_out`, `num_pkts_in`, `num_pkts_out`, `bytes_ratio`, `time`, `avgdelay`, `maxdelay`.
- Trained a **Logistic Regression** model with a train/test split.
- Evaluated with accuracy and a **confusion matrix**.
- Computed **permutation feature importance** to see which features matter most.

## 📊 Results

- **Accuracy: 99.88%**

| Feature | Importance |
|---|---|
| `bytes_ratio` | 0.265 |
| `avgdelay` | 0.050 |
| `num_pkts_in` | 0.002 |
| `time` | 0.001 |
| others | ≈ 0 |

## ✅ Key Takeaways

- Even a simple linear classifier detects DoH tunneling almost perfectly.
- The model depends mainly on **byte ratio** and **average delay**. Tunneling traffic sends and receives data in unusual proportions and timing.

## ⚠️ Not Done Yet

- No cross-validation; precision/recall per class not reported separately.

## ▶️ How to Run

`pip install pandas scikit-learn matplotlib seaborn`, then run `Logistic_Regression.ipynb` with the combined DoH dataset.
