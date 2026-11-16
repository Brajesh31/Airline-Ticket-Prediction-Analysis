# Project architecture

## Current architecture

This repository is a single-notebook analysis project. It does not contain a separately packaged application, service layer, database, or model-serving endpoint.

```text
Authorized external CSV
        |
        v
PDS_PROJECT.ipynb
        |
        +--> pandas DataFrame loading
        |
        +--> Matplotlib exploratory plots
        |
        +--> LabelEncoder preprocessing
        |
        +--> train_test_split (80/20, random_state=42)
        |
        +--> LinearRegression fit
        |
        +--> MSE and R-squared output
        |
        +--> illustrative single-row prediction
```

## Main components

**Input:** A CSV with the column names referenced in the notebook. The file is absent from the Git repository.

**Exploration:** pandas loads the tabular data. Matplotlib plots price against days remaining and contains a second chart with a known label/data mismatch.

**Preprocessing:** LabelEncoder is applied to selected fields. It is currently fitted over the complete data before the split. This should be changed in a future modeling revision to ensure transformations are learned only from training folds.

**Estimator:** scikit-learn LinearRegression estimates a continuous ticket-price target from nine selected predictors.

**Evaluation:** The notebook calculates mean squared error and R-squared for a random held-out partition. No automated benchmark or statistical validation pipeline is included.

## Boundaries

The following components do not exist in the current repository: a REST API, front-end user interface, persistent database, ingestion scheduler, model registry, packaged inference service, monitoring, authentication, or deployment infrastructure. The API and database guides explicitly document that these are not present.

## Suggested future separation

If the notebook grows into a maintained application, consider separating data validation, feature preprocessing, model training, evaluation, and inference into tested Python modules. Keep notebooks for exploration and communication, and make the training pipeline reusable and testable outside the notebook.
