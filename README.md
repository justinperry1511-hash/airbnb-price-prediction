# Airbnb Price Prediction & Market Segmentation

End-to-end machine learning project analyzing 7,000+ Austin Airbnb listings to predict nightly prices and segment the market into distinct customer tiers using R.

## Overview

This project addresses a real pricing problem faced by Airbnb hosts and the platform itself: how should a listing be priced? Using publicly available listing data, I built a price prediction model and a market segmentation framework that together can inform both host pricing strategy and platform-level recommendations.

## Results

| Model | Accuracy |
|-------|----------|
| Linear Regression | 13.96% |
| Support Vector Machine (SVM) | 16.57% |
| **Random Forest** | **91.72%** |

**Final model (Random Forest):**
- R² = 0.9723 — explains 97.23% of price variation
- RMSE = $27.51
- MAE = $8.19

## Market Segmentation

K-means clustering (K=3, validated via Elbow Method and Silhouette Scores) identified three distinct listing tiers:

| Cluster | Avg Price | Avg Guests | Superhost Rate | Profile |
|---------|-----------|------------|----------------|---------|
| 1 | $359.24 | 9.52 | 58.3% | Luxury / large group |
| 2 | $149.76 | 4.00 | 53.7% | Mid-range / small group |
| 3 | $142.33 | 2.28 | 31.2% | Budget / solo traveler |

## Key Price Drivers

- **Accommodates** — capacity is the strongest predictor of price
- **Bedrooms** — more bedrooms = higher price
- **Superhost status** — superhosts command a price premium
- **Number of reviews** — established listings price higher

## Methodology

### Data Preparation
- Removed rows with missing values in key columns
- Converted categorical variables (`room_type`, `host_is_superhost`) to numeric
- Scaled all numeric features for clustering comparability

### Feature Engineering
- `accommodates_bedroom_ratio`
- `accommodates_bathroom_ratio`
- `price_per_bedroom`

### Modeling
- Compared Linear Regression, SVM, and Random Forest
- Random Forest selected for its ability to handle complex, non-linear relationships
- Hyperparameters tuned via grid search: `mtry = 3`, `min.node.size = 5`, `num.trees = 1000`

## Tech Stack

- **Language:** R
- **Libraries:** `tidyverse`, `caret`, `ranger`, `tidymodels`, `parsnip`, `cluster`, `ggplot2`, `scales`

## Files

```
Final_Project.Rmd       # Full analysis with code and narrative
Final_Project.pdf       # Rendered report with results and visualizations
```

## Running the Analysis

1. Clone the repo and open `Final_Project.Rmd` in RStudio
2. Place `austin_listings.csv` in the same directory
3. Install required packages:

```r
install.packages(c("tidyverse", "cluster", "caret", "ranger", "tidymodels", "parsnip", "scales"))
```

4. Knit the document to reproduce all results

## Author

Justin Perry — [LinkedIn](https://linkedin.com/in/justin-perry-4b1275232)
