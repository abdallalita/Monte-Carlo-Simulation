# Table of Contents
1. ## General Description
Monte Carlo Simulation is a computational algorithm which relies on repeated random sampling to create a representative view of the future.
It entails the following four steps to achieve results:
* Observations
Analyzing historical data to describe past movements of a variable with the help of a probability distribution (statistical measures), which describes past behaviour.
* Distributions
Once we understand the past behaviour, we can approximate the distribution of future behaviour. However if we don't have any observations of this past behaviour, we can select an appropriate distribution based on the knowledge that we have
* Simulations
We can use our distribution to create many random but plausible future scenarios. Repeating this process over and over again is the key to making confident predictions.
* Quantifications
Combining the results of many scenarios or simulations, we can quantify the chances of an event occurring or the scale of risk we are exposed to as a business.
Overall the algorithm helps in modelling uncertainty in predictive and forecasting models and it is based on the [Law of Large Numbers](https://www.britannica.com/science/law-of-large-numbers)
2. ## Stock Prices Forecast
* [Overview](#overview-1)
* [Steps](#steps-1)
3. ## Net Income Forecast
* [Overview](#overview-2)
* [Steps](#steps-2)
4. ## Value at Risk Forecast
* [Overview](#overview-3)
* [Steps](#steps-3) 
### Overview 1
Modelleling the randomness of GOOGL stock price to predict plausible range of stock prices based on 20 years of historical data.
I used 20 years of data so as to consider the long term economic growtth, however one can choose how far back to go on the sampling method (shorter period of time) especially if we want the price to be mostly affected by current economic growth.

---
### Steps 1
* Use historical stock prices from [Yahoo Finance](https://finance.yahoo.com/) and calculate daily log returns and statistical measures (mean, standard deviation, drift).
* The probability distribution of the daily returns will be used to simulate 10,000 price movements over the next 252 days (one trading year stock price movement).
* Calculate the price progression for each of the simulation to give one final price per simulation and quantify the conclusions (worst, average and best prices) using an appropriate confidence level.
--- 
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
### Overview 3
We may want to calculate the value of an investment that is at risk or have a certain amount of capital set aside to cover at a certain confidence level. This helps us to insure ourselves against the risk we have identified or we might develop a hedging strategy to help mitigate some of the downside we are exposed to.
Here I shall assess the risk of purchasing 1000, GOOGL shares and holding them for one month ( 30-day historical data)

---
### Steps 3
* Use key information or parameters such as current value of the investment at the current time and the volatility of the stock.
* Simulate the investment return of holding the stock for one month using 5000 scenarios.
* Based on how the 5000 returns are distributed, we acan find the one month VaR at 90%, 95% and 99% confidence levels.




