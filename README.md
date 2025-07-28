# Interactive U.S. Price Predictor

A Python tool that fetches U.S. housing, gas, and food market data, trains a Random Forest model, blends it with expert‐forecasted annual rates, and produces interactive Plotly charts with 2‑year forecasts.

## Table of Contents

- [Features](#features)  
- [Demo](#demo)  
- [Forecast Methodology](#forecast-methodology)  
- [Installation](#installation)  


## Features

- **Historical Data**: Pulls VNQ (housing), USO (gas), and DBA (food) ETFs as proxies.  
- **Normalization**: Indexes each series to a base value (e.g. 5000, \$3.00, 100).  
- **Machine Learning**: Trains a `RandomForestRegressor` on date ordinals.  
- **Expert Blend**: Mixes model forecasts 50/50 with linear compound growth from WSJ/EIA/USDA projections.  
- **Interactive Charts**: Beautiful dark‐mode Plotly graphs with range selectors and hover templates.  
- **Insights**: Prints current vs. 2‑year predicted prices with trend classification.  

## Demo

![Housing Forecast](demo/housing.png)  
![Gas Forecast](demo/gas.png)  
![Food Forecast](demo/food.png)  

*(Put your own screenshots in a `/demo` folder.)*

## Forecast Methodology

1. **Random Forest**  
   - Dates → ordinal integers → `MinMaxScaler` → 100‑tree `RandomForestRegressor`.  
2. **Expert Rates**  
   - Housing: 0.0% over 2 years  
   - Gas: –3.0% in Year 1  
   - Food: +2.2% per year  
3. **Blending**  
   - Compute RF predictions for each future day.  
   - Compute a compounding linear forecast using the expert rate.  
   - Take the 50/50 average of the two series.  

## Installation

1. **Clone** this repo  
   ```bash
   git clone https://github.com/YourUsername/price-predictor.git
   cd price-predictor
