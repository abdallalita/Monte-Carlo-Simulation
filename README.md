# Table of Contents
# [Gold Price Forecasting](#Introduction)

## Introduction
Gold is one of the most important and actively traded assets in global financial markets. Its price often fluctuates with economic indicators, market indices, and geopolitical events, making both volatility forecasting and price simulation essential for risk management, portfolio allocation, and trading strategies.
In this project, I use the GARCH(1,1) model (Generalized Autoregressive Conditional Heteroskedasticity) to forecast gold price volatility and then apply a Monte Carlo simulation framework to generate potential future gold price paths based on these forecasts.

Qbjectives are:

- To capture and predict fluctuations in gold’s returns (volatility modeling).
- To simulate multiple future price scenarios, quantifying uncertainty and potential risks (Monte Carlo simulation).

This combination allows traders, investors, and risk managers to assess not only expected volatility but also the range of possible price outcomes under different scenarios.

## Dataset
- Observations: 1718 daily records
- Source: Yahoo Finance
- Period: November 18, 2011 – December 31, 2018
- Columns: Date and Adjusted Closing Price

## Data Preprocessing
- Checked for duplicates → None found.
- Sorted dates chronologically to ensure time-series integrity.
- No missing values detected.
- Computed log returns to transform raw prices into a stationary series suitable for volatility modeling.

## Exploratory Data Analysis (EDA)
Key findings before applying the model:

1. Price Trends: Gold prices showed a downward trend across the sample. Since raw prices are non-stationary, we model log returns instead.
2. Returns: Log returns oscillate around zero with no visible trend; ADF test confirmed stationarity.
3. Volatility Clustering: Periods of high volatility followed by periods of high volatility, and vice versa, a feature justifying GARCH use.
4. Autocorrelation: Significant autocorrelation in squared returns (via ACF and Ljung-Box test) supports GARCH suitability.
5. Summary Statistics:
Mean approximately 0 hence no drift.
Std. Dev. approximately 2.45% hence moderate volatility.
Extreme shocks between -11.31% and +12.00%.
Slightly positive skewness.
6. Return Distribution: Leptokurtic (fat tails), confirming extreme moves occur more often than under normal distribution.

## Volatility Modeling with GARCH(1,1)
Chosen model: GARCH(1,1) because it balances simplicity and strong empirical performance.

Variance depends on both past shocks (ARCH term) and past volatility (GARCH term).

- Diagnostics

Residuals: No significant autocorrelation remained (ACF + Ljung-Box test).

ARCH Effects: ARCH-LM test confirmed no residual heteroskedasticity.

Parameters: All statistically significant; α + β approximately to 1 indicates persistence in volatility.

## Model Validation

Rolling window forecasts: Ensures adaptability to changing market conditions.

Results: Forecasted vs realized volatility tracked each other closely.

Confirms GARCH(1,1) captured volatility clustering effectively.

## Evaluation Metrics

MAE: Forecast errors were small on average.

MSE: Penalized large errors, remained low.

QLIKE: Low value, tailored for volatility forecast evaluation.

All metrics confirmed reliable volatility forecasts.

## Monte Carlo Price Simulation

Building on the volatility estimates, I simulated 5000 of possible future gold price paths:

1. Inputs:

- Drift (average return trend).

- Volatility from GARCH forecasts.

- Residuals modeled with a Student’s t distribution to account for fat tails.

2. Simulation:

- Generated many scenarios for gold prices over the test period.

- Summarized with percentiles (P5, P25, P50, P75, P95).

3. Results (Fan Chart):

- P5–P95 (90% band): 90% of simulated paths fell within this interval each day.

- P25–P75 (50% band): Central scenarios capturing half of all paths.

- Actual prices (black line): Stayed within the 90% band throughout, confirming the model captured uncertainty well.

- Median forecast (P50): Slight downward trend, suggesting mild expected decline.

- Upper band (P95): Bullish case, prices up to approximately 27.5.

- Lower band (P5): Bearish case, potential drop to approximately 12.5.

## Interpretation:
The simulation provides not just a single point forecast but a range of possible futures, allowing traders and risk managers to evaluate both optimistic and pessimistic outcomes. The widening bands over time represent growing uncertainty the further out we forecast.

## Conclusion
This project demonstrates the integration of **statistical volatility modeling (GARCH)** with **Monte Carlo Somulation** to provide a richer picture of gold price dynamics:

- GARCH successfully modeled conditional volatility and captured clustering.
- Monte Carlo extended the analysis to simulate multiple future price paths, providing probabilistic insight into risks and opportunities.
  
---

2. ## Stock Prices Forecast
* [Overview](#overview-1)
* [Steps](#steps-1)
3. ## Net Income Forecast
* [Overview](#overview-2)
* [Steps](#steps-2)
4. ## Value at Risk Forecast
* [Overview](#overview-3)
* [Steps](#steps-3) 
### Stock price foreast 
#### Overview 1
Modelling the randomness of GOOGL stock price to predict plausible range of stock prices based on 20 years of historical data.
I used 20 years of data so as to consider the long term economic growtth, however one can choose how far back to go on the sampling method (shorter period of time) especially if we want the price to be mostly affected by current economic growth.

---
#### Steps 1
* Use historical stock prices from [Yahoo Finance](https://finance.yahoo.com/) and calculate daily log returns and statistical measures (mean, standard deviation, drift).
* The probability distribution of the daily returns will be used to simulate 10,000 price movements over the next 252 days (one trading year stock price movement).
* Calculate the price progression for each of the simulation to give one final price per simulation and quantify the conclusions (worst, average and best prices) using an appropriate confidence level.
--- 
### Net Income forecast
### Overview 2
Instead of three possible scenarios (worst case, common case, best case) to tell a story about how a future might look like, we might consider evaluating a range of cases using unlimited scenarios along with the probabilities of those events occurring.
With this information, we can make forward looking decisions such as assessing a required budget or come up with an expected view of what the future cashflows would be based on many simulations.
Here, I shall forecast a certain company's net income based on the Sales (revenue) and the Cost of good sold,

---
### Steps 2
* Use given assumptions about the company such as average  and standard deviation of Sales and cost of goods as a percentage of sales.
* Generate 10000 samples of sales and cost of goods sold. For each simulation, calculate the net profit in that scenario.
* Quantify the Best case, worst case and average case of the net income value. Plot the probability distribution and find the profit range with certain level of confidence.

---
### Value at Risk forecast
#### Overview 3
We may want to calculate the value of an investment that is at risk or have a certain amount of capital set aside to cover at a certain confidence level. This helps us to insure ourselves against the risk we have identified or we might develop a hedging strategy to help mitigate some of the downside we are exposed to.
Here I shall assess the risk of purchasing 1000, GOOGL shares and holding them for one month ( 30-day historical data)

---
### Steps 3
* Use key information or parameters such as current value of the investment at the current time and the volatility of the stock.
* Simulate the investment return of holding the stock for one month using 5000 scenarios.
* Based on how the 5000 returns are distributed, we acan find the one month VaR at 90%, 95% and 99% confidence levels.




