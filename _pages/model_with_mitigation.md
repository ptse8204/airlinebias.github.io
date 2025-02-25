---
title: "Models with Mitigation"
permalink: /mitigatedmodels/
layout: single
---


## Bias Mitigated Model Development Summary

<img src="../assets/Bias_mitigation.png">


## Metrics Explaination:

We will evaluate our bias-mitigated models using various fairness metrics provided by the AIF360 package. We will give a thorough touch on each metric used to better help comprehend how our models perform. And we will interpret metrics from our baseline model (no bias mitigator, logistic regression)  as an example.

* **Balanced Accuracy (BC)**: It is the mean between the true positive rate and the true negative rate. It measures the average accuracy obtained from both the minority and the majority class. A score of 0.876 signals a good model performance in identifying negative and positive classes. However, the metric itself offers trivial indications regarding fairness. 


* **Average Odds Difference (AOD)**: It is the average difference in False Positive Rate (FPR) and True Positive Rate (TPR) for unprivileged and privileged groups. A value of 0 would indicate equality of chance of odds. Therefore, the metric with value close to 0 would suggest fairness: The FPR and TPR are relatively similar between privileged groups and unprivileged groups. 


* **Disparate Impact (DI)**: It is the probability of positive classification in the unprivileged group divided by the probability of positive classification in the privileged group. In a fair situation, we expected DI to be close to 1. Therefore, the metric with value of 1.243 signals unfairness even though the results favor the under-privileged groups: the probability of positive classification is significantly higher in the under-privileged group than the privileged group.


* **Statistical Parity Difference (SPD)**: The metric measures the differences between the probability of positive classification in the unprivileged group and the probability of positive classification in the privileged group. A value that is different than 0 will indicates unfairness as probability of positive classification is different between privileged and unprivileged groups. A positive value here would agree with the DI value found above, where the probability of positive classification is significantly higher in the under-privileged group than the privileged group. 


* **Equal Opportunity Difference (EOD)**: This metric measures the difference between the TPR of the unprivileged group and the true positive rate of the privileged group. A value that is significantly different than 0 will indicate unfairness as the TPR is different between privileged and unprivileged groups. Therefore, the metric with value close to 0 would suggest fairness: The TPR is relatively similar between privileged group and unprivileged group. 


* **Theil Index (TI)**: It is the generalized entropy index with alpha = 1. It measures an entropic "distance" the population is away from the "ideal" egalitarian state. 0 will indicate perfect equality, and 1 will indicate maximum inequality. Since the value is not exactly 0, the metric reveals at least some level of unfairness. 

## FarePerMile Results:

<img src="../assets/images/FPM_Table_Results.png">

From our results, we can see that random forest classifiers has worse accuracy compared to logistic regression, but is more fair initially. After applying Reweighing, we can see how our disparate impact reaches near ideal 1. Overall, Logistic Regression with Reweighing has the best results, as it has the highest accuracy (other than using no mitigation), best Disparate Impact and best Statistical Parity Difference. However, we can see there are some tradeoffs with using other options as it has one of the worse Equal Odds Difference and Theil Index

## FareClass Results

<img src="../assets/images/fareclass_results.png">

The Disparate Impact of 1.2261 on the model prior to any mitigation methods suggests a fair model from the very beginning. Now the focus would be to see how the Reweighing will improve the fairness of the model. After applying the preprocessing technique of Reweighing, we see the model fairness improves slightly including the balanced accuracy of the model. We see disparate impact reducing to get closer to the ideal value of 1 and equal opportunity difference and theil index reducing from 0.1957 to 0.059 and 0.1542 to 0.1440 respectively. 
