#AWS Forecast Workshop

Hierarchy:
ML Infra -> Sagemaker -> Forecast

##Managed Models (Predictors)

##Baseline Models: 

Statistical - 100s of datapoints
ARIMA: Auto regressive integrated moving average - simple statistical regression 
ETS: Exponetial smoothing - trend, seasonality, and residual

Flexible Local - 1000s of datapoints 
Prophet 
Good for: trend, seasonality, cyclical, holiday effects 

NN - 1,000,000s
DeepAR++ 
Good for: complex patterns / cold start problems 

##AutoML vs Manual 

- Depending on algo - different resources are used 

DataSets -> Predictors -> Forecast (BackTesting)

##Ways to judge model accuracy: 
Error / Loss 
weighted quantile loss 
RMSE - root mean squared 

https://aws.amazon.com/forecast/

Generall Impression: 
Seems useful for quick discovery of trends and predications with precanned models. Doesn't seem like something to productionaize. 
