# Development

Keep changes focused on correctness and reproducibility. Confirm data rights and provenance, validate columns and types, run from a fresh kernel, fit preprocessing only on training folds, choose validation appropriate to the task, compare metrics with a baseline, remove stale outputs and sensitive data, and update docs when assumptions change.

Use a Pipeline to prevent leakage. Prefer one-hot encoding for nominal fields and preserve numeric semantics. Extract reusable modules and add tests if the notebook grows. Pull requests should describe changed cells, data source, environment, validation, metrics and caveats. Do not claim improvement from training metrics alone.
