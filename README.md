# Retail Data Science Analysis

## Introduction

The purpose of this project was to develop my skills as a data scientist by working with a retail dataset provided by Kaggle.com. The dataset provides customer and sales data for a business operating in the retail furniture sector. 

[Dataset from Kaggle](https://www.kaggle.com/datasets/tanayatipre/store-sales-forecasting-dataset)

I approached the data with an open mind, allowing my exploratory data analysis to inform possible areas of focus. I ultimately decided to focus on gaining a better understanding of profit trends. 
I noticed that annual profits seem to fluctuate year by year without any obvious cause (annual sales did not exhibit this pattern).


![Untitled](https://github.com/user-attachments/assets/138c1669-285e-4f92-9a8d-0eee103856be)

Such variability in profits, with 2015 and 2017 vastly underperforming 2014 and 2016, would have severe implications for the furniture retailer. However, the underlying cause or causes were a mystery, so I decided to focus my efforts on investigating these patterns.

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

Lastly, after I had a more comprehensive understanding of the data, I trained a Random Forest Regression model to see if I could get a model that could assist with predicting future profits. I engineered lag and rolling profit features and encoded categorical features using OneHotEncoder. I trained the model on sale years 2014-2016 and reserved 2017 for my test set.

## Results and Conclusions

Ultimately, none of the factors delineated above were found to be responsible for the observed variability in profit trends. No patterns emerged in sales, discounts, transaction counts, etc. that correlated with profit trends. However, when I plotted annual profits again with profit outliers removed, I noticed the variability had disappeared:


![Untitled](https://github.com/user-attachments/assets/8be7ab3a-1377-4fbb-8396-250cf99be69f)

Taking a closer look at the low outliers (below 3 std devs), I noticed 11 were removed from 2017 and 7 were removed from 2015. Conversely, only 4 were removed from 2015 and 3 were removed from 2016. Therefore, it appears that higher quantities of low outliers in 2015 and 2017 were responsible for total profits being lower in those years. Additionally, sales of the Tables product sub-category accounted for 20 of the 25 low outliers.

One other notable trend was the profitability of sales was very regionally dependent. Average profit margins hovered around 10~15% for the East, South and West while hanging at -19% for Central US. Of the Central states, all except two had positive profit margins: Illinois and Texas. However, together these two states accounted for nearly 70% of orders in the region, and thus had a huge impact on overal regional profit trends. 

Poor performance in Illinois and Texas did not contribute to the yearly variation in profits, but it did uniformly drag down overall profits every year by as much as 78%. I plotted the actual profits (without outliers) alongside a hypothetical case where no sales were made in Illinois and Texas to highlight the impact of these two states:


![Untitled](https://github.com/user-attachments/assets/b8e307d1-9db2-4ffd-affb-d2cb4cadea7e)

Given the marked improvement in overall annual profits when ignoring the effects of sales in Illinois and Texas, I would recommend this furniture business carefully reconsider its strategy in these two states. If market conditions allow for it, they may consider adjusting their prices or discount strategy so that individual sales return more profit on average. If such measures are not feasible then they may want to consider not selling in these states at all given the extreme negative impact they have on their bottom line.

