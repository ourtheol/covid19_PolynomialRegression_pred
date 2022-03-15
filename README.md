### Polynomial Regression on the confirmed cases of COVID-19time series dataset

Between 2011 and 2018, the World Health Organization (WHO) tracked 1483 epidemic events in 172 countries (GPMB,2019 A World at Risk: Annual report on global preparedness for health emergencies). Epidemic-prone diseases such as influenza, Severe Acute Respiratory Syndrome (SARS), Middle East Respiratory Syndrome (MERS), Ebola, Zika, and the current pandemic of COVID-19 highlight the importance of global coordination mechanisms that can monitor the spread of pathogens and the necessity of tools that can infer the true state of a pandemic using down sampled data that imperfectly represent the true amount of the population being infected by the pathogen. 

In this project polynomial regression models are fitted on time series datasets of the number of confirmed COVID-19 cases from different countries in order to construct the curve that best characterizes the growth of the epidemic in each country and to predict the near future number of confirmed COVID-19 cases using the already available data. Then the autoregressive integrated moving average (ARIMA) model is fitted on the time series datasets of the number of confirmed COVID-19 cases from the same countries in order to construct the curve that best characterizes the growth of the epidemic in each country and to predict the near future number of confirmed COVID-19 cases using the already available data, using as benchmark a simpler polynomial fitting model.

#### Polynomial Regression
Polynomial regression analysis finds the unknown parameters of the nth degree polynomial in x that best characterizes the relationship between the independent variable x and the dependent variable y, based on minimizing the sum of the squared errors between the true y values of the data and the y values calculated from the nth degree polynomial (least squares estimation). Polynomial regression is a subcategory of multiple linear regression analysis because the unknown parameters of the polynomial that are estimated from the data are linear. Linear
regression is a simple first approach, computationally inexpensive that can give a first impression on the relationship between the independent and the dependent variable and could work as a benchmark for more advanced approaches. The downside of using linear regression models for time series data is that they do not extrapolate reliably.

Time series data from different countries (China, South Korea, Japan, Italy, Spain, France, UK, Germany, Netherlands, USA, and Greece) retrieved from the kaggle website ("Novel Corona Virus 2019 Dataset", 2020) were used in order to identify the optimal model from the simple parametric family of polynomials (with degree up to 9). The time series data from each of the aforementioned countries until date X (which in this study is selected to be March 20, 2020) were split randomly into a train set (2⁄3 of the dataset) and a test set (1⁄3 of the dataset). The train set of each country was used to find the unknown parameters of the polynomials of degree 1 to degree 9 and the test set was used to test the polynomial models’ performance by calculating the root mean square error of the true y value of the test set minus the y value calculated by the different polynomial models for each model, in order to check for data over fitting. A table containing the R-square value, the adjusted R-square value, the BIC value and the root mean square error of each polynomial model for each country was printed in order to identify the
optimal polynomial that best characterizes the growth curve of COVID-19 cases in each country. The selection of the best polynomial model for each country was done based on how well the regression line approximates the train set points (R-squared), by taking into consideration the number of observations and the degrees of freedom of the residuals (adjusted R-squared: penalizes the excessive number of features and decreases, whereas the R-square will remain high), the value of the BIC criterion (smaller values were preferable) and by minimizing the test set error (root mean square error of the test set). After the optimal model for each country was determined, future numbers of confirmed cases beyond date X (March 20, 2020), until March 26, 2020, were predicted. The predicted data were compared to the true counts of confirmed cases for each day and the root mean square error was calculated. The true counts of confirmed cases were collected from the visual dashboard of the Johns Hopkins University.

#### ARIMA model
ARIMA models are widely used for forecasting a time series dataset with non-stationarity in means, which can be made to be “stationary” by differencing. ARIMA models are a generalization of an autoregressive moving average (ARMA) model, that requires the time series to be stationary.
A nonseasonal ARIMA model is classified as an "ARIMA(p,d,q)" model, where:

● p is the number of autoregressive terms,

● d is the number of nonseasonal differences needed for stationarity, and

● q is the number of lagged forecast errors in the prediction equation.

To determine the order of a non-seasonal ARIMA model, a useful criterion is the Akaike information criterion (AIC) and the Bayesian Information Criterion. The objective is to minimize the AIC or BIC values for a good model. ARIMA has been a classical approach taking into account the autoregressive nature of the data in Epidemiological research. MethodsTime series data from different countries (China, South Korea, Japan, Italy, Spain, France, UK,
Germany, Netherlands, USA, and Greece) retrieved from the kaggle website ("Novel Corona Virus 2019 Dataset", 2020), until date X (which in this study is selected to be March 20, 2020) were used. The autocorrelation and the partial autocorrelation plots for the original time series dataset for each country as well as for the 1st differencing and the 2nd differencing of the dataset were plotted in order to select the order of differencing (d), of the AR term (p) and of of the MA term (q) in the ARIMA model.

Selection of the order of differencing (d) in the ARIMA model:
The d parameter of the ARIMA model is selected based on the stationarity of the series, inspecting the autocorrelation plots.

Selection of he order of the AR term (p) in the ARIMA model: The required number of AR terms is selected by inspecting the Partial Autocorrelation (PACF) plot for the number of lags that cross the significance limit in the PACF plot.

Selection of he order of the MA term (q) in the ARIMA model: The required number of MA terms is selected by inspecting the Autocorrelation (ACF) plot for the number of lags well above the significance limit in the ACF plot.

The BIC criterion was used for model selection.

The ARIMA model determined was used to forecast the counts of confirmed cases of COVID-19 in the future dates: 21-03-2020 to 26-03-2020 and the predicted data were compared to the true counts of confirmed cases for each day and the root mean square error was calculated. The true counts of confirmed cases were collected from the visual dashboard of the Johns Hopkins University. The root mean square deviation of the predicted minus the true counts was then compared to the root mean square deviation of the best polynomial model for each country.

#### Poisson regression
For Epidemiological time series datasets, Poisson regression and Poisson autoregressive regression models have been applied to various studies. The Poisson regression model was fitted to a train set (2/3 of the dataset) and a test set (1/3 of the dataset).

In the case of the COVID-19 time series dataset, the Poisson regression model did not seem to perform well. The reported values of Deviance and Pearson Chi-square are very large and when checking the chi-square table for p=0.05 and Degrees of freedom of residuals for the observed statistic, the chi-square value of the table was much smaller than the one reported. So, in spite of demonstrating a good visual fit, the model has fit the training data poorly.


#### Conclusions
The ARIMA models can do reliable predictions for countries that are coming out of the exponential phase and have more complicated curves where plateau phases or steeper/slower increase are present. There are cases where the ARIMA models do not work well and simpler models such as polynomial regression can do more precise predictions.
