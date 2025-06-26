# Weekly Sales Forecasting for Product Demand Estimation

This repository presents a comprehensive approach to forecasting weekly product sales using both classical time series models and tree-based machine learning algorithms. The objective is to develop a scalable, accurate, and reproducible forecasting pipeline that can generalize across multiple products with minimal manual adjustment.

---

## Project Overview

Accurate sales forecasting is crucial for inventory management, supply chain optimization, and business planning. This project:

- Compares traditional time series models with modern tree-based machine learning methods.
- Builds both univariate and multivariate forecasting pipelines.
- Evaluates models using robust metrics (RMSE, MAE) on a hold-out test set.
- Focuses on scalability and minimal manual intervention for multiple products.

---

## Project Structure

```
forecasting_project/
├── data/           # Input datasets (one CSV file per product)
├── notebooks/      # Exploratory notebooks and prototypes
├── scripts/        # Main automation scripts
├── utils/          # Modular Python files for each model
│   ├── univariate/     # Holt, ARIMA, tree models (univariate)
│   └── multivariate/   # ARIMAX, tree models (multivariate)
├── output/         # Results, logs, trained models, forecast plots
│   ├── results/
│   ├── models/
│   ├── logs/
│   └── images/
├── requirements.txt    # Python dependencies
└── README.md           # Project documentation
```

---

## Methodology

### 1. Univariate Forecasting

Models weekly sales as a function of time only. Methods include:

- **Holt’s Exponential Smoothing:** Manual tuning of smoothing parameters.
- **ARIMA:** Manual or automated order selection.
- **Tree-based Models:** XGBoost, LightGBM, CatBoost using time indices as features.

Validation: Cross-validation and holdout validation tailored to each model.

### 2. Multivariate Forecasting

Incorporates additional predictors:

- Unit price
- Discount rate
- Product group/category

Models:

- **ARIMAX:** Time series with exogenous variables.
- **Tree-based Models:** With engineered features.

Validation: Time-based cross-validation or walk-forward validation.

---

## Getting Started

### 1. Environment Setup
We recommend creating a virtual environment:

```bash
python -m venv venv
venv\Scripts\activate        # Windows
# or
source venv/bin/activate     # macOS/Linux

pip install -r requirements.txt

### 2. Data Preparation

- Place your cleaned product-level CSV files inside the data/ folder.
- Each file should be named like: product_<product_id>.csv
- Each dataset must include:
    + A date column (e.g., week_start)
    + A target column (e.g., WeeklySales)
    + Optional features for multivariate modeling

### 3. Running the Pipeline

- Use scripts in the `scripts/` directory to train and evaluate models.
- What this will do:

    + Train Holt, ARIMA, and tree-based models (Univariate and Multivariate)
    + Evaluate performance using RMSE and MAE
    + Save model results in output/results/
    + Save forecast plots in output/images/
    + Log process details in output/logs/

---

## Evaluation

Model performance is assessed using:

- **Root Mean Squared Error (RMSE)**
- **Mean Absolute Error (MAE)**

Comparisons are made across products and model types to identify the best-performing approach.

---

## Forecast Plots

Each model generates a prediction plot comparing actual vs. predicted sales on the test set. These plots are stored in:
output/images/product_<product_id>/

---

## references


---

## Contact
This project was developed by Quynh Hoang
Master’s Thesis at Amsterdam University of Applied Sciences (HvA)
In collaboration with LTP Company
For academic inquiries, please contact: quynh.hoang@hva.nl
