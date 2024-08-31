# Retail Data Science Analysis

## Introduction

The purpose of this project was to develop my skills as a data scientist by working with a retail dataset provided by Kaggle.com. The dataset provides customer and sales data for a business operating in the retail furniture sector. 

[Kaggle Dataset Page](https://www.kaggle.com/datasets/tanayatipre/store-sales-forecasting-dataset)

I approached the data with an open mind, allowing my exploratory data analysis to inform possible areas of focus. Through EDA I discovered that annual profits were highly variable across the four years the data encompasses. Total profits seemed to fluctuate year by year without any obvious cause.


![Untitled](https://github.com/user-attachments/assets/138c1669-285e-4f92-9a8d-0eee103856be)

Such variability in profits, with 2015 and 2017 vastly underperforming 2014 and 2016, would have severe implications for the furniture retailer. However, the underlying cause or causes were a mystery; while profits varied wildly, total annual sales steadily increased each year. This both perplexed and excited me, and from that point on I decided to focus my efforts on exploring the drivers behind profit patterns.

## Methodology

My programming language of choice was Python, which I selected on account of my prior familiarity as well as the prominance of its pandas, numpy, matplotlib, and scikit-learn libraries in the data science field. All of my code is consolidated in one Jupyter Notebook:

[Jupyter Notebook Code](https://github.com/Matlabrodoodle/Retail-Data-Science-Project/blob/main/Retail%20Data%20Science%20Project.ipynb)

Throughout work on this project I made frequent use of data visualizations, particularly bar graphs and pie charts, to help investigate data trends. I devised and tested several hypotheses for what was causing the observed variation in annual profits:

1.  Variation in average annual discounts causes variation in annual profits.
2.  Variation in annual mean sales causes variation in annual profits.
3.  Variation in annual transaction/order totals causes variation in annual profits.
4.  Goods sold in lower-profit years have lower average unit prices.
5.  Regional trends cause variation in annual profits.

Lastly, I trained a Random Forest Regression model to assist with predicting future profits. I engineered lag and rolling profit features and encoded categorical features using OneHotEncoder. I trained the model on sale years 2014-2016 and reserved 2017 data for my test set. Profit outliers outside 3 standard deviations were excluded from model training.

## Results and Conclusions

### Profit Trends

Ultimately, none of the factors delineated above were responsible for the observed variability in profit trends. No patterns emerged in sales, discounts, transaction counts, etc. that correlated with the variation in profit trends. However, when I plotted annual profits again with profit outliers removed, the variability disappeared:


![Untitled](https://github.com/user-attachments/assets/8be7ab3a-1377-4fbb-8396-250cf99be69f)

Taking a closer look at the low outliers (below 3 std devs), I noticed 11 were removed from 2017 and 7 were removed from 2015. Conversely, only 4 were removed from 2015 and 3 were removed from 2016. Therefore, it appears that higher quantities of low outliers in 2015 and 2017 were responsible for total profits being lower in those years.

One other notable trend was the profitability of sales was very regionally dependent. Average profit margins hovered around 10~15% for the East, South and West while hanging at -19% for Central US. Of the Central states, all except two had positive profit margins: Illinois and Texas. However, together these two states accounted for nearly 70% of orders in the region, and thus had a huge impact on overall regional profits. 

Poor performance in Illinois and Texas did not contribute to the yearly variation in profits, but it did uniformly drag down overall profits every year by as much as 78%. I plotted the actual profits (still with outliers removed) alongside a hypothetical case where sales in Illinois and Texas were excluded to highlight the enormous impact of these two states on overall profits:


![Untitled](https://github.com/user-attachments/assets/b8e307d1-9db2-4ffd-affb-d2cb4cadea7e)

Given the marked improvement in overall annual profits when ignoring the effects of sales in Illinois and Texas, I would recommend this furniture business carefully reconsider its strategy in these two states. If market conditions allow for it, they may consider adjusting their prices or discount strategy so that individual sales return more profit on average. If such measures are not feasible then they may want to consider not selling in these states at all given the extreme negative impact they have on their bottom line.

### ML Results
After much experimentation, I found a collection of features which yielded reasonably low prediction errors during testing of my Random Forest model. The features used as well as their relative importances are plotted below:


![Untitled](https://github.com/user-attachments/assets/d0f7d055-b00d-4c5c-b143-b2b01d466b53)

The state of sale was the most important feature, which was not surprising given the enormous impact that sales in states like Illinois and Texas had on profits. Lag and rolling features were also generally important. The RMSE of predicted profit values for the year 2017 when compared against the actual values was about $89 (for comparison, the standard deviation of profits was $136). To better contextualize this RMSE figure, I divided it by the profit range to get a relative RMSE of 11.14%. Lastly, I plotted the total 2017 predicted profits alongside the actual profit values for each year for visual comparison:


![Untitled-1](https://github.com/user-attachments/assets/6d31bce3-759a-44b1-abae-98a932cb4c26)

Overall, this Random Forest model performed reasonably well during testing. However, due to the relatively small quantity of available sales data, it was not practical to set aside data for a validation set, so it is possible the model is overfit to the testing data. With this caveat in mind, I would advise this furniture business use it only as a rough baseline for predicting future profits.


