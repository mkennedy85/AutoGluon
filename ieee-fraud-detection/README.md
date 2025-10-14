## IEEE-CIS Fraud Detection — AutoGluon Fast Demo

This notebook presents a lightweight **AutoGluon Tabular** pipeline for the *IEEE-CIS Fraud Detection* Kaggle competition.  
It demonstrates a full workflow — setup, training, inference, and submission — optimized for **speed and academic clarity**.

---

### 🧩 Overview
- **Goal:** Show a rapid, reproducible approach to binary classification with AutoGluon.  
- **Sample size:** 20 000 rows (subset of the full training data).  
- **Focus:** Fast execution and correctness rather than top leaderboard accuracy.

---

### 📘 Notebook Structure

1. **Setup**
   - Installs required packages (`kaggle`, `autogluon.tabular`).
   - Authenticates with the Kaggle API via `kaggle.json` in Google Drive.
   - Downloads and extracts the **IEEE-CIS Fraud Detection** dataset to `/content/data/ieee-fraud-detection/`.
   - Prepares an AutoGluon output directory (`/content/data/AutoGluonModels/`).

2. **Fast Training and Prediction**
   - Loads and merges `train_transaction.csv` and `train_identity.csv` on `TransactionID`.
   - Samples **20 000 rows** for efficient runtime.
   - Performs minimal preprocessing:
     - Drops `TransactionID`.
     - Fills object columns with `"NA"` and numeric columns with `-999`.
     - Casts `isFraud` to integer.
   - Trains a **single LightGBM model** (`GBM`) with a short time limit (≈120 s).
   - Aligns the test data to the model’s feature set — adding any missing columns such as `id_01`–`id_38` — ensuring inference stability.
   - Writes results to `submission.csv`.

3. **Submission**
   - Submits the generated `submission.csv` to the Kaggle competition.
   - Prints the recent submission history for confirmation.

---

### ⚡ Why a 20 K Sample?
This workflow is intended as an **academic demonstration** of AutoGluon’s automation and simplicity.  
Training on 20 000 rows achieves fast runtime while preserving the structure of a full production-grade pipeline.

---

### 📁 Expected Artifacts
| Artifact | Description |
|-----------|-------------|
| `/content/data/ieee-fraud-detection/train_transaction.csv` | Main transactional data |
| `/content/data/AutoGluonModels/` | Trained AutoGluon model files |
| `/content/data/AutoGluonModels/submission.csv` | Output file for Kaggle submission |

---

### ▶️ How to Run
1. Ensure your `kaggle.json` is in `/MyDrive/kaggle.json`.  
2. Run the **setup** cell to install dependencies and download data.  
3. Run the **training** cell to produce predictions.  
4. Run the **submission** cell to send the results to Kaggle.

---

### 🎓 Key Takeaway
This notebook highlights **AutoGluon’s rapid modeling capabilities** on complex tabular data.  
Even with a reduced sample, it demonstrates the complete machine-learning lifecycle — from dataset preparation to model deployment via Kaggle submission — in a compact, educational format.
