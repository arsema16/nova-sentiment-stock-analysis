# Financial News Sentiment & Stock Price Correlation Analysis

## Project Overview
This project, developed for **Nova Financial Solutions**, aims to bridge the gap between qualitative market narratives and quantitative price action. By architecting a pipeline that transforms raw financial news into sentiment scores, we establish measurable statistical correlations with stock price movements to develop predictive investment strategies.

## Technical Architecture
* **Data Processing:** Efficient handling and vectorization of a **1.407M article** dataset (FNSPID).
* **NLP Engine:** Sentiment quantification using **VADER** (Valence Aware Dictionary and sEntiment Reasoner) to handle short-form financial headlines.
* **Quantitative Analysis:** High-performance technical indicator computation using the **TA-Lib** C-based library.

## Automation & CI/CD
To ensure data integrity and code reliability, this repository utilizes GitHub Actions:
* **Unit Testing (`unittests.yml`):** Automatically triggered on pushes to `task-1`, `task-2`, and `main`. It validates data preprocessing scripts and ensures that NLP bigram extractions are consistent.
* **Task 1 Alignment:** The workflow specifically validates the EDA pipeline scripts located in `src/` to ensure 1.4M rows are processed without data loss.

## Key Insights (Interim Phase)

### 1. News Sentiment Exploratory Data Analysis (Task 1)
* **Data Consistency:** Analysis of 1.4M headlines revealed a median length of **64 characters**, confirming the data is ideally structured for NLP sentiment scoring.
* **Temporal Spikes:** Identified critical publication spikes, notably on **2020-03-12**, providing high-density "signal" periods for stress-testing correlation models.
* **Publisher Influence:** Discovered that a concentrated group of publishers (e.g., Paul Quintaro, Lisa Levin) dominates the news volume, allowing for source-weighted sentiment analysis.
* **Topic Distribution:** Preliminary keyword extraction identified primary drivers such as "Earnings," "FDA Approvals," and "Interest Rates," which assist in filtering market noise.

### 2. Quantitative Technical Analysis (Task 2)
* **Indicator Implementation:** Successfully deployed **Simple Moving Averages (SMA)** and the **Relative Strength Index (RSI)** to track AAPL price action.
* **Market Momentum:** The RSI implementation effectively identifies overbought and oversold regimes, serving as the quantitative backbone for upcoming correlation mapping.
## Project Structure

```text
nova-sentiment-stock-analysis/
├── .github/                # CI/CD workflows and GitHub Actions
├── data/
│   ├── raw/                # Read-only original datasets (AAPL.csv, ratings.csv)
│   └── processed/          # Cleaned data and computed technical indicators
├── notebooks/
│   ├── 01_EDA.ipynb        # Task 1: News analysis and text visualizations
│   ├── 02_Quant.ipynb      # Task 2: TA-Lib implementation & stock analysis
│   └── 03_Correlation.ipynb # Task 3: Sentiment-Price statistical mapping
├── src/
│   ├── __init__.py         # Makes src a Python package
│   ├── data_preprocessor.py # Modular cleaning and normalization logic
│   └── indicators.py        # Technical analysis functions (SMA, RSI, MACD)
├── tests/                  # Unit tests for data integrity and logic
├── .gitignore              # Prevents tracking of venv and large data files
├── requirements.txt        # Project dependencies and versions
└── README.md               # Professional project documentation
```
## Next Steps
* **Complete Indicator Suite:** Finalize implementation of remaining required indicators, including **EMA** and **MACD**.
* **Statistical Modeling:** Execute **Pearson correlation** calculations between daily sentiment averages and daily stock log-returns.
* **Visualization:** Develop **scatter plots** to visualize the relationship between sentiment shifts and price action.
* **Predictive Analysis:** Conduct **lead-lag analysis** to determine if sentiment shifts act as a leading indicator for price movements.

## Installation & Setup
1.  **Environment:** Python 3.11+
2.  **Core Dependencies:** `pandas`, `numpy`, `vaderSentiment`, `matplotlib`, `seaborn`, `nltk`, `scikit-learn`.
3.  **Technical Analysis:** **TA-Lib** (requires specific `.whl` binary for Windows 11 environments).

---
**Analyst:** Arsema Tefera  
**Date:** May 10, 2026 
