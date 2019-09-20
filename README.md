# HPI-localizer-validation

Estimating US regional home price indices via a linear regression on core stochastic simulations, validating estimated volatility against historical data.

### Financial Background:

HPI measures the percent change in house prices over a sample, with the baseline normalized to 100. It is commonly understood that the underlying value of a home is a significant risk factor in mortgage-backed securities, and so AD-Co models *projected* HPI as part of their proprietary mortgage risk model. 

The HPI model can be thought of as a two-component system, a core simulator and a localizer. The core simulator focuses on 5 indices, corresponding to 5 indices of Radar Logic's (since discontinued) RPX housing-price forward contracts, New York, Miami, Phoenix, Los Angeles, and a 25-city composite. The original reasoning behind this choice is that, while the RPX indices were being traded, accurate forward prices were available to supplement the model's projections. As HPA (returns on HPI) series tend to resemble geometric Brownian motion (local random 'jumps', long-term 'drift'), the HPI core model makes use of a stochastic differential equation, further discussed in the "HPI Black Volatility 3" notebook, the coefficients of which are estimated from empirical data. Thus, New York's HPI has a lower volatility than, say, that of Phoenix. 

From these core indices, we run a constrained linear regression to estimate HPI series in the 50 states, in numerous Metropolitan Statistical Areas, and nationwide. The reasoning is that a given locality's HPI may be positively or negatively correlated against any of the core indices.

### The Problem:

The localizer achieves a high level of accuracy in terms of an R^2 score (see the notebook "localzier/HPA Localizer.ipynb" for details), but the linear regression method has at least one shortcoming: the regression tends to exaggerate HPI volatility in localities with a large set of coefficients. (In simplified terms, expanding stochastic by a scalar multiple and combining them will result in more extreme, coincident jumps.) 

In the principle notebook, I derive historical and simulated "Black" Volatility (named after Fischer Black of the Black-Scholes model) in all indices and identify where the model errs. 
