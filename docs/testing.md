# Testing and validation

## Automated checks

GitHub Actions runs repository checks for relevant changes. The notebook-quality workflow:

- Installs dependencies declared in `requirements.txt`.
- Parses notebook JSON.
- Verifies notebook v4 structure and non-empty cells.
- Parses each non-empty Python code cell with Python's AST parser.
- Checks relative links in the root README.

These checks validate structure and syntax. They do not execute notebook cells or validate statistical correctness.

## Manual notebook validation

When an authorized dataset copy is available:

1. Confirm required columns and actual data types.
2. Restart the notebook kernel.
3. Run all cells in order.
4. Confirm that each chart uses the intended x and y series.
5. Inspect warnings, exceptions, missing values, and implausible values.
6. Recompute metrics on the documented test partition.
7. Compare model results to a simple baseline.
8. Inspect error distributions and relevant route/airline/class segments.

## Model tests to add

A future maintainable modeling module should include tests for:

- Missing required columns.
- Unexpected or unseen categorical values.
- Missing, negative, or malformed prices.
- Duration and days-left parsing.
- Duplicate and near-duplicate observations.
- Train/test separation and preprocessing fit boundaries.
- Stable output shape and finite predictions.
- Metric calculation against known synthetic values.
- Pipeline behavior on categories not observed during training.

Use small synthetic test data rather than distributing the project's external CSV.

## What CI cannot currently verify

The complete analysis cannot be run in CI because its required CSV is not checked in and no permitted public download source is configured. Do not mistake a green syntax-validation job for a successful model training run.
