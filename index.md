**Do you think there is always some kind of bias exist on flight tickets, we found out...**

<img src="https://blog.asaptickets.com/wp-content/uploads/2018/09/Consolidated-airfares.png">


## Introduction

Price discrimination is the practice of setting significantly different prices for different groups of people for the same or similar commodity. This is specifically known as third-degree price discrimination. As a result, this can often lead to optimized profits for the seller, with a subset of buyers left paying higher prices. In the airline industry, there are several features associated with distance and the airports themselves that can affect the fare price as well as external forces such as market concentration and competitors. In turn, the **local demographics** of airport metro areas are features we hypothesize may distinguish significant pricing discrimination between majority and minority populations in airfare prices when comparing similarly comparable flights. Our goal is to identify potential factors in the dataset that may be causing biases in model implementations, mitigating these biases and ultimately developing fairer machine learning models for fairer airfare pricing.



This website showcase our investigation on how airline price discriminate on certain 
<details open>
<summary>proctected groups/features,</summary>
<br>
"protected groups" refer to groups of individuals who are considered to be historically disadvantaged or marginalized based on certain characteristics, such as race, gender, age, or ethnicity. These characteristics are often associated with systemic inequalities and discrimination in various aspects of society, including employment, education, healthcare, and criminal justice.
</details>


including but not limit to:
* Race

<details open>
<summary><img src="https://penntoday.upenn.edu/sites/default/files/2021-06/iStock-1202344480.jpg" width="400" height="400"></summary>
<br>
Race: In our case, it would be the proportion of White Vs. Non White population in the local airport metro area.
</details>

<br>
* Income

<details open>
<summary><img src="https://cdn.mos.cms.futurecdn.net/Xv3k77UcipignuVPtHsC43.jpg" width="400" height="400"></summary>
<br>
Income: In our case, it would be a categorical variable that determine the income of the local airport metro area (Low Vs. High). Low income is defined to be whether the median of the local income is less than or equal to the 25th quantile threshold found from a distribution of median incomes across all metro areas. And high income is defined to be whether the median of the local income is larger than or equal to the 75th quantile threshold found from a distribution of median incomes across all metro areas.
    
</details>


Our bias analysis and mitigation will be conducted with support of the <a href="https://github.com/Trusted-AI/AIF360">AI Fairness 360 (AIF360)</a> toolkit. In turn, we aim to develop a model that balances both accuracies as well as fairness between our classes.


We understand that airfare pricing is a business decision that was driven by revenues. However, by investigating such factors, it may also drives airline's bottom line as the result could be useful for more attractive pricing for passengers.


## Methodology
### Dataset

We mainly use airline ticket and pricing data from the **Airline Origin and Destination Survey (DB1B)**. We decide to use such a dataset instead of web-scraping because the data point in the dataset represents the final/actual fare that customers pay for. The DB1B database is maintained by the United States Department of Transportation Bureau of Transportation Statistics. The <a href="https://www.transtats.bts.gov/tables.asp?QO_VQ=EFI&QO_anzr=Nv4yv0r">DB1B datasets</a> has data from 1993 to the 2nd Quarter of 2022, however, due to the constrain of our environment capabilities, we are only using the data **from 2018 to the most recent available record** in our project. 

While the DB1B database does not include demographics such as race, age, or income, for our purposes, we are instead using **U.S. Census data** in order to get feature variables that describe the local populations of the origin airport metropolitan area and the destination airport metro area. By merging these two datasets, we are able to investigate the relationship between local population demographics and airline ticket prices.



### How does finding bias work?
We aim our investigation (mainly) in 2 directions:
* Investigate whether there is price discrepency in protected groups on existing dataset
* Feed the data on to our custom build models, and see whether the model would generate results that showcase strong bias. In especially models that are extremely accuracte, and has a hard time to correctly identity areas that has a strong influence with protected groups.

## Expected Goals and Outcomes
### Goals
* Discover bias, if any
* Creating an accurate model, that is both accurate and unbias, using various accuracy measurments, and bias mitogation techniques.
* Discover any trend shift of airfare pre-pandemic and post-pandemic

### Outcomes
* An unbias model for extimatting the fair price that customers pay
* An indicator allow consumers to know whether they are price dscriminated and whether they are paying the fair price

## Credits
Tba :)

## Notes
We will keep updating the repo alongside with our progress.
readme file last update: Feb 12, 2023
