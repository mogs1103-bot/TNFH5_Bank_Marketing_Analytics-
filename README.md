# MSIN0097 Predictive Analytics — Individual Coursework
## Predicting Term Deposit Subscription in Bank Marketing Campaigns

**Candidate:** TNFH5  
**Module:** MSIN0097 Predictive Analytics, UCL  
**Dataset:** UCI Bank Marketing (id=222) — Moro, Cortez & Rita (2014)

---


## Project Overview

This project builds a supervised binary classification model to predict whether a bank client will subscribe to a term deposit following a direct marketing campaign. The pipeline covers data loading, EDA, preprocessing, model comparison, fine-tuning, and final evaluation.

---

## Repository Contents

```
├── TNFH5_-_Bank_Marketing_Campaigns.ipynb   # Main project notebook
├── requirements.txt                          # Python dependencies
├── README.md                                 # This file
└── reports/
    ├── figures/                              # All EDA and evaluation plots (auto-generated)
    └── metrics/                              # JSON artefacts (auto-generated)
```

> **Note:** The `reports/` directory is created automatically when the notebook is run. You do not need to create it manually.

---

## Data Access

The dataset is fetched automatically from the UCI ML Repository using the `ucimlrepo` package. No manual download is required.

```python
from ucimlrepo import fetch_ucirepo
bank_marketing = fetch_ucirepo(id=222)
```

If you prefer to download the data manually, it is available at:  
https://archive.ics.uci.edu/dataset/222/bank+marketing

The dataset is licensed under a Creative Commons Attribution 4.0 International licence (CC BY 4.0).

---

## Environment Setup

### Option A — pip (recommended)

```bash
# 1. Clone or download this repository
# 2. Create and activate a virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate        # macOS / Linux
venv\Scripts\activate           # Windows

# 3. Install dependencies
pip install -r requirements.txt
```

### Option B — conda

```bash
conda create -n bank-marketing python=3.11
conda activate bank-marketing
pip install -r requirements.txt
```

**Python version:** 3.10 or higher required.

---

## Running the Notebook

```bash
# Launch Jupyter
jupyter notebook TNFH5_-_Bank_Marketing_Campaigns.ipynb
```

Then run all cells in order using **Kernel → Restart & Run All**.

The notebook is designed to be fully reproducible from a clean kernel state. All random seeds are fixed at `random_state=42`.

**Expected runtime:** approximately 5–10 minutes on a standard laptop (the 5-fold CV step and permutation importance are the slowest cells).

---

## Output Artefacts

After a full run the following files will be created automatically:

| File | Description |
|---|---|
| `reports/figures/target_distribution.png` | Class imbalance bar chart |
| `reports/figures/missingness_summary.png` | Missing values by column |
| `reports/figures/numeric_histograms.png` | Numeric feature distributions |
| `reports/figures/top_categorical_features.png` | Categorical feature frequencies |
| `reports/figures/numeric_correlation_heatmap.png` | Correlation heatmap |
| `reports/figures/hgb_convergence.png` | HGB convergence plot |
| `reports/figures/pr_curve_validation.png` | Validation PR curve with threshold |
| `reports/figures/roc_curve_validation.png` | Validation ROC curve |
| `reports/figures/calibration_curve.png` | Test-set calibration diagram |
| `reports/figures/grouped_feature_importance.png` | Permutation feature importance |
| `reports/metrics/step1_data_summary.json` | Dataset statistics |
| `reports/metrics/final_model_metrics.json` | Final model performance record |

---

## Reproducibility Notes

- The test set is used **exactly once** (Step 5b). No hyperparameter decisions were made after viewing test results.
- The decision threshold (0.1018) was selected on the validation set only and frozen before test evaluation.
- All preprocessing transformers are fitted on training data only and applied to validation and test sets.
- Agent tooling (GitHub Copilot / Codex) was used for code scaffolding. Full documentation of agent interactions, corrections, and governance is in the report appendix.
