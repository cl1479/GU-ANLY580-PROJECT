# GU-ANLY580-PROJECT

# Reddit Posts Classifying Project 

## Introduction & background

The ultimate goal of this project is to create an automatic classification model for text posts. With the emergence and quick adoption of smartphones, people are spending tremendous amounts of time interacting with each other online using social media. However the system is not so smart yet where people have to choose what category they want to post to. By adopting such system created by using multiple ensemble classification, neural networks or nlp models, users can decide where they want to post from the smart categories suggestion or even automatically send messages without even thinking what categories the messages belong to which could help people to post things faster, connect with other people more easily and make people more addicted to the platform.

The topic of this project is “The Reddit Self-Post Classification”. Reddit is a social news site with the slogan: A voice ahead of the news, a voice from the Internet. Users (also called redditors) can browse and submit links to content on the Internet or post their own original or relevant user-submitted text. Other users can vote on the links posted with high or low scores, and links with outstanding scores will be placed on the front page. In addition, users can comment on posted links and reply to other commenters, thus creating an online community. Reddit users can create their own section of the argument, both informal for those posting links and comments, and formal for those posting links and comments, like Reddit user submissions, and formal for associations. In this project, we will focus on self-posts, with a title and a body of markdown text written by users on Reddit.

Self-posts are divided into various “subreddits” based on the types of posts being submitted, for example “r/politics” or “r/MachineLearning”. However, subreddits are usually created by users themselves rather than the administrator of Reddit. Thus, sometimes redditors may not know which community (or subreddit) their self-posts belong to and they may need recommendation from the website. Therefore, the purpose of our project is to create a text classifier which groups users’ posts into different topics so that the website can provide recommendations for users based on the results from our text classifier. 

## Dataset

The dataset will be downloaded from Kaggle, which is called “The reddit self-post classification task’.  https://www.kaggle.com/ammar111/reddit-top-1000
The data consists of 1013M self-posts, posted from 1013 subreddits (1000 examples per class) from 2016/06/01 to 2018/06/01. For each post, there will be the subreddit, the title and content of the self-post. It is worth noting that the subreddits here are not the subreddits shown on the Reddit website. Instead, the author of the dataset builds a taxonomy of subreddits --- classifying each subreddit into categories, and subcategories since classifying into the original subreddits is often not feasible due to massive overlap between the topics of different subreddits. As the author of this dataset has already organized the last 20% of the data as a random, stratified sample of all the data, we will split out the first 80% of the data as a train set and the last 20% as a test set.



## Methologies

###### Naive Bayes

Naive Bayes methods are a set of supervised learning algorithms based on applying Bayes’ theorem with the “naive” assumption of conditional independence between every pair of features given the value of the class variable. Bayes’ theorem states the following relationship, given class variable y and dependent feature vector X1 through Xn: P(y|x1,....,xn) = P(y)P(x1,...,xn|y)/P(x1,...xn).

Using the naive conditional independence assumption that P(xi|y,x1,...xi-1,xi+1,....xn) = P(xi|y), for all i, this relationship is simplified to P(y|x1,...,xn) = P(y)Since P(x1,...,xn) is constant given the input, we can use the following classification rule:  P(y|x1,...,xn) P(y)= argmax(y)P(y)

###### Bert:
A pre-trained model based on wikipedia data and it captures the context and meaning of the word by utilizing the sentences around it using Transformer which is an encoder-decoder architecture using attention mechanism which means it trains on all nodes, forward and back.
######Countvectorizer:
a vector on the basis of the frequency (count) of each word that occurs in the entire text.

###### SVD:
Singular value decomposition (SVD) is a method of representing a matrix as a series of linear approximations that expose the underlying meaning-structure of the matrix. The goal of SVD is to find the optimal set of factors that best predict the outcome.

###### XGBoost:
A tree-based(decision tree) ensemble machine learning model scalable for tree boosting.

## Result Comparison

| Model name | F1-Score | Precision | Accuracy | Training Time |
| ---------- | -------- | --------- | -------- | ------------- |
| Naive Bayes | 53.47% | 55.06% | 58.56% | 13.78s |
| XGBoost + Bert | 40.64% | 38.28% | 43.58% | 54.55s |
| XGBoost + Countvectorizer | 70.50% | 70.65% | 72.02% | 7.61s |
| XGBoost +Countvectorizer + SVD | 46.75% | 45.63% | 48.58% | 5.84s |

This table clearly shows the four model evaluation criteria: F1-score, precision, accuracy and training time. For the first three criteria, the best performer is XGboost + countvectorizer. then there is NB which also performs well. XGB + SVD took the least amount of time in terms of training time spent. But the accuracy was very poor.

XGBoost + Countvectorizer has the best accuracy score. Although it ranks second in terms of training time, 7.61 seconds is pretty fast.



## Conclusion

XGBoost + Countvectorizer is the optimal model that we tested and compared. BOW (Countvectorizer) has the best performance in the whole project dealing with Text. The reason could be the single dimensionality of the data.

###### Possible Improvements

- Limitation of data

Our data contains only the first 1000 posts in 18 categories at a short time. Therefore, the data does not include all types and long time periods. If we want our classification model to be more comprehensive, we need to increase the size and dimensionality of the data.

- Classification Model Objectives

When we created the Naive Bayes model, we used the title of the post to perform the classification. The accuracy of the created model will be higher than that of selftext. hence, changing the target may result in a higher accuracy model.

