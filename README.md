# Tweet Classifier
--------------------------

Below is a description of my Capstone Showcase Project as part of my requirements to graduate from Galvanize's Data Science Immersive program. The following work was done in a time period of 3 weeks. The specific python script has  been left out of this repository. 



## Introduction
--------------------------


Apposphere is a leads generation company interested in using Machine Learning to match potential leads with appropriate clients. For example, the following tweet would get classified as "graphic design" and thus get sent to clients that deal with graphic design. 

![traffic law](https://github.com/prakhar523/TweetClassifier/blob/master/images/appopshere_explanation_1.png?raw=true)

Currently, Apposphere uses simple key word searches to match tweets to different industries. My job was to build a machine learning algorithm that would learn to classify tweet into categories. 

## Apposphere
--------------------------
Click below to watch a short video on Apposphere. 


[![Apposphere](https://img.youtube.com/vi/DgDYZ0M6PcI/0.jpg)](https://www.youtube.com/watch?v=DgDYZ0M6PcI)


## The Project
--------------------------

I approached [Apposphere](https://apposphere.io/) hoping to work with their data for our Galvanize Capstone Project. I was given two potential projects to work on.

1.) Build a Machine Learning algorithm that classifies tweets into one of 36 industry categories<br>
2.) Build a Machine Learning algorithm that classifies a tweet into how promising it looks as a lead, on a scale from 0 to 4, with a 4 being a solid lead. 

This github repo is a summary of my findings working on the first task. My goal was to train a machine learning algorithm to pick up on the keywords used to classify tweets into different industries. My hope was that by doing this, my algorithm will also pick up on terms not specified in the initial classification steps done by Apposphere. My goal was to make a more robust sorting procedure for the company. After building the classifier, the next step was to build a REST API that could be queried with information from twitter's API and would give a predicted industry classification in response. 




## Technologies
--------------------------

  * [Python 2.7](https://www.python.org/download/releases/2.7/)
  * [Pandas](http://pandas.pydata.org/)
  * [Numpy](http://www.numpy.org/)
  * [scikit-learn](http://scikit-learn.org/stable/)
  * [flask](http://flask.pocoo.org/)
  * [amazon web services](https://aws.amazon.com/)
  * [MySQL](https://www.mysql.com/)
  

## Data
--------------------------
Data was collected by [Apposphere](https://apposphere.io/) using twitter's API and stored in their MySql database. There was a semi-automated classification process used to provide labels for over 1 million tweets and store the labels along with the tweets. I queried Apposphere's database to access my data. 

## Exploratory Data Analysis
--------------------------
1. There are 36 different industry classifications
2. 97,000 classified tweets 
3. There are class imbalances
    - some categories had as many as 10,000 tweets in them while others had as little as 30
     

## Model 
--------------------------
Before training my model I used sci-kit learn's Count Vectorizer to create a bag of words representation of my tweets. I also attempted to tf-idf transform my data but it resulted in a less accurate model. The first classifier I attempted to use was a Multinomial Naive Bayes classifier. This gave me an accuracy of 0.7803. I also tried using doc2vec without better results. I ended up using a Support Vector Machine with Stochastic Gradient Descent to train my model. I achieved a .9907 accuracy score when testing my algorithm on an out of sample test.



## REST API 
----------
The second portion of this project was to deploy a REST API so that Apposphere can easily request a label from the model a built. I used flask to build my API and AWS to deploy it. Below is an example request and response. The number '17' in the response dictionary represents a certain industry label. 

![Rest API](https://github.com/prakhar523/TweetClassifier/blob/master/images/restapi.png?raw=true)



## Results
----------------
My SVM using SGD learning acheived a great accuracy score for labeling an incoming tweet into its appropriate industry category. My next steps to make this better suited for industry use are to refine the category labels initially assigned to the training set.
