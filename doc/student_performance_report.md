
# DSCI522 Group 403 - Student Performance Report

## Motivation & Data Set

Our selected data set summarizes Portuguese high school student’s
academic performance in both Math and Portuguese. For this project we
are trying to answer the question: what are the top five features that
most strongly predict high school student’s performances in their
Portuguese language course? In developing social intiatives to improve
high school student performance, it could be immensely useful to
understand what attributes play a strong role in predicting student
performance. Without identifying these key factors, such intiatives
would likely be less effective and would fail to provide a high return
on the school board or government’s investment.

The data set was sourced from the UCI Machine Learning Repository
(Cortez 2014) which can be found
[here](https://archive.ics.uci.edu/ml/datasets/Student+Performance), and
the original research paper (Cortez and Silva 2008) can be found
[here.](http://www3.dsi.uminho.pt/pcortez/student.pdf) The data was
compiled from official school reports as well as questionaires provided
to students. Attributes include the student grades, demographic, social
and other school related features. Two datasets are provided regarding
the performance in two distinct subjects: Mathematics (`mat`) and
Portuguese language (`por`). For the purpose of this analysis, we have
decided to focus only on the Portuguese dataset to investigate which
student attributes are the strongest predictors of performance in that
subject.

Some key highlights regarding the data set’s attributes:

  - The feature of interest is `G3` which represents the final subject
    grade score at the end of the academic year. The score ranges from 0
    to 20.
  - Multi-categorical attributes such as family size (`famsize`),
    parent’s education (`Fedu`/`Medu`) or weekly study time
    (`studytime`)
  - Binary attributes such as home internet access (`internet`) or
    family educational support (`famsup`)
  - Count attributes such as number of days of absence (`absences`) or
    student’s age (`age`)

## Exploratory Data Analysis

Before building our model, we partitioned the data into a training and
test set (split 80%:20%) and performed exploratory data analysis to
investigate the distribution of our predictive features and explore
whether there are any highly correlated features we might want to ommit
from our analysis.

Figure 1 - Feature Correlations

As we can see from the correlation matrix, our target attribute `G3` has
a strong correlation with attributes `G2` and `G1`. This occurs because
`G3` is the grade issued at the end of the year, while `G1` and `G2`
correspond to the grades for the 1st and 2nd school terms of that year.
Though it will be more difficult to get accurate predictions without
these features, it makes sense to drop them in light of our research
question and motivations outlined above. We’re more interested in which
attributes, other than recent acadmemic performance, will be most
predictive of future academic performance.

Figure 2 - Feature Distribution Boxplots

Figure 3 - Feature Scatterplot for Absences

Looking at the feature distributions, we can see that some of the most
noteworthy features include student’s past number of course failures
(`failures`), parental education levels (`Medu`, `Fedu`), alcohol
consumption on weekdays and the weekeend (`Dalc`, `Walc`), and the
school they attended (`school`). Each of these appears to show a clear
trend with respect to G3, so we would expect to see some of these
features having strong predictive power in the machine learning models
we develop.

The student’s number of absences (`absences`) does not appear to show a
strong correlation with our target variable.

Figure 3 - Distribution of Response Variable, G3

Our response variable shows an approximately normal distribution, with a
mean/median of abc out of 20. There are outliers at the low end which
end up dragging down the mean value.

## Predictive Modelling

To answer the predictive question posed above, we built and compared
several predictive regression models. We constructed the following
models, optimizing each according to the specified hyperparameters.
Model performance was evaluated using RMSE.

Figure

We found that the RandomForest model performed best with a RMSE of xyz
(figure/table?).

#### TODO: Do we need to justify model choices more? simplified version of what tiffanys done below?

    Given that all measurements are continuous in nature, and the outcome we are trying to predict is one of two classes, one suitable and simple approach that we plan to first explore is using a k-nearest neighbours classification algorithm. 
    
    - With this algorithm, we will have to choose K, the number of nearest neighbours to use for prediction. 
    - We will choose K via cross-validation using ~ 30 folds because this Wisconsin Breast Cancer data set is not very large, having only 569 observations. We will use overall accuracy to choose K. 
    - A line plot of overall accuracy versus $K$ will be included as part of the final report for this project.

## Ranked Features & Conclusions

The top five ranked features from our Random Forest regression model
were as follows:

Ranked Features: ![alt tag](../img/ranked_features.png)

For the most part, the results are inline with our expectations
following EDA. One noteworthy observation is the importance of
`absences`. Although it was not evident from our EDA scattlerplot,
absences turned out to be a strong predictor.  
\#\#\#\# TODO: Update based on brayden’s new plot.

Given we have identified attributes that predict academic performance,
this information could be very useful when developing social programs or
intitatives intending to improve student’s academic performance.
Targetting these attributes should improve the effectiveness of the
programs and thereby provide better return on investment for those
initiatives.

## Reflections & Next Steps

#### TODO: Not using the right regression approach? Brayden notes

We dropped features `G1` and `G2` after our EDA with the intent of
removing features based on recent academic performance. `Failures`,
which ended up being our top predictor, is highly correlated with `G1`
and `G2` and could perhaps be removed in subsequent analysis attempting
to focus on non-academic predictive attributes.

For this analysis, we decided to focus on only one of two available
student performance data sets. We looked at student performance in
Portuguese, rather than Math. In the future it would be interesting to
explore whether the same model features are strong predictors across
both subjects, or whether different subjects are predicted better by
different features. We would be curious to see if students who perform
strongly in Math tend to have a low value for the ‘going out with
friends’ attribute.

# References

<div id="refs" class="references">

<div id="ref-CortezUCI">

Cortez, Paulo. 2014. “UCI Machine Learning Repository.” University of
California, Irvine, School of Information; Computer Sciences.
<http://archive.ics.uci.edu/ml>.

</div>

<div id="ref-Cortezetal">

Cortez, P., and A. Silva. 2008. “Using Data Mining to Predict Secondary
School Student Performance.” In *Proceedings of 5th Future Business
Technology Conference*, edited by A. Brito and J. Teixeira, 1905:5–12.
FUBUTEC. <https://doi.org/978-9077381-39-7>.

</div>

</div>