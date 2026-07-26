# ✅ Risk Management Mini-Capstone — Development Log

This document tracks the major milestones completed throughout the development of the capstone.

---

# 📘 Project 1 — Problem Formulation & Data Collection

## Data Engineering

- [x] Built an automated data ingestion pipeline integrating the FRED API and Yahoo Finance API.
- [x] Collected monthly macroeconomic and financial market data spanning January 2000 to the present.
- [x] Unified heterogeneous datasets into a single analytical framework.

## Data Preparation

- [x] Implemented time-indexed merging of all economic indicators.
- [x] Addressed missing observations using interpolation and forward/backward filling where appropriate.
- [x] Generated stationary log-return series from non-stationary price data.
- [x] Verified stationarity using the Augmented Dickey-Fuller (ADF) test.

## Exploratory Data Analysis

- [x] Examined long-term macroeconomic trends.
- [x] Identified volatility clustering.
- [x] Investigated leptokurtic return distributions.
- [x] Produced visualizations for exploratory analysis.

---

# 📗 Project 2 — Methodology Description & Model Development

## Hidden Markov Models

- [x] Reviewed Hidden Markov Model theory.
- [x] Documented Forward, Backward, Baum-Welch, and Viterbi algorithms.
- [x] Trained Gaussian Hidden Markov Models.
- [x] Identified latent market regimes.

## Bayesian Networks

- [x] Discretized continuous variables.
- [x] Learned Bayesian Network structures using Hill Climb Search.
- [x] Applied Bayesian Information Criterion (BIC) for model selection.
- [x] Estimated Conditional Probability Tables (CPTs).
- [x] Identified the Markov Blanket of the target variable.
- [x] Implemented probabilistic inference using Variable Elimination.

---

# 📙 Project 3 — Interpretation of Results & Improving the Model

## Model Validation

- [x] Implemented chronological 80/10/10 train-validation-test splitting.
- [x] Prevented look-ahead bias throughout model development.
- [x] Evaluated forecasting performance using unseen out-of-sample data.

## Performance Evaluation

- [x] Measured classification accuracy.
- [x] Generated confusion matrices.
- [x] Evaluated directional forecasting performance.
- [x] Interpreted predictions from a quantitative risk management perspective.

## Research & Discussion

- [x] Compared model performance against a passive Buy-and-Hold strategy.
- [x] Discussed strengths and limitations of probabilistic forecasting.
- [x] Reviewed relevant literature supporting Bayesian methods in financial econometrics.
- [x] Produced final project conclusions and recommendations.

---

# 📊 Overall Project Deliverables

- [x] Automated data collection pipeline
- [x] Data preprocessing and feature engineering
- [x] Stationarity analysis
- [x] Exploratory Data Analysis
- [x] Hidden Markov Model implementation
- [x] Bayesian Network implementation
- [x] Markov Blanket discovery
- [x] Bayesian inference engine
- [x] Out-of-sample forecasting
- [x] Model validation and evaluation
- [x] Research interpretation
- [x] Technical documentation
