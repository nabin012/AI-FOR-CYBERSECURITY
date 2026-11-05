# 📦 Project 1: DoH Traffic Feature Extraction & Exploration

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![NFStream](https://img.shields.io/badge/NFStream-Flow%20Analysis-darkgreen)
![pandas](https://img.shields.io/badge/pandas-Data-150458?logo=pandas)

## 📘 Overview

Before any model can detect malicious traffic, raw network packets must be turned into numbers. This project converts a **DNS-over-HTTPS packet capture (`.pcap`)** into **flow-level features** and explores how benign DoH traffic differs from malicious DoH tunneling traffic (dnscat2).

## 🔍 What I Did

- Used **NFStream** to read `Doh_traffic.pcap` and group packets into network flows with statistical analysis enabled.
- Engineered 14 features per flow and saved them to `sample-features.csv`:
  - **Volume:** sent/received bytes, sent/received packets
  - **Ratios:** byte ratio, packet ratio
  - **Timing:** connection duration, min/avg/max receive delay (ms)
  - **Packet size:** average and variance of sent/received packet sizes
- Loaded the benign (Cloudflare) and malicious (dnscat2) DoH datasets and compared them with **pairplots** of traffic-volume, packet-size, median/ratio, and timing features.

## 📊 Findings

- Malicious tunneling flows have noticeably different **byte ratios, packet sizes, and delays** than normal DoH traffic, so the classes are separable using flow statistics alone, even though the traffic is encrypted.

## 📁 Files

| File | Description |
|---|---|
| `Data_Creation.ipynb` | pcap → flow features with NFStream |
| `Dataset_Exploration.ipynb` | Visual comparison of benign vs. malicious traffic |
| `Doh_traffic.pcap` | Sample DoH packet capture |
| `sample-features.csv` | Extracted flow features |

## ⚠️ Not Done Yet

- Only one sample capture is included; the full benign/malicious CSV datasets are not in the repo.

## ▶️ How to Run

`pip install nfstream pandas matplotlib seaborn`, then open the notebooks in Google Colab and upload the pcap/CSV files.
