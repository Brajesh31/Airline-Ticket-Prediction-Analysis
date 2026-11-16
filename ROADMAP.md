# Roadmap

Planned work only. These items are not implemented yet.

## Data and reproducibility
- [ ] Document authoritative data source, license, collection period and currency.
- [ ] Add schema and data-quality validation.
- [ ] Pin tested dependencies.
- [ ] Replace hard-coded Colab path with configurable input.

## Modeling
- [ ] Correct scatter plot label/data mismatch.
- [ ] Replace global LabelEncoder preprocessing with train-fitted Pipeline.
- [ ] Preserve numeric duration and days-left values.
- [ ] Add leakage-aware chronological or grouped validation.
- [ ] Compare naive, regularized linear and tree-based baselines.
- [ ] Report MAE, RMSE, R-squared and residual diagnostics.

## Engineering
- [ ] Extract reusable functions.
- [ ] Add synthetic-fixture tests.
- [ ] Add notebook validation and test automation.
- [ ] Define artifact versioning and monitoring before any deployment.