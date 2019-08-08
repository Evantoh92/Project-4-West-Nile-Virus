# Project-4-West-Nile-Virus

# Problem Statement
West Nile virus can cause a fatal neurological
disease in humans. It is mainly transmitted to
people through the bites of infected
mosquitoes.

Treatments often involve hospitalization,
intravenous fluids, respiratory support, and
prevention of secondary infections.

No vaccine is available for humans.

Studies estimated the economic impact of the
WNV disease outbreak in 2002 in Louisiana,
which resulted in 24 deaths. Total epidemic
costs were ≈$20.14 million for the 329 cases,
including $9.2 million for mosquito control and
public health agency costs.

As mosquito control is an expensive exercise,
the state would like our team to propose a
cost-effective plan for pesticide deployment.

# Executive Summary 
XXX classifiers were built and the best combinations of parameters from each model was included in the ensemble model. Trap locations, Months, Weeks, Cool, Heat, WetBulb and species played an important role in predicting WNV.
The best result xxx..xxx with an AUC of xxx.

# Data Description 

Data|Train|Test|Weather|Spray|
|---|---|---|---|---|
cases|10506| 116293| 2944 |14835 

## Train/Test Dataset

Train - Period covered: 2007,	  2009,	  2011	  and	  2013
Test  - Period covered: 2008,	  2010,	 2012	 and	 2014

Variables dropped - Address, Block, Street, AddressNumberAndStreet, AddressAccuracy. 

Variables created - Stations: closest weather station to Traps. How we did it: We adopt the method done by https://www.johndcook.com/blog/python_longitude_latitude/.

## Weather Dataset

We imputed missing values using the following methods:
Tavg - using the average of Tmax and Tmin
WetBulb,Depart,Heat,Cool,AvgSpeed - using the responses from other stations
PrecipTotal - fill trace values as 0.005

## Spray Dataset

Period: 2011 and 2013

## Data Merging
We mereged the train/test dataset for ease and robust analysis. The unique identifer used: Data and Station
