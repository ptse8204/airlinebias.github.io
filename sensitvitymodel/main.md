# Price Sensitivity Model

## Introduction
The price sensitivity model is a model that predict on a scale from 0-1 to showcase whether the price would be offered. On the training data, 0 represents the lowest price available in the dataset on a given city-pair and airline, and 1 represents the highest price available in the dataset on a given city-pair and airline. Essentially, the values are the CDF of the distribution. The price of the data is adjusted by the CPI index (Airfare category) to 2022 dollars. The model was trained based on data from 2016-2022 DS1B dataset.

We interpret if the model predicts 1, means that the passenger would be least likely to make a purchase of a fare and the airline would most likely offer such a fare. If the model predict 0, means the passenger would be most likely to make a purchase of a fare and the airline would least likely offer such a fare. If the model predicts anything that is > 1 or < 0, it means that the price is never going to happen.

This model is a model that runs based on 2 assumptions:
- Passengers/Consumers will always purchase a lower fare if possible
- Airlines will always offers a higher fare if possible

## Initial Model and Results
The initial model of such a prediction runs extremely well, our first initial model uses sci-kit learn's linear regression (`sklearn.linear_model.LinearRegression`), and train based on the following parameters below:


## Bias Mitagation on Initial Model

## Final Model Created Based on Initial Model 

## Demo of the Final Model
