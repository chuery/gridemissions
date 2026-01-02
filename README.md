# Carbon Neutrality Assessment of Microsoft’s Texas Data Center Strategy

**Research Question:** If Microsoft opens a data center in Texas and also signs a power purchase agreement (PPA) for the same amount of renewable energy generated in Texas, is this “carbon neutral”?

# Background
- Microsoft carbon negative by 2030 goal
-Renewable subsidies are expensive
- Additionality: do renewables actually displace fossil fuel generation?
- Texas has large renewable energy capacity
- Estimate marginal effects of load & renewable generation on carbon emissions with Texas electricity market data from 2021-2024


# What is Carbon Neutrality?
_Rubin Causal Model _
Treatment: data center & PPA purchase
Outcome: change in carbon emissions
Texas electricity market data (2021-2024)

Carbon neutral if 
data center usage = PPA generation
𝛽renewable = 𝛽emissions

# Data Description
TXGridData.csv: system-wide quantity demanded, wind and solar generation, and total CO2 emissions in Texas for each hour of 2021–2024
from ERCOT & the EPA Clean Air Markets Program
Key Variables
- load: system load (MWh)
- wind-gen: wind generation (MWh)
- solar-gen: solar generation (MWh)\
- co2: CO2 emissions (metric tons)
Correlations 
- Load and emissions 
- Load and solar generation
- Solar generation and year 
<img width="512" height="449" alt="image" src="https://github.com/user-attachments/assets/752ea5b4-2df0-4a20-9714-50237c1282ff" />

# Empirical Methodology
Basic model:
<img width="512" height="67" alt="image" src="https://github.com/user-attachments/assets/88ec7465-578e-4cec-a809-f5653daf946c" />

Load model:
<img width="418" height="44" alt="Screenshot 2026-01-01 at 9 08 01 PM" src="https://github.com/user-attachments/assets/c93f84e7-9bf1-46a0-ba8a-566d331bb457" />

Month-Hour + Load FE model:
<img width="476" height="45" alt="Screenshot 2026-01-01 at 9 08 12 PM" src="https://github.com/user-attachments/assets/7f00eade-7c0b-4ffe-afd0-e2d3710b49e9" />

Standard errors are HAC (Newey West) with 48 lags for serial correlation

# Fixed Effects

_Problem: omitted variable bias 
_
Solar generation is correlated with 
Time of day
Season
Confound solar effects with other patterns
Random effects alternative not applicable


_Fixed Effects Solution
_
Hour FE: control for systematic differences by hour of day 
Month FE: control for seasonal patterns
Month-hour FE: control for hour of day patterns that vary by season 
Month-hour-load FE

# Solar Hour Fixed Effect
Hourly variation (1695.55 MWh) is around 50% of average solar generation (3379.66 MWh)
Solar production curve peaks midday
Hourly trends that repeat across 100 days
Fluctuating energy generation with surpluses in some periods and shortages in others
<img width="918" height="790" alt="image" src="https://github.com/user-attachments/assets/4e58620d-5cdb-4aeb-a10f-7859b8513a22" />

# Results
Renewable Effects
𝛽solar = -0.531 metric tons CO2 per MWh solar 

𝛽wind = -0.523 metric tons CO2 per MWh wind 

Load Effects
𝛽load = 0.606 metric tons CO2 per MWh of additional load

Net Effect: Not Carbon Neutral 
0.6 - 0.5 = 0.1 metric tons CO2 per MWh for both wind and solar renewable energy

# Conclusion
PPA ≠ Zero-Carbon 
In the short-term, purchasing PPAs and adding a data center will still add net 0.1 metric tons CO2 per MWh. 
In the long-term, Microsoft data centers should be built with consideration of energy sourcing (nuclear, geothermal, etc.) and investing in grid infrastructure (transmission lines, distribution networks, etc.) 

Renewables + Batteries
Renewables are dependent on external factors such as weather and time-of-day. To maximize renewable energy, PPAs should be purchased alongside batteries (lithium-ion, sodium-ion, etc.) for energy storage during times of production deficiency. 

