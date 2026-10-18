# Airline Ticket Prediction Analysis

This repository contains a Jupyter notebook for exploring airline ticket pricing and building a supervised regression model. The notebook is an educational data-science artifact; its exact features, preprocessing, and results are defined by `PDS_PROJECT.ipynb`.

## Contents

- `PDS_PROJECT.ipynb` - exploratory analysis, preprocessing, model training, and evaluation.

## Setup

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install jupyter pandas numpy scikit-learn matplotlib seaborn
jupyter notebook
```

Open `PDS_PROJECT.ipynb` and run cells in order. Update the dependency list if the notebook imports additional libraries.

## Modeling notes

Linear regression assumptions should be checked against the actual data. Use time-aware or grouped validation where applicable, avoid leakage from future or target-derived fields, and report MAE/RMSE/R² together with the split and preprocessing details. Predictions are not guaranteed to reflect current market prices.

See [docs/data.md](docs/data.md), [docs/reproducibility.md](docs/reproducibility.md), and [docs/development.md](docs/development.md).

Maintained by Brajesh Kumar (`brajesh31`).

Last updated: 2026-10-18 22:51 UTC
