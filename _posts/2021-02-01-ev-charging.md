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
<figcaption>Figure 1. Hourly consumption (*kWh/h*) of a randomly selected member of the no-EV (top) and EV (bottom) group.</figcaption>
<br/>
The usual yearly variation observed in Norwegian households is seen in both examples. Hour-to-hour variability due to daily changes in electricity consumption is also observed. In the next paragraph, we will first try to look at the level of electricty consumption between the groups.

Daily : min, average and max
Per household type

## Weekly patterns analysis
Explain how we generate the hourly-based weekly XXX
EV vs non EV
Per household type


## Appendix 
Correcting for yearly variation -- why it is not useful in this case
For one person
For all the EV owners
