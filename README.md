# Crime-in-DC

### Introduction
It is known that crime rates are much higher in big cities than as opposed to small cities,
towns, or rural areas. With a population of over six hundred thousand, it is no surprise that crime is
pervasive in the District of Columbia. Washington D.C. is ranked as the 16th most dangerous place
in America (Taylor & Staff, 2018). It has a violent crime rate that is 141% higher than the national
average and a property crime rate that is 76% higher than the national average (2). While data on
crime is ever persistent thanks to the exponential growth of technology, data on crime and rankings
don’t necessarily tell the exact story. Major cities that have significant segregation, poverty, and
inequality usually have high rates of violence, but it is concentrated within specific areas of the city
(communities, blocks, neighborhoods, etc.); where these areas will vary on the rates of crime.
Washington, D.C. has a unique demographic, geography, and criminal justice system.
Additionally, recent gentrification efforts have begun to transform the demographics in distressed
neighborhoods, thus seeing a rise in population. With more people coming to live in the city it is
important for to understand the trends in crime, and what can be done to make the city safer. The
District of Columbia is separated by eight distinct regions (wards) where the boundaries are
defined and redistricted every ten years. With each ward being distinguished, it is possible to
analyze the data pertaining to each ward to look for data that could possibly tell the story of crime
for each area. With the domain of public safety in mind, the aim of this report is to see if analyzing
datasets on crime along with relevant possible predictor variables can be used with algorithms to
potentially explain the data. I provided 78 total variables that can be used in different by grouping
them together based on categories (types of crime, time of day for crime, population, race data,
households, income, education, etc.) ran a multitude of classifiers conducting various tests on their
results. With my analyses, I concluded that no explanations could be established as more research
is needed

### Data
#### Crimes reported in DC: 
The initial data used in this report is, of course, data from crimes
reported in the District of Columbia from years 2008-2021. The data had many variables
that were used or the analyses. The data could be separated by year. And they could most
importantly be distinguished by ward. The data also showed what type of offense was
committed, whether a weapon was used, and the time of day the crime occurred.
#### Business Establishments: 
It is very possible that crimes can vary by amount of business
establishments per ward. Because of this, I extracted the data set titled
“Certified_Bussiness_Enterprise”. With this, I extracted the columns for wards, and then
made a total amount of business establishment per ward column by aggregating the data by
the count of business establishments and grouping them by ward.
#### Demographic Data: 
The last dataset was the most complex. It was titled “Ward_from_2012”
which included demographic data for each ward in 2012. This data was the most up to date
census data for residents in DC, and they could be grouped by ward. Data included the total
population of each ward, area of each ward in square miles, population data by race,
household and household income data, and education level data. These variables were
useful as they can be possible predictor variables for predicting crime in a ward. I also
created the variable “Population Density” by dividing the population by the area in square
miles as I deemed that population density could be a potential predictor for crime.

### Methods
First off, I used python on jupyter notebook for all my analyses. I imported several libraries
including pandas, matplotlib, scipy, os, plotnine, numpy, seaborn, statsmodels, and sklearn. I first
made a function to load all the csv datasets for crimes, and for the census data. The data was
manipulated in different ways as python functions to select certain year ranges could be employed
to see if results were more accurate as opposed to looking at a ten-year span of crime data and
trying to generalize the findings based on the other data which doesn’t get updated every year.
With this, I conducted tests using machine learning techniques to look at crime data versus ward,
census data versus ward, and census data versus total number of crimes per ward. All variables
were aggregated by count and grouped by each ward. I ran Linear Regression, Decision Tree,
Random Forest, and K-means, K-nearest neighbor, Naive Bayes. I ran various tests with these
classifiers such as accuracy scores, confusion metrics, variance scores, MAE scores, MSE,
sensitivity and specificity, f1 scores, etc.

