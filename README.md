# Life Insurance Premium Forecasting — Time Series Analysis

SARIMA-based time series modelling of LIC first-year premium data, with full stationarity testing, seasonal decomposition, and 12-month out-of-sample forecasting.

---

## Overview

This project models and forecasts **LIC (Life Insurance Corporation of India) first-year premium underwritten** using classical time series methods. The analysis covers the complete pipeline — from raw data cleaning and visual inspection through stationarity testing, model selection, diagnostic checking, and final out-of-sample forecasting with confidence intervals.

Multiple SARIMA specifications are compared on both raw and log-transformed scales to identify the most parsimonious and well-fitting model.

---

## Dataset

- **Source:** Life Insurance Corporation of India (LIC) — First Year Premium Underwritten (manipulated for academic use)
- **Frequency:** Monthly
- **Target:** First-year premium underwritten (₹)
- **Format:** CSV with date index

---

## Approach

| Step | Details |
|------|---------|
| Data Loading | CSV parsing with encoding handling, date indexing |
| Visualisation | Raw time series plot, trend inspection |
| Decomposition | Additive seasonal decomposition (period = 12) — trend, seasonal, residual components |
| Stationarity Testing | ADF test and KPSS test on raw, log-transformed, and differenced series |
| ACF / PACF Analysis | Lag plots on original and differenced series to determine SARIMA orders |
| Log Transformation | Applied to stabilise variance; inverse transformation applied to forecasts |
| Model Fitting | Multiple SARIMA(p,d,q)(P,D,Q,12) configurations compared |
| Auto Selection | `pmdarima` auto-ARIMA used for order benchmarking |
| Forecasting | 12-month ahead forecast with 95% confidence intervals |
| Evaluation | RMSE, R² on test set (last 12 months held out) |
| Diagnostics | Residual plots, Ljung-Box test for autocorrelation in residuals |

---

## SARIMA Configurations Explored

| Order (p,d,q) | Seasonal (P,D,Q,m) | Scale |
|---|---|---|
| (1,1,1) | (1,1,1,12) | Raw |
| (2,1,1) | (1,1,1,12) | Raw |
| (3,1,1) | (1,1,1,12) | Raw |
| (3,1,1) | (2,1,1,12) | Log |
| (3,1,1) | (3,1,1,12) | Log |
| (3,1,1) | (3,1,0,12) | Log |
| (3,1,1) | (2,1,0,12) | Log |

Final model selected based on AIC, residual diagnostics, and out-of-sample RMSE.

---

## Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)
![Statsmodels](https://img.shields.io/badge/Statsmodels-4051B5?style=flat-square&logoColor=white)
![pmdarima](https://img.shields.io/badge/pmdarima-AutoARIMA-009688?style=flat-square&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C8CBF?style=flat-square&logoColor=white)

---

## Repository Structure

```
life-insurance-time-series/
│
├── Time_Series_Project_Final_Code.ipynb   # Main notebook
└── Life_Insurance_LI_First_Year_Premium_Underwritten_FP_manipulated.csv
```

---

## Key Concepts Demonstrated

- Seasonal decomposition (additive model)
- Stationarity testing — ADF and KPSS
- ACF/PACF interpretation for order selection
- Log transformation for variance stabilisation
- SARIMA model fitting and diagnostic checking
- Ljung-Box test for residual white noise
- Out-of-sample forecasting with confidence intervals

---

*Part of coursework in Statistical and Predictive Analytics (SPA) — PGDBA, IIM Calcutta · IIT Kharagpur · ISI Kolkata*
