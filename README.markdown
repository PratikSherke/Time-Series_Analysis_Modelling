# Automobiles Sales Time Series Analysis (1992–2019)

![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)
![Status](https://img.shields.io/badge/status-complete-brightgreen.svg)
![Jupyter](https://img.shields.io/badge/jupyter-notebook-orange.svg)

## Overview

This project conducts a detailed time series analysis of Automobiles sales in the US retail market from 1992 to 2019, using the `us_retail.csv` dataset. The analysis explores trends, seasonality, and stationarity in the data, applying various time series models to understand and forecast sales. The project includes Exploratory Data Analysis (EDA), stationarity tests, decomposition, and modeling with multiple forecasting techniques. A dedicated script provides a 5-year sales forecast (2020–2024) using the SARIMA model.

### Objectives
- Analyze historical Automobiles sales data to identify trends, seasonality, and correlations with other retail categories.
- Perform stationarity tests and apply transformations to prepare data for modeling.
- Implement and evaluate multiple time series forecasting models.
- Generate a 5-year sales forecast (2020–2024) using SARIMA and present results in a tabular format.
- Visualize key insights and model performance for better understanding.

## Dataset

The dataset (`us_retail.csv`) contains monthly retail sales data for various categories in the US from 1992 to 2019. Key columns include:
- **Month**: Date of sales (YYYY-MM).
- **Automobiles**: Sales of automobiles (in USD).
- **GeneralMerchandise**, **FoodAndBeverage**, **Clothing**, **Appliances**, **BuildingMaterials**: Other retail categories for multivariate analysis.

The dataset is sourced from the [U.S. Census Bureau Retail Sales Data](https://www.census.gov/retail/). Ensure you have permission to share this dataset if including it in the repository.

## Methodology

### Exploratory Data Analysis (EDA)
- **Summary Statistics**: Descriptive statistics for sales data across categories.
- **Time Series Plot**: Visualize Automobiles sales to identify trends and seasonality.
- **Seasonal Subseries Plot**: Box plots of monthly sales to highlight seasonal patterns.
- **Additional Analyses** (from notebook):
  - Correlation analysis to explore relationships between retail categories.
  - Distribution analysis (histograms, KDE) to assess sales distribution.
  - Rolling statistics to evaluate volatility over time.

### Stationarity Testing
- **ADF Test**: Tests for unit root to check stationarity (p-value < 0.05 indicates stationarity).
- **KPSS Test**: Tests for trend-stationarity (p-value > 0.05 indicates stationarity).
- **Transformations**: Applied differencing, log, square root, and Box-Cox transformations to achieve stationarity.

### Time Series Decomposition
- **Classical Decomposition (Additive)**: Separates data into trend, seasonal, and residual components.
- **STL Decomposition**: Robust decomposition for complex seasonality.

### Forecasting Models
- **AutoRegressive (AR)**: Models with lag order 30.
- **Moving Average (MA)**: Models with moving average order 30.
- **ARMA**: Combines AR and MA with orders (7,0,7).
- **ARIMA**: Includes differencing with orders (7,1,7).
- **SARIMA**: Seasonal model with orders (7,1,7)(1,1,1,12).
- **VAR**: Multivariate model using Automobiles and BuildingMaterials.
- **VARMAX**: Extended VAR with MA components (order 14,14).
- **Smoothing Techniques**: Simple Moving Average (SMA), Weighted Moving Average (WMA), Exponential Moving Average (EMA), Simple Exponential Smoothing (SES), Double Exponential Smoothing (DES), and Triple Exponential Smoothing (TES).

### 5-Year Forecast
- A dedicated script (`sarima_forecast.py`) uses the SARIMA model to forecast Automobiles sales for 2020–2024 (60 months).
- Outputs a formatted table with forecasted sales and 95% confidence intervals, a visualization, and a CSV file (`automobiles_sales_forecast_2020_2024.csv`).

### Model Evaluation
- Metrics: RMSE, MAE, MSE, MAPE, AIC, BIC.
- Visualizations: Actual vs. predicted sales plots, ACF/PACF for parameter estimation.
- Tests: Granger Causality, Ljung-Box, and KS tests to validate model assumptions.

## Requirements

To run the project, install the required Python packages listed in `requirements.txt`:

```bash
pip install -r requirements.txt
```

Key dependencies:
- Python 3.8+
- pandas
- numpy
- matplotlib
- seaborn
- statsmodels
- scikit-learn
- scipy
- tabulate (for forecast table)

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/automobiles-sales-time-series.git
   cd automobiles-sales-time-series
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Ensure the dataset (`us_retail.csv`) is in the project directory.

## Usage

### Running the Analysis
1. Open and run the Jupyter notebook:
   ```bash
   jupyter notebook SALES_time_series_project.ipynb
   ```
2. The notebook will:
   - Perform EDA with visualizations (e.g., time series plots, seasonal subseries).
   - Conduct stationarity tests and transformations.
   - Fit and evaluate multiple forecasting models.
   - Generate plots and performance metrics.

### Generating the 5-Year Forecast
1. Run the forecasting script:
   ```bash
   python sarima_forecast.py
   ```
2. The script will:
   - Fit the SARIMA model and forecast sales for 2020–2024.
   - Display a formatted table of forecasted sales and confidence intervals.
   - Plot historical and forecasted sales.
   - Save the forecast to `automobiles_sales_forecast_2020_2024.csv`.

## Results

- **EDA Insights**:
  - Automobiles sales exhibit a clear upward trend and strong annual seasonality (e.g., peaks in December).
  - High correlations with GeneralMerchandise and BuildingMaterials, indicating economic linkages.
  - Sales distribution is right-skewed, with occasional high sales periods.
- **Stationarity**: Original data is non-stationary (ADF p-value > 0.05, KPSS p-value < 0.05). First differencing achieves stationarity.
- **Model Performance**: SARIMA and Triple Exponential Smoothing outperform simpler models (AR, MA, ARMA) in capturing seasonality, with lower RMSE and MAPE.
- **Multivariate Models**: VAR and VARMAX leverage relationships with BuildingMaterials, improving short-term forecast accuracy.
- **Forecast**: The 5-year SARIMA forecast (2020–2024) provides monthly sales predictions with confidence intervals, saved as a CSV and visualized.

## Project Structure

```
automobiles-sales-time-series/
├── SALES_time_series_project.ipynb  # Main Jupyter notebook for analysis
├── sarima_forecast.py               # Script for 5-year SARIMA forecast
├── us_retail.csv                    # Dataset (if permitted to share)
├── requirements.txt                 # Python dependencies
├── .gitignore                       # Git ignore file
└── README.md                        # Project documentation
```

## Contributing

Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/your-feature`).
3. Commit changes (`git commit -m 'Add your feature'`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a Pull Request.

Please ensure code follows PEP 8 style guidelines and includes relevant documentation.

## Notes
- **Dataset Sharing**: If `us_retail.csv` cannot be shared due to licensing or size constraints, include a note in the repository with instructions to download it from the [U.S. Census Bureau](https://www.census.gov/retail/).
- **Customization**: Replace `[your-username]` in the installation instructions with your GitHub username.
- **Testing**: Test the notebook and script locally to ensure all dependencies are correctly installed and the code runs without errors.

## Acknowledgments

- Data source: [U.S. Census Bureau](https://www.census.gov/retail/)
- Libraries: pandas, numpy, matplotlib, seaborn, statsmodels, scikit-learn, scipy, tabulate
- Inspiration: Time series forecasting techniques for retail analytics

---

For questions or issues, please open an issue on GitHub or contact [your-email@example.com].