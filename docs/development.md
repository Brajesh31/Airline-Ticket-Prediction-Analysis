# Development guide

## Development scope

Contributions should improve the correctness, clarity, reproducibility, or maintainability of the existing notebook analysis. The project is not currently an API or deployed application.

## Local setup

Follow [installation.md](installation.md), install `requirements.txt`, and use an authorized local dataset copy. Do not commit the CSV or private data.

## Suggested workflow

1. Create a focused branch for your change.
2. Inspect the current notebook and relevant documentation before editing.
3. Keep changes scoped to one issue or improvement.
4. Restart the notebook kernel and execute affected cells in order when the dataset is available.
5. Validate notebook JSON and Python cell syntax.
6. Update documentation when behavior, assumptions, dependencies, or limitations change.
7. Open a pull request with validation evidence and any limitations.

## Notebook practices

- Use descriptive variable names and keep cell responsibilities clear.
- Explain non-obvious transformations in Markdown.
- Avoid hidden dependencies on files outside the repository without documenting them.
- Prefer deterministic operations and explicit random seeds.
- Do not claim a feature, metric, or chart is correct without validating its inputs.
- Keep outputs compact and remove accidentally exposed personal or restricted data.

## Modeling changes

For changes to preprocessing or evaluation, explain why the split matches the intended prediction task. Avoid fitting encoders, scalers, imputers, or feature selection on held-out data. Include comparisons with a baseline and report metrics with currency and dataset version.

## Pull request evidence

A contribution should state which notebook cells or files changed, the dataset version used for testing (if any), commands executed, metric changes with evaluation design, and any checks that could not be completed because the CSV was unavailable.
