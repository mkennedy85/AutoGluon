# Tabular Feature Engineering — Demo (AutoGluon)

This repo contains a **demo-led notebook** that shows how AutoGluon detects, transforms, and engineers features from mixed tabular data (numeric, categorical, datetime, and short text). All outputs are written to a local `./artifacts/` directory beside the notebook so the repo stays clean.

> Presenter: **Michael Kennedy** · Runtime: ~3–6 min per run on small data

## What’s in the demo
- **Mixed-type synthetic dataset** (numeric, categorical, datetime, text)
- **Default** `AutoMLPipelineFeatureGenerator` → see what it creates & why
- **Quick model fit** with `TabularPredictor` (just to exercise the pipeline)
- **Missing-values** robustness
- **Custom generator pipeline** (datetime expansion, category thresholds, TF‑IDF text)
- **Wrap‑up + visual**: quick bar chart comparing resulting feature counts

## Repo layout
```
.
├── Tabular_Feature_Engineering_Demo.ipynb   # the notebook you run
├── artifacts/                                # all outputs land here (safe to gitignore)
│   ├── raw_demo.csv
│   ├── feature_metadata.txt
│   ├── leaderboard_fe.csv
│   └── FE_AutoGluonModels/                   # AutoGluon model directory
└── README.md
```

> If `artifacts/` isn’t present, the notebook creates it automatically in the same folder as the notebook (using `Path.cwd() / "artifacts"`).

## Quickstart (Vertex Workbench or local)

**Python 3.10+ recommended.** If you already have an AutoGluon environment, you can skip to “Run”.

### Option A — Conda env
```bash
conda create -n agpu310 python=3.10 -y
conda activate agpu310
pip install -U pip wheel
pip install autogluon
```

### Option B — PIP only (venv)
```bash
python -m venv .venv
source .venv/bin/activate            # Windows: .venv\Scripts\activate
pip install -U pip wheel
pip install autogluon
```

> If you plan to run on CPU only, the basic `autogluon` meta‑package is sufficient for this demo.

## Run
Open the notebook and run all cells. The code will:
1) Create synthetic mixed‑type data
2) Fit the default feature generator and show what features it builds
3) Train a small AutoGluon model and write a leaderboard to `./artifacts/leaderboard_fe.csv`
4) Inject a few NaNs to show the pipeline remains stable
5) Run a **custom** pipeline (datetime expansion, category handling, TF‑IDF text) for comparison
6) Plot a mini bar chart comparing feature counts across snippets

## Key paths
- **Notebook dir**: `Path.cwd()`
- **Artifacts**: `Path.cwd() / "artifacts"`
- **Model dir**: `artifacts/FE_AutoGluonModels`
- **Feature metadata**: `artifacts/feature_metadata.txt`
- **Leaderboard**: `artifacts/leaderboard_fe.csv`

## Notes & tips
- Feature generators operate on **X only** (`fit(X)`), not `(X, y)`.
- Datetime features only appear if your column is actual `datetime64[ns]` (the notebook coerces it).
- If you don’t have any text columns (dtype `object`), the TF‑IDF step is a no‑op.
- Keep `artifacts/` in `.gitignore` to avoid committing large model files.

## Troubleshooting
- **No features detected**: ensure your columns have expected dtypes; for datetime, coerce with `pd.to_datetime(...)`.
- **Slow first install**: AutoGluon pulls multiple dependencies the first time; subsequent runs are fast.
- **Out of memory**: reduce `N`, use lighter presets (e.g., `presets="medium"`), or skip TF‑IDF.

---

**Attribution / Source**  
This README summarizes the companion notebook and outputs produced by the *Tabular Feature Engineering Demo*. For the exact code and logs, see the notebook and files in `./artifacts/`.
