# Sport price analysis in Norway in regard to energy arbitrage with batteries

Analysis done at [Hagal](www.hagal.com)


## Intro :wink:

price one pays energy to its energy provider : spot price, decided by the day-ahead market at NordPool.  
<a href="www.hagal.com"><img src="images/2021-12-01-battery-spot-price/spot_price.png" align="left" height="212" width="212" ></a>

As consumer, pay it to the energy provider. Norway: Tibber, Fjordkraft, Fortum, etc...  

Hourly variations in this price : hours with cheaper prices and hours with higher prices  
[![Minimum price per day](/images/2021-12-01-battery-spot-price/minimum_spot_price_day.png)](/images/2021-12-01-battery-spot-price/minimum_spot_price_day.png){:target="_blank"}
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

 - spot price (NOK/MWh) : 
    - $SP_{min,N}$: average of the N hours of minimum spot price
    - $SP_{max,1}$: average of the N hours of maximum spot price
    - $\Delta_N$: difference between $SP_{max,N}$ and $SPD_{min,N}$
 - battery : 
    - $C$: capacity (kWh)
    - $\nu_{charge}$ : fraction of energy (kWh) lost when charging
    - $\nu_{discharge}$ : fraction of energy (kWh) lost when discharging
 - building consumption (kWh/h) : 
    - Con_{min,N} : average industry consumption during the N hours of minimum price
    - Con_{max,N} : average industry consumption during the N hours of maximum price



3. Energy arbitrage

Cost of charging during the minimum N hours of the day
$$
Total_cost_{min,N} = Con_{min,N} + Charge_{min,N}
$$

Battery charging cost
$$
Charge_{N} = SP_{min,N} \times C \times (1+\nu_{charge})
$$

Cost of discharging during the maximum hour(s) of the day
$$
Total_cost_{max,N} = Con_{max,N} - Discharge_{max,N}
$$

Battery discharging savings
$$
Discharge_{N} = SP_{max,N} \times C \times (1-\nu_{discharge})
$$

Gain. We want gain to be > 0 : 
$$
Gain_N = Discharge_{N} - Charge_{N} > 0
$$ 


3. Calculation
$$
Gain = SP_{max,N} \times C \times (1-\nu_{discharge}) - SP_{min,N} \times C \times (1+\nu_{charge}) > 0 \\
Gain = C \times \left(SP_{max,N} \times (1-\nu_{discharge}) - SP_{min,N} \times (1+\nu_{charge})\right) > 0 \\
SP_{max,N} \times (1-\nu_{discharge}) > SP_{min,N} \times (1+\nu_{charge}) \\
SP_{max,N} > SP_{min,N} \times \frac{(1+\nu_{charge})}{(1-\nu_{discharge})} \\
\frac{SP_{max,N}}{SP_{min,N}} >  \frac{(1+\nu_{charge})}{(1-\nu_{discharge})} \\
$$ 
















$$ 
\Delta_N = SP_{max,N} - SP_{min,N} \\
SP_{max,N} = \Delta_N + SP_{min,N}
$$


$$
\Delta_N + SP_{min,N} > SP_{min,N} \times \frac{(1+\nu_{charge})}{(1-\nu_{discharge})} \\
\Delta_N + SP_{min,N} - SP_{min,N} \times \frac{(1+\nu_{charge})}{(1-\nu_{discharge})} > 0 \\
\Delta_N + SP_{min,N} \times \left(1 - \frac{(1+\nu_{charge})}{(1-\nu_{discharge})}\right) > 0 \\
$$ 




2. Energy arbitrage
 - Cost of charging during the minimum hour(s) of the day
$$
Total_cost_{1} = Con_{min,1} + Charg_{1}
$$

Battery charging cost
$$
Charg_{1} = SP_{min,1} \times E_{charge}
$$

Cost of discharging during the maximum hour(s) of the day
$$
cost_{dis} = Con_{max,1} - Dis_{1}
$$

Battery discharging savings
$$
Dis_{1} = SP_{max,1} \times E_{discharge} = SP_{max,1} \times E_{charge} \times C \times \nu
$$

Gain. We want gain to be > 0 : 
$$
Gain = Dis_{1} - Charg_{1} > 0
$$ 
Calculus
$$
Gain = SP_{max,1} \times E_{charge} \times C \times \nu - SP_{min,1} \times E_{charge} > 0 \\
Gain = E_{charge} \times \left(SP_{max,1} \times \nu - SP_{min,1} ) > 0 \\
SP_{max,1} \times \nu - SP_{min,1} > 0 \\
$$

