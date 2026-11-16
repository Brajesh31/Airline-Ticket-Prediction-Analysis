# Modeling methodology

The notebook uses scikit-learn `LinearRegression`, nine predictors and `PRICE` as target. It uses a random 80/20 split with `random_state=42` and prints MSE and R-squared. Recompute metrics against the exact dataset; no validated performance figure is asserted here.

`LabelEncoder` is fitted before splitting, exposing held-out categories to preprocessing and potentially failing for unseen categories. Integer codes for nominal fields can be interpreted as ordered distances. `DURATION` and `DAYS_LEFT` are numeric-like and should normally remain numeric.

A stronger approach uses `ColumnTransformer`, `OneHotEncoder(handle_unknown="ignore")` and a `Pipeline`, fitting transformations only inside training folds. Compare against a naive baseline and alternative regressors. Choose chronological validation for future booking-price prediction or group-aware splitting for repeated flights/routes. Report MAE, RMSE and R-squared with currency, dataset version, test population and split boundaries. Inspect errors by route, airline, class and days-left range.

The example converts duration and days-left to strings for encoding and may fail if those categories are not present. A fitted Pipeline and explicit input validation are safer.
