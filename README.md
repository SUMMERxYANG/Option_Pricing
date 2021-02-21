# Option Pricing
This is my attempt at pricing options using the [Black Scholes Model](https://en.wikipedia.org/wiki/Black%E2%80%93Scholes_model) and [Monte Carlo methods](https://en.wikipedia.org/wiki/Monte_Carlo_method#Finance_and_business). The details of how I implemented these methods are documented in the notebook.

## Brief Overview

**Black Scholes method**: Using the solution to the Black Scholes PDE, I created functions to calculate prices for calls, puts, as well as the option greek vega to determine implied volatilities.

**Monte Carlo method**: Monte Carlo simulations rely on randomness. For each option, I generated random paths for which the stock prices could take (below are the first 100 of 100,000 outcomes). I calculated the option's intrinsic value for each path, and took the average of positive intrinsic values to be the predicted price.

<img src="Plots/priceCone.png" width="500">

More info:
[Random Walk & Geometric Brownian Motion](https://www.investopedia.com/articles/07/montecarlo.asp)


## The Results
Using the ask price as a benchmark, the predictions were accurate overall. As shown in the plots below, the predicted prices are very close to the ask price. 
The Black Scholes model was the less accurate method. It tended to overprice options - especially those that were out-of-the-money. The Monte Carlo predictions fit y=x (plotted as a grey line) much more closely.


Black Scholes              |  Monte Carlo
:-------------------------:|:-------------------------:
<img src="Plots/accuracyBS.png" width="500"> | <img src="Plots/accuracyMC.png" width="500">

## Regression Analysis
Upon discovering that in-the-money calls were priced more accurately, I wanted to find out which of the factors provided in the option chain were correlated with accuracy, other than the strike price. Below are the results:
<img src="Plots/corrBS.png" width="1000">
<img src="Plots/corrMC.png" width="1000">
