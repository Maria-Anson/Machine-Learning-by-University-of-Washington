### Implementing ridge regression via gradient descent
> 
> Total points 8
> 
> 1.
> 
> Question 1
> 
> We run ridge regression to learn the weights of a simple model that has a single feature (sqft_living), once with l2_penalty=0.0 and once with l2_penalty=1e11.
> 
> **_What is the value of the coefficient for sqft_living that you learned with no regularization, rounded to 1 decimal place? Use American-style decimals (e.g. 30.5)_**
> 
> 1 point
> 
> Enter answer here

      263.02
> 
> 2.
> 
> Question 2
> 
> This question refers to the same model as the previous question.
> 
> **_What is the value of the coefficient for sqft_living that you learned with high regularization (l2_penalty=1e11)? Use American-style decimals (e.g. 30.5) and_** **_round your answer to 1 decimal place._**
> 
> 1 point
> 
> Enter answer here

      124.57
> 
> 3.
> 
> Question 3
> 
> This question refers to the same model as the previous question.
> 
> **_Comparing the lines you fit with the with no regularization versus high regularization (l2_penalty=1e11), which one is steeper?_**
> 
> 1 point
> 

      Line fit with no regularization (l2_penalty=0) 
> 
>  Line fit with high regularization (l2_penalty=1e11) 
> 
> 4.
> 
> Question 4
> 
> This question refers to the same model as the previous question.
> 
> **_Using the weights learned with no regularization (l2_penalty=0), make predictions for the TEST data. In which of the following ranges does the TEST error (RSS) fail?_**
> 
> 1 point
> 
>  Between 8e13 and 2e14 
> 

      Between 2e14 and 5e14 
> 
>  Between 5e14 and 8e14 
> 
>  Between 8e14 and 1e15 
> 
>  Between 1e15 and 3e15 
> 
> 5.
> 
> Question 5
> 
> We run ridge regression to learn the weights of a model that has two features (sqft_living, sqft_living15), once with l2_penalty=0.0 and once with l2_penalty=1e11.
> 
> _**What is the value of the coefficient for sqft_living that you learned with no regularization, rounded to 1 decimal place? Use American-style decimals (e.g. 30.5).**_
> 
> 1 point
> 
> Enter answer here

      243.05
> 
> 6.
> 
> Question 6
> 
> This question refers to the same model as the previous question.
> 
> _**What is the value of the coefficient for sqft_living that you learned with high regularization (l2_penalty=1e11)? Use American-style decimals (e.g. 30.5) and round your answer to 1 decimal place.**_
> 
> 1 point
> 
> Enter answer here

      91.49
> 
> 7.
> 
> Question 7
> 
> This question refers to the same model as the previous question.
> 
> **_Using_****_high_penalty_weights,_****_make predictions for the TEST data. In which of the following ranges does the TEST error (RSS) fall?_**
> 
> 1 point
> 
>  Between 8e13 and 2e14 
> 
>  Between 2e14 and 4e14 
> 

      Between 4e14 and 8e14 
> 
>  Between 8e14 and 1e15 
> 
>  Between 1e15 and 3e15 
> 
> 8.
> 
> Question 8
> 
> This question refers to the same model as the previous question.
> 
> _**Predict the price of the first house in the test set using the weights learned with no regularization. Do the same using the weights learned with high regularization. Which weights make better prediction**__**for the first house in the test set**__**?**_
> 
> 1 point
> 
>  The weights learned with no regularization (l2_penalty=0) 
> 

      The weights learned with high regularization (l2_penalty=1e11)
>
> -- https://www.coursera.org/learn/ml-regression/exam/6JDi6/implementing-ridge-regression-via-gradient-descent/attempt#Tunnel Vision Close
