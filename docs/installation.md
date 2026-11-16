# Installation

The notebook imports pandas, Matplotlib and scikit-learn. Install Jupyter to execute it. Python 3.10+ is a practical starting point, but dependency versions are not pinned.

```bash
python -m venv .venv
python -m pip install --upgrade pip
python -m pip install jupyter pandas matplotlib scikit-learn
jupyter notebook
```

Activate with `.venv\\Scripts\\Activate.ps1` in Windows PowerShell or `source .venv/bin/activate` on macOS/Linux. Open `PDS_PROJECT.ipynb` and run cells in order. The CSV at `/content/AIRLINES DATASET PRACTICAL - Sheet1.csv` is not included. Update the `pd.read_csv` path and use data you are permitted to process.
