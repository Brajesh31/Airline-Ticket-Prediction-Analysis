# Contributing

This is an educational notebook-based analysis. Contributions should improve correctness, transparency or reproducibility.

Before contributing, read the README, documentation index and SECURITY.md. Confirm that source data is licensed for use. Never add passenger identity, booking references, contact/payment data or credentials.

Use a Python virtual environment with Jupyter, pandas, Matplotlib and scikit-learn. The repository does not pin dependency versions.

Notebook changes should validate schema and types, fit preprocessing only on training data, avoid treating nominal labels as numeric quantities, use a suitable chronological or group split, report MAE/RMSE/R-squared with units, and run from a clean kernel. Remove stale outputs and sensitive data.

Pull requests must explain changed cells, data source/license, dependencies, validation design, metrics and limitations. Do not claim production readiness or live-fare accuracy from notebook results.