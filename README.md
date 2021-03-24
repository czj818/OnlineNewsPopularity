# OnlineNewsPopularity

The key question is to classify popular and unpopular news and find out what factor affect the popularity the most.

## Introduction

The news popularity prediction model predicts whether the post will be popular or not and gives media industry and content-creators some idea about the factors that create most impact on the popularity.
 
Our dataset is called the Online News Popularity data, retrieved from UCI datasets repository. The data contains 39644 observations with 61 columns. Our features can be classified into 4 categories: we have features like number of words in the news, titles, number of keywords, the posting time, number of images and videos in the news, # of links and NLP features. 

feature summary 1            |  feature summary 2
:-------------------------:|:-------------------------:
![](https://github.com/czj818/OnlineNewsPopularity/blob/main/img/feature_sum.png)  |  ![](https://github.com/czj818/OnlineNewsPopularity/blob/main/img/feature_sum2.png)

## Data Preprocessing

To determine which news is popular we looked at the shares of each post and if the share is greater than the median of shares, it counts as popular. We found that from the box plot of shares, there is a lot of outliers, huge number of shares in the data.  After removing the outliers, we decide to standardize the data because some features have large numeric values, but some have very small numeric values.
![](https://github.com/czj818/OnlineNewsPopularity/blob/main/img/boxplot.png)

## Correlation Check

Next up, we checked the correlation between variables and found out that some of the variables are highly correlated and those features are representing similar meanings. For example, the first three are about word count in the news, these two are about the topic of the news, keywords, shares of reference article.

![](https://github.com/czj818/OnlineNewsPopularity/blob/main/img/corr.jpeg)
![](https://github.com/czj818/OnlineNewsPopularity/blob/main/ppt/Slide6.png)

## Exploratory Data Analysis

During the Exploratory data analysis, we found that popularity of the news might relates to posting on different days of a week. 
From the chart here, from Monday to Thursday, the number of popular news and unpopular news does not have a large difference. But from Friday to Sunday, number of popular news are way more than unpopular news. Posting on weekends has a bigger chance to become popular.

![](https://github.com/czj818/OnlineNewsPopularity/blob/main/img/day.pdf)

Then we want to investigate whether different data channels effect on the popularity. It seems that news from technology, social media and lifestyle channels are more likely to become popular. The largest number of popular new belongs to the technology channel.

![](https://github.com/czj818/OnlineNewsPopularity/blob/main/img/channel.pdf)

## Model

We have implemented different method to do classifications:
- logistic regression
- naïve bayes
- K-nearest neighbor (5-fold cross validation)
- Random forest
- XGBoost
- Convolution neural network
For K-nn, we used the 5-fold cross validation to select the hyperparameters, others we used grid search to find the best hyperparameter values. CNN we trained for 20 epoch, batch size 10 sigmoid activation because binary classification and RMSprop as the optimizer because it has the highest accuracy and it converge fast. 

## Result and Evaluation

![](https://github.com/czj818/OnlineNewsPopularity/blob/main/ppt/Slide10.png)
![](https://github.com/czj818/OnlineNewsPopularity/blob/main/ppt/Slide11.png)
![](https://github.com/czj818/OnlineNewsPopularity/blob/main/ppt/Slide12.png)
![](https://github.com/czj818/OnlineNewsPopularity/blob/main/ppt/Slide13.png)
![](https://github.com/czj818/OnlineNewsPopularity/blob/main/ppt/Slide14.png)

Here is the importance graph from the random forest.  From the mean decrease accuracy, we can see that posting day, data channel of the news, number of shares of reference article are important in predicting popularity.  Same thing happened to the XGBoost. Although each features might be different, we can found that data channel, posting day, reference shares, number of keywords have the impact on the popularity.

![](https://github.com/czj818/OnlineNewsPopularity/blob/main/ppt/Slide15.png)

Here are the accuracy rates, mean squared errors and AUC scores of different models. All AUC score are greater than 0.5 which means better than random guess and some are greater than 0.7 which can be considered as a good model. The XG boost has highest accuracy rate and highest AUC score, next highest is CNN.

## Feature Importance

From the importance of variable plot, the top five important variables are data channel is world, data channel is entertainment, reference article average shares, whether the posting time is the weekend and data channel is technology. As we can see that features like different types of data channel, posting day and number of shares of the reference article are the most important in predicting the popularity.

![](https://github.com/czj818/OnlineNewsPopularity/blob/main/img/XGBimportance.jpeg)
