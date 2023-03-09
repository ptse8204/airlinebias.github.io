---
title: "Price Sensitivity Model"
excerpt: "The price sensitivity model is a model that predict on a scale from 0-1 to showcase whether the price would be offered. This is a model based on using the distribution (CDF) of the airfare of a given city-pair origin and destination and the carrier from the DB1B dataset. "
sitemap: true
layout: single
---

## Introduction
The price sensitivity model is a model that predict on a scale from 0-1 to showcase whether the price would be offered. This is a model based on using the distribution (CDF) of the airfare of a given city-pair origin and destination and the carrier from the DB1B dataset. The CDF serve as an indicator of whether a given airfare would appear to indicate how sensitive a given fare is to the stakeholders (Airline and Passengers), as it is able to capture the probability of whether a given ticket would be valid.

The sensitivity metric is calculated by taking all the ticket prices and the related fare per mile in 2022 dollars from the dataset (2016-2022) and ranking them in ascending order between the interval of 0 to 1 in groups of origin, destination, and the airline. On the training data, 0 represents the lowest price available in the dataset on a given city-pair and airline, and 1 represents the highest price available in the dataset on a given city-pair and airline. Essentially, the values are the CDF of the distribution. All price of the data is adjusted by the CPI index (Airfare category) to 2022 dollars. The model was trained based on data from 2016-2022 DB1B dataset.

We interpret if the model predicts 1, means that the passenger would be least likely to make a purchase of a fare and the airline would most likely offer such a fare. If the model predict 0, means the passenger would be most likely to make a purchase of a fare and the airline would least likely offer such a fare. If the model predicts anything that is > 1 or < 0, it means that the price is never going to happen.

After creating the model, we run test on the model by providing various scenarios that are in the trainset, not in the trainset and imagine scenarios. From our test, we aim to see what bias exist and how we could mitatgate such, and provide a showcase on how an airline or an individual would be able to benefit of such a model.

This model is a model that runs based on 2 assumptions:
- Passengers/Consumers will always purchase a lower fare if possible
- Airlines will always offers a higher fare if possible

## Initial Model and Results
The initial model of such a prediction runs extremely well, our first initial model uses sci-kit learn's linear regression (`sklearn.linear_model.LinearRegression`), and LightGBM's (`lightgbm.LGBMRegressor`). Since the large scale of the dataset, we decided the initial model would only train a small subset that is randomly selected from 2018 Q2, and test on another subset of the same quarter. We believe such an approach to test and train our model would appropiate during our initial stage, as we are only finding ways to see what model approach and variable would be a best predictor. We found the best model is trained based on the following parameters below:
### Predictor

|Columns Used|Detail|Processing Method|
|---|---|---|
|OriginCityMarketIDCoupon|Flight Segment Origin Market Area (e.g.: LAX and SNA would be in Los Angeles Market Area), defined by USDOT [here](https://www.transtats.bts.gov/FieldInfo.asp?Svryq_Qr5p=b4vtv0%FDNv42146%FP%FDPv6B%FDZn4xr6%FDVQ.%FDPv6B%FDZn4xr6%FDVQ%FDv5%FDn0%FDvqr06vsvpn6v10%FD07zor4%FDn55vt0rq%FDoB%FDhf%FDQbg%FD61%FDvqr06vsB%FDn%FDpv6B%FDzn4xr6.%FD%FDh5r%FD6uv5%FDsvryq%FD61%FDp1051yvqn6r%FDnv421465%FD5r48v0t%FD6ur%FD5nzr%FDpv6B%FDzn4xr6.&Svryq_gB2r=a7z&Y11x72_gnoyr=Y_PVgl_ZNeXRg_VQ&gnoyr_VQ=FLM&flf_gnoyr_anzr=g_QOEO_Pbhcba&fB5_Svryq_anzr=beVTVa_PVgl_ZNeXRg_VQ)|`sklearn.preprocessing.OneHotEncoder`|
|DestCityMarketID|Flight Segment Destination Market Area (e.g.: LAX and SNA would be in Los Angeles Market Area), defined by USDOT [here](https://www.transtats.bts.gov/FieldInfo.asp?Svryq_Qr5p=b4vtv0%FDNv42146%FP%FDPv6B%FDZn4xr6%FDVQ.%FDPv6B%FDZn4xr6%FDVQ%FDv5%FDn0%FDvqr06vsvpn6v10%FD07zor4%FDn55vt0rq%FDoB%FDhf%FDQbg%FD61%FDvqr06vsB%FDn%FDpv6B%FDzn4xr6.%FD%FDh5r%FD6uv5%FDsvryq%FD61%FDp1051yvqn6r%FDnv421465%FD5r48v0t%FD6ur%FD5nzr%FDpv6B%FDzn4xr6.&Svryq_gB2r=a7z&Y11x72_gnoyr=Y_PVgl_ZNeXRg_VQ&gnoyr_VQ=FLM&flf_gnoyr_anzr=g_QOEO_Pbhcba&fB5_Svryq_anzr=beVTVa_PVgl_ZNeXRg_VQ)|`sklearn.preprocessing.OneHotEncoder`|
|RPCarrier|Reporting Carrier Code, shown [here](https://www.transtats.bts.gov/FieldInfo.asp?Svryq_Qr5p=er2146v0t%FDPn44vr4%FDP1qr&Svryq_gB2r=Pun4&Y11x72_gnoyr=Y_PNeeVRef&gnoyr_VQ=FLM&flf_gnoyr_anzr=g_QOEO_Pbhcba&fB5_Svryq_anzr=eRcbegVaT_PNeeVRe)|`sklearn.preprocessing.OneHotEncoder`|
|RoundTrip|Boolean Round Trip Indicator (1=Yes)|`sklearn.preprocessing.OneHotEncoder`|
|FarePerMile|Itinerary Fare Per Miles Flown in Dollars (ItinFare/MilesFlown)|`sklearn.preprocessing.StandardScaler`|
|CouponDistance|Segment Distance In Miles|`sklearn.preprocessing.StandardScaler`|
|MilesFlown|Itinerary Miles Flown (Track Miles)|`sklearn.preprocessing.StandardScaler`|
|LOAD_FACTOR|Ratio of Passenger Count and Seat Count from T-100 dataset|`sklearn.preprocessing.StandardScaler`|

### Perfomance of Inital Model
Using the same year as the training and testing data (where train and test sets are separated), the model's initial accuracy in $R^2$: .92

### Bias Mitagation on Initial Model
To improve accuracy on the protected group compared to the privilege group, oversampling was applied to the protected group to address the issue of bias. As a result, the accuracy of the protected group increased from .85 to .9, indicating some degree of bias mitigation. However, the accuracy of the privilege group decreased from .97 to .94. It is important to note that the accuracy of the original test set remained unchanged, indicating that oversampling did not negatively affect the generalizability of the model. The oversampling technique represents an effort to promote fairness in the model's predictions for both the privilege and protected groups. 

Since the oversampling technique work reasonably well on the initial model, therefore, we decided to build our final model based on such an assumption.
## Final Model Created Based on Initial Model 

## Demo of the Final Model
