# Airline Ticket Prediction Analysis

A notebook-based exploratory analysis and baseline regression exercise for airline ticket prices.

[![Jupyter](https://img.shields.io/badge/Jupyter-notebook-orange?logo=jupyter)](PDS_PROJECT.ipynb)
[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## Table of contents
- [Overview](#overview)
- [Repository contents](#repository-contents)
- [Notebook workflow](#notebook-workflow)
- [Input data](#input-data)
- [Installation and execution](#installation-and-execution)
- [Modeling methodology](#modeling-methodology)
- [Known limitations](#known-limitations)
- [Responsible use](#responsible-use)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [License](#license)

## Overview

This project studies airline ticket prices using a Jupyter notebook. It plots price against days remaining before departure and builds a basic scikit-learn Linear Regression model from selected flight attributes.

The notebook reads `AIRLINES DATASET PRACTICAL - Sheet1.csv` from a Google Colab `/content/` path. That CSV is **not included** in this repository. The notebook's saved output displays 2,030 rows and 12 columns, but this is only an observed output snapshot, not a verified description of the original dataset.

This is an educational analysis. It is not a live fare-search service, airline booking system or guaranteed price estimator.

## Repository contents

| Path | Purpose |
| --- | --- |
| `PDS_PROJECT.ipynb` | Main exploratory analysis, plots, preprocessing, regression and sample prediction |
| `docs/` | Data, methodology, setup, reproducibility, testing and maintenance guidance |
| `.github/workflows/` | Notebook JSON validation workflow |
| `CHANGELOG.md` | Repository changes |
| `CITATION.cff` | Citation metadata |
| `LICENSE` | MIT license |

## Notebook workflow

The current notebook performs the following steps:

1. Loads the CSV into a pandas DataFrame.
2. Plots `PRICE` against `DAYS_LEFT`.
3. Uses LabelEncoder on `AIRLINES`, `SOURCE_CITY`, `DEPARTURE_TIME`, `STOPS`, `ARRIVAL_TIME`, `DESTINATION_CITY`, `CLASS`, `DURATION` and `DAYS_LEFT`.
4. Selects those nine columns as predictors and `PRICE` as the target.
5. Makes a random 80/20 split with `random_state=42`.
6. Fits `LinearRegression` and prints mean squared error and R-squared.
7. Attempts one illustrative Vistara, Delhi-to-Mumbai, Economy prediction.

The second scatter plot currently labels its x-axis as flight number but still passes the previously selected `DAYS_LEFT` series to `plt.scatter`. It is therefore not a valid flight-number plot and should be corrected before interpreting it.

## Input data

The code references these columns: `AIRLINES`, `FLIGHT_NO.`, `SOURCE_CITY`, `DEPARTURE_TIME`, `STOPS`, `ARRIVAL_TIME`, `DESTINATION_CITY`, `CLASS`, `DURATION`, `DAYS_LEFT` and `PRICE`. The saved DataFrame output displays 12 columns, while the code explicitly references 11 names. Confirm the complete schema with the original data provider.

Before relying on results, document the original source, collection date, route coverage, currency, fare inclusions, license, missing-value policy and whether repeated rows describe the same flight or itinerary.

## Installation and execution

Use Python 3.10 or newer as a practical starting point. The visible notebook imports pandas, Matplotlib and scikit-learn. Jupyter is required to run the notebook.

```bash
python -m venv .venv
```

Activate the environment:

```powershell
# Windows PowerShell
.venv\Scripts\Activate.ps1
```

```bash
# macOS / Linux
source .venv/bin/activate
```

Install the direct notebook dependencies:

```bash
python -m pip install --upgrade pip
python -m pip install jupyter pandas matplotlib scikit-learn
```

Launch Jupyter:

```bash
jupyter notebook
```

Open `PDS_PROJECT.ipynb` and execute cells in order. Update the hard-coded Google Colab CSV path to match the location of a permitted dataset copy. Do not commit private or restricted data.

## Modeling methodology

The current implementation is a baseline, not a validated production model. It reports MSE and R-squared but does not report MAE or RMSE, compare against a naive baseline, inspect residuals, or evaluate errors across routes, airlines, cabin classes and booking windows.

Important methodological risks:

- LabelEncoder maps nominal categories to integers, which can create a false numeric ordering for linear regression.
- Duration and days-left are numeric-like measurements but are encoded as labels.
- Encoders are fitted to the full dataset before the train/test split. This is preprocessing leakage.
- A random split may mix related routes, dates or repeated itineraries across train and test sets.
- The sample prediction encodes duration and days-left as strings. It can fail when those exact values are absent from the fitted encoder classes.
- The second scatter plot's displayed x-axis label does not match the x values passed to the plotting function.

A stronger version should use a scikit-learn Pipeline and ColumnTransformer, one-hot encoding for nominal categories, numeric parsing for measurements, and transformations fitted only on training folds. Choose chronological or group-aware validation based on the intended prediction scenario. Report MAE, RMSE and R-squared with units and the exact evaluation design. See [modeling](docs/modeling.md).

## Known limitations

- The required CSV is not checked into the repository.
- Dataset provenance, usage rights, collection period and currency are undocumented.
- The notebook uses a hard-coded Google Colab path.
- Dependencies are not pinned in a requirements file or lockfile.
- No automated test suite or production CI pipeline exists.
- Only a basic linear regression baseline is implemented.
- No prediction API, application, database, monitoring or scheduled data refresh exists.
- A plot label/data mismatch and preprocessing risks remain in the notebook.

These are limitations, not implemented features.

## Responsible use

Airline fares change with availability, timing, fare rules, taxes, currency, route and airline policies. Historical data can become stale quickly. Results must not be presented as live prices or booking guarantees. Do not use passenger identities, booking references, contact details or payment information in public datasets or notebook outputs.

## Documentation

- [Documentation index](docs/README.md)
- [Installation](docs/installation.md)
- [Data dictionary and provenance](docs/data.md)
- [Architecture](docs/architecture.md)
- [Modeling methodology](docs/modeling.md)
- [Reproducibility](docs/reproducibility.md)
- [Development](docs/development.md)
- [Testing](docs/testing.md)
- [Deployment considerations](docs/deployment.md)
- [API status](docs/api.md)
- [Database status](docs/database.md)
- [Privacy](docs/privacy.md)
- [Known limitations](docs/limitations.md)
- [FAQ](docs/faq.md)
- [Troubleshooting](docs/troubleshooting.md)

## Contributing

Read [CONTRIBUTING.md](CONTRIBUTING.md) before making changes. Data, preprocessing, validation and metric changes should include reproducible evidence.

## License

Licensed under the MIT License. See [LICENSE](LICENSE).

Maintained by Brajesh Kumar.
