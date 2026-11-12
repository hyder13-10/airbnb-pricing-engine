Business question: What should a host charge per night, and which features add the most value?

# Airbnb Pricing Engine (New York City)

**Business question:** What should a host charge per night, and which features add the most value?

## Data
Inside Airbnb detailed listings for New York City (~29.9k listings, 90 columns). Raw data is not committed (see `.gitignore`); download it from insideairbnb.com/get-the-data.

## Progress
**Day 1:** Repo setup, data loaded, initial exploration.

**Day 2: Cleaning (in progress)**
- Dropped empty columns and kept ~25 relevant features.
- Removed columns that would leak the target (price quotes, estimated revenue/occupancy).
- Dropped ~35% of rows with no price. Price is the target, so it is never imputed.
- Filled `beds` and `bedrooms` with the median.
- Kept review scores as NaN (missing means "no reviews yet") and added a `has_reviews` flag.
- Converted `bathrooms_text` into a numeric `bathrooms` column.
- Price is heavily right-skewed (median ~$180, max originally $31k+), so I plotted it on a log scale.
- Removed price outliers by filtering (not capping): kept $25 to the 99th percentile (~$1,849). This removed 202 rows (~1%), leaving 19,097.
- Next: type fixes, save the clean dataset.

## Planned
EDA, feature engineering, XGBoost model, SHAP explanations, error analysis, Streamlit app.

## Status
Day 2 of 10