# Subreddit Classification & NLP EDA

### Table of Contents
1) [Introduction & Problem Statement](#introduction-&-problem-statement)
2) [Data Collection & Cleaning](#data-collection-&-cleaning)
3) [EDA](#EDA)
4) [Modeling](#Modeling)
5) [Conclusion](#conclusion-&-recommendations)
### Introduction & Problem Statement 
I am a Data Scientist for the 2024 Presidential Campaign. My role is to collect and analyze data in order to identify what topics Democrats and Republicans are most concerned with and how these topics resonates within each group so that we can formulate a winning campaign strategy. Lastly we would like to build a model that can identify whether a voter is Democrat or Republican based on their posts.

Approach
1. Pull posts from the Republican and Democrat Subreddit API 
2. Clean & Prepare Data for Modeling utilizing Regex
3. Analyze Common Topics & Sentiment using Vader Sentiment & Count Vectorizer 
4. Build and Evaluate the accuracy across various Classification Models
---

### Data Collection & Cleaning
Democrat Subreddit- (Include Link to Subreddit)
Republican Subreddit- (Include Link to Subreddit)

In total I pulled approximately 10k submission from each Subreddit thread. I filtered out submissions that were removed from the thread so that I only include posts that are currently on each thread as many submissions are removed by moderators or users themselves. Once I filtered down on live posts I performed the following cleaning steps.

1. Lowercase the titles
2. Remove Duplicates
3. Remove URLs
4. Identify Word Count of Each Post & Remove Posts below the interquartile range because they had too few words to be used meaningfully.

### EDA
I identified the most common words in each subreddit, words frequently used by one group but not the other as well as sampling of posts with high sentiment scores to see what voters feel strongly about. The takeaway from this EDA is that there is significant overlap between what the two groups are focused on and the words that they use to discuss these topics. This overlap will make modeling quite challenging so I will need to deploy a series of techinques to improve accuracy.

Most Common Overlapping Topics:
Trump, Biden, Democrats, Republicans

Republican Specific Topics:
Hunter Biden, Disney, Elon Musk, Nancy Pelosi

Democrat Specific Topics:
Greg Abbott, Abortion, HealthCare

### Modeling
I built and tuned 5 models including LogisticRegression, RandomForestClassifier, AdaBoost, Gradient Boost, and a stacked combination of a select group of classification models employing Pipelines and GridSearch to optimize my hyperparamters for each model. The baseline accuracy for this dataset was 55% with the Republican subreddit being the majority class. All of the models suffered from overfitting, however random forest was the most optimal model with a test score of ~75%, sensitity of 79%, and specificity of 69% which was the highest in each category.


### Conclusion & Recommendations
(#Conclusion-&-Recommendations)
In conclusion I identified several overlapping and unique topics which can be used for building a strategic campaign where we appeal to both groups or one group individually. Although challenging we can build a model that classifies a user as Democrat or Republican based on social media posts on platforms such as Reddit. Our top model Random Forest Classifier has proven to accurately classify 75% of users and if we are more concerned about misclassifying our base party as the other political party we can use sensitivity (optimize false negatives) if our base is Republican or specificity(optimize false positives) if our base is Democrat.