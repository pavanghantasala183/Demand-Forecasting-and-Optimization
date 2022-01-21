# Demand-Forecasting-and-Optimization
1. Introduction
Building T is being supplied with water by two sources. One source is through contracts 
from Water Corporation (Main Water) and the other source is through internal 
precipitation mechanism (Cooling Water). We have water consumption data for 92 
weeks of Building T from the source which it came from in all the corresponding weeks. 
Water corporation sells water to building T through two types of contracts, one with 15 
cents per gallon with a minimum purchase of 25000 gallons per week and the other with 
12 cents per gallon with a minimum purchase of 35000 gallons per week.
For precipitation cooling, it costs the company 18 cents per gallon in the first two weeks 
and 10 cents per gallon through process improvements in the second two weeks. The 
precipitated water is stored in the water tank whose level must be maintained at least
30000 gallons. Currently the tank is at 62500 gallons level. Because of environmental 
reasons, Building T should be using 25% water through precipitation. 

We must forecast reliable estimates for the water demand for the 
next four weeks and use these estimates to find the optimal contract from the water 
corporation and how much precipitation water should be manufactured so that it 
reduces the total water cost for the company.

2. Forecasting
We have used the ARIMA model, Auto Regressive and Integrated Moving Average 
model, for forecasting. As can be seen from the below table, the probability value is 
greater than the significance level of 0.05, so the model we chose, the ARIMA model, is 
very suitable for prediction.
The white noise probability vs. lag plot below conveys the same message, the 
probability is greater than the significance level.
We have chosen the forecasting models 
which are reliable according to low white 
noise and consistent Auto Regression and 
Seasonal ARIMA models. We took the 
average ensemble of forecasts for three 
models addressing seasonality and trend 
components.
 
 Forecasts for the Cooling Water Forecasts for the Main Water from Water Corp
The total water demand forecasts combining both cooling and main water are as 
follows:
Week Forecasts
1 54172.24
2 54223.42
3 53514.76
4 53675.54

3. Optimization
From the forecast estimates from the model, we have the demand for water 
consumption in the next four weeks. We can use optimization and operations 
research techniques to find out the best contract alternative and respective 
amounts of water to be ordered from the water corporation and storage tank. 
We can formulate the problem as an optimization problem trying to reduce the 
total cost and use the corresponding LP/MILP/NLP problems to solve it.
Our variables in the model would be the amount of water ordered from each 
source in each week. 
Wij – amount of water ordered from ith source in jth week
 i -> {Water Corp., Storage Tank}
j -> { 1,2,3,4} (Next 4 weeks)
Let Rij be the rate of water per gallon sourced from ith source and jth week same 
as above. For the first two weeks Rprecip is 0.18 dollars per gallon and next two 
weeks it is 0.10 dollars as mentioned in the case. RWater Corp,j would be constant 
either 0.15 dollars if first contract is selected or 0.12 dollars if second contrat is 
selected.
We also need two more binary variables one for each contract (xa,xb), with their 
values suggesting whether that particular contract is selected or not. Only one of 
these variables should be having 1 and the other one should be 0 which can be 
implemented using a constraint. (xa + xb = 1) makes only one of the variable 1 and 
the other 0.
Given these values we have one more condition that water in the storage tank 
should always be greater than 30000. We were given the values of water 
precipitated each month, let that be WPj for the month j. For this we can define, 
the storage at the beginning of the month as 

Sj = Sj-1 + WPj-1 - Wprecip,j-1

Objective Function:

Minimize Total Cost = ∑{(𝑊𝑊𝑎𝑡𝑒𝑟 𝐶𝑜𝑟𝑝,𝑗 ∗ (𝑋𝑎 ∗ 𝑅𝑎 + 𝑋𝑏 ∗ 𝑅𝑏)) + (𝑊𝑝𝑟𝑒𝑐𝑖𝑝,𝑗 ∗ 𝑅𝑝𝑟𝑒𝑐𝑖𝑝,𝑗)}

Subject to the following constraints

Wi,j >= 0 for all i,j (non-negativity constraint)

Sj >= 30000 gallons for all j (Storage tank constraint) 

Wprecip,j > = 0.25 * (Wprecip,j + WWater Corp, j )

Wprecip,j + WWater Corp, j >= Forecasts

Xa + Xb = 1

Xa is binary

Xb is binary

WWater Corp, j >= (25000* Xa + 30000* Xb ) (Water Corp base Constraint)

From the formulation of the problem above we can see that it is a nonlinear
optimization problem as the objective function we are trying to solve has a 
multiplicative component between two variables. Using SAS optimization techniques, 
we have solved the problem and following are the results.
