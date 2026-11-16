# FAQ

## Is this a live fare predictor?
No. It is an educational notebook with an illustrative linear regression baseline.

## Where is the CSV?
The notebook expects `AIRLINES DATASET PRACTICAL - Sheet1.csv` in Colab `/content`. It is not included.

## Why does it fail locally?
Update the hard-coded `pd.read_csv` path to a permitted local copy.

## What model is implemented?
scikit-learn LinearRegression.

## Are prices guaranteed?
No. Outputs are not live quotes and depend on data freshness, quality and validation.

## Why is LabelEncoder a concern?
Nominal codes can be treated as ordered values, and current encoders are fitted before splitting.

## Is there a database or API?
No.

## What should improve first?
Document provenance/license, correct preprocessing, select representative validation and compare against a baseline using MAE/RMSE as well as R-squared.
