# Installation and execution

## Requirements

- Python 3.10 or newer.
- Git, if cloning the repository.
- The external airline CSV referenced by the notebook, obtained from a source whose terms permit your intended use.
- Internet access for initial package installation.

The project uses Jupyter, pandas, Matplotlib, and scikit-learn. Direct dependencies are listed in [requirements.txt](../requirements.txt).

## Clone the repository

```bash
git clone https://github.com/Brajesh31/Airline-Ticket-Prediction-Analysis.git
cd Airline-Ticket-Prediction-Analysis
```

## Create a virtual environment

```bash
python -m venv .venv
```

Activate it using the command for your operating system.

**Windows PowerShell**

```powershell
.venv\Scripts\Activate.ps1
```

**Windows Command Prompt**

```bat
.venv\Scripts\activate.bat
```

**macOS/Linux**

```bash
source .venv/bin/activate
```

## Install dependencies

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

## Configure the dataset

The notebook currently reads:

```python
pd.read_csv('/content/AIRLINES DATASET PRACTICAL - Sheet1.csv')
```

That is a Google Colab-style path. For local use, place an authorized CSV copy in a local `data/` directory and change the path to:

```python
pd.read_csv('data/AIRLINES DATASET PRACTICAL - Sheet1.csv')
```

The `data/` directory and CSV are not tracked by Git. Verify the expected fields using [data.md](data.md) before running the notebook. Do not upload credentials or data access tokens.

## Launch Jupyter

```bash
jupyter notebook
```

Open `PDS_PROJECT.ipynb` and execute cells in order. Kernel execution may stop if the CSV is missing, columns differ, or expected categories are absent.

## Verify the environment

```bash
python --version
python -m pip show pandas matplotlib scikit-learn jupyter
```

For troubleshooting, see [troubleshooting.md](troubleshooting.md).
