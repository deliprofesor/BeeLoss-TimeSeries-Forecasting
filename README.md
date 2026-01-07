# 🐝 BeeLoss-TimeSeries-Forecasting

![arı](https://github.com/user-attachments/assets/a2ca839b-2ba9-4669-b9a1-179a959dbfc6)

## U.S. Honey Bee Colony Loss Percentage Forecasting: Multivariate Time Series Analysis

###  Project Overview

This project is a data science study focused on forecasting the future percentage of honey bee colony losses (`percent_lost`) in the United States using quarterly time-series data from the USDA.

Given the critical role of bees in global food security and ecosystem health, accurate forecasting allows policymakers, beekeepers, and environmental organizations to implement **proactive measures**—such as timely Varroa mite treatments or pesticide regulations—and ensures **efficient resource allocation** to high-risk periods.

### Dataset

The project utilizes the `save_the_bees.csv` file, which contains quarterly, state-level data on colony loss, additions, renovations, and the factors attributed to losses.

| Column Name | Description | Role in Project |
| :--- | :--- | :--- |
| `year`, `quarter` | Temporal information. | Used to create the Time Series Index. |
| **`percent_lost`** | **Percentage of Colony Loss.** | **Target Variable (Y).** |
| `varroa_mites` | Percentage of loss attributed to Varroa mites. | Exogenous Regressor. |
| `pesticides` | Percentage of loss attributed to pesticides. | Exogenous Regressor. |
| `diseases` | Percentage of loss attributed to diseases. | Exogenous Regressor. |
| `percent_renovated`| Percentage of colonies renovated. | Control/Exogenous Regressor. |

###  Problem Statement and Goal

**Problem:** What will be the percentage of honey bee colony loss (`percent_lost`) in the upcoming quarters across the United States?
**Goal:** Develop robust forecasting models that account for historical trends, seasonality, and causative external factors (Varroa mites, pesticides) to produce highly accurate predictions.

###  Methodology and Analysis Pipeline

The project is approached as a **Multivariate Time Series Forecasting** problem, incorporating various factors that influence colony health.

#### 1. Data Preprocessing & EDA (Exploratory Data Analysis)

* **Aggregation:** State-level data is aggregated (averaged and summed) by `year` and `quarter` to represent the overall U.S. national trend.
* **Time Series Transformation:** `year` and `quarter` columns are converted into a proper time series index with full timestamps.
* **Missing Value Imputation:** Missing values are handled using time series-appropriate methods (e.g., interpolation or forward-fill).
* **Visualization:** Analysis of trend, seasonality, and correlations between the target variable (`percent_lost`) and key regressors (e.g., `varroa_mites`, `pesticides`).

#### 2. Modeling

We leverage models capable of handling time-dependent data and incorporating exogenous variables (regressors):

1.  **SARIMAX (Seasonal Autoregressive Integrated Moving Average with Exogenous Regressors):** A classical statistical method that simultaneously models trend, seasonality, and the impact of external variables.
2.  **Prophet (Meta):** Used as an alternative for benchmarking, known for its ability to easily model strong seasonality and incorporate additional regressors.

**Exogenous Regressors (X):** `varroa_mites`, `pesticides`, `diseases`, `percent_renovated`.

#### 3. Model Evaluation

Model performance is evaluated on a held-out test set using industry-standard metrics:

* **RMSE (Root Mean Squared Error):** Measures the magnitude of prediction errors.
* **MAPE (Mean Absolute Percentage Error):** Provides the error as a percentage, offering easy interpretability.

###  Technologies

* **Language:** Python 3.x
* **Data Manipulation:** `pandas`, `numpy`
* **Time Series Modeling:** `statsmodels` (for SARIMAX), `prophet`
* **Visualization:** `matplotlib`, `seaborn`

### Setup and Execution

To run this project locally, follow these steps:

#### 1. Clone the Repository

```bash
git clone [https://github.com/YourUsername/BeeLoss-TimeSeries-Forecasting.git](https://github.com/YourUsername/BeeLoss-TimeSeries-Forecasting.git)
cd BeeLoss-TimeSeries-Forecasting
