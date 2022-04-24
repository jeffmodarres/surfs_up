# Challenge 9: Surfs_up
## Overview
W. Avy likes oure previous analysis, but he wants more information about temperature trends before opening the surf shop. Specifically, he wants temperature data for the months of June and December in Oahu, in order to determine if the surf and ice cream shop business is sustainable year-round.
## Goal
Goal is to query temperature for the month of June and December for all the previous years and show the statistics. 
## Result
The requested data collected and summarized in Fig.1 and Fig2. Here are the differences:  

* There is more data for June compared to December
* Average temperature for June(74F) is slightly higher than December(71F)
* Minimum temprature for June(64F) is higher than December(56F) 
* Maximum temperature for June(85F) is slightly higher than December(83F)


![June_stats](/June_temp.png)  
**Fig1. June_stats**  
  
![Dec_stats](/Dec_temp.png)  
**Fig2. December_stats**  

## Summary
 Based on the two queries, the overall temperatuer is the same for June and December. The minimum temperature for December is a bit chilly.

 ### Query1: 
 This Query can be used to gather precipitation data for June.
 **session.query(Measurement.prcp).filter(extract("month", Measurement.date) == '06')**  

 This query can be used to query December data
 **session.query(Measurement.prcp).filter(extract("month", Measurement.date) == '12')**  

 The result shows that it rains more in December than June.

 ### Query2:  
 This query can be used to count the number of days that has rained in June.
 **session.query(func.count(Measurement.prcp)).\
                     filter(extract("month", Measurement.date) == '06').\
                     filter(Measurement.prcp>0)**
