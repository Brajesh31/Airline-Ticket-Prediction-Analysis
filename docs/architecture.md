# Architecture

The project is one interactive notebook, not a packaged application.

```text
CSV in Colab /content path -> pandas DataFrame -> plots
                           -> LabelEncoder features
                           -> train_test_split
                           -> LinearRegression
                           -> MSE and R-squared
                           -> example prediction
```

Nine predictors are used: airline, source city, departure time, stops, arrival time, destination city, class, duration and days-left. `PRICE` is the target. No reusable module, CLI, persisted model, API or application is present.

Risks include encoders fitted before splitting, nominal categories interpreted as ordered integers, numeric fields encoded as labels, random splitting of related records, example prediction depending on known categories, and a flight-number plot label that does not match its x series.

A future design should separate loading/validation, exploration, preprocessing, split strategy, training and evaluation. A Pipeline and ColumnTransformer should fit transforms only on training folds. This is proposed work, not current functionality.
