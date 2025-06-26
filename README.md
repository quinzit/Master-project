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
```

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
```bash
output/images/product_<product_id>/
```
---

## References

1. Ramos, P., Santos, N., & Rebelo, R. (2015). *Performance of state space and ARIMA models for consumer retail sales forecasting*. Robotics and Computer-Integrated Manufacturing, 34, 151–163. https://doi.org/10.1016/j.rcim.2015.01.002

2. Parmezan, A. R. S., Souza, V. M., & Batista, G. E. (2019). *Evaluation of statistical and machine learning models for time series prediction: Identifying the state-of-the-art and the best conditions for the use of each model*. Information Sciences, 484, 302–337. https://doi.org/10.1016/j.ins.2019.01.076
   
---

## Acknowledgements

This project was supported through academic, business, and domain expertise by:

- **Dr. Debarati Bhaumik** — Academic Supervisor, Amsterdam University of Applied Sciences (HvA)  
- **Mr. Raymond Dinh** — Company Supervisor, LTP Company  
- **Mr. Trung Nguyen** — Independent Expert in Inventory and Supply Chain Management

Their guidance and feedback contributed significantly to the design and evaluation of the forecasting models.

---

## Contact

This project was developed by **Quynh Hoang**  as part of the Master’s Thesis in the **Digital Driven Business** program  at the **Amsterdam University of Applied Sciences (HvA)**,  in collaboration with **LTP Company**.

For academic or project-related inquiries, please contact:  [quynh.hoang@hva.nl](mailto:quynh.hoang@hva.nl)

---

