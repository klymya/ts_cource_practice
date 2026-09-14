# Time Series — Practice Homework

Six notebooks, from smoothing a series to forecasting it with neural networks.
Each one is graded by an automated test suite.

## Run it

```bash
pip install -r requirements.txt
jupyter lab     # open notebooks/practice1.ipynb
```

## How grading works

Your notebooks are marked by an automated test suite you do not have. It imports
**only** the `setup` and `graded` cells — never your plots.

| cell | tag | marked |
|---|---|---|
| imports | `setup` | imported |
| functions you complete | `graded` | **yes** |
| plots, prints, exploration | *(none)* | no |

Each `graded` cell gives you a signature and a docstring stating the contract.
Fill in the body and **change nothing else about it**: rename a function, drop a
parameter or return a list where a `Series` was asked for, and the marker cannot
find or use your work. The docstring is the specification — read it twice.

Before you hand in, restart the kernel and run the notebook top to bottom. Some
cells carry `assert` checks that catch the common mistakes on the spot, and a
notebook that does not run end to end will not mark.

## Practices

| # | Topic |
|---|---|
| 1 | Moving averages, exponential smoothing, Holt, trend extraction |
| 2 | Error measures, naive baseline, SES, Holt, Holt-Winters |
| 3 | Stationarity, Dickey-Fuller, differencing, ACF/PACF, AR, SSA |
| 4 | Residual modelling, ADF + KPSS, ARIMA order selection, Ljung-Box |
| 5 | Feature engineering without leakage, Ridge/Lasso/SVR, comparison |
| 6 | MLP, LSTM, bidirectional LSTM in PyTorch |

Do 3 before 4: differencing is taught in 3 and is the `d` of ARIMA(p, d, q) in 4.
Practice 6 trains three networks, about 40 seconds on a laptop CPU.

## Two rules the tests enforce hardest

**No feature may see the present (practice 5).** A rolling mean that includes
`y[t]`, or `diff = y[t] - y[t-1]`, hands the model its own target. The symptom is
a *better* score, not an error — with those features every model scores
R² = 1.000. `test_no_model_can_predict_white_noise` builds features from pure
noise and fails if anything can predict it. Section 1.1 of that notebook shows
you how to run the same check on your own features.

**Split before you scale (practice 6).** Fit the scaler on the training split
only. Fit it on the whole series and the test set's min and max leak into
training, and nothing in the loss curve will tell you.

## Data

`data/` holds five series: Melbourne daily minimum temperature (1981–1990),
monthly sunspots (1749–1983), daily births in California (1959), monthly airline
passengers (1949–1960), and German daily electricity consumption (2006–2017).

One trap: `opsd_germany_daily.csv` has empty `Wind`/`Solar` cells before 2012, so
a bare `df.dropna()` also drops those rows and costs you half the `Consumption`
series. Select your columns first. Practice 1 has a test for it.

## Environment

Pinned in `requirements.txt`, verified end to end on Python 3.12.11 with
pandas 2.3.0, scikit-learn 1.7.0, statsmodels 0.14.5 and torch 2.9.1.
PyTorch is not in a default Anaconda install; `requirements.txt` includes it.

## Layout

```
data/        datasets
notebooks/   the practices you complete
```

## Reading

Two sources run through the whole course:
**FPP** — [Forecasting: Principles and Practice](https://otexts.com/fpp3/) for the
theory, and [fpp3-python-readalong](https://github.com/zgana/fpp3-python-readalong)
for the same chapters worked in Python.

**1 · Trend analysis**
- FPP [2 Graphics](https://otexts.com/fpp3/graphics.html) ·
  [3 Decomposition](https://otexts.com/fpp3/decomposition.html)
- Code: [02 Graphics](https://github.com/zgana/fpp3-python-readalong/blob/master/02-Time-series-graphics.ipynb) ·
  [03 Decomposition](https://github.com/zgana/fpp3-python-readalong/blob/master/03-Time-series-decomposition.ipynb)
- [Decomposition from scratch](https://github.com/bhattbhavesh91/time-series-decomposition-from-scratch/blob/master/time-series-decomposition-from-scratch.ipynb)

**2 · Trend predictive models**
- FPP [3.3 Moving averages](https://otexts.com/fpp3/moving-averages.html) ·
  [8 Exponential smoothing](https://otexts.com/fpp3/expsmooth.html)
- Code: [08 Exponential smoothing](https://github.com/zgana/fpp3-python-readalong/blob/master/08-Exponential-smoothing.ipynb) ·
  [PTS ch.2 moving averages](https://github.com/PacktPublishing/Practical-Time-Series-Analysis/blob/master/Chapter02/Chapter_2_Moving_Averages.ipynb)
- [Hands-on Time Series Analysis with Python](https://github.com/Apress/hands-on-time-series-analylsis-python)

**3 · Dynamic predictive models**
- FPP [9.3 AR models](https://otexts.com/fpp3/AR.html)
- [SSA for decomposition, walked through](https://github.com/fabsta/interesting_notebooks/blob/master/introducing-ssa-for-time-series-decomposition.ipynb)
- [pssa](https://github.com/aj-cloete/pssa) — a ready-made SSA library, for comparison

**4 · ARIMA**
- FPP [9.3 AR](https://otexts.com/fpp3/AR.html) ·
  [9.4 MA](https://otexts.com/fpp3/MA.html) ·
  [9 ARIMA](https://otexts.com/fpp3/arima.html)
- Code: [09 ARIMA models](https://github.com/zgana/fpp3-python-readalong/blob/master/09-ARIMA-models.ipynb) ·
  [PTS ch.4 AR, MA, ARMA](https://github.com/PacktPublishing/Practical-Time-Series-Analysis/tree/master/Chapter04)

**5 · Machine learning**
- [Python Data Science Handbook: Linear Regression](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/05.06-Linear-Regression.ipynb) ·
  [Support Vector Machines](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/05.07-Support-Vector-Machines.ipynb)
- [scikit-learn on data leakage](https://scikit-learn.org/stable/common_pitfalls.html#data-leakage) — read this one before you start

**6 · Neural networks**
- [Deep Learning with PyTorch](https://github.com/TomasBeuzen/deep-learning-with-pytorch):
  [1 Gradient descent](https://github.com/TomasBeuzen/deep-learning-with-pytorch/blob/main/chapters/chapter1_gradient-descent.ipynb) ·
  [2 Stochastic gradient descent](https://github.com/TomasBeuzen/deep-learning-with-pytorch/blob/main/chapters/chapter2_stochastic-gradient-descent.ipynb)

**PTS** (*Practical Time Series Analysis*, chapters 2 and 4) is distributed as a
[course copy on Drive](https://drive.google.com/file/d/1hNwRd60bmNJGvbE2evXuZxMEPhA_9P3S/view?usp=drive_link)
and needs your course account. The code above is public and needs nothing.
