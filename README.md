# Air Passengers Time-Series Forecasting

A time-series forecasting project comparing multiple approaches on the classic Air Passengers dataset (144 monthly observations, 1949-1960).

## Project Overview

**Objective:** Predict monthly airline passenger counts using time-series forecasting techniques.

**Dataset:** 144 monthly records of airline passengers (in thousands) from 1949-1960.

**Approach:** Compare baseline models against ML approaches using proper time-based validation.

## Models Compared

| Model | MAPE |
|-------|------|
| **Linear Regression** | **4.40%** |
| XGBoost | 8.55% |
| Seasonal Naive | 9.15% |
| Naive Baseline | 10.26% |

**Best model (Linear Regression) achieves 57% MAPE improvement over naive baseline.**

## Key Methodology

- **Train/Test Split:** Time-based (last 20% held out), no random shuffling
- **Feature Engineering:**
  - Lag features (t-1, t-2, t-3, t-12)
  - Rolling statistics (3-month and 12-month windows)
  - Calendar features (month, quarter)
  - Trend component
- **Evaluation:** MAPE and MAE on held-out test set

## Repository Structure

```
├── AirPassengers.csv           # Dataset
├── air_passengers_forecasting.ipynb  # Main analysis notebook
├── README.md                   # This file
```

## Key Findings

1. **Seasonality dominates:** The lag_12 feature (same month last year) is highly predictive
2. **Trend matters:** Long-term growth trend improves all models
3. **Linear Regression wins:** On small datasets with clear patterns, simpler models often outperform complex ones
4. **Proper validation is critical:** Time-based splits prevent data leakage

## Tech Stack

- Python 3.10+
- pandas, NumPy
- scikit-learn
- XGBoost
- matplotlib

## How to Run

```bash
pip install pandas numpy scikit-learn xgboost matplotlib
jupyter notebook air_passengers_forecasting.ipynb
```

## Author

Gabriel Blackstock
