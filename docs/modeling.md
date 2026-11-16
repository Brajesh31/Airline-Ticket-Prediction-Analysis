# Modeling methodology

## Current implementation

The notebook uses nine predictors:

`AIRLINES`, `SOURCE_CITY`, `DEPARTURE_TIME`, `STOPS`, `ARRIVAL_TIME`, `DESTINATION_CITY`, `CLASS`, `DURATION`, and `DAYS_LEFT`.

The target is `PRICE`. The notebook applies LabelEncoder to every selected predictor, splits rows using `train_test_split(test_size=0.2, random_state=42)`, fits scikit-learn `LinearRegression`, and prints MSE and R-squared.

These are descriptions of the checked-in code, not an endorsement of its statistical validity. Metrics depend on the external CSV and cannot be reproduced from repository contents alone.

## Methodological concerns

### Preprocessing leakage

The notebook fits each LabelEncoder before splitting into training and test rows. This exposes the preprocessing stage to the full dataset, including the held-out partition. Use a Pipeline and fit transformations only within training folds.

### Nominal categories treated as ordered numbers

Airline names, cities, departure-time categories, and cabin classes do not have natural numeric distances. Assigning integer labels can cause a linear model to treat arbitrary code differences as meaningful. OneHotEncoder is generally a more defensible starting point for nominal features.

### Numeric features encoded as labels

Duration and days-left are numeric-like measurements. Converting their distinct values into class labels discards numeric spacing. Parse them into consistent numeric units, validate ranges, and preserve them as numeric features.

### Split design

A random row split may put near-duplicate flights or related observations in both training and test partitions. If the intended use is predicting future fares, consider a chronological split based on booking or departure time. If repeated itineraries exist, consider group-aware validation. The correct design depends on the dataset and deployment question.

### Prediction input fragility

The example prediction transforms strings using fitted encoders. Any category absent during fitting can raise an error. A fitted preprocessing Pipeline with explicit input validation and `handle_unknown="ignore"` for one-hot categories is safer.

## Recommended baseline redesign

A future revision should:

1. Validate required columns, types, missingness, and target range.
2. Separate nominal categorical and numeric columns.
3. Use `ColumnTransformer` with `OneHotEncoder(handle_unknown="ignore")` for nominal data and numeric imputation/scaling where appropriate.
4. Wrap preprocessing and the estimator in a scikit-learn Pipeline.
5. Choose a split strategy that matches future prediction and repeated-record structure.
6. Compare LinearRegression with a simple naive baseline and suitable alternative regressors.
7. Report MAE, RMSE, MSE, and R-squared.
8. Inspect residuals and segment performance by airline, route, class, and days-left interval.
9. Persist the validation design, data version, feature definitions, and random seeds.

## Metric interpretation

MSE is expressed in squared price units, which can be difficult to interpret. RMSE returns to the target's price unit. MAE measures average absolute error in the same unit. R-squared describes variance explained relative to a constant-mean baseline and can be negative on held-out data.

Never publish a bare score. Include currency, dataset version, test split, sample count, and evaluation date. See [reproducibility.md](reproducibility.md).
