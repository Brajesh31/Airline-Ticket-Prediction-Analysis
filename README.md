# Airline Ticket Prediction Analysis

A Jupyter Notebook project for exploring airline fare data and building an educational baseline regression model.

[![Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](PDS_PROJECT.ipynb)
[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)](https://www.python.org/)
[![scikit--learn](https://img.shields.io/badge/scikit--learn-Regression-F7931E?logo=scikitlearn&logoColor=white)](https://scikit-learn.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Notebook Quality](https://github.com/Brajesh31/Airline-Ticket-Prediction-Analysis/actions/workflows/notebook-quality.yml/badge.svg)](https://github.com/Brajesh31/Airline-Ticket-Prediction-Analysis/actions/workflows/notebook-quality.yml)

## Table of contents

- [Overview](#overview)
- [Current capabilities](#current-capabilities)
- [Repository structure](#repository-structure)
- [Dataset requirements](#dataset-requirements)
- [Environment setup](#environment-setup)
- [Run the notebook](#run-the-notebook)
- [Analysis and modeling workflow](#analysis-and-modeling-workflow)
- [Evaluation and interpretation](#evaluation-and-interpretation)
- [Known technical limitations](#known-technical-limitations)
- [Validation and automation](#validation-and-automation)
- [Responsible data use](#responsible-data-use)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [Maintainer and license](#maintainer-and-license)

## Overview

This repository contains a notebook-based analysis of airline ticket prices. The notebook explores the relationship between booking lead time and fare, creates visualizations, applies categorical encoding, trains a scikit-learn Linear Regression estimator, and reports basic regression metrics.

The project is intended for learning and experimentation with tabular data, exploratory analysis, feature preparation, regression, and model evaluation. It is not a live fare-search engine, airline booking platform, or production pricing service.

> **Dataset availability:** The notebook references `AIRLINES DATASET PRACTICAL - Sheet1.csv`, but that CSV is not committed to this repository. You must obtain a lawful copy separately and configure the notebook to use its location.

## Current capabilities

The checked-in notebook currently includes:

- A scatter plot of `DAYS_LEFT` against `PRICE`.
- A second scatter plot whose axis label says flight number, although its x values currently come from `DAYS_LEFT`. Treat this plot as a known notebook defect, not a valid flight-number analysis.
- Label encoding of airline, city, time, stops, class, duration, and days-left fields.
- An 80/20 random train/test split using `random_state=42`.
- A scikit-learn `LinearRegression` model.
- Mean squared error and R-squared output.
- An illustrative prediction for one flight configuration.

The repository does not currently contain an API, web interface, database, deployed model, scheduled fare ingestion, or monitoring service.

## Repository structure

```text
.
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.yml
│   │   ├── feature_request.yml
│   │   ├── documentation_request.yml
│   │   └── config.yml
│   ├── workflows/
│   │   ├── update-readme.yml
│   │   └── notebook-quality.yml
│   └── PULL_REQUEST_TEMPLATE.md
├── docs/
│   ├── README.md
│   ├── installation.md
│   ├── data.md
│   ├── architecture.md
│   ├── modeling.md
│   ├── reproducibility.md
│   ├── development.md
│   ├── testing.md
│   ├── deployment.md
│   ├── api.md
│   ├── database.md
│   ├── faq.md
│   ├── troubleshooting.md
│   ├── privacy.md
│   └── limitations.md
├── PDS_PROJECT.ipynb
├── requirements.txt
├── .env.example
├── CHANGELOG.md
├── CITATION.cff
├── CODEOWNERS
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── LICENSE
├── README.md
├── ROADMAP.md
├── SECURITY.md
└── SUPPORT.md
```

## Dataset requirements

The notebook expects a CSV with fields referenced in its code:

| Field | Current use | Expected meaning |
|---|---|---|
| `AIRLINES` | Predictor | Airline name/category |
| `FLIGHT_NO.` | Plotted label only | Flight identifier |
| `SOURCE_CITY` | Predictor | Origin city |
| `DEPARTURE_TIME` | Predictor | Departure time category |
| `STOPS` | Predictor | Stop count/category |
| `ARRIVAL_TIME` | Predictor | Arrival time category |
| `DESTINATION_CITY` | Predictor | Destination city |
| `CLASS` | Predictor | Cabin/fare class |
| `DURATION` | Predictor | Flight duration |
| `DAYS_LEFT` | Predictor | Days remaining before departure |
| `PRICE` | Target | Ticket price |

The notebook's saved output has displayed 12 columns, while the code names 11 fields. Confirm the complete schema with the original dataset before running the notebook. Currency, taxes, data source, data collection period, licensing, and route coverage are not established by this repository. See [Data documentation](docs/data.md).

## Environment setup

Python 3.10 or newer is recommended. Create and activate a virtual environment:

```bash
python -m venv .venv
```

Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

macOS/Linux:

```bash
source .venv/bin/activate
```

Install the notebook dependencies:

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

The dependency file covers the notebook's direct imports and the Jupyter runtime. See [Installation](docs/installation.md) for environment and dataset configuration details.

## Run the notebook

Start Jupyter:

```bash
jupyter notebook
```

Open `PDS_PROJECT.ipynb` and execute the cells in order after making the dataset accessible. In the notebook, update the hard-coded path:

```python
data = pd.read_csv('/content/AIRLINES DATASET PRACTICAL - Sheet1.csv')
```

For a local run, replace it with the correct local path, for example:

```python
data = pd.read_csv('data/AIRLINES DATASET PRACTICAL - Sheet1.csv')
```

The example path assumes you create a local `data/` directory and place your permitted dataset copy there. The data directory is not part of the repository. Do not commit a dataset unless its license explicitly permits redistribution.

## Analysis and modeling workflow

At a high level, the notebook:

1. Imports pandas and Matplotlib for tabular analysis and visualization.
2. Loads the external CSV.
3. Visualizes ticket price against days remaining before departure.
4. Encodes selected columns with `LabelEncoder`.
5. Uses nine selected fields as predictors and `PRICE` as the target.
6. Splits rows into training and test sets.
7. Trains `LinearRegression`.
8. Calculates mean squared error and R-squared on the test set.
9. Attempts one illustrative prediction using fitted encoders.

Read [Architecture](docs/architecture.md) and [Modeling methodology](docs/modeling.md) for a more detailed explanation and caveats.

## Evaluation and interpretation

MSE and R-squared are not enough to establish that a fare model is accurate or useful. A credible evaluation should also report MAE and RMSE, state the fare currency, compare against a simple baseline, define the test population, and examine errors across airlines, routes, classes, and booking windows.

Do not quote a model score without naming the dataset version and validation split. The results depend on the external CSV and cannot be reproduced from this repository alone.

## Known technical limitations

The checked-in notebook has limitations that should be addressed before using it for decision-making:

- The CSV input is external and its provenance and license are not documented.
- The data path is hard-coded to a Google Colab location.
- The second scatter plot labels the x-axis as `FLIGHT_NO.` but passes `DAYS_LEFT` as the x data.
- Label encoders are fitted to the full dataset before the train/test split, leaking information about test categories.
- Integer codes for nominal categories can imply a false order and distance in linear regression.
- `DURATION` and `DAYS_LEFT` are numeric-like but are label-encoded.
- The illustrative prediction can fail when an input category is absent from the fitted encoder classes.
- A random row split may overstate generalization when repeated flights, routes, or related observations appear in both partitions.
- No automated model-accuracy test or executed-notebook CI job exists.

The new CI workflow checks notebook structure and Python syntax. It does not prove that all notebook cells execute successfully or that the estimator is statistically sound. See [Known limitations](docs/limitations.md) and [Testing](docs/testing.md).

## Validation and automation

GitHub Actions runs notebook quality checks on relevant pushes and pull requests. The workflow installs declared dependencies, validates notebook JSON, parses code-cell syntax, and checks local README links.

A separate notebook validation workflow is retained for structural validation. Because the dataset is not included, CI does not run the full analysis. Review workflow results in the [Actions tab](https://github.com/Brajesh31/Airline-Ticket-Prediction-Analysis/actions).

## Responsible data use

Use only datasets you are authorized to access and process. Do not publish passenger names, contact details, booking references, payment information, or other personal data. Respect the dataset provider's license and terms. Historical fare estimates must not be represented as current offers or guaranteed booking prices.

## Documentation

| Guide | Coverage |
|---|---|
| [Documentation index](docs/README.md) | Guide map and project scope |
| [Installation](docs/installation.md) | Python environment, dependencies, notebook startup |
| [Data](docs/data.md) | Expected columns, provenance, validation, data handling |
| [Architecture](docs/architecture.md) | Notebook components and data flow |
| [Modeling](docs/modeling.md) | Current estimator, risks, recommended evaluation |
| [Reproducibility](docs/reproducibility.md) | Dataset/version tracking and repeatable experiments |
| [Development](docs/development.md) | Local workflow and change practices |
| [Testing](docs/testing.md) | Automated checks and model-validation strategy |
| [Deployment](docs/deployment.md) | Current execution model and future deployment criteria |
| [API status](docs/api.md) | Why there is no HTTP API today |
| [Database status](docs/database.md) | Why there is no database today |
| [Privacy](docs/privacy.md) | Data minimization and safe handling |
| [Limitations](docs/limitations.md) | Known gaps and risks |
| [FAQ](docs/faq.md) | Common questions |
| [Troubleshooting](docs/troubleshooting.md) | Common setup and notebook problems |

## Contributing

Contributions are welcome when they improve correctness, reproducibility, documentation, or maintainability. Read [CONTRIBUTING.md](CONTRIBUTING.md) and the [development guide](docs/development.md) before submitting a change. Never include restricted data or personal information in issues, commits, notebooks, or test fixtures.

## Maintainer and license

Maintained by **Brajesh Kumar**.

This repository's code and documentation are distributed under the MIT License. See [LICENSE](LICENSE). Dataset rights are separate and are not granted by the repository license.
