# Reproducibility

## Current limitations

The repository contains the notebook but not the CSV it reads. Its saved output cells may reflect a dataset version that is unavailable to a new user. Consequently, a fresh checkout cannot reproduce model metrics until an authorized copy of the input dataset is supplied.

The notebook uses `random_state=42` for its random train/test split, but this alone does not make the analysis reproducible. Dataset identity, preprocessing, package versions, and split semantics matter as well.

## Experiment record

For each reported run, record:

| Item | Record |
|---|---|
| Dataset source | Provider and acquisition reference |
| Dataset version | Version, snapshot date, or checksum |
| Dataset period | Earliest/latest observation dates |
| Dataset size | Rows before and after cleaning |
| Schema | Field names and data types |
| Target | Price field and currency |
| Cleaning | Filters, missing-value policy, duplicate handling |
| Features | Exact predictors and transformations |
| Split | Random, temporal, or group-aware; boundaries and seed |
| Environment | Python and dependency versions |
| Model | Estimator and hyperparameters |
| Results | MAE, RMSE, MSE, R-squared and sample count |

## Repeatable execution

- Use the same authorized dataset snapshot.
- Install dependencies from `requirements.txt`.
- Record any manual notebook edits and execution order.
- Restart the kernel and run cells from top to bottom.
- Save outputs only when they can be shared lawfully and do not expose private records.
- Record the exact split and preprocessing strategy with the reported metrics.

## Future improvement

For stronger reproducibility, move data loading and model training into reusable functions, add a machine-readable experiment configuration, and use a Pipeline so preprocessing and model fitting cannot accidentally diverge between training and evaluation.
