# 🌳 Project 4: Decision Tree & Random Forest Detection

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Trees-orange?logo=scikit-learn)

## 📘 Overview

This project detects malicious DoH traffic with **tree-based models**, which are easy to interpret because you can see exactly which feature thresholds the model uses.

## 🔍 What I Did

- Trained a **Decision Tree** (max depth 2) and visualized the full tree with `plot_tree`.
- Compared tree depths **2, 3, 5, and 10**.
- Trained a **Random Forest** with 100 trees.
- Evaluated with accuracy, precision, recall, F1-score, and confusion matrices.

## 📊 Results

| Model | Accuracy | Precision | Recall | F1 |
|---|---|---|---|---|
| Decision Tree (depth 2) | 0.9988 | 0.9990 | 0.9995 | 0.9993 |
| Decision Tree (depth 3–10) | 0.9992 | – | – | – |
| **Random Forest (100 trees)** | **1.00** | **1.00** | **1.00** | **1.00** |

## ✅ Key Takeaways

- A tree with only **2 levels** is already ~99.9% accurate, so a couple of simple rules on traffic features separate the classes.
- Random Forest reached perfect scores on the test split.

## ⚠️ Not Done Yet

- Perfect scores suggest the dataset is very easy to separate; testing on other tunneling tools would show whether the model generalizes.

## ▶️ How to Run

`pip install pandas scikit-learn matplotlib`, then run `Decision_Tree_Random_Forest.ipynb` with the combined DoH dataset.
