# Project Tasks & Problem Solving Log

This document outlines the specific analytical and programmatic challenges solved during the development of this mini-capstone project.

### Phase 1: Problem Formulation
- [x] **Task 1:** Formulated the quantitative problem of forecasting crude oil prices by analyzing the limitations of traditional models (e.g., rigid reliance on ARMA variance).
- [x] **Task 2:** Justified the selection of Bayesian Belief Networks (BNs) and Markov modeling to handle high-dimensional, dynamically changing financial data.

### Phase 2: Data Engineering
- [x] **Task 3:** Successfully bridged `fredapi` (monthly economic data) and `yfinance` (daily trading data).
- [x] **Task 4:** Solved critical timezone localization and frequency mismatch bugs by utilizing naive datetimes and `.resample('MS').mean()`.
- [x] **Task 5:** Implemented a robust data cleaning pipeline involving time-based interpolation to eliminate NaNs.
- [x] **Task 6:** Swapped standard Z-score outlier detection for the Interquartile Range (IQR) method to preserve the natural "fat tails" inherent in commodity returns.

### Phase 3: Mathematical Transformation & EDA
- [x] **Task 7:** Transformed continuous asset prices into stationary log-differenced returns ($r_t = \ln(P_t) - \ln(P_{t-1})$).
- [x] **Task 8:** Conducted Augmented Dickey-Fuller (ADF) tests programmatically to statistically prove stationarity ($p < 0.05$ across all vectors).
- [x] **Task 9:** Generated a comprehensive suite of EDA visualizations, including leptokurtic distribution plots, time-series volatility clusters, and a multivariate correlation heatmap.

### Phase 4: Model Architecture
- [x] **Task 10:** Documented the mathematical theory differentiating Structure Learning (Hill Climbing/BIC) from Parameter Learning (Bayesian Estimation).
- [x] **Task 11:** Drafted **Algorithm 1: Inferred Causality** using formal academic pseudocode to demonstrate how Markov Blankets isolate variables for computationally efficient target forecasting.