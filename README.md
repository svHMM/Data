# Financial Datasets for Stochastic Volatility Models

This repository contains the financial time series utilized in the paper **"Stochastic Volatility in Mean Models with Heavy Tails: A Fast Approximate Bayesian Inference Using Hidden Markov Models"**. 

The main objective of this repository is to ensure the reproducibility of data collection, preprocessing, and exploratory analysis of the indices analyzed in the study (S&P 500, Nikkei 225, DAX 30, and IBOVESPA).

## Data Description & Methodology

The raw historical data is fetched directly from **Yahoo Finance** using the `quantmod` package in R. 

For each index, the daily closing price sequence $\{P_t\}_{t=1}^T$ (specifically the Adjusted Close price) is collected and filtered to remove missing values (`NA`). The daily percentage log-returns ($y_t$) are then calculated using the standard financial transformation:

$$y_t = 100 \times \left( \log P_t - \log P_{t-1} \right), \quad t = 2, \dots, T$$

This transformation stabilizes the variance of the series and allows the evaluation of stylized facts of financial markets, such as volatility clustering and heavy tails.

## Prerequisites

To run the data collection script and generate the exploratory plots, you need to have **R** installed along with the following packages:

```R
install.packages(c("quantmod", "ggplot2", "gridExtra", "moments"))
