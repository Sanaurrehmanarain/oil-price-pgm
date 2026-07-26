<div align="center">
  <a href="ProjectReport.pdf">
    <img src="rm1.png" alt="banner" width="100%">
  </a>
  <p><em>Click the banner to view the full analysis report</em></p>
</div>

# 🛢️ Crude Oil Price Forecasting via Probabilistic Graphical Models

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Bayesian Networks](https://img.shields.io/badge/Model-Bayesian_Networks-green.svg)
![HMM](https://img.shields.io/badge/Model-Hidden_Markov_Models-orange.svg)
![Finance](https://img.shields.io/badge/Domain-Quantitative_Finance-darkred.svg)

## 📌 Project Overview

This repository presents a quantitative risk management framework for forecasting the spot price of WTI Crude Oil using **Probabilistic Graphical Models (PGMs)** and **Hidden Markov Models (HMMs)**.

Crude oil is one of the most economically significant and volatile commodities in global markets. Its price is influenced by an intricate combination of supply-demand dynamics, macroeconomic conditions, financial market sentiment, and geopolitical events. Traditional time-series models such as ARIMA and GARCH are effective for capturing linear dependencies and volatility clustering but may struggle to represent nonlinear relationships and structural shifts in market behavior.

This project addresses these challenges by combining:

- **Hidden Markov Models (HMMs)** to identify latent market regimes and volatility states.
- **Bayesian Networks** to learn probabilistic relationships among macroeconomic indicators.
- **Markov Blanket Discovery** to isolate the most informative variables for forecasting and inference.

The resulting framework emphasizes both **predictive capability** and **model interpretability**, making it suitable for quantitative risk management applications.

---

## 📊 Dataset & Variables

Data was programmatically collected from the **Federal Reserve Economic Data (FRED)** and **Yahoo Finance** APIs using a Monthly-Start (`MS`) frequency spanning from January 2000 to the present.

### Target Variable

- **WTI Crude Oil Spot Price** (`WTISPLC`)

### Exogenous Macroeconomic Variables

#### Economic Activity
- **Industrial Production Index** (`INDPRO`)

#### Inflation & Energy Markets
- **Consumer Price Index: Energy** (`CPIENGSL`)
- **Energy Select Sector SPDR Fund** (`XLE`)

#### Supply-Side Conditions
- **Capacity Utilization: Oil & Gas** (`CAPUTLG211S`)

#### Financial Market Sentiment
- **S&P 500 Index** (`^GSPC`)
- **US Dollar Index** (`DX-Y.NYB`)

These variables were selected to represent key demand, supply, inflationary, and financialization mechanisms commonly cited in commodity market literature.

---

## 🧠 Methodology & Architecture

### 1. Data Preparation & Stationarity

Macroeconomic and financial datasets were merged using a time-indexed outer join to preserve all available observations.

Data preprocessing included:

- Missing-value handling through time-based interpolation
- Alignment of differing publication frequencies
- Transformation of price series into log-differenced returns

The return transformation is defined as:

`r_t = ln(P_t) - ln(P_{t-1})`

Stationarity was validated using the **Augmented Dickey-Fuller (ADF)** test.

---

### 2. Exploratory Data Analysis (EDA)

Exploratory analysis focused on identifying stylized facts commonly observed in financial time series:

- Fat-tailed (leptokurtic) return distributions
- Volatility clustering
- Structural shifts during periods of market stress
- Long-term trends across more than two decades of observations

Visualization techniques included:

- Time-series plots
- Histograms
- Boxplots based on the Interquartile Range (IQR)
- Rolling volatility analysis

---

### 3. Regime Detection with Hidden Markov Models

A continuous-emission `GaussianHMM` was employed to identify latent market regimes.

The model was trained using the **Baum-Welch (Expectation-Maximization)** algorithm and decoded using the **Viterbi Algorithm**.

This approach enables the classification of oil market behavior into distinct volatility and return regimes, providing insight into changing market dynamics over time.

Potential regime categories include:

- Bull Market Regime
- Neutral/Stagnant Regime
- Bear Market or Crisis Regime

---

### 4. Bayesian Network Structure Learning

To uncover probabilistic dependencies among macroeconomic indicators, a Bayesian Network was learned directly from the data.

The structure-learning process utilized:

- **Hill Climb Search**
- **Bayesian Information Criterion (BIC)** scoring

This approach allows the network structure to emerge empirically rather than being manually specified, reducing subjective modeling assumptions.

The resulting Directed Acyclic Graph (DAG) provides an interpretable representation of relationships among economic variables relevant to crude oil prices.

---

### 5. Parameter Learning & Probabilistic Inference

After learning the network structure, model parameters were estimated using Bayesian techniques to construct Conditional Probability Tables (CPTs).

Inference was performed using:

- **Variable Elimination**
- **Posterior Probability Estimation**
- **Markov Blanket Analysis**

Markov Blanket identification isolates the minimum set of variables required for optimal probabilistic prediction of the target variable, improving both computational efficiency and interpretability.

---

## 📈 Key Techniques Demonstrated

- Financial Time-Series Analysis
- Hidden Markov Models (HMMs)
- Bayesian Networks
- Probabilistic Graphical Models (PGMs)
- Markov Blanket Discovery
- Causal Structure Learning
- Bayesian Inference
- Variable Elimination
- Feature Engineering
- Stationarity Testing
- Macroeconomic Modeling
- Quantitative Risk Management

---

## 📦 Requirements

- Python 3.8+
- pandas
- numpy
- scipy
- matplotlib
- statsmodels
- yfinance
- fredapi
- hmmlearn
- pgmpy
- scikit-learn
- python-dotenv

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

This project requires a valid FRED API key.

Create a `.env` file in the project root directory:

```text
FRED_API_KEY=your_actual_key_here
```

### 4. Execute the Notebook

Launch the notebook:

```bash
jupyter notebook Notebook.ipynb
```

or open `Notebook.ipynb` directly in **VS Code** and run all cells.

The notebook will:

- Collect macroeconomic and market data
- Perform preprocessing and stationarity testing
- Conduct exploratory data analysis
- Train Hidden Markov Models for regime identification
- Learn Bayesian Network structures
- Estimate Conditional Probability Tables
- Perform probabilistic inference and forecasting

---

## 🎓 Academic Context

This project was developed as a quantitative finance and risk management study exploring the application of probabilistic machine learning techniques to commodity price forecasting.

The primary objective is to combine regime-switching models and Bayesian inference to create an interpretable forecasting framework capable of capturing nonlinear market dynamics while maintaining economic intuition.

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