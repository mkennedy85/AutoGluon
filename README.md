# AutoGluon Kaggle Demos — Academic Edition

This repository contains two fast, reproducible **AutoGluon Tabular** workflows demonstrating how to build, train, and submit models to Kaggle competitions directly from Google Colab.

Each notebook focuses on **clarity, speed, and reproducibility** rather than leaderboard optimization, making them ideal for academic presentations or portfolio demonstrations.

---

## 🧭 Repository Structure

| Competition | Notebook | Sample Size | Problem Type | Description |
|--------------|-----------|-------------|---------------|--------------|
| [🏠 California Housing Prices](california-house-prices/README.md) | `california-house-prices.ipynb` | 20 000 rows | Regression | Predicts home sale prices using a fast LightGBM model. |
| [🔐 IEEE-CIS Fraud Detection](ieee-fraud-detection/README.md) | `ieee_cis_fraud_detection.ipynb` | 20 000 rows | Classification | Detects fraudulent transactions with AutoGluon’s LightGBM backend. |

Each subfolder includes:
- A ready-to-run **Jupyter notebook**
- A **README.md** describing the workflow
- The generated **submission.csv** for Kaggle upload

---

## ⚙️ Environment and Setup

Both notebooks are designed for **Google Colab** with lightweight configuration:

1. Place your Kaggle API key at:  
   `/MyDrive/kaggle.json`
2. Run the setup cell to install:
   ```bash
   pip install -q kaggle autogluon.tabular

## 🎓 Kaggle AutoGluon Demos

| Competition | Notebook | Video |
|--------------|-----------|--------|
| IEEE-CIS Fraud Detection | [View Notebook](ieee-fraud-detection/ieee_cis_fraud_detection.ipynb) | [🎥 Watch](ieee_cis_fraud_detection/ieee-fraud-detection.mp4) |
| California Housing Prices | [View Notebook](california-house-prices/california_housing_prices.ipynb) | [🎥 Watch](california_housing_prices/california-house-prices.mp4) |