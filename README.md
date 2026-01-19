# Fairness-Aware Stock Market Prediction

This repository contains the code and experiments developed for an MSc dissertation on **fairness-aware stock market prediction using machine learning and event-driven news sentiment**.  
The project evaluates whether incorporating financial news sentiment improves short-term stock prediction performance and whether such improvements are consistent across market sectors.

---

## Project Overview

Stock market prediction models often rely exclusively on historical price data. This project investigates whether **event-driven news sentiment** can provide additional predictive value and whether sentiment integration affects sectors differently.

The study evaluates multiple machine learning and deep learning models on **40 S&P 500 stocks across 10 sectors**, comparing price-only models with sentiment-enhanced models using time-series-aware validation.

Key objectives:
- Assess the predictive impact of news sentiment on stock returns
- Compare performance across sectors to identify uneven benefits
- Evaluate fairness in terms of sector-level consistency rather than individual asset optimisation

---

## Data Sources

- **Historical price data**: Yahoo Finance (daily OHLCV)
- **News sentiment data**: Polygon.io financial news API
- **Sentiment scoring**: VADER (lexicon-based sentiment analysis)

Raw data are retrieved via APIs at runtime and are **not stored in this repository** due to size and licensing constraints.

---

## Models Implemented

- Linear Regression
- Ridge Regression
- Lasso Regression
- Random Forest Regressor
- XGBoost Regressor
- Voting Regressor (ensemble)
- Long Short-Term Memory (LSTM) network

Both **price-only** and **sentiment-enhanced** variants are evaluated.

---

## Feature Engineering

- OHLCV-based numerical transformations (returns, lagged values, volatility)
- Event-driven sentiment features derived from news articles
- Lagged sentiment features (1–3 days)
- Recursive Feature Elimination (RFE) for balanced feature selection

Sentiment and numerical features are combined at the feature level with careful temporal alignment to avoid data leakage.

---

## Evaluation Methodology

- **TimeSeriesSplit** cross-validation to preserve temporal order
- Regression metrics:
  - R²
  - RMSE
  - MAE
- Directional metric:
  - Directional Accuracy (next-day return sign)

Sector-level aggregation is used to assess consistency and fairness.
