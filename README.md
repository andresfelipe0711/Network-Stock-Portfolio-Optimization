# Unveiling Connections: Network Analysis of the S&P 500 Stocks

A data science project that uses **network analysis** to study relationships among S&P 500 stocks and build portfolios (central vs. peripheral) that are then evaluated against the S&P 500 index.

## Overview

Active investing aims to beat the market’s average returns. This notebook simulates portfolio construction by:

1. Modeling the S&P 500 as a **correlation network** (stocks as nodes, correlations as edges).
2. Using **graph theory** (e.g. Minimum Spanning Trees and centrality) to identify “central” and “peripheral” stocks.
3. Building **central** and **peripheral** portfolios and comparing their performance to the S&P 500 over a hold-out year (2021).

## Goals

- Load and clean S&P 500 price data (2011–2020 for analysis, 2021 for evaluation).
- Compute **daily log returns** and **correlation matrices** (yearly and full period).
- Build **graphs** from correlations and filter them with **Minimum Spanning Trees (MST)**.
- Identify **central** and **peripheral** stocks using network metrics (degree, closeness, betweenness, eigenvector centrality).
- Construct **central** and **peripheral** portfolios and evaluate their performance vs. the S&P 500 in 2021.

## Data

- **Training**: S&P 500 adjusted close prices, 2011–2020  
  - `snp500_price_data_2011_to_2020.csv` (from GitHub).
- **Evaluation**: S&P 500 prices for 2021  
  - `snp500_price_data_2021.csv` (from GitHub).

## Notebook Structure

| Section | Description |
|--------|-------------|
| **Exploratory Analysis** | Load data, inspect missing values, split by year. |
| **Daily Log Returns** | Compute log returns for stationarity and variance stabilization. |
| **Correlation** | Yearly correlation matrices and heatmaps (2011–2020), with short discussion of major events (e.g. 2020 COVID-19). |
| **Creating Graphs** | Build fully connected graphs from correlation matrices; introduce MST to reduce noise and show structure. |
| **Filtering: MST** | Distance from correlation \( \sqrt{2(1 - \rho)} \), build MST per year, plot and interpret. |
| **Statistics Over Time** | Average shortest path length over years (e.g. higher dispersion in 2011, more clustering in 2020). |
| **Portfolio Construction** | Single correlation matrix over 2011–2020, distance matrix, MST, and centrality (degree, closeness, betweenness, eigenvector). |
| **Selecting Stocks** | **Central portfolio**: top 10% by degree or betweenness. **Peripheral portfolio**: degree = 1 or betweenness = 0, then top 15 by average distance. |
| **Performance Evaluation** | Simulate portfolio values for 2021; compare central portfolio, peripheral portfolio, and S&P 500. |

<img width="2420" height="855" alt="image" src="https://github.com/user-attachments/assets/402afe52-7a91-4c08-83ea-a70162f92f72" />


## Key Concepts

- **Log returns**: Used for stationarity and stable variance in time series.
- **Correlation distance**: \( d = \sqrt{2(1 - \rho)} \) to turn correlation into a distance for the MST.
- **Minimum Spanning Tree (MST)**: Connects all stocks with minimal total distance, highlighting the main correlation “backbone.”
- **Centrality**: Degree, closeness, betweenness, and eigenvector centrality identify influential (central) vs. marginal (peripheral) nodes in the stock network.

## Results (from the notebook)

- The S&P 500 network is summarized with an MST and centrality measures; a small set of stocks (e.g. a few hubs) stand out as central.
- **Central portfolio**: Stocks with highest degree/betweenness (and related centrality).
- **Peripheral portfolio**: Stocks with degree 1 or betweenness 0, then the 15 farthest by average distance.
- Performance is compared in 2021: central portfolio, peripheral portfolio, and S&P 500 (e.g. cumulative value or returns). The notebook includes the exact comparison and any outperformance metrics.
