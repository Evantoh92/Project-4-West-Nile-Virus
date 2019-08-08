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

3 classifiers - logistic regression, random forests and support vector machines (SVM) were built and combined two best performing models with best parameters in the ensemble model. Months, Weeks, WetBlub, Species (top 4) played an important role in predicting WNV. Our ensemble classifier has an ROC AUC of 0.54 and a F1 score of 0.80.

Future possible developments:
- Research on weather variables further to use them more effectively
- Try gradient boosting to optimize model
- Ensemble more models 

# Data Description 

Data|Train|Test|Weather|Spray|
|---|---|---|---|---|
cases|10506| 116293| 2944 |14835 

## Train/Test Dataset

Train - Period covered: 2007,	  2009,	  2011	  and	  2013
Test  - Period covered: 2008,	  2010,	 2012	 and	 2014

Variables dropped - Address, Block, Street, AddressNumberAndStreet, AddressAccuracy. 

Variables created - Stations: closest weather station to Traps. How we did it: We adopt the method done by https://www.johndcook.com/blog/python_longitude_latitude/.

One of the key challenges we faced was that the dataset involved significantly imbalanced classes. Approximately 95% of the traps were negative, leading to high baseline accuracy score. We decided to deal with the imbalanced dataset using the oversampling method. 
We oversampled the positive data in our training data set, in order to give our models artificially balanced classes to train on.
The oversampling process consists of simply calculating how many additional positive samples one would need to balance the training classes, and then sampling the positive training data, with replacement, to generate those data.

## Weather Dataset

We imputed missing values using the following methods:
Tavg - using the average of Tmax and Tmin
WetBulb,Depart,Heat,Cool,AvgSpeed - using the responses from other stations
PrecipTotal - fill trace values as 0.005

## Spray Dataset

Period: 2011 and 2013

## Data Merging
We mereged the train/test dataset for ease and robust analysis. The unique identifer used: Data and Station

## Feature engineering:
1. Identified distinguishable characteristics of the virus based on external research by comparing very crudely the means of interesting columns of those with the virus vs those without the virus.
2. Plotted histograms to identify if the feature is important in distinguishing whether or not there is a virus.
3. Identified a range to select out the value of the feature that best describes whether it has a virus.
4. Those within range will be assigned value of 1 those out of the range will be assigned value of 0 to help the model better distinguish positive features. This is also because it is an imbalanced dataset.
5. Features that were selected included Month, WetBulb, DewPoint, Tavg, Cool, AvgSpeed, Daytime.
6. Converted certain columns into dummy variables. These included Trap, week of the year from the Year, Month, date data and Species data.
7. Species data was consolidated to reflect CULEX PIPIENS/RESTUANS.
8. Oversampling was used to balance the data when training the model.
