# Retail Data Science Project

## Introduction

The purpose of this project was to develop my skills as a data scientist by working with a retail dataset provided by Kaggle.com. The dataset provides customer and sales data for a business operating in the retail furniture sector. 

[Dataset from Kaggle](https://www.kaggle.com/datasets/tanayatipre/store-sales-forecasting-dataset)

I approached the data with an open mind, allowing my exploratory data analysis to inform possible areas of focus. After stumbling down a few dead ends, I ultimately decided to fixate on the causes behind annual profit trends. 
I noticed that annual profits seems to wildly fluctuate year by year. This seemed particularly unusual because annual sales did not exhibit this pattern, instead increasing each subsequent year.


![Untitled](https://github.com/user-attachments/assets/138c1669-285e-4f92-9a8d-0eee103856be)

Such variability in profits, with 2015 and 2017 underperforming 2014 and 2016 by a factor of about 100%, would no doubt have severe implications for the furniture retailer. However, any underlying cause or causes were a mystery,
and so I decided to focus my efforts on investigating these patterns.

## Methodology

My programming language of choice was Python, particularly its pandas, numpy, matplotlib, and scikit-learn libraries. This choice was informed by both my prior familiarity with Python syntax and its prevelance in the data science field.
All my code is contained in one Jupyter Notebook.

[Jupyter Notebook Code](https://github.com/Matlabrodoodle/Retail-Data-Science-Project/blob/main/Retail%20Data%20Science%20Project.ipynb)

Throughout working on this project I leaned heavily on visualizations, particularly bar graphs and pie charts, to help investigate data trends. I explored a few hypotheses for what was causing the profit fluctuations:

1.  Variation in average annual discounts causes variation in annual profits.
2.  Variation in annual mean sales causes variation in annual profits.
3.  Variation in annual transaction/order totals causes variation in annual profits.
4.  Goods sold in lower-profit years have lower average unit prices.
5.  Regional trends cause variation in annual profits.

Additionally, after I had a more comprehensive understanding of the data, I trained a Random Forest model to see if I could get a model that could assist with predicting future profits. For the purposes of ML modeling I
removed profit outliers by cutting off values outside 3 standard deviations of the mean. I engineered lag and rolling profit features and encoded categorical features using OneHotEncoder. I trained the model on sale years 2014-2016
and reserved 2017 for model validation.

## Results and Conclusions

In development.
