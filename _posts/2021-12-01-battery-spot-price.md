# Sport price analysis in Norway in regard to energy arbitrage using batteries

This technical analysis done at [Hagal](www.hagal.com) presents some data-driven reflections on the feasibility of energy arbitrage using batteries. 

## Intro

There has been a tremendous amount of discussions about the high energy prices these last months, driven by historically high energy prices in the Nordic countries. Norway has recently seen its highest daily average price with €156/MWh in average for the Friday 26th of November. This energy price, or spot price, are decided in the day-ahead market (at NordPool in Norway) and sets the price of energy per hour. End users, both private and businesses, sign a contract with an energy market provider (Tibber, Fjordkraft, Fortum) that sell them energy at the spot price.

[![Spot price](/images/2021-12-01-battery-spot-price/spot_price.png)](/images/2021-12-01-battery-spot-price/spot_price.png){:target="_blank" :width=200px}
<figcaption>Figure 1. Spot price for NO1 (Oslo region) from Jan 2013 to Nov 2021</figcaption>
<br/>

The spot price, as shown in Figure 1 for the Oslo region (NO1), varies from hour to hour. A quick summary statistics (Figure 2) where we look at the maximum and minimum prices for each day in the analysed period shows the following pattern:
 - the most common hours in a day with the minimum price are during the night (hours starting at 2, 3 and 4) 
 - the most common hours in a day with the maximum price are during the morning (hours 9, 10, 11) and afternoon (hour 17)

[![Minimum price per day](/images/2021-12-01-battery-spot-price/minimum_maximum_spot_price_day.png)](/images/2021-12-01-battery-spot-price/minimum_maximum_spot_price_day.png){:target="_blank"}
<figcaption>Figure 2. Minimum (green) and maximum (violet) for each day represented as a function of time (left) or as a histogram (right) representing how often a certain hour of the day was either minimum or maximum (total number of days in this analysis: 2479)</figcaption>
<br/>

At Hagal, the discussion about using batteries to take taking advantage of this difference in price is recurrent. This use-case, called *energy arbitrage*, is simple to understand. During the cheaper hours of a day, a battery is charged at the cheaper prices. During the more expensive hours of the day, the battery is used as an energy provider, thus requiring to draw *less* energy from grid at these hours.
As the spot price for the next day is published around 12:45 (Europe/Oslo timezone) every day for the next day, then a simple algorithm could implement this use-case. 

But how profitable is this ? This is what we try to start digging into in this analysis.

## Energy cost and grid cost

Before we dive into the analysis, it is important to remember your energy bill is made of to two parts : 
 - electricity cost : what you pay for the energy delivered at your industry
 - grid cost : what you pay to the distribution system operator (DSO, Elvia in Oslo for example) for getting energy 24/7 delivered at your industry
In addition, the grid costs are made of three parts:
 1. fixed part: taxes, etc...
 2. energy part: a fee per energy used (often in øre/kWh) 
 3. power part: a fee related to your maximum kW in a given period (in the case of Norway, NOK/kWh/h)
There has been some spotlights on the third part (power part) lately as the power part is being implemented for all end users from 1st Jan 2022. How the power part is calculated is dependant on the DSO delivering electricity in your region. As an example, Elvia's power tariffs for industries looks at the maximum hourly energy (kWh/h) in a given month and uses this value to derive the cost. What this means is that one hour of very consumption can change drastically your electricity bill.

This said, this analysis of energy arbitrage (EA) is focusing solely on electricity cost. Nevertheless, we will see during the analysis that power tariff are important to have in mind. 


## Variables

Let's pose the problem we are trying to solve in words, and then let's define the variables needed to solve this problem.
Our objective is the following : given historical spot prices in a certain region (here NO1) and given a battery pack, would the implementation of energy arbitrage be profitable during these past days and can we spot a trend in the evolution of this profitability ?

To answer this question, let's define some variables:
 - spot price : 
    - $SP_{min,N}$: average of the $N$ hours of minimum spot price (NOK/MWh)
    - $SP_{max,1}$: average of the $N$ hours of maximum spot price (NOK/MWh)
 - battery : 
    - $C$: capacity available for energy arbitrage in the battery (kWh)
    - $\lambda_{charge}$ : fraction of additional energy required to charge the battery with $C$ (theoretically $\lambda_{charge}$ could be any positive number, in reality it is often between 0.05 and 0.3)
    - $\lambda_{discharge}$ : fraction of energy lost when discharging $C$ (between 0 and 1, often between 0.05 and 0.3)
 - $N$ : the number of hours required to charge the battery of $C$ without increasing the power tariff


## Energy arbitrage in equations

The cost of charging the battery of $C$ during the minimum $N$ hour(s) of the day:
$$
Charge_{N} = SP_{min,N} \times C \times (1+\lambda_{charge})
$$

The savings of discharging the battery of $C$ during the maximum $N$ hour(s) of the day:
$$
Discharge_{N} = SP_{max,N} \times C \times (1-\lambda_{discharge})
$$

Therefore the total savings/costs (NOK) of operating the battery is: 
$$
\Delta_{cost,N} = SP_{max,N} \times C \times (1-\lambda_{discharge}) - SP_{min,N} \times C \times (1+\lambda_{charge})
$$
It is also interesting to have an expression independent of $C$ (NOK/MWh):
$$
\frac{\Delta_{cost}}{C} = \left(SP_{max,N} \times (1-\lambda_{discharge}) - SP_{min,N} \times (1+\lambda_{charge})\right) 
$$

Then we have a simple metric ($\Delta_{cost,N}$ or \frac{\Delta_{cost}}{C}) to follow : 
   - if the metric is positive, then energy arbitrage is profitable
   - the pattern of this metric informs on potential trends

## Results

The two main results are presented below in different forms. Given a charge and discharge loss fraction and a number of hours for charge of the battery (parameters $\lambda_{charge}$, $\lambda_{discharge}$ and $N$ ), the total percentage of days when the energy arbitrage is profitable is presented as an image with parameter $N$ in vertical and parameter $\lambda$ in horizontal


The choice of N is dependant on the 
The parameters $\lambda_{charge}$ and $\lambda_{discharge}$ are battery depedant, with conventional batteries + inverter being around 20 to 30% whereas Hagal unique technology is speced to be much lower than that.
## Conclusion

Revenue stacking



## 8.Appendix
- building consumption (kWh/h) : 
    - $Con_{min,N} : average industry consumption during the $N$ hours of minimum price
    - $Con_{max,N}$ : average industry consumption during the $N$ hours of maximum price