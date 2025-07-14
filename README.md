# Forecasting US Macroeconomic Indicators Using Cryptocurrency Volatility

## Authors
- **Alice Ye** ([xy2680@barnard.edu](mailto:xy2680@barnard.edu))
- **Annie Wang** ([tw3067@columbia.edu](mailto:tw3067@columbia.edu))
- **Tianyi Shen** ([ts3678@columbia.edu](mailto:ts3678@columbia.edu))

## Introduction

Studies have shown U.S. monetary policy announcements and macroeconomic shocks influence cryptocurrency volatility. However, the reverse effect of crypto volatility on US macroeconomic indicators is largely unexplored.

## Research Topic

We aim to understand to what extent volatility in major cryptocurrencies,
including stablecoins and non-stablecoins, can help improve forecasts of key U.S. macroeconomic
indicators. Our results show how the cryptomarket links to real economic signals.

## Data Collection and Processing

We collected data and computed monthly volatility for 8 macroeconomic variables and log-
transformed monthly volatility for 8 cryptocurrencies between 2017-09 and 2025-01.
![Data](Data.png)

To prepare the data, we computed log volatility of cryptocurrencies:
<p align="center">
  <img src="log_vol.png" alt="Log Volatility" width="400"/>
</p>

## Methodology
#### SARIMAX
We used SARIMAX model to evaluate cryptocurrencies’ predictive powers and SARIMA model as a benchmark for comparison. Our SARIMAX model:
![Equation](SARIMAX.png)

- Determine orders: d by the ADF Test (p < 0.05), seasonal differencing order D by the
Canova-Hansen Test, found the optimal AR order p, MA order q, seasonal AR order P , and
seasonal MA order Q by AIC minimization, and set the period for seasonal differencing to
S = 3 months (quarterly marker).
- Model Fitting: we generated 0-6 month lags for each crypto asset, identified significant
variables (p-value<0.05) and ranked by MAPE improvement. 
- Model evaluation: We evaluated model performance by p-value and MAPE (Mean Absolute Percentage Error). 

#### Sliding Window
Using the sliding window method, we aim to answer the question, whether crypto can help fore-
cast US macroeconomic variables, for 3 windows capturing periods including the COVID shock,
without the shock, and a more holistic period post-shock. Each model was trained using 3 windows with different macroeconomic regimes:
- Window 1 (high volatility): 2019–07 to 2022–02
- Window 2 (low volatility): 2022–04 to 2025–01
- Window 3 (moderate volatility): 2020–06 to 2025–01

## Results & Discussion
Combining all significant MAPE percentage changes across the three windows, we found improvement ranging from 2% to 93% and an average improvement of 32%.
![Heat](heat_map.png)
*Figure 1: MAPE Improvement(%) by SARIMAX vs. SARIMA for each Macro-Crypto Pair, Windows 1-3*

Across periods of varying macroeconomic volatility, we find that different cryptocurrencies enhance the forecasting accuracy of different macroeconomic indicators. 
In Window 1 (high volatility), incorporating Dogecoin volatility with a two-month lag improves predictions for LFPR, r, and IM, with MAPE reductions of 69.65%, 45.63%, and 65.48%, respectively. 
In Window 2 (low volatility), volatility from six cryptocurrencies (LTC, ETH, BTC, USDT*, USDC*, and XRP) contributes to reducing forecast error for CPI. Additionally, Cardano at a three-month lag yields the greatest improvement in this window, reducing the MAPE for r forecasting by 19.91%.
In Window 3 (moderate volatility), forecasts of the M1 money supply benefit the most from in-
corporating cryptocurrency volatility, with Dogecoin at a two-month lag reducing the MAPE by a substantial 93.39%.

## Conclusion

Our analysis reveals that cryptocurrencies demonstrate predictive power for macroeconomic variables across periods of different macroeconomic volatility. Notably, Dogecoin consistently predicts key indicators such as LFPR, r, and IM, across all three time windows, suggesting that investor sentiment may be more closely linked to the broader economy than previously understood. In the low volatility regime, 6 crypto assets demonstrated an increased explanatory strength for inflation rate (CPI), suggesting that during calm market phases, investor sentiment and liquidity conditions may become more closely aligned with crypto dynamics. Ultimately, while crypto’s predictive utility may be conditional on market regime, its performance suggests a potential role in hybrid forecasting models that combine traditional assets with a new, rapidly-growing market.

## Acknowledgements

This research was conducted as part of the Columbia Summer Undergraduate Research Experiences in Mathematical Modeling (CSUREMM). We are grateful to our advisors George Dragomir, Vihan Pandey, and Dobrin Marchev for their mentorship and support.
