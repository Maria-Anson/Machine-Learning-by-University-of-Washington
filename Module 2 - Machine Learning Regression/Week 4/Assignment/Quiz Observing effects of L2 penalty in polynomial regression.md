## Observing effects of L2 penalty in polynomial regression
> 
> Total points 7
> 
> 1.
> 
> Question 1
> 
> We first fit a 15th order polynomial model using the 'sqft_living' column of the 'sales' data frame, with a tiny L2 penalty applied.
> 
> _**What is the absolute value of the learned coefficient of feature power_1? Round your answer to the nearest whole integer. Example: 29**_
> 
> 1 point
> 
> Enter answer here

      103
> 
> 2.
> 
> Question 2
> 
> Next, we split the sales data frame into four subsets (set_1, set_2, set_3, set_4) and fit a 15th order polynomial model using each of the subsets.
> 
> **_For the models learned in each of these training sets, what are the smallest value you learned for the coefficient of feature power_1? Choose the range that contains this value._**
> 
> 1 point
> 
>  Between -10000 and -1000 
> 

      Between -1000 and -100 
> 
>  Between -100 and 0 
> 
>  Between 0 and 100 
> 
>  Between 100 and 1000 
> 
>  Between 1000 and 10000 
> 
> 3.
> 
> Question 3
> 
> This question refer to the same models as the previous question.
> 
> **_For the models learned in each of these training sets, what are the largest value you learned for the coefficient of feature power_1? Choose the range that contains this value._**
> 
> 1 point
> 
>  Between -10000 and -1000 
> 
>  Between -1000 and -100 
> 
>  Between -100 and 0 
> 
>  Between 0 and 100 
> 
>  Between 100 and 1000 
> 

      Between 1000 and 10000 
> 
> 4.
> 
> Question 4
> 
> Using the same 4 subsets (set_1, set_2, set_3, set_4), we train 15th order polynomial models again, but this time we apply a large L2 penalty.
> 
> **_For the models learned with the high level of regularization in each of these training sets, what are the smallest value you learned for the coefficient of feature power_1?_** **_Round your answer to 2 decimal places, and use American-style decimals. Example: 2.11_**
> 
> 1 point
> 
> Enter answer here

      1.91
> 
> 5.
> 
> Question 5
> 
> This question refer to the same models as the previous question.
> 
> **_For the models learned with the high level of regularization in each of these training sets, what are the largest value you learned for the coefficient of feature power_1? Round your answer to 2 decimal places, and use American-style decimals. Example: 2.11_**
> 
> 1 point
> 
> Enter answer here

      2.59
> 
> 6.
> 
> Question 6
> 
> This question refers to the section "selecting an L2 penalty via cross-validation".
> 
> **_What is the best value for the L2 penalty according to 10-fold validation? Round your answer to 2 decimal places._**
> 
> 1 point
> 
> Enter answer here

      1000
> 
> 7.
> 
> Question 7
> 
> **_Using the best L2 penalty found above, train a model using all training data. Which of the following ranges contains the RSS on the TEST data of the model you learn with this L2 penalty?_**
> 
> 1 point
> 

      Between 8e13 and 4e14 
> 
>  Between 4e14 and 6e14 
> 
>  Between 6e14 and 8e14 
> 
>  Between 8e14 and 1e15 
> 
>  Between 1e15 and 3e15
>
> -- https://www.coursera.org/learn/ml-regression/exam/A0as6/observing-effects-of-l2-penalty-in-polynomial-regression/attempt#Tunnel Vision Close
