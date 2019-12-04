# Project 3

**Commodity Flow Survey Data Analysis**

**Dataset:** 2012 Commodity Flow Survey: The CFS data are used by policy makers and transportation planners in various federal, state, and local agencies for assessing the demand for transportation facilities and services, energy use, and safety risk and environmental concerns. The report is released every 5 years (2012 most recent completed survey), and includes 4.5 million individual shipments with 20 features each. More information on the dataset can be found here: https://www.bts.gov/cfs. 

**Contributors:**

Michael Eby
Melissa Munz

**Background:**

Flatiron Data Science Module 4
Feature Engineering and Regression Analysis for Machine Learning

**Study Aim:** 

To predict shipment value in USD given:

- NAICS type
- Origin state 
- Destination state
- Quarter
- Mode of transportation
- Distance routed in miles
- Shipment weight in USD

**Feature Engineering:** 

In-depth analysis provided in commodity_flow_survey_regression.ipynb in this repository.

1. NAICS Codes (North American Industry Classification System) were originally classified into 46 different codes. We filtered these into 8 subgroups: Mining, Manufacturing, Wholesale, Online shopping, Fuel, Storage, Publishing, Administration

2. Transportation Mode filtered from 20 types into 8 subgroups: Parcel, Pipeline, Air, Water, Truck, Rail, Truck and rail, Other/multiple

3. Significant variation between mean shipment values of the NAICS and transportation types as well as abnormally distributed data and varying scales for continuous independent variables meant that values needed to be normalized for the model. Min-max scaling failed to improve model performance. Instead, log transformation of the shipment value, shipment weight, and distance travelled yielded higher performance.

**Final Model:** 

Lasso and ridge regression were discarded in favor of an Ordinary Least Squares regression model. Other models such as ANOVA, polynomial regression, and interactions were also tried, but these failed to yield the results of OLS.

R2 = 0.694 
Train Mean Squared Error: 1.984468
Test Mean Squared Error: 1.990008

Coefficients for discrete and continuous independent variables can be found in the notebook.

**Primary Implications:**

- Storage related exports  have  higher total shipment value
- Commodities shipped by pipeline or by water have higher total shipment value

**Further Research:**

Further areas of study include time-series analysis to see how shipment value is affected by the variables over the years, especially as compared to 2017 data.
