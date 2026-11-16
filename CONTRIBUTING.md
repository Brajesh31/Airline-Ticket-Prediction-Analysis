# Contributing

Thank you for considering a contribution to Airline Ticket Prediction Analysis. The project is a notebook-based educational analysis. Contributions should improve correctness, reproducibility, clarity, accessibility, or repository maintenance.

## Before opening a change

1. Read the [README](README.md), [documentation index](docs/README.md), and [security policy](SECURITY.md).
2. Search existing issues and discussions for related work.
3. Confirm that any dataset used is authorized for the proposed purpose.
4. Keep each contribution focused and explain the problem it solves.

## Local environment

Follow [docs/installation.md](docs/installation.md). Install dependencies with:

```bash
python -m pip install -r requirements.txt
```

The CSV used by the notebook is not included. Obtain a lawful copy separately and keep it outside version control.

## Notebook and modeling expectations

- Preserve the original analysis unless a change is intentional and explained.
- Use accurate variable names, axis labels, units, and chart captions.
- Document data cleaning and transformations.
- Never fit preprocessing on held-out test data.
- Treat nominal categories as categories, not ordered quantities.
- Select a validation design that matches the intended future prediction task.
- Report MAE, RMSE, MSE, and R-squared where relevant, with currency, dataset version, sample size, and split details.
- Do not describe a metric as improved unless it was measured under a comparable evaluation design.
- Use synthetic fixtures for tests. Do not commit restricted datasets.

## Validation before submitting

- Validate notebook JSON and code-cell syntax.
- Run affected cells from a restarted kernel when the required dataset is available.
- State which checks you ran and which could not be run.
- Verify all documentation links and update the docs when behavior changes.
- Review notebook outputs for personal data, credentials, private paths, and excessive output.

GitHub Actions performs structural and syntax checks. A green workflow does not demonstrate model accuracy or successful execution against an external CSV.

## Pull requests

Use the repository pull request template. Explain the motivation, implementation, validation evidence, impact on data or methodology, and any remaining limitations. Include no personal passenger data or credentials in the description, screenshots, or logs.

## Scope

Do not add a web application, API, database, deployment environment, or unrelated features as part of a documentation or maintenance change. Propose substantial architectural changes separately so they can be evaluated on their merits.