### Analysis
#### KNN: 
I first constructed a ward classifier to see if crime data for each year selected could
predict the ward. I wrote a function to take in the year ranges and within, the data would be
tested against different k values, random states, and whether to scale the data. The data then
displayed the accuracy score of the model on training data along with accuracy score on
actual crime data from other years. Results are shown in Table 1. Trying different inputs,
the KNN was successful in predicting the training data with high accuracy, however the
score steeply declined when the models would attempt to predict wards from actual
datasets.
#### Linear Regression: 
I then constructed a crime classifier to see which census variables
contribute to predicting them, and additionally constructed a ward classifier to see if wards
could be predicted by crime data using LR. For the crime classifier, I tried different random
states to obtain different MSE’s and see the coefficients between variables. Results are
shown in Tables 2-3. For the ward classifier, I scaled the data and trained it to construct a
classifier and predicted it on test data along with actual crime data. Again, the accuracy
scores were high on the test but dropped when predicting actual datasets. Results for this
classifier are shown in Table 4. I also conducted an Ordinary Least Squares Regression
Test on Total crime v. various census data. Results are shown in table 5.
#### Decision Trees & Random Forest: 
Using Random Forest and Decision Trees, I used
multiple years to get accuracy scores on training and real data for each ward. Additionally,
crim indicators were displayed. Accuracy on the train data was high but also declined when
tested on actual data. Indicators are shown in Table 7, and accuracy is displayed in figure 7.
Subsequentially, I provided MAE and Variance scores for the data as well as shown in
Table 8. The scores for actual data were way lower than the test scores.
#### Confusion Metrics: 
I then conducted confusion metrics on ward v. crime data using the
following classifiers: NB, KNN, LR, and RF. The scores were overfit as the training data
was nearly perfect each time it was ran, but slightly lower on actual data. Results are shown
in Table 9.
#### K-means: 
I first used the total crime v. census data in a standard scaler to normalize the
data. To find the optimal number of clusters, I tested the data against 8 clusters, getting the
amount of cluster errors for each. I then plotted them to visually find the optimal number of
clusters to use, using the elbow method. The results are shown in figure 1. The data begins
to fall off after the third cluster, so I decided to use 3 clusters for the model. I then ran the
k-means clustering analysis with three clusters to fit the data, find centroids, and label the
data. Ward 1, 4, and 6 were in their own cluster, Wards 5, 7, and 8 were in their own, and
Wards 2 and 3 were in their own clusters. The crime clusters are in Figure 2.

### Results
After conducting various tests, many proved to show promising potential as the test scores
came back with acceptable accuracy when predicting the training data. However, the results on
actual data always were lower than the scores on test data. Despite this, individual variables
showed that they were correlated with crime rates. For example, Age range 25-29, business
establishments, median household income, were positively correlated while the population of
African Americans were negatively correlated. Conducting an OLS Regression Test, no conclusive
evidence was found either.

### Conclusion
The purpose of this report was to explore if data on crime along with possible predictor
variables could be analyzed with data science techniques to potentially show explanations and
stories that could be used for predicting total crime. Initial steps taken showed that there are three
potential clusters for crime, based on wards. And that linear regression can potentially explain
population and crime. At this point and time, there is no conclusive evidence for these results, I
have offered 78 different variables on one dataset so future work should analyze the data in other
ways based on the three models I used in the function to get variance scores and mean absolute
errors. Also, different variables should be used separately for clustering. It is possible that other
machine learning algorithms can potentially explain higher variance and lower mean absolute error
scores so future work should also implement more models. It is possible that there can be other
predictors, so it is recommended to maybe even analyze other Ward data versus the crime for each
ward. Digging deeper into possible socio-economic and census causalities to explain crime trends
is complex and tricky. But, as mentioned, this is an initial step into this process. From the first
figure in the results, we can see that the multiple linear regression model has an r squared value of
0.99, provisionally indicating that this model explains 99.99% of the variance in our dependent
variable. As the exploratory variables increase by one, the dependent variable decreases by
2569.36, decreases by 0.346, increases by 2.019, increases by 1616.224, decreases by 0.207,
decreases by 456.316, and increases by 95.079 respectively. There are no significant p values. The
f statistic was significantly low at 0.0656. Consequentially, we fail to reject the null hypothesis that
the independent variables can predict the dependent variable. Consequentially, we fail to reject the
null hypothesis that the independent variables can predict the dependent variable when running a
multiple linear regression model. For every other multiple linear regression model, the outcome
was the same. It appears that the random forest and decision tree models were promising as they
would consistently predict the correct ward with at least 80% accuracy. However, it this would
only be on the training data and when put up to the test on actual real-world data, the accuracy was
much lower. All in all, no significant results were found and therefore we can't make any
conclusions. This may be due to the limitations of data out there. The only constantly updated data
available is the crime incident reports and and there are many factors that can be explored to
potentially find significant results. Regarding the basic demographic data, it was last updated in
2012 so it certainly would help if there was more recent data. Additionally, the analyses had many
shortcomings as only data from the span of ten years and total numbers were assessed. Essentially,
the data was generalized. Future research should go deeper into the analyses of crime trends per
ward by looking at distinct types of crime along with possibly analyzing the data on race
populations per ward (which is fortunately available on the ‘Ward From 2012’ dataset).
Additionally, playing around more with the years to see if there are ranges more accurate than
others should be considered, as well as maybe accounting for the static demographic data. These
steps could potentially explain the variation of crime between wards in DC. This research was a
step in the right direction. However, after analyzing all the data, I found no conclusive evidence
that any of the exploratory variables could predict the number of crime incidents reported per ward.

### References
1. https://opendata.dc.gov/
2. https://www.areavibes.com/washington-dc/crime/
3. Taylor, D. Staff, P. (2018). DC Is America's 16th Most Dangerous City: A review of 2017
crime data ranks the most dangerous big cities in America. See how D.C. fared. Patch.com
