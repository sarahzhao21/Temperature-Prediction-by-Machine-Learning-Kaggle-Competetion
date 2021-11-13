# Trout Lake Temperature Prediction (Kaggle Competetion, Team Name: Libra, Team Member: Sarah Zhao)

### Introduction
Lake monitoring provides important information for environment protection and pollution identification, such as temperature/thermal monitoring. In this Kaggle task, the instructor will provide thermal sensor data for multiple lakes and ask people to predict/estimate the temperature at a certain depth for certain lakes.

### Dataset
The instructor provide Lake Trout’s data during the period of Apr 20th, 2012 - Apr 19th, 2018. There will be multiple sensors at different depths, and what will be provided include: lake_id, time, depth and the corresponding temperature at this depth and time point. 

|Date_Time	           |Water_Temp_C	|Depth_m|
|:-----------------:|:-----------:|:-------:|
|2012-04-20 00:00:00	 |5.257	        |1.5|
|2012-04-20 00:00:00	 |5.257        	|2.5|
|2012-04-20 00:00:00	 |5.257       	|3.5|
|2012-04-20 00:00:00	 |5.205	        |4.5|
|2012-04-20 00:00:00	 |5.205         |5.5|

### Task
Predicting/estimating the temperature of Trout Lake at depth 10.5 m during Apr 20th, 2018 - Apr 19th, 2019. 

Benchmark 1:  MSE < 0.065
Benchmark 2:  MSE < 0.032

### Model
The temperature of a specific depth should be in the range between the temperature of the depth that slightly higher or lower of the target depth. Thus, to estimate the depth of 10.5, the temperatures of all the other depth could be considered as the features. So, the train set can be obtained by creating the pivot table of the raw data:

|Depth_m	          |1.5	|2.5	|3.5	|4.5	|5.5	|6.5	|7.5	|8.5	|9.5	|10.5	|11.5	|12.5	|14.5	|16.5	|18.5	|20.5|
|:----------------:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|									
|2012-04-20 00	|5.257	|5.257	|5.257	|5.205	|5.205	|5.154	|5.231	|5.128	|5.102	|5.076	|4.792	|4.818	|4.766	|4.792	|4.792	|4.818|
|2012-04-20 01	|5.205	|5.231	|5.231	|5.179	|5.205	|5.154	|5.231	|5.128	|5.024	|4.999	|4.792	|4.818	|4.766	|4.792	|4.792	|4.792|
|2012-04-20 02	|5.231	|5.231	|5.231	|5.154	|5.179	|5.128	|5.154	|4.973	|4.895	|4.895	|4.792	|4.792	|4.740	|4.792	|4.792	|4.792|
|2012-04-20 03	|5.205	|5.231	|5.205	|5.154	|5.154	|5.102	|5.128	|4.999	|4.895	|4.921	|4.766	|4.818	|4.766	|4.792	|4.792	|4.766|
|2012-04-20 04	|5.205	|5.231	|5.154	|5.050	|5.050	|4.999	|5.076	|4.999	|4.947	|4.973	|4.818	|4.844	|4.792	|4.792	|4.792	|4.766|  

Algorithms that have been tried for the prediction include: Ridge, Lasso and SVR of the sklearn python package, and dimention expantion(PolynomialFeatures) has been used to optimize the accuracy.

### Result 
Team-Libra (Team member: Sarah Zhao) get the **MSE: 0.02451**, ranked the 13th among the 48 teams in this competetion.
I used the Ridge regression model and dimention expantion to solve this problem.

[Kaggle link](https://www.kaggle.com/c/si670fall2020/leaderboard)








