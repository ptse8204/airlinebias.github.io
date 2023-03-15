---
title: "Models without Mitigation"
permalink: /models/
layout: single
---

## FarePerMile Models using Protected Group Race

There are many ways to approach predicting FarePerMile in what we want each row to represent. While we are initially given tickets, we can expand each ticket to passengers and we can also group by flight path (unfortunately due to a lack of Flight ID in our dataset grouping by flights was not possible). 

Each grouping has thier own downsides: passengers would expand out tickets which would result in many duplicate rows, but from a fairness perspective, we care most about an individual and the other groupings include a variable amount of passengers to represent a row (so some passengers matter less than others). Tickets, on the other hand, represent multiple people, but has no duplicates and does not lose information. With flight path grouping, we need to summarize many flights together and while we lose a lot of information, we also get rid of many outliers which happens many times. 

What we ultimately decided was that across each type of grouping, the bias metrics should ideally all be relatively fair. In order to measure how fair models are assigning outcomes, we decided to use disparate impact, which measures probability of favorable outcome for the unprivileged group divided by favorable outcome for the priviliged group. The ideal disparate impact is 1.0, where the favorable outcome is the same probability 

### Passenger Level
When looking at the passenger-level and breaking down passangers by distance they flew, the disparate impact for each distance group was consistently around 0.98, which is considered incredibly fair. 

### Ticket Level
When looking at the ticket-level, models gave a disparate impact of around 0.97, which is also considered fair.

### Flight Path Level
When looking at the flight path-level, models gave a disparate impact of 1.24, which actually means that the unpriviliged group actually has a higher chance of a favorable outcome. This can be due to many factors, like lower pricing due to having lower socioeconomic status to afford the pricing. However, since the disparate impact is more unbalanced, we decided to use this level to mitigate the bias so that we can see how the disparate impact changes with mitigation.

##FareClass Model
Another model utilized within model development was the FareClass Model. The FareClass is a random forest classifier that predicts if the given ticket is either a favorable or unfavorable FareClass.  The classification for the FareClass feature was determined through the distribution of the FarePerMile attribute for each of the FareClass. Observing the distributions, favorable classes had distributions that were centered either below or right at the average FarePerMile for all FarePerMiles values together. Other features incorporated into the model included RoundTrip, DollarCred, Passengers, ItinFare,BulkFare, Distance, MilesFlown, White alone proportion and Non-White alone proportion. The results from this model revealed the limited bias within the dataset.
