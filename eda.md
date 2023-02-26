# Introduction

What are the thoughts when you are purchasing an flight ticket? Did you felt that you should be purchased it a bit earlier, or maybe a bit later so that prices would change? Though a lot of people knows that purchasing the fare at the last moment usually yield the highest price, it turns out that for average people, they purchase quite literally a very similar fare across the board. As our reaesrach shows, over 70% of all fares has a fare per mile of 20-30 cents.

We also found that most people are purchasing the median fare, rather than the highest fare or the lowest fare, as expected. These findings here helps aid our reasearch and model building the discover the bias related in the other sections.

# Datasets

Our project used the following datasets:

* [Airline Origin and Destination Survey (DB1B) by the _Bureau of Transportation Statistics](https://www.transtats.bts.gov/Tables.asp?QO_VQ=EFI&QO_anzr=Nv4yv0r%FDb4vtv0%FDn0q%FDQr56v0n6v10%FDf748rB%FD%FLQOEO%FM&QO_fu146_anzr=b4vtv0%FDn0q%FDQr56v0n6v10%FDf748rB)

  The Airline Origin and Destination Survey (DB1B) is a 10% sample of airline tickets from reporting carriers collected by the Office of Airline Information of the Bureau of Transportation Statistics. Data includes origin, destination and other itinerary details of passengers transported. This database is used to determine air traffic patterns, air carrier market shares and passenger flows.
  
  We use this dataset for the main charcteristics of a given flight ticket
* [Air Carrier Statistics (Form 41 Traffic)- All Carriers (T-100) (US only segment) by the _Bureau of Transportation Statistics_](https://www.transtats.bts.gov/Tables.asp?QO_VQ=EEE&QO_anzr=Nv4%FDPn44vr4%FDf6n6v56vp5%FD%FLS14z%FDHE%FDg4nssvp%FM-%FDNyy%FDPn44vr45&QO_fu146_anzr=Nv4%FDPn44vr45)

  The Air Carrier Statistics database, also known as the T-100 data bank, contains domestic and international airline market and segment data. Certificated U.S. air carriers report monthly air carrier traffic information using Form T-100. The data is collected by the Office of Airline Information, Bureau of Transportation Statistics.
  
  We use this dataset for getting a orgin and destination pair statistics, for example: flight counts, passengers count, seat counts and seat ratios.

* [Median Household Income and Demographics per Metropolitian Area by the _US Census Bureau_](https://www.census.gov/)

  We are using the median household income and demographics of a metropolitain area to determine which airports are in the protected groups.
