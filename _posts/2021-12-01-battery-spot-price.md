# Sport price analysis in Norway in regard to energy arbitrage with batteries

[Hagal](www.hagal.com)


## Intro :wink:

price one pays energy to its energy provider : spot price, decided by the day-ahead market at NordPool.
As consumer, pay it to the energy prodvider. Norway: Tibber, Fjordkraft, Fortum, etc...
Hourly variations in this price : hours with cheaper prices and hours with higher prices

[![Minimum price per day](/images/2021-12-01-battery-spot-price/minimum_spot_price_day.png)](/images/2021-04-09-ev-charging/minimum_spot_price_day.png){:target="_blank"}
[![Maximum price per day](/images/2021-12-01-battery-spot-price/maximum_spot_price_day.png)](/images/2021-04-09-ev-charging/maximum_spot_price_day.png){:target="_blank"}
<figcaption>Figure 1. Hourly consumption (kWh/h) of a randomly selected member of the no-EV (top) and EV (bottom) group.</figcaption>
<br/>

Energy arbitrage : batteries can charge during hours with low prices and discharge during hours with high prices
Knowledge of spot price for the next day : prices published around 12:45 (Europe/Oslo timezone) every day for the next day. 

How feasible is this ?

Brief presentation of the cost of energy for an industrial customer : 
 - electricity cost
 - grid cost
    - fixed part: taxes, etc...
    - energy part: a fee per kWh used
    - power part: a fee related to your maximum kW (in the case of Norway, kWh/h)

