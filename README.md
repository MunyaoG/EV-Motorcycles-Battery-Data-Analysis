# EV Motorcycles Battery Data Analysis

This repository analyzes battery data from an EV motorcycle fleet to identify underperforming batteries and forecast future usage. It combines exploratory data analysis, regression modelling, and time series forecasting (ARIMA) to turn raw swap and battery-feature data into actionable maintenance insights.

## Contents

| File | Description |
|---|---|
| `ev-battery-data-analysis.ipynb` | Main notebook — all data extraction, cleaning, EDA, modelling, and forecasting code. |
| `main.py` | Script version of (or supporting utilities for) the analysis. |
| [`EV-Battery-Analysis-Presentation.pdf`](https://github.com/MunyaoG/EV-Motorcycles-Battery-Data-Analysis/blob/main/EV-Battery-Analysis-Presentation.pdf) | Slide deck summarizing the approach and findings for a non-technical audience. |
| `swap_data.csv` | Raw battery swap records (swap-in/swap-out times). |
| `10-month-predicted-average-usage.csv` | ARIMA forecast of average battery usage hours for the next 10 months. |
| `batteries_with_low_usage_generally.csv` | Batteries flagged with statistically low average usage time. |
| `batteries_with_fast_decline.csv` | Batteries flagged with a fast-declining usage trend. |
| `requirements.txt` | Python dependencies needed to run the notebook. |

## Project Overview

**Objectives:**
* Identify batteries with low usage time
* Use battery features to predict future usage patterns
* Apply time series analysis to forecast battery life

**Data sources:**
* **Swap data** — records of battery swaps, including swap-in and swap-out times
* **Battery features data** — attributes such as capacity, cycle count, state of charge (SOC), and temperature during operation

**Methodology:**
1. **Identify low-usage batteries** — grouped swap data by battery ID and month, then flagged batteries below a statistical usage threshold (z-score) and those with fast-declining usage.
2. **Feature integration** — merged swap data with battery feature data to understand what drives usage time.
3. **Forecast usage time** — built regression models to predict average usage time from battery features.
4. **Time series analysis** — applied ARIMA to model and forecast battery life trends.

**Key results:**
* 22 batteries (1.36%) identified as low-usage; 75 batteries (4.64%) identified as fast-declining
* Low usage was driven mainly by low total charged capacity, low alarm-flag values, and low maximum charge current
* Regression model achieved an MSE of 1.35 on test data; the ARIMA forecast achieved an MAE of 4.34
* A 10-month usage forecast was generated and saved as a CSV

The [presentation](https://github.com/MunyaoG/EV-Motorcycles-Battery-Data-Analysis/blob/main/EV-Battery-Analysis-Presentation.pdf) walks through this in more detail — objectives, methodology, EDA charts (including the z-score plots used to flag batteries and usage-hour histograms), model evaluation, and recommendations for the battery maintenance team (avoiding overcharging, monitoring alarm flags, and matching charging-system current ratings to battery specs).

## Dependencies

* zipfile
* pandas
* numpy
* requests
* os
* csv
* warnings
* sklearn.cluster.KMeans
* matplotlib.pyplot
* scipy.stats.linregress
* sklearn.model_selection.train_test_split
* sklearn.linear_model.LinearRegression
* sklearn.preprocessing.MinMaxScaler
* statsmodels.tsa.arima.model.ARIMA
* sklearn.metrics.mean_squared_error
* sklearn.ensemble.GradientBoostingRegressor
* sklearn.tree.DecisionTreeRegressor

## How to Run

1. Install the required dependencies:
   ```
   pip install -r requirements.txt
   ```
2. Open the notebook in Jupyter:
   ```
   jupyter notebook ev-battery-data-analysis.ipynb
   ```
3. Follow the steps in the notebook to reproduce the analysis and outputs.

## Workflow Summary

**1. Data download and extraction**
* Code is included to download zipped dataset files from Google Cloud Storage.
* Requires valid credentials to access the bucket.
* Downloaded files are extracted for further analysis.

**2. Data cleaning and preprocessing**
* Load the extracted dataset into a pandas DataFrame.
* Handle missing values, clean noisy data, and ensure correct data types/formats.

**3. Exploratory data analysis (EDA)**
* Visualize usage-time distributions and other patterns with matplotlib.
* Compute summary statistics to understand distributions and relationships.

**4. Model building**
* Apply regression and clustering techniques (KMeans, LinearRegression, DecisionTreeRegressor, GradientBoostingRegressor) as specified in the notebook.
* Split data into training and testing sets for validation.

**5. Model evaluation**
* Evaluate performance using metrics such as mean squared error (MSE).

**6. Forecasting**
* Use ARIMA for time series forecasting of battery usage trends.
* Compare predictions against historical values to assess reliability.

**7. Output generation**
* Save processed data, flagged battery lists, and forecast results as CSV files.

## Notes

* Ensure all dependencies are installed before running the notebook.
* Modify the notebook as needed to suit additional requirements.
