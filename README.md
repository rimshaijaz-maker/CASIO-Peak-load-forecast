# CAISO Peak Load Forecasting & Shape Factor Analysis

Forecasting peak electricity demand and hourly load profiles for the 
California Independent System Operator (CAISO) grid using historical 
hourly load data (Nov 2024 – Oct 2025).

## Problem
Grid operators need accurate peak load and hourly demand forecasts to 
balance supply, prevent blackouts, and optimize energy procurement. 
This project builds data-driven forecasts for CAISO's March 2026 peak.

## Tools & Methods
- Python (Jupyter Notebook), Pandas, NumPy, Matplotlib
- Time-series preprocessing and feature engineering
- Persistence baseline model with backtesting
- Analog-day shape factor (slice-of-day) forecasting

## Key Results
| Task | Output |
|------|--------|
| **Q1a** March 2026 Peak Forecast | **29,422 MW** (4.6% annual growth) |
| **Q1b** Forecasted Peak Date | **March 13, 2026** (Friday, mid-month) |
| **Q1d** Persistence Model MAPE | **8.43%** (MAE: 2,929 MW) |
| **Q3c** Peak Hour (d*)| **Hour Ending 11** (11 AM), sh = 1.00 |

## Methodology

**Q1 — Point Forecast**  
Growth rate derived from Nov 2024–Oct 2025 average load trend 
(annualized from 11-month span). Applied to March 2025 observed peak 
to forecast March 2026.

**Q1d — Persistence Baseline Backtest**  
Forecast(month t) = Actual peak of month (t-1). Evaluated across 11 
months; high errors in May and October due to seasonal transitions.

**Q3c — Slice-of-Day Shape Factors**  
Analog day: March 14, 2025 (observed March 2025 peak day, Friday).  
Shape factor: sh_h = L_h / L* (normalized to daily peak = 1.0).  
Multiplied by L* = 29,422 MW to produce hourly forecast for March 13, 
2026. Profile exhibits a midday trough consistent with California's 
duck curve.

## How to Run
1. Place `CAISOHourlyLoadCSV.csv` in the same directory
2. Open `homework 1 energy analytics.ipynb` in Jupyter
3. Run all cells sequentially
