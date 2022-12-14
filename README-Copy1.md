# Group Project 4: Comparing 3 Models for Predicting Recidivism
**TABLE OF CONTENTS**
[Executive Summary](#executive-summary)
[Data Dictionary](#data-dictionaries)
[Data Acquisition & Cleaning](#data-acquisition-and-cleaning) 
[EDA](#exploratory-data-analysis)
[Modeling](#modeling)
[Results & Recommendations](#results-and-recommendations)


# Executive Summary**

**Problem Statement**: We are a team of policy researchers trying to determine if an algorithm can accurately predict whether an inmate will be reincarcerated. We will build and evaluate a series of different classification models to determine what features most predict whether someone will recidivate. 

**Approach & Goal**: Our approach will entail collecting, cleaning, feature engineering, building, tuning, and evaluating a variety of classification models. Models to be considered will include logistic regression, KNN, Decision Trees, Random Forest & Ensemble Models, Naive Bayes and  Neural Networks. Our aim goal is to optimize the accuracy of recidivism classifications. A successful model is one that substantially outperforms the baseline accuracy, ideally at or above 80% accuracy.

**Software Requirements**: Running the analysis in our notebooks will require Pandas, Scikit-Learn, and Tensorflow.


# Data Dictionaries

Due to the combined length of the data dictionaries for the 3 models, they are linked separately here:

- Data dictionary for [Model 1: New York](./data/NY/data_dictionary_NY.md)
- Data dictionary for [Model 2: Florida](./data/FL/data_dictionary_FL.md)
- Data dictionary for [Model 3: Georgia](./data/GA/data_dictionary_GA.md)

# Data Acquisition and Cleaning 
(Notebook is [here](./notebooks/01_data_acq_clean.ipynb))

We identified three datasets from three different states in the US with varying features to be used for modeling. Data was collected from various sources including government websites and Kaggle. Null values were imputed or dropped, please see acquisition and cleaning notebook for detailed steps and logic applied.

Datasets:
<br>Basic- New York - 188k Observations - 5 basic features including gender, age at release, and county of indictment.  
<br>Criminal History- Florida - 11k Observations - 25 Features relating to the type and frequency of criminal charges of each offender.
<br>Behavorial- Georgia - 25k Observations - 58 Features relating to various behavorial traits of the individual including gang affiliation, drug use, education level, etc.

# Exploratory Data Analysis 
(Notebook is [here](./notebooks/02_eda.ipynb))

The purpose of this notebook is to "play" with a few aspects of the data, helping us to hone in on the useful columns and identify any problematic data that might cause us problems when modeling. Following are summaries/examples of the explorations conducted:

**BASELINE ACCURACY**

<br>Basic Dataset: 58% 
<br>Criminal History Dataset: 61% 
<br>Behavorial Dataset: 60% 

**KEY FINDINGS** 

Percent Days Employed: We saw a strong negative correlation between recidivism and percent days employed. Those who did not work at all were 71% more likely to recidivate than those who worked all days 
![Employment Impact](./visualizations/employment.png)

Gang Affiliation & Prior Arrests: Those who are gang affiliated are twice as likely to recidivate as those who are not gang affiliated. Similary we saw a clear upward trend between number of prior arrests and recidivism rates whereby those with fewer priors had lower recidivism rates.
![Gang Affiliation](./visualizations/gangaffiliation.png)

Drug Use: There is a positive correlation between drug use and recidivism whereby those who tested positive for THC, Cocaine, and Meth saw higher rates of recidivism than those who did not test positive.
![Drug Use](./visualizations/druguse.png)
  

# Modeling 
(Notebook is [here](./notebooks/03_modeling.ipynb))

We built, tuned, and evaluated a variety of classification models across three different datasets from New York, Georgia, and Florida each having different sets of features. 

Basic Dataset- NY- Modeling with only age at release, gender, and county of indictment did not result in sufficient improvement from baseline. Our best performing model was a stacked ensemble of random forest and gradient boosting at level one and logistic regression at level two. From this model we only saw a 2% improvement in accuracy from 58% baseline to 60% test accuracy. 

Behavorial Dataset- Georgia - Modeling with behavorial data saw significant bump in accuracy. We ran 9 different classification models on the dataset with the best performing model being gradient boost which saw an 11% increase from baseline accuracy of 60% to 71% test accuracy.

Criminal History Dataset- Florida - Modeling with criminal history dataset resulted in the highest overall and average accuracy scores. We ran a series of classification models and ultimately a neural network was the most accurate seeing a 25% improvement from a baseline accuracy of 61% to test accuracy of 86%.

# Results and Recommendations
(Notebook is [here](./notebooks/04_results.ipynb))

In conclusion when given adequate data it is possible to accurately predict recidivism. Our best performing model was a neural network utilizing criminal history features and seeing a 25% improvement from the baseline accuracy to correctly classify 86% of recidivism. 

Policy Recommendations
<br>Increase Employment Opportunities
<br>Focus on Rehabilitation Services
<br>Target Gang Affiliations to Break Recidivism Cycle
<br>Increase Access to College and Educational Programs for the Incarcerated


**PRESENTATION**

See [here](./presentation/presentation.pdf) for a brief, fairly non-technical presentation summarizing the problem, modeling process and results.

**SOURCES**