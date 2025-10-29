# AutoGluon Tabular Demos — Academic Edition

This repository contains a collection of **AutoGluon Tabular workflows** demonstrating how to engineer features, combine multimodal inputs, and build reproducible tabular models for both academic and applied data-science use.

Each notebook is designed for **clarity, speed, and reproducibility**, making them ideal for graduate coursework, research labs, or portfolio demonstrations.

---

## 🧭 Repository Structure

| Module | Notebook | Problem Type | Description |
|---------|-----------|---------------|--------------|
| [🏠 California Housing Prices](california-house-prices/README.md) | `california_housing_prices.ipynb` | Regression | Predicts home sale prices using a lightweight AutoGluon workflow. |
| [🔐 IEEE-CIS Fraud Detection](ieee-fraud-detection/README.md) | `ieee_cis_fraud_detection.ipynb` | Classification | Detects fraudulent transactions using AutoGluon’s LightGBM backend. |
| [🧩 Tabular Feature Engineering](tabular-feature/README.md) | `tabular-feature.ipynb` | Feature Generation | Demonstrates AutoGluon’s feature generators, including datetime, categorical, and text n-gram transformations with outputs in `artifacts/`. |
| [🧠 Tabular Multimodal](tabular-multimodal/README.md) | `tabular-multimodal.ipynb` | Multimodal Fusion | Combines numeric, categorical, and image-based features into a single unified AutoGluon training pipeline. |
| [⚙️ Tabular Predictor](tabular-predictor/tabular_predictor.ipynb) | `tabular_predictor.ipynb` | Model Deployment | Demonstrates AutoGluon’s tabular predictor interface and leaderboard evaluation for reproducible experiments. |

Each subfolder includes:
- A **notebook** (`.ipynb`)
- A **README.md** describing inputs, outputs, and methodology
- An **artifacts/** directory containing generated model files and metadata

---

## ⚙️ Environment and Setup

All notebooks are runnable in **Vertex AI Workbench** or **Google Colab**.

### Recommended Environment (Vertex Workbench)
```bash
conda create -n agpu310 python=3.10 -y
conda activate agpu310
pip install -U pip wheel
pip install autogluon pandas pyarrow matplotlib
```

Each notebook automatically manages its own `artifacts/` directory in the same folder for clean, reproducible execution.

---

## 📊 Outputs

Common outputs include:
- `artifacts/leaderboard.csv` — leaderboard summary  
- `artifacts/feature_metadata.txt` — record of generated features  
- `artifacts/AutoGluonModels/` — trained models  
- `artifacts/predictions.csv` — model predictions

---

## 🎥 Demo Videos

All videos are hosted in the [`/assets/`](assets/) directory for direct GitHub playback.

| Demo | Video |
|------|--------|
| 🏠 **California Housing Prices** | [🎥 Watch Demo](assets/california-house-prices.mp4) |
| 🔐 **IEEE-CIS Fraud Detection** | [🎥 Watch Demo](assets/ieee-fraud-detection.mp4) |
| 🧩 **Tabular Feature Engineering** | [🎥 Watch Demo](assets/tabular-feature.mp4) |
| 🧠 **Tabular Multimodal** | [🎥 Watch Demo](assets/tabular-multimodal.mp4) |
| ⚙️ **Tabular Predictor** | [🎥 Watch Demo](assets/tabular-predictor.mp4) |

> You can preview any of these directly on GitHub — they are optimized for 720p playback and progressive loading.

---

## 🧠 Purpose

This repository serves as a compact academic showcase for:
- Feature engineering experimentation  
- AutoML and model interpretability  
- Multimodal data handling  
- Reproducible pipelines for graduate-level coursework

> Curated and presented by **Michael Kennedy**, M.S. Software Engineering candidate at SJSU.  
> Designed for demonstration in **CMPE 272 / 273** and professional research environments.

---

**License:** MIT  
**Framework:** [AutoGluon](https://auto.gluon.ai)
