# Known limitations

- Input CSV is absent and provenance is undocumented.
- Notebook path is hard-coded to Colab.
- Saved output shows 2,030 rows and 12 columns, not a verified data specification.
- Encoders are fitted before splitting.
- Nominal categories are integer-coded for linear regression.
- Duration and days-left are encoded as categories.
- Random split may mix related observations and may not represent future prices.
- Second scatter plot label does not match its x values.
- Example prediction may fail for unseen encoder values.
- No pinned dependencies, test suite, API, database, deployment or monitoring exists.
- No model performance is guaranteed for current fares.
