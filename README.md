# Sales Forecasting for a Small Retailer

This repository contains a small exploratory and modeling notebook for forecasting sales (final transaction amount) from a grocery transactions dataset.

**Contents**

- `grocery.csv` — primary dataset of transactions (transaction_date, quantity, unit_price, total_amount, discount_amount, final_amount, loyalty_points, store_name, etc.).
- `main.ipynb` — Jupyter Notebook with data loading, cleaning, exploratory data analysis (visualizations), feature engineering, and a simple linear regression model.

**Project Overview**

The goal is to explore transaction-level grocery data and build a baseline model that predicts `final_amount` from transaction features. The notebook covers basic preprocessing, EDA (histograms, boxplots, pairplots, heatmap), simple feature engineering (date parts, discount ratio), and a Linear Regression model with an R² score and an Actual vs Predicted scatter plot.

Quick summary of what `main.ipynb` does:

- Reads `grocery.csv` and parses `transaction_date` as datetime.
- Cleans numeric columns (`quantity`, `unit_price`, `total_amount`, `discount_amount`, `final_amount`) and drops rows with missing core values.
- Visualizes distributions and relationships using `seaborn` and `matplotlib` (histograms, countplot per store, correlation heatmap, pairplot, boxplot).
- Adds engineered features: `year`, `month`, `day`, `dayofweek`, and `discount_ratio`.
- Trains a `LinearRegression` model using features `['quantity','unit_price','discount_amount','loyalty_points','discount_ratio','dayofweek']` to predict `final_amount` and reports R².

Requirements

This project uses standard Python data science libraries. Install them with pip:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
# optional: xgboost (not used in the notebook by default)
pip install xgboost
```

How to run

- Open and run interactively with Jupyter Notebook or JupyterLab:

```bash
jupyter lab
# or
jupyter notebook
```
- To execute the notebook headlessly (run all cells) and produce an executed notebook:

```bash
jupyter nbconvert --to notebook --execute main.ipynb --output main_executed.ipynb
```

Notes about plotting

The notebook sets `matplotlib` to use the `Agg` backend to allow headless execution in some environments. When running interactively, plots will display in the notebook.

Project structure

- `grocery.csv` — dataset (place your CSV here)
- `main.ipynb` — analysis and modeling notebook
- `README.md` — this file

Modeling and results

The current baseline model is an ordinary least-squares `LinearRegression` predicting `final_amount`. The notebook prints the R² score and shows an Actual vs Predicted scatter plot. This is intended as a starting point; improvements can be made with feature engineering, more expressive models, and careful validation.

Suggested next steps

- Add a `requirements.txt` or `environment.yml` for reproducible environments.
- Try regularized linear models (Ridge/Lasso) and tree-based models (RandomForest, XGBoost) with cross-validation.
- Engineer features at transaction or store level (e.g., rolling averages, store seasonality, promotions flags).
- Handle outliers and currencies carefully if present; investigate extreme `final_amount` values.
- Add unit tests or a small evaluation script to reproduce metrics.

Contact

If you have questions or want help iterating on models or visualizations, open an issue or contact the project owner.


