This repository contains practice homework for time-series courses.

### Practices:
1. Trend analysis
    * Time series smoothing
    * Trend estimation and extraction

2. Trend predictive models
    * Naive Approach
    * Simple Exponential Smoothing
    * Holt's Linear Trend Model
    * Holt Winter's Model

3. Dynamic predictive models
    * Residual analisys. Dickey-Fuller test
    * Autocorelation analisys
    * Predicting Time series: AR Model
    * Singular Spectrum Analysis (SSA)

4. ARIMA models and advanced techniques
    * Predicting Time series: Moving Average Model
    * ARMA and ARIMA Models
    * Model Selection and Diagnostics
    * Stationarity Testing

5. Machine Learning for Time Series Forecasting
    * Feature Engineering for Time Series
    * Linear Regression for Time Series Forecasting
    * Support Vector Machine (SVM) for Time Series Forecasting
    * Model Comparison and Evaluation

6. Neural Networks for Time Series Forecasting
    * Multi-layer Perceptron (MLP) for Time Series
    * Recurrent Neural Networks (RNN/LSTM)
    * PyTorch Implementation and Training
    * Advanced Neural Network Architectures


### Datasets:
- daily-min-temperatures.csv - the dataset containce the minimum daily temperatures over 10 years (1981-1990) in the city Melbourne, Australia. 
- monthly-sunspots.csv - describes a monthly count of the number of observed sunspots for just over 230 years (1749-1983).
- daily-total-female-births.csv - the dataset describes the number of daily female births in California in 1959.
- airline-passengers.csv - the dataset describe number of air passengers per month from 1949 to 1960.
- opsd_germany_daily.csv - contains electricity consumption, wind power production, and solar power production for 2006–2017.

### Structure:
* /data - contains csv files with data
* /notebooks - contains - ipynb files with prectices

### Requirements:
To complete this practice you need to install [Anaconda](https://www.anaconda.com/products/individual). Anaconda is a Python data science distribution with preinstalled libraries.

**Additional requirements for advanced practices:**
- PyTorch (for Practice 6): `pip install torch`
- scikit-learn: `pip install scikit-learn`
- statsmodels: `pip install statsmodels`

### Useful links:

**Textbooks and Theory:**
- [Forecasting: Principles and Practice (3rd ed)](https://otexts.com/fpp3/) - Comprehensive textbook on forecasting methods
- [FPP3 Python Code Examples](https://github.com/zgana/fpp3-python-readalong) - Python implementations of FPP3 examples

**Practical Resources:**
- [Machine Learning Mastery. Introduction to Time Series Forecasting (Python)](https://machinelearningmastery.com/start-here/#timeseries)
- [Practical Time Series Analysis GitHub](https://github.com/PacktPublishing/Practical-Time-Series-Analysis) - Code examples from PTS book
- [Python Data Science Handbook](https://github.com/jakevdp/PythonDataScienceHandbook) - ML foundations

**Advanced Topics:**
- [Singular Spectral Analysis Tutorial](https://github.com/fabsta/interesting_notebooks/blob/master/introducing-ssa-for-time-series-decomposition.ipynb) - SSA implementation
- [PyTorch Deep Learning Course](https://github.com/TomasBeuzen/deep-learning-with-pytorch) - Neural networks for time series
- [Python SSA Library](https://github.com/aj-cloete/pssa) - Ready-to-use SSA implementation

**Russian Resources:**
- [Открытый курс машинного обучения. Тема 9. Анализ временных рядов с помощью Python](https://habr.com/ru/company/ods/blog/327242/)