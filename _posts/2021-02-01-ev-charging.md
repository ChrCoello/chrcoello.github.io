# Charing electric vehicles from home -- An analysis of charging patterns in Norway in 2020

As part of [Elvia](https://www.elvia.no/)'s large [pilot study on power tariff](https://www.elvia.no/effekttariff), a survey was conducted to understand the pilot end user relationship with using and saving energy. Two questions of this survey targeted electric vehicles (EV), as we asked the end users if they owned an EV vehicle in 2020 and if they did, if their household was the main charging point for their car. This sparked interest in our pilot team to conduct a side analysis looking at the real consumption patterns of EV and non EV owners.

## Dataset
The dataset gathered for this analysis is as follows: 
 - the hourly consumption (active energy, *kWh/h*) for 2020 of **181** end users that own and charge their EV at home (EV group)
 - the hourly consumption for 2020 of **978** end users that don't own an EV (no-EV group)
 - the type of household these end users live in, with four categories possible: detached house (*enebolig*), apartment (*leilighet*), townhouse (*rekkehus*) and tomannsbolig (*semi-detached house*) 

We filtered the hourly consumption by keeping only households where we had 99% of all hourly points available for 2020 (8696 out of 8784 data points).

## Comparing EV and non EV-owners
The raw data for a randomly picked end user from the no-EV group (top) and a randomly picked end user from the EV group (bottom) can be observed in Figure 1.
<img src="/images/2021-02-01-ev-charging/example_no_ev_owner_00.png" width="800" class="center" alt="no EV group">
<img src="/images/2021-02-01-ev-charging/example_ev_owner_00.png" width="800" class="center" alt="EV group">
<figcaption>Figure 1. Hourly consumption (kWh/h) of a randomly selected member of the no-EV (top) and EV (bottom) group.</figcaption>
<br/>
The usual yearly variation observed in Norwegian households is seen in both examples. Hour-to-hour variability due to daily changes in electricity consumption is also observed. In the next paragraph, we look at the level of electricty consumption between the groups the two groups.

### Extracting min, average and max per day
In order to compare levels between groups, each hourly consumption was summarized into a daily consumption, leading to reduction of teh time series length from 8794 points to 366 points. Three series per end user were obtained (Figure 2) as the average per day (daily_avg), min per day (min_day) and max per day (max_day) were used to summarize the daily consumption.
<img src="/images/2021-02-01-ev-charging/example_no_ev_owner_00_max_min_avg_per_day.png" width="800" class="center" alt="no EV group">
<img src="/images/2021-02-01-ev-charging/example_ev_owner_00_max_min_avg_per_day.png" width="800" class="center" alt="EV group">
<figcaption>Figure 2. Average, minimum and maximum consumption per day (kWh/h) of a randomly selected member of the no-EV (top) and EV (bottom) group.</figcaption>
<br/>

When all the members of the group are tranformed, one can represent the mean maximum, mean minimum and mean average and the respective   confidence interval of each mean, represented here using the [standard error of the mean] (https://en.wikipedia.org/wiki/Standard_error).
<img src="/images/2021-02-01-ev-charging/all_no_ev_owner_max_min_avg_per_day.png" width="400" class="center" alt="no EV group">
<img src="/images/2021-02-01-ev-charging/all_ev_owner_max_min_avg_per_day.png" width="400" class="center" alt="EV group">
<figcaption>Figure 3. Mean average, mean minimum and mean maximum consumption per day (kWh/h) of the no-EV (top) and EV (bottom) group.</figcaption>
<br/>

We clearly see that both the mean daily average and even more the mean daily maximum are higher in the EV group. We believe that two main factors explain these differences : 
 - larger households in the sample of the EV owners 
 - the charging of EV 
In the next paragraph, we will show more in details which effect  these two factors have.


## Weekly patterns analysis
In this paragraph, we will look at the **ho**urly-**b**ased **w**eekly **a**verage (HOBWA) patterns. This representation of the data allows to an easy analysis of weekly patterns.

### Generating HOBWA curves
The HOBWA curves are generated as follows. For each end user: 
 1. Start the hourly consumption for the whole dataset
 2. For each timestamp, generate a variable containing the hour of the week. The Hourof the week is between 0 and 167.
 ```python
 df['hour_of_week'] = df['date'].dt.dayofweek * 24 + (df['date'].dt.hour)
```
 3. For each hour of the week, measure the average consumption
At the end, you have a reduced the dimensionality from 8794 points to 168 points. 

Then, for each group (EV and no-EV group), the group mean is calculated:
\\[ HOBWA_{EV} = \frac{1}{N_{EV}}\sum_{i=1}^{N_{EV}}{HOBWA_i} \\] 


### EV vs. no-EV
<img src="/images/2021-02-01-ev-charging/weekly_averages.png" width="800" class="center" alt="not centered">
<img src="/images/2021-02-01-ev-charging/weekly_averages_centered.png" width="800" class="center" alt="centered">
<figcaption>Figure 4. The weekly patterns not centered (top) and centered (bottom) for both groups.</figcaption>

Per household type


## Appendix 
Correcting for yearly variation -- why it is not useful in this case
For one person
For all the EV owners
