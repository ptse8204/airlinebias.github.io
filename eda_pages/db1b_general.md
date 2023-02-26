---
title: "Airline Origin and Destination Survey (DB1B) Dataset General Statistics"
excerpt: ""
sitemap: true
layout: single
---

## General Statistics
### Dependent Variables
#### FarePerMile
The Fare Per Mile variable is a value that is calculated as the ratio of ticket fare of the total flown miles of a given ticket. 

![db1b_avg_fpm_yy_qq](https://user-images.githubusercontent.com/88422737/221441408-279b8f7b-7ed5-473a-9114-efd8617e2b8c.png)
*Fare Per Miles Per Quarter, [click here for the interactive graph](avgFPM.html)*

On average the variable is relatively stable, prior to the 2020 Q1, hovering between 26-27 cents in each quarter. There is a significant drop during the first 3 quarters of 2020 from the average of 25 cents to the lowest at 18 cents. The variable since then steadily rebound to 24 cents at the last quarter of 2021, and spike to the highest point in 2022 Q2 and Q3 of 28 cents. 

#### ItinFare (Ticket Fare)
The Ticket Fare variable is a value that represent the total dollar amount paid of a given ticket. 
![db1b_avg_itinfare_yy_qq](https://user-images.githubusercontent.com/88422737/221444507-de3a135f-9e64-4f57-a9bb-a4ef08ea2313.png)
*ItinFare Per Quarter, [click here for the interactive graph](avgItinFare.html)*

On average the variable is relatively stable, prior to the 2020 Q1, hovering between $400-$430 in each quarter. There is a significant drop during the first 3 quarters of 2020 from the average of $390 to the lowest at $270. The variable since then steadily rebound to $390  at the last quarter of 2021, and spike to the highest point in 2022 Q2 and Q3 of $470. 

It is important to note that this variable is highly influence by the rate of round-trip travel, as a round-trip ticket fare is count as the same as a one-way trip ticket in this variable. Our analysis found (also shown below), on average 60% of the tickets are classified as round-trip travels.
