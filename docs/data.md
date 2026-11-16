# Data dictionary, provenance and quality

## Data dependency

The notebook expects a file named `AIRLINES DATASET PRACTICAL - Sheet1.csv`. The file is not included in the repository. It must be acquired separately from a source that permits the intended analysis.

Notebook output previously saved in the file displays 2,030 rows and 12 columns. That is an output snapshot, not a verified current dataset contract. The notebook's code explicitly references the following 11 fields:

| Field | Current role | Interpretation |
|---|---|---|
| `AIRLINES` | Predictor | Airline category |
| `FLIGHT_NO.` | Not in regression feature list | Flight identifier used in a plot label |
| `SOURCE_CITY` | Predictor | Origin city |
| `DEPARTURE_TIME` | Predictor | Departure time category |
| `STOPS` | Predictor | Number/category of stops |
| `ARRIVAL_TIME` | Predictor | Arrival time category |
| `DESTINATION_CITY` | Predictor | Destination city |
| `CLASS` | Predictor | Cabin/fare class |
| `DURATION` | Predictor | Flight duration |
| `DAYS_LEFT` | Predictor | Days remaining before departure |
| `PRICE` | Target | Ticket price |

Confirm exact spelling, types and the unexplained twelfth column against the actual source file before executing the notebook.

## Provenance that must be recorded

Before publishing metrics or redistributing a dataset, record:

- Original provider and source URL or acquisition reference.
- Acquisition date and date range covered by observations.
- Dataset version, checksum, or immutable snapshot identifier.
- Geographic and route coverage, airline coverage, and fare classes.
- Price currency and whether taxes, baggage, seat selection, and other fees are included.
- License, terms of use, attribution obligations, and redistribution permission.
- Collection method and known sampling or selection bias.
- Data dictionary and the meaning of every field.

The repository currently does not establish these details. Do not infer them from column names.

## Data quality checks

A responsible analysis should inspect:

- Missing values by field and row.
- Duplicate records and repeated itineraries.
- Negative or implausible prices.
- Invalid city, airline, or cabin categories.
- Impossible or inconsistent duration values.
- Negative or implausible days-left values.
- Currency consistency and mixed units.
- Outliers and whether they represent genuine fares or data errors.
- Whether flight identifiers are unique, reused, or anonymized.

Record every filter and transformation so the analyzed row count can be reconciled to the source.

## Leakage and target integrity

Ensure that the target `PRICE` and any derived target information do not appear in predictors. Fit learned preprocessing only on training data, using a scikit-learn Pipeline or equivalent workflow. Consider repeated flight identifiers or near-duplicate itineraries when designing train/test splits.

## Privacy and redistribution

Do not commit passenger names, email addresses, phone numbers, booking references, ticket numbers, payment data, or other personal information. Do not redistribute a dataset merely because it was downloadable. Follow the provider's license and applicable terms. Keep local datasets out of version control.
