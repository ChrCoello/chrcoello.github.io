# Sport price analysis in Norway in regard to energy arbitrage with batteries

Analysis done at [Hagal](www.hagal.com)


## Intro :wink:

price one pays energy to its energy provider : spot price, decided by the day-ahead market at NordPool.  

As consumer, pay it to the energy provider. Norway: Tibber, Fjordkraft, Fortum, etc...  

Hourly variations in this price : hours with cheaper prices and hours with higher prices  
<img src="/images/2021-12-01-battery-spot-price/minimum_spot_price_day.png" alt="drawing" width="200" target="_blank"/>
[![Maximum price per day](/images/2021-12-01-battery-spot-price/maximum_spot_price_day.png)](/images/2021-12-01-battery-spot-price/maximum_spot_price_day.png){:target="_blank"}
<figcaption>Figure 1. Hourly consumption (kWh/h) of a randomly selected member of the no-EV (top) and EV (bottom) group.</figcaption>
<br/>

Energy arbitrage : batteries can charge during hours with low prices and discharge during hours with high prices
Knowledge of spot price for the next day : prices published around 12:45 (Europe/Oslo timezone) every day for the next day. 

How feasible is this ?

1. Etat des lieux

Brief presentation of the cost of energy for an industrial customer : 
 - electricity cost
 - grid cost
    - fixed part: taxes, etc...
    - energy part: a fee per kWh used
    - power part: a fee related to your maximum kW (in the case of Norway, kWh/h)

Only focus on electricity cost here, but with power tariff in mind when doing the calculation

Standard energy consumption of an industrial partner: (include a typical week here)

2. Variables

 - spot price : 
    - $D_{min,1}$: daily minimum
    - $D_{max,1}$: daily maximum
    - $\Delta_1$: difference between $D_{max,1}$ and $D_{min,1}$
    - $D_{min,3}$: average of the three minimum prices of the day
    - $D_{max,3}$: average of the three maximum prices of the day
    - $\Delta_3$: difference between $D_{max,3}$ and $D_{min,3}$
 - battery : 
    - $C$: capacity
    - $\nu$: efficiency

2. Energy arbitrage
