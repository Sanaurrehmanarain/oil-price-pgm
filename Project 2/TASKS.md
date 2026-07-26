# ✅ Project 2 Tasks & Problem Solving Log

This document tracks the specific methodological and programmatic challenges resolved during the **Model Development & Methodology** phase of the Risk Management Mini-Capstone.

### Phase 1: Algorithmic Theory & HMM Design
- [x] **Task 1:** Drafted formal academic pseudocode for the **Forward and Backward Algorithms**, explaining their role in calculating the probability of observed market sequences.
- [x] **Task 2:** Drafted formal pseudocode for the **Viterbi Algorithm**, outlining the dynamic programming approach to decoding the single most likely path of hidden regimes.
- [x] **Task 3:** Drafted formal pseudocode for the **Baum-Welch Algorithm**, explaining Expectation-Maximization (EM) for learning transition and emission parameters from raw data.

### Phase 2: Macroeconomic Framework & Parameter Learning
- [x] **Task 4:** Engineered a comprehensive macroeconomic literature review justifying the inclusion of `INDPRO`, `CAPUTLG211S`, `CPIENGSL`, the `S&P 500`, and the `USD Index` based on supply/demand inelasticity and commodity financialization.
- [x] **Task 5:** Implemented the `hmmlearn.GaussianHMM` module. Resolved issues with continuous float emissions by applying full covariance matrices (`covariance_type="full"`) to mathematically capture "fat-tailed" financial shocks.

### Phase 3: Regime Execution & Decoding
- [x] **Task 6:** Trained the HMM on the stationary WTI log-returns dataset generated in Project 1.
- [x] **Task 7:** Decoded the Viterbi path and successfully classified chronological market data into three latent regimes: **Bull (High Growth)**, **Bear (High Volatility)**, and **Stagnant (Mean-Reverting)**.
- [x] **Task 8:** Generated an overlay plot mapping the decoded HMM regimes against the historical timeline, accurately capturing the 2008 and 2020 macroeconomic crises.
- [x] **Task 9:** Documented the mathematical distinction between univariate time series (HMMs) and multivariate time series (Bayesian Networks).

### Phase 4: Causal Discovery & Network Validation
- [x] **Task 10:** Discretized continuous log-returns into binary momentum states (1 = Up, 0 = Down) to facilitate mathematical structure learning.
- [x] **Task 11:** Executed a minimal working example of the **Hill Climb Search** using `pgmpy` to algorithmically discover the Directed Acyclic Graph (DAG) of the global economy.
- [x] **Task 12:** Implemented the **Bayesian Information Criterion (BIC)** as the heuristic scoring objective to penalize network complexity and prevent structural overfitting.
- [x] **Task 13:** Extracted the **Markov Blanket** for WTI Crude Oil and defined the latent macroeconomic meaning behind the algorithmically discovered causal arrows.