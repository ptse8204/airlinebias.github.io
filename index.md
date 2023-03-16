<img src="https://blog.asaptickets.com/wp-content/uploads/2018/09/Consolidated-airfares.png">

**After the pandemic, airfare prices skyrocketed in a level unseen before. You may question yourself, is there more than just supply and demand involve?** 

**Our project and our initial report provides a couple insights. Discover what role does bias and discrimination plays in your flight ticket with sections below.**


# Initial Report
[Click here!](http://ptse8204.github.io/flightpricebias/DSC180B_Report.pdf)


# Introduction
<details close>
    <summary> What is Price Discrimination?</summary>
Price discrimination is the practice of setting significantly different prices for different groups of people for the same or similar commodity. This is specifically known as third-degree price discrimination. As a result, this can often lead to optimized profits for the seller, with a subset of buyers left paying higher prices. In the airline industry, there are several features associated with distance and the airports themselves that can affect the fare price as well as external forces such as market concentration and competitors. In turn, the **local demographics** of airport metro areas are features we hypothesize may distinguish significant pricing discrimination between majority and minority populations in airfare prices when comparing similarly comparable flights. Our goal is to identify potential factors in the dataset that may be causing biases in model implementations, mitigating these biases and ultimately developing fairer machine learning models for fairer airfare pricing.
</details>

<details close>
<summary>How's Our Project Related to Finding Discriminatory Efforts?</summary>
This website showcase our investigation on how airline price discriminate on certain proctected groups/features, "protected groups" refer to groups of individuals who are considered to be historically disadvantaged or marginalized based on certain characteristics, such as race, gender, age, or ethnicity. These characteristics are often associated with systemic inequalities and discrimination in various aspects of society, including employment, education, healthcare, and criminal justice.



including but not limit to:
* Race
<img src="https://penntoday.upenn.edu/sites/default/files/2021-06/iStock-1202344480.jpg" width="400" height="400">
<br>
Race: In our case, it would be the proportion of White Vs. Non White population in the local airport metro area.

* Income
<img src="https://cdn.mos.cms.futurecdn.net/Xv3k77UcipignuVPtHsC43.jpg" width="400" height="400">
<br>
Income: In our case, it would be a categorical variable that determine the income of the local airport metro area (Low Vs. High). Low income is defined to be whether the median of the local income is less than or equal to the 25th quantile threshold found from a distribution of median incomes across all metro areas. And high income is defined to be whether the median of the local income is larger than or equal to the 75th quantile threshold found from a distribution of median incomes across all metro areas.
</details>

<details close>
    <summary> How are bias and discriminatation discovered and investigated?</summary>
Our bias analysis and mitigation will be conducted with support of the <a href="https://github.com/Trusted-AI/AIF360">AI Fairness 360 (AIF360)</a> toolkit. In turn, we aim to develop a model that balances both accuracies as well as fairness between our classes.

We understand that airfare pricing is a business decision that was driven by revenues. However, by investigating such factors, it may also drives airline's bottom line as the result could be useful for more attractive pricing for passengers.
</details>

# Methodology
![Current Progress made in the project](https://user-images.githubusercontent.com/88422737/225416617-1dcfe519-b07f-40b7-ab08-0986cf57910d.png)
*All Progress made in the project currently, shown in a flow chart*

<details close>
    <summary> Dataset used</summary>
    
**[Click here for the dataset page](https://ptse8204.github.io/flightpricebias/eda/#datasets-used)**

We mainly use airline ticket and pricing data from the **Airline Origin and Destination Survey (DB1B)**. We decide to use such a dataset instead of web-scraping because the data point in the dataset represents the final/actual fare that customers pay for. The DB1B database is maintained by the United States Department of Transportation Bureau of Transportation Statistics. The <a href="https://www.transtats.bts.gov/tables.asp?QO_VQ=EFI&QO_anzr=Nv4yv0r">DB1B datasets</a> has data from 1993 to the 2nd Quarter of 2022, however, due to the constrain of our environment capabilities, we are only using the data **from 2018 to the most recent available record** in our project. 

While the DB1B database does not include demographics such as race, age, or income, for our purposes, we are instead using <a href="https://www.census.gov/data.html">**U.S. Census data**</a> in order to get feature variables that describe the local populations of the origin airport metropolitan area and the destination airport metro area. By merging these two datasets, we are able to investigate the relationship between local population demographics and airline ticket prices.
</details>

<details close>
    <summary> Hypothesis</summary>
There is a significant difference between flight fares for privileged and unprivileged classes. (classes determined by race (white and non-white), and income (high and low) of the local airport metro area population).
</details>

<details close>
    <summary> Main investigative objectives </summary>
    
We aim our investigation (mainly) in 2 directions:
* Investigate whether there is a price discrepancy in protected groups on an existing dataset
* Feed the data onto our custom build models, and see whether the model would generate results that showcase strong bias: especially models that are extremely accurate, and have a hard time correctly identifying areas that have a strong influence on protected groups.

</details>
    
# Goals and Outcomes
<details close>
    <summary> Goals </summary>
    
* Identify potential bias, if any, through EDA and model development process.
* Using the <a href="https://github.com/Trusted-AI/AIF360">AIF360</a> toolkit, compare results for models with and without bias mitigation. Identify feature importance and improvement areas for future models
* Using various accuracy measurements and bias mitigation techniques, Create and evaluate a model that is both accurate and unbiased. 
* Since we are using airfare data from 2016 to 2022, we also want to discover if there is any trend shift in airfare pre-pandemic and post-pandemic. And whether such a trend shift correlates with any changes in model fairness.
    
</details>
    
<details close>
    <summary> Outcomes </summary>
    
**[Click here for the models page](https://ptse8204.github.io/flightpricebias/models)**
    
* An thorough understanding of current problems in flight ticket price setting applications.   
* An unbiased model for estimating the fair price that customers should pay. 
    * Price Sensitivity Model
* An indicator allows consumers to know whether they are price discriminated against and whether they are paying the fair price. 
    * High Fare Indicator Model

</details>
<details close>
<summary> Models Developed </summary>
    
**[Click here for the models page](https://ptse8204.github.io/flightpricebias/models)**
* High Fare Indicator Model
* Price Sensitivity Model
* FareClass Classifying Model
    
</details>

# Credits
## Team Members
* Edwin Tse
* Garrick Su
* Joseph Perez
* Maricela Vasquez
* Qixi Huang


## Mentors
We would also want to dedicate this section to thank you the continous support of our mentors:

* Deloitte: 
    * Rasmus Nielsen
    * Jeffry Liu
    * Nandita Rahman
    * Aritra Nath
    * Emma Harvey
    * Meira Gilbert
* UCSD: 
    * Prof. David Danks

# Github Repo
[Click here!](https://github.com/ptse8204/airlinedatabias)

## Notes
We will keep updating the website alongside with our progress.
Last update: March 15, 2023
