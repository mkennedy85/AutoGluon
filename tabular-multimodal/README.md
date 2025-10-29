# AutoGluon Tabular (Multimodal)

This repository contains a **reproducible AutoML demonstration** built with [AutoGluon Tabular](https://auto.gluon.ai/stable/index.html), showcasing a multimodal pipeline that combines **tabular, text, and image features** to predict pet adoption speed using the PetFinder dataset.

---

## 🧩 Project Overview

This notebook demonstrates the use of **AutoGluon’s TabularPredictor** to automatically train, ensemble, and evaluate multiple models with minimal code, while maintaining reproducibility and structured experiment outputs.

It includes a self-contained workflow designed for **Google Vertex AI Workbench**, **JupyterLab**, or **Colab** environments.

### Highlights

- **Portable & reproducible:** All generated artifacts are saved under `./artifacts/` for isolation and clarity  
- **Multimodal support:** Integrates text, numeric, and image columns using AutoGluon’s feature metadata system  
- **GPU-aware configuration:** Automatically skips the deep multimodal model if no GPU is available  
- **Explainable:** Includes summaries, visualizations, and reports to interpret model behavior  
- **Practical:** Exports leaderboards, predictions, and manifests for automation and grading

---

## 🧠 Workflow Summary

1. **Data Preparation**
   - Downloads and unpacks the **PetFinder Kaggle** dataset.
   - Creates a local folder structure under `./artifacts/`.
   - Samples 500 training rows for fast experimentation.

2. **Feature Engineering**
   - Parses text (pet descriptions) and image paths.
   - Declares feature types explicitly using AutoGluon’s `FeatureMetadata`.

3. **Model Training**
   - Trains multiple models: `LightGBM`, `CatBoost`, `XGBoost`, and `NeuralNetTorch`.
   - Builds an ensemble (`WeightedEnsemble_L2`) that outperforms individual models.
   - Uses a 300-second time limit for reproducibility.

4. **Evaluation**
   - Saves outputs to `./artifacts/` including:
     - `leaderboard.csv` — model ranking and metrics
     - `predictions.csv` — predicted adoption speeds
     - `feature_importance.csv` — model interpretability (optional)
     - `manifest.json` — pointers to all generated outputs

5. **Visualization**
   - Displays model leaderboard and class prediction distribution.

6. **Interpretation**
   - The ensemble achieved the highest validation accuracy (~0.47).  
   - Prediction distribution reflects dataset imbalance, dominated by class 4 outcomes.

---

## 📊 Key Results

| Model | Validation Accuracy | Notes |
|-------|---------------------|-------|
| WeightedEnsemble_L2 | 0.47 | Combined strengths of top models |
| CatBoost | 0.44 | Strong single-model baseline |
| NeuralNetTorch | 0.40 | Deep model without GPU |
| LightGBMLarge | 0.39 | Larger feature space variant |
| XGBoost | 0.38 | Consistent, interpretable gradient boosting |

---

## 🧭 Insights

- AutoGluon’s **ensembling** substantially improves performance with minimal tuning.
- Dataset **class imbalance** affects precision/recall for minority classes.
- The modular structure allows extension to GPU multimodal training (`AG_AUTOMM`).

---

## ⚙️ Environment

| Component | Version |
|------------|----------|
| Python | 3.10 |
| AutoGluon | 1.4.0 |
| pandas | 2.x |
| scikit-learn | 1.3+ |

To reproduce this environment via `conda`:

```bash
conda create -n autogluon python=3.10 -y
conda activate autogluon
pip install autogluon~=1.4 pandas scikit-learn matplotlib
```

---

## ▶️ How to Run

1. Launch your Jupyter or Vertex AI Workbench instance.  
2. Open the notebook `tabular_multimodal.ipynb`.  
3. Execute all cells sequentially.  
4. Explore generated artifacts in the `artifacts/` directory.

To view your leaderboard:

```bash
cat artifacts/leaderboard.csv | head -n 10
```

---

## 🧾 Repository Structure

```
├── tabular_multimodal.ipynb     # Main notebook
├── artifacts/                   # Generated outputs
│   ├── AutoGluonModels/         # Saved model folder
│   ├── leaderboard.csv
│   ├── predictions.csv
│   ├── manifest.json
│   ├── feature_importance.csv
│   └── run.txt
└── README.md
```

---

## 📈 Visualization Example

Below is an example of the validation performance and class distribution generated at the end of the notebook:

![Leaderboard Visualization](assets/top_models.png)

![Prediction Distribution](assets/pred_distribution.png)

---

## 🔍 Interpretation of Results

- **Top AutoGluon Models — Validation Performance:**  
  WeightedEnsemble_L2 achieved the best accuracy, showing the power of AutoGluon’s ensembling.  
  CatBoost and XGBoost followed closely, indicating strong generalization.

- **Prediction Distribution:**  
  Class 4 dominates, followed by class 1 — consistent with the training data imbalance.

**Next Steps:**
- Enable GPU and reintroduce multimodal deep models (`AG_AUTOMM`).
- Perform hyperparameter tuning or longer training.
- Add cross-validation for more robust evaluation.

---

**Author:** Michael Kennedy  
**Date:** October 2025  
**License:** MIT
