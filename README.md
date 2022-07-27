# Welcome to Aaron Sullivan PhD's Github portfolio page
Here I am showcasing some of my data science projects for you to become familiar with my work.



## Project 1: [COVID Bubble Estimator](https://github.com/asullivan42/COVID_Bubble_Estimator)

In this project I attempted to answer some basic questions about the relative safity of each state and county in the USA with regards to COVID infections and death.

**Scope:** This project included data from Datahub.io COVID tracking database, the CDC, John's Hopkins COVID tracking projects, wikipedia and the US census to accumulate population and COVID data per county in the USA.

### A county by county look at Covid Cases
The size of the dots are relative to the population sizes in the counties, color relates to number of deaths

![US Map](https://github.com/asullivan42/COVID_Bubble_Estimator/blob/master/figures/County_Cases_deaths.png)

Interestingly California which has the largest population in the USA at over 39.1 million residents has a moderate mortality rate where Texas, Forida and New York the next three largest population centers are doing much more poorly.  Even more interesting is the fact that some of the smallest counties are struggling the most. 

### Regression analysis of predictive features

I was able with the current data construct a KNN Regression algorithm which had ~88% accuracy in predicting the number of deaths given the current factors in my dataset.

![KNN Regression](https://github.com/asullivan42/COVID_Bubble_Estimator/blob/master/figures/knn_regression_by_county.png)

I am sure this can be further be improved by updating the dataset with even more factors.  Suggestions I have come up with include population demographics, hospital capacity, average distance to the nearest hospital, and weather.  I'm sure there are many more important factors that should be considered.

### Conclusions

COVID continues to be a difficult virus to predict safety with, however some states and counties appear to be doing fairly well within the united states.  These states include the northwest and northeeast as well as Utah.  It is of course not a complete picture, but it is an informative look at how COVID is affecting the United States.

## Project 2: [Aims Iowa House price predction](https://github.com/asullivan42/CapstoneTwo)

This is my first capstone, participation in the Kaggle challenge to predict home prices in Ames Iowa 2006-2010.


![Housing image](https://storage.googleapis.com/kaggle-competitions/kaggle/5407/media/housesbanner.png)

### Overview

Finding the right home is difficult enough but trying to predict how much a home will go for is even trickier.  This challenge gives a number of features of houses sold in Ames Iowa 2006-2010 and allows us to compete in predicting how much a home may go for depending on it's home features like neighborhood, # cars that fit in the garage, lot and home size etc...

> * [Kaggle Dataset](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data)
> * [Ames Iowa](https://www.google.com/maps/vt/data=im9DfE6g0vL8wC3dDOHSu5eH2ShEMWlPs4BSR8_Yrn9hYIDcmhKkYgs4oXNgSKzIDmbHon4mOyaGIvfaaS5jZ_IqnkkL7dcbMiHlTIOr6nd5AGVlEqJ-IYYemN-hZp-_qfOv0XaF42chHaqhltKMLiVuSBP8XDfqug5T5I4Dnrb3Mt381udqkHi-05obPXOTFQoslPVfqLiUWhAFyXY8YtHHBgAAM5lVnoQ27T19bqmPyDJuX-Oh)
> * [Ames Population Report](https://www.census.gov/quickfacts/amescityiowa)

### Algorithms & Machine Learning

I chose to try regression models because my output was a continous variable (Sales Price).  First thing I tried was to do some principal component analysis.  Unfortunately the analysis could only at best capture 44% of the variability and that took over 20 principal components.

Next I tested out a number of machine learning algorithms.
The algorithms I testes were:
* Linear Regression 	       88.48%
* KNN Regression	           74.37%
* <font color='green'> Random Forest	               97.96%</font>
* Gradient Boost Regression	   83.90%
* CatBoost Regression	       93.00%

>***NOTE:** There were a number of columns which had a large number of NaN values.  I dropped all the columns with more than 600 NaN values.*
**WINNER: Random Forest Regressor**

I did attempt to do some optomization of the algorithm with the Bayseian method of hyperperameter tuning, but kept getting a pandas error within the optomization code which couldn't deal with some boolians generated wihtin.  CatBoosting on the otherhand did show some improvement over the other methods, but not better than the initial Random Forest regressor.  It did allow me to determint the top features which contributed to the price.

<img src="https://github.com/asullivan42/CapstoneTwo/blob/main/figures/Category_Importance2.png">
