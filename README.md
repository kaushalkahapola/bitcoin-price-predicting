# Time Series Forecasting - Predicting Bitcoin Price

This notebook provides a comprehensive approach to time series forecasting by predicting Bitcoin prices using historical price data. The project begins with a baseline Naive model and plans to implement more advanced models for accurate predictions.

## Table of Contents

1. [Introduction](#introduction)
2. [Dataset](#dataset)
3. [Modeling Process](#modeling-process)
4. [Usage](#usage)
5. [Evaluation](#evaluation)
6. [Results](#results)
7. [Future Work](#future-work)

## Introduction

The goal of this notebook is to predict future Bitcoin prices using time series forecasting techniques. We utilize historical data to train models and make predictions. This project includes:

- Data Preprocessing and Visualization
- Train-Test Splitting
- Baseline Model (Naive Forecast)
- Model Evaluation using various metrics

This is an ongoing project, and we plan to experiment with more advanced forecasting models.

## Dataset

The dataset used for this project is the historical price data of Bitcoin (BTCUSDT) from Binance. The columns include:

- `Unix`: Unix timestamp of the data
- `Date`: Date of the recorded price
- `Symbol`: Trading pair (BTCUSDT)
- `Open`: Opening price
- `High`: Highest price during the day
- `Low`: Lowest price during the day
- `Close`: Closing price
- `Volume BTC`: Volume traded in BTC
- `Volume USDT`: Volume traded in USDT
- `tradecount`: Number of trades

The dataset contains 2,605 daily entries from August 17, 2017, to October 3, 2024.

## Modeling Process

The project is structured as follows:

1. **Data Preprocessing**: The dataset is reversed to ensure the oldest data comes first. We extract and plot the 'Close' prices to visualize trends.
2. **Train-Test Split**: The dataset is split into training (80%) and testing (20%) sets.
3. **Models and Approaches**:
   
   - **Exponential Smoothing**: We used an **expanding window** approach, where the model is retrained after each prediction on the test set. The **forecast horizon** was set to 1, predicting the next day's price based on past data.
   
   - **AutoARIMA**: We used an **expanding window** approach, where the model was retrained after each prediction, with a **forecast horizon** of 30 days, predicting 30 days into the future based on the historical data.

   - **LSTM**: We applied a **sliding window** approach with a **window size of 7 days**, predicting 1 day ahead. The model used the previous 7 days of data to make the next day's prediction.
   
4. **Baseline Model (Naive Forecast)**: We used the previous day's price as the prediction for the next day.
   
5. **Evaluation**: The models were evaluated using various metrics:
   - Mean Absolute Error (MAE)
   - Mean Squared Error (MSE)
   - Root Mean Squared Error (RMSE)
   - Mean Absolute Percentage Error (MAPE)
   - Mean Absolute Scaled Error (MASE)

## Usage

This notebook contains all the necessary steps for data loading, preprocessing, model training, and evaluation. Simply run the cells in sequence.

## Evaluation

The following evaluation metrics are used to assess model performance:

- **MAE**: Mean Absolute Error
- **MSE**: Mean Squared Error
- **RMSE**: Root Mean Squared Error
- **MAPE**: Mean Absolute Percentage Error
- **MASE**: Mean Absolute Scaled Error (assumes no seasonality)

## Results

The baseline Naive model achieved the following performance on the test set:

- **MAE**: `858.908`
- **MSE**: `1760665.9`
- **RMSE**: `1326.9009`
- **MAPE**: `1.7169135`
- **MASE**: `0.9988737`

The Exponential Smoothing approach achieved the following performance on the test set:

- **MAE**: `869.7958`
- **MSE**: `1842781.0`
- **RMSE**: `1357.4907`
- **MAPE**: `1.7346842`
- **MASE**: `1.0126762`

The AutoARIMA approach achieved the following performance on the test set:

- **MAE**: `3364.1926`
- **MSE**: `25689692.0`
- **RMSE**: `5068.5`
- **MAPE**: `6.7582207`
- **MASE**: `3.9168253`

The LSTM model achieved the following performance on the test set:

- **MAE**: `24360.203`
- **MSE**: `666612600.0`
- **RMSE**: `25818.842`
- **MAPE**: `52.317856`
- **MASE**: `28.329887`

Further experimentation with other models will aim to improve these metrics.

## Future Work

This project is still in progress. In the future, I plan to:

- Implement deep learning models like NBeats and LSTM with different window and horizon sizes.
- Explore hybrid approaches combining statistical models with machine learning
- Fine-tune model hyperparameters to improve performance
