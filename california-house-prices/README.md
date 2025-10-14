## California Housing Prices — AutoGluon Fast Demo

This notebook demonstrates a complete **AutoGluon Tabular** workflow for the *California Housing Prices* Kaggle competition — from environment setup to model training and final submission.  
It is designed for academic demonstration, emphasizing **speed, reproducibility, and clarity** rather than leaderboard optimization.

---

### 🧩 Overview
- **Goal:** Show how AutoGluon can train and predict on tabular regression data efficiently.  
- **Sample size:** 20 000 rows (subset of training data for faster demonstration).  
- **Focus:** Speed and correctness; valid predictions in under a few minutes.

---

### 📘 Notebook Structure

1. **Setup**
   - Installs minimal dependencies (`kaggle`, `autogluon.tabular`).
   - Authenticates using a `kaggle.json` key from Google Drive.
   - Downloads and extracts the competition data into `/content/data/california-house-prices/`.
   - Creates directories for storing models and results.

2. **Training and Prediction**
   - Loads the training and test datasets.
   - Samples **20 000 rows** for quick runtime.
   - Applies minimal preprocessing:
     - Drops the `Id` column.
     - Applies `np.log1p` to numeric features for stability.
     - Uses `LightGBM` only (`GBM`) with a short `time_limit`.
   - Generates predictions on the full test set, applies inverse scaling (`np.expm1`), and saves them as `submission.csv`.

3. **Submission**
   - Submits the generated `submission.csv` to Kaggle using the CLI.
   - Displays recent submissions to verify successful upload.

---

### ⚡ Why a 20 K Sample?
The notebook intentionally trains on a smaller subset to highlight **AutoGluon’s usability and workflow**, not raw performance.  
This approach produces valid, interpretable results quickly — ideal for instructional use or lightweight experiments.

---

### 📁 Expected Artifacts
| Artifact | Description |
|-----------|--------------|
| `/content/data/california-house-prices/train.csv` | Source training data |
| `/content/data/AutoGluonModels/` | AutoGluon model directory |
| `/content/data/AutoGluonModels/submission.csv` | Predictions for Kaggle submission |

---

### ▶️ How to Run
1. Place your `kaggle.json` in Google Drive under `/MyDrive/kaggle.json`.  
2. Run the **setup** cell to authenticate and download data.  
3. Run the **training** cell to generate predictions.  
4. Run the **submission** cell to upload your results to Kaggle.

---

### 🎓 Key Takeaway
This notebook illustrates how **AutoGluon Tabular** can deliver an end-to-end Kaggle workflow — from raw data to submission — in only a few lines of code.  
It’s a concise, reproducible example for classroom or portfolio demonstrations.
