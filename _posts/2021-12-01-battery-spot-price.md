# Sport price analysis in Norway in regard to energy arbitrage with batteries

Analysis done at [Hagal](www.hagal.com)


## Intro :wink:

price one pays energy to its energy provider : spot price, decided by the day-ahead market at NordPool.  

As consumer, pay it to the energy provider. Norway: Tibber, Fjordkraft, Fortum, etc...  

Hourly variations in this price : hours with cheaper prices and hours with higher prices  
[![Minimum price per day](/images/2021-12-01-battery-spot-price/minimum_spot_price_day.png) {width:200px}](/images/2021-12-01-battery-spot-price/minimum_spot_price_day.png){:target="_blank"}
[![Maximum price per day](/images/2021-12-01-battery-spot-price/maximum_spot_price_day.png)](/images/2021-12-01-battery-spot-price/maximum_spot_price_day.png)
<figcaption>Figure 1. TODO</figcaption>
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
    - $SP_{min,1}$: daily minimum spot price
    - $SP_{max,1}$: daily maximum spot price
    - $\Delta_1$: difference between $SP_{max,1}$ and $SPD_{min,1}$
    - $SP_{min,3}$: average of the three minimum prices of the day
    - $SP_{max,3}$: average of the three maximum prices of the day
    - $\Delta_3$: difference between $SP_{max,3}$ and $SP_{min,3}$
 - battery : 
    - $C$: capacity
    - $\nu$: efficiency
 - building consumption : 
    - Con_{min,1} : industry consumption during the hour of minimum price
    - Con_{max,1} : industry consumption during the hour of maximum price
    - Con_{min,3} : average industry consumption during the three hours of minimum price
    - Con_{max,3} : average industry consumption during the three hours of minimum price

2. Energy arbitrage
 - Cost of charging during the minimum hour(s) of the day
$$
Total_cost_{1} = Con_{min,1} + Charg_{1}
$$
Battery charging cost
$$
Charg_{1} = SP_{min,1} \times C \times (1+\nu)
$$
 - Cost of discharging during the maximum hour(s) of the day
$$
cost_{dis} = Con_{max,1} - Dis_{1}
$$
Battery discharging savings
$$
Dis_{1} = SP_{max,1} \times C \times (1-\nu)
$$
 - Gain. We want gain to be > 0 : 
$$
Gain = Dis_{1} - Charg_{1} > 0
$$ 
$$
Gain = SP_{max,1} \times C \times (1-\nu) - SP_{min,1} \times C \times (1+\nu) > 0
$$ 