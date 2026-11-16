# Roadmap

This roadmap describes possible maintenance and research improvements. It is not a statement that these features are implemented or scheduled.

## Priority 1: Correctness and data transparency

- [ ] Fix the mismatch between the second scatter plot's axis label and x data.
- [ ] Replace the hard-coded dataset location with a documented configuration or notebook parameter.
- [ ] Add required-column and data-type validation.
- [ ] Record dataset source, license, collection period, currency, and schema.
- [ ] Define a documented missing-value and duplicate-record policy.

## Priority 2: Modeling validity

- [ ] Move preprocessing into a scikit-learn Pipeline and ColumnTransformer.
- [ ] Use OneHotEncoder for nominal categories.
- [ ] Preserve duration and days-left as numeric measurements.
- [ ] Prevent preprocessing leakage by fitting transforms only on training folds.
- [ ] Evaluate temporal or group-aware splits appropriate to the prediction use case.
- [ ] Add MAE, RMSE, baseline comparisons, residual analysis, and segment-level errors.

## Priority 3: Software quality

- [ ] Extract reusable data preparation and model evaluation functions.
- [ ] Add unit tests using synthetic data.
- [ ] Add a documented experiment configuration and dataset version record.
- [ ] Add notebook execution testing with a small synthetic fixture if the project is refactored to support it.
- [ ] Define a release and dependency update process.

## Out of scope unless separately proposed

A web application, API, database, live fare ingestion, automated booking, and production deployment are not current project capabilities. They should be considered only when a concrete user need, data rights, security model, and maintenance plan exist.
