# Troubleshooting

**CSV FileNotFoundError:** notebook reads `/content/AIRLINES DATASET PRACTICAL - Sheet1.csv`. Confirm it exists in Colab or update the path.

**Missing package:** activate the environment and install `jupyter pandas matplotlib scikit-learn` with pip.

**LabelEncoder cannot transform a value:** example values must exist in encoder classes. Duration and days-left are currently strings; a fitted Pipeline with unknown-category handling is safer.

**Results differ:** check data/package versions, seed, cell order, preprocessing and split design. Current split uses `random_state=42`.

**Metrics look too optimistic:** inspect duplicate itineraries, related route/date observations across partitions, target-derived fields and transforms fitted before splitting.

**Plot label mismatch:** the second plot labels flight number but uses `DAYS_LEFT`.

**Stale output:** restart kernel, clear outputs and run all cells in order.
