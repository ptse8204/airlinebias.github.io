---
title: "Models without Mitigation"
permalink: /models/
layout: single
---

## Introduction to Initial Models

There are many ways to approach this problem in what we want each row to represent. While we are initially given tickets, we can expand each ticket to passengers and we can also group by flight path (unfortunately due to a lack of Flight ID in our dataset grouping by flights was not possible). 

Each grouping has thier own downsides: passengers would expand out tickets which would result in many duplicate rows, but from a fairness perspective, we care most about an individual and the other groupings include a variable amount of passengers to represent a row (so some passengers matter less than others). Tickets, on the other hand, represent multiple people, but has no duplicates and does not lose information. With flight path grouping, we need to summarize many flights together and while we lose a lot of information, we also get rid of many outliers which happens many times. 

What we ultimately decided was that across each type of grouping, the bias metrics should ideally all be relatively fair. 

## Passenger Level
When looking at the passenger-level, models gave 

## Ticket Level
When looking at the ticket-level, models gave

## Flight Path Level
When looking at the flight path-level, models gave
