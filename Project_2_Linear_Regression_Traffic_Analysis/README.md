# 📈 Project 2: Linear Regression on Network Traffic Features

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Regression-orange?logo=scikit-learn)

## 📘 Overview

This project uses regression to understand **how DoH traffic features relate to each other**: which features predict others and which are redundant. That helps choose good features for the classifiers in later projects.

## 🔍 What I Did

- Combined the benign and malicious DoH datasets into one dataset (`combined_doh_dataset.csv`).
- **Simple linear regression** between related feature pairs:

| Target ← Input | Coefficient | MSE |
|---|---|---|
| `bytes_out` ← `bytes_in` | 1.004 | 0.0010 |
| `num_pkts_out` ← `num_pkts_in` | 1.056 | 0.0020 |
| `av_pkt_size_out` ← `av_pkt_size_in` | 0.295 | 0.0024 |

- **Multiple linear regression** with 4 and then 9 input features (MSE dropped to ~0.00007), and checked for **zero / near-zero coefficients**.
- **Lasso regression:** R² = **0.994**, while setting 7 of 9 coefficients to zero, which works as automatic feature selection.
- **Non-Negative Least Squares (NNLS):** constrained all coefficients to be ≥ 0 (MSE 0.0003).

## ✅ Key Takeaways

- Incoming and outgoing bytes and packet counts are almost perfectly linearly related.
- Average packet size in vs. out is only weakly related.
- Lasso shows that only **2 features** carry most of the information, so many traffic features are redundant.

## ⚠️ Not Done Yet

- No train/validation comparison of regularization strength (alpha) for Lasso.

## ▶️ How to Run

`pip install pandas numpy scikit-learn matplotlib seaborn`, then run `Linear_Regression.ipynb` with the benign and malicious DoH CSV files available.
