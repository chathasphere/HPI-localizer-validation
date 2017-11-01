# HPI-localizer-validation
Estimating local home price indices via a linear regression on core stochastic simulations and validating volatility estimates

This respository contains the second of two projects I undertook during my internship at Andrew Davidson & Co, this time under the supervision of the Financial Engineering team. 


***
I worked on my second project with MRC's financial engineering department, in an effort to validate their Home Price Index model's localizer. (The 'worth' of a home, as I learned, is one of the main factors in credit risk, so a good HPI forecast is a useful thing in modeling MBS's.) The HPI model stochastically simulates home price movements in five core localities, and the localizer, via a constrained linear regression on historical HPI data, predicts HPI in all states and MSAs. First, I validated the coefficients of the regression. Next, I applied stochastic analytic techniques to derive the historical and simulated volatilities of the HPI time series. Lastly, I identified certain problematic regions where the model predicted ahistorically high volatility.
