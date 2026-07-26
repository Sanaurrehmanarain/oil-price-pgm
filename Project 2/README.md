<div align="center">
  <a href="ProjectReport.pdf">
    <img src="rm2.png" alt="banner" width="100%">
  </a>
  <p><em>Click the banner to view the full analysis report</em></p>
</div>

# 🛢️ Risk Management Mini-Capstone: Crude Oil Price Forecasting

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![hmmlearn](https://img.shields.io/badge/Model-Hidden_Markov_Models-orange.svg)
![pgmpy](https://img.shields.io/badge/Model-Bayesian_Networks-green.svg)
![Risk Management](https://img.shields.io/badge/Domain-Quantitative_Finance-darkred.svg)

## 📌 Project Overview

This repository contains a graduate-level quantitative risk management pipeline designed to forecast the spot price of WTI Crude Oil. Traditional linear forecasting models such as ARIMA or GARCH often struggle to capture the nonlinear dynamics and fat-tailed behavior associated with global commodity markets.

To address this challenge, this capstone employs a dual-model architecture:

1. **Hidden Markov Models (HMMs):** Capture the temporal evolution of market volatility and classify continuous price movements into distinct latent market regimes.
2. **Probabilistic Graphical Models (PGMs):** Specifically, Bayesian Networks are used to learn structural relationships among macroeconomic indicators and identify the target variable's **Markov Blanket**.

---

## 📊 Dataset & Macroeconomic Framework

Data was programmatically collected from the **Federal Reserve Economic Data (FRED)** and **Yahoo Finance** APIs using a Monthly-Start (`MS`) frequency spanning January 2000 to the present.

Variables were selected based on established macroeconomic literature to represent supply, demand, and financialization dynamics:

### Target Variable
- **WTI Crude Oil Spot Price** (`WTISPLC`)

### Demand Dynamics
- **Industrial Production Index** (`INDPRO`)

### Supply Constraints
- **Capacity Utilization: Oil & Gas** (`CAPUTLG211S`)

### Financial Sentiment
- **S&P 500 Index** (`^GSPC`)
- **US Dollar Index** (`DX-Y.NYB`)

### Downstream Linkages
- **Energy CPI** (`CPIENGSL`)
- **Energy Sector ETF** (`XLE`)

All continuous asset prices were transformed into stationary log-differenced returns:

`r_t = ln(P_t) - ln(P_{t-1})`

Stationarity was subsequently validated using **Augmented Dickey-Fuller (ADF)** tests.

---

## 🧠 Model Architecture & Methodology

### Phase 1: Regime Decoding (Hidden Markov Models)

A continuous-emission `GaussianHMM` with full covariance matrices was trained using the **Baum-Welch (Expectation-Maximization)** algorithm.

The model identified three latent market states:

- 🟢 **Bull Regime (High Growth):** Positive drift with relatively low volatility (`σ² = 0.0051`)
- ⚪ **Stagnant Regime (Mean-Reverting):** Near-zero drift with moderate volatility
- 🔴 **Bear Regime (High Volatility/Crisis):** Negative drift with substantial volatility expansion (`σ² = 0.0837`)

The decoded regimes closely align with major periods of market stress, including the **2008 Global Financial Crisis** and the **2020 COVID-19 market shock**.

### Phase 2: Causal Discovery (Bayesian Networks)

To transition from a univariate forecasting framework to a multivariate probabilistic framework, the dataset was discretized and analyzed using a **Hill Climb Search** algorithm.

Candidate Directed Acyclic Graphs (DAGs) were evaluated using the **Bayesian Information Criterion (BIC)** to penalize model complexity and reduce structural overfitting.

#### Key Finding: Markov Blanket Identification

The learned Bayesian Network identified the following Markov Blanket for WTI Crude Oil:

**MB(WTI) = { CPI_Energy, Energy_Sector_ETF }**

This result suggests that localized energy inflation and energy equity market conditions contain the most directly relevant probabilistic information for forecasting WTI price movements within the learned network structure.

---

## 📦 Requirements

- Python 3.8+
- pandas
- numpy
- yfinance
- fredapi
- scipy
- statsmodels
- matplotlib
- hmmlearn
- pgmpy
- python-dotenv
- scikit-learn

Install all dependencies using:

```bash
pip install -r requirements.txt
```

---

## 🚀 How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/sanaurrehmanarain/oil-price-pgm.git
cd oil-price-pgm
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure Environment Variables

Create a `.env` file in the project root directory:

```text
FRED_API_KEY=your_actual_key_here
```

### 4. Execute the Pipeline

Launch the notebook:

```bash
jupyter notebook code.ipynb
```

or open `code.ipynb` directly in **VS Code**.

The notebook will:

- Collect and preprocess macroeconomic data
- Perform stationarity transformations and ADF testing
- Train the Hidden Markov Model and decode market regimes
- Learn the Bayesian Network structure
- Identify the Markov Blanket of the target variable
- Generate visualizations and analytical outputs

---

## 📈 Key Techniques Demonstrated

- Time Series Analysis
- Regime-Switching Models
- Hidden Markov Models (HMMs)
- Bayesian Networks
- Probabilistic Graphical Models
- Markov Blanket Discovery
- Macroeconomic Feature Engineering
- Stationarity Testing
- Quantitative Risk Management
- Financial Data Engineering

---

## 🎓 Academic Context

This project was developed as a quantitative risk management mini-capstone, demonstrating the application of machine learning, probabilistic modeling, and macroeconomic analysis to commodity price forecasting.

The objective is not only predictive performance but also model interpretability through regime identification and causal structure discovery.

---

## Copyright Notice

© 2026 Sana Ur Rehman Arain. All rights reserved.

This project is proprietary and is **not open source**.

You may view and run this project for personal, educational, and
reference purposes only. Copying, modifying, redistributing, sublicensing,
or creating derivative works — in whole or in part — is prohibited without
prior written permission from the copyright holder.

This project is provided "as is," without warranty of any kind.

For permission requests, contact: <sana.arain.work@gmail.com>

See the [LICENCE](LICENCE) file for the complete license terms.

---

## Citation

If permission is granted to use this project in academic research,
publications, educational materials, or derivative works, please retain
the original copyright notice and provide appropriate credit.

This repository includes a `CITATION.cff` file, so GitHub provides a
**"Cite this repository"** button in the repository sidebar, which you
can use to obtain citations in BibTeX, APA, and other supported formats.

**Suggested citation:**

Arain, S. U. R. (2026). oil-price-pgm (Version 1.0) [Software].
<https://github.com/sanaurrehmanarain/oil-price-pgm>

**Author:** Sana Ur Rehman Arain

**Profession:** Data Scientist

**GitHub:** <https://github.com/sanaurrehmanarain>