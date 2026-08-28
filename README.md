# EV Motorcycles Battery Data Analysis
This repository contains a Jupyter Notebook designed for battery data analysis. It demonstrates proficiency in data extraction, cleaning, preprocessing, exploratory data analysis, model building, and evaluation. The project incorporates machine learning techniques and time series forecasting to generate insights and predictions from the dataset.

## Structure
### Notebook:
- `code-for-DS-assessment.ipynb` - contains all the analysis and code required for the task.
- Environment: Python, Jupyter Notebook

## Dependencies
- zipfile
- pandas
- numpy
- requests
- os
- csv
- warnings
- sklearn.cluster.KMeans
- matplotlib.pyplot
- scipy.stats.linregress
- sklearn.model_selection.train_test_split
- sklearn.linear_model.LinearRegression
- sklearn.preprocessing.MinMaxScaler
- statsmodels.tsa.arima.model.ARIMA
- sklearn.metrics.mean_squared_error
- sklearn.ensemble.GradientBoostingRegressor
- sklearn.tree.DecisionTreeRegressor

## How to Run
- Install the required dependencies in requirements.txt
- Open the notebook in Jupyter
    - jupyter notebook `code-for-DS-assessment.ipynb`

## Usage
Follow the steps outlined in the notebook to perform the analysis and generate the required results.

In summary:
### Data Download and Extraction:
- The notebook includes code to connect to download zip files containing the dataset from Google Cloud Storage.
- NB: If you have correct credentials to access the bucket, you can connect to Google Cloud Storage and download files.
- Extract the downloaded file for further analysis.

### Data Cleaning and Preprocessing:
- Load the extracted dataset into a pandas DataFrame.
- Handle missing values, clean noisy data, and ensure data is in the correct format.

### Exploratory Data Analysis (EDA):
- Visualize patterns in the data using matplotlib.
- Calculate basic statistics to understand distributions and relationships.

### Model Building:
- Use regression or clustering techniques (e.g., KMeans, LinearRegression, DecisionTreeRegressor, GradientBoostingRegressor) as specified in the notebook.
- Split the data into training and testing sets for validation.

### Model Evaluation:
- Evaluate the model performance using metrics like mean squared error (MSE).

### Forecasting:
- Implement time series forecasting using ARIMA for trend prediction.
- Visualize predictions versus historical values to assess reliability.

### Generate Final Output:
- Save the processed data or model outputs as required.

## Notes
- Ensure that all dependencies are installed before running the notebook.
- Modify the notebook as needed to suit additional requirements.
