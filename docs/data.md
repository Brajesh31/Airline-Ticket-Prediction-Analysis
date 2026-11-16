# Data and provenance

The notebook expects `AIRLINES DATASET PRACTICAL - Sheet1.csv` at `/content/AIRLINES DATASET PRACTICAL - Sheet1.csv`. The CSV is not committed. Saved notebook output displays 2,030 rows and 12 columns, but that is only an output snapshot.

| Field | Role | Notes |
| --- | --- | --- |
| `AIRLINES` | Predictor | Airline category |
| `FLIGHT_NO.` | Available/displayed | Not a regression predictor |
| `SOURCE_CITY` | Predictor | Origin city |
| `DEPARTURE_TIME` | Predictor | Time-of-day category |
| `STOPS` | Predictor | Stop-count category |
| `ARRIVAL_TIME` | Predictor | Time-of-day category |
| `DESTINATION_CITY` | Predictor | Destination city |
| `CLASS` | Predictor | Cabin/fare class |
| `DURATION` | Predictor | Numeric-like duration |
| `DAYS_LEFT` | Predictor | Days before departure |
| `PRICE` | Target | Currency unspecified |

The displayed table has 12 columns, while the notebook references 11 named fields. Confirm the complete schema with the provider. Document source, collection period, route coverage, currency, taxes/fees, license and refresh cadence. Inspect missing values, duplicates, invalid prices and impossible duration or days-left values. Never commit passenger identities, booking references, payment or contact data. Do not redistribute data without permission.
