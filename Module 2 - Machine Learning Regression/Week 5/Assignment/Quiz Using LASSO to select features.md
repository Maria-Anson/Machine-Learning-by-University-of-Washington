### Using LASSO to select features
> 
> Total points 6
> 
> 1.
> 
> Question 1
> 
> We learn weights on the entire house dataset, using an L1 penalty of 1e10 (or 5e2, if using scikit-learn). Some features are transformations of inputs; see the reading.
> 
> **_Which of the following features have been chosen by LASSO, i.e. which features were assigned nonzero weights? (Choose all that apply)_**
> 
> 1 point
> 
>  yr_renovated 
> 
>  waterfront 
> 

      sqft_living 
> 

      grade 
> 
>  floors 
> 
> 2.
> 
> Question 2
> 
> We split the house sales dataset into training set, test set, and validation set and choose the l1_penalty that minimizes the error on the validation set.
> 
> **_In which of the following ranges does the best l1_penalty fall?_**
> 
> 1 point
> 

      Between 0 and 100 
> 
>  Between 100 and 1000 
> 
>  Between 1000 and 10000 
> 
>  Between 10000 and 100000 
> 
>  Greater than 100000 
> 
> 3.
> 
> Question 3
> 
> **_Using the best value of l1_penalty as mentioned in the previous question, how many nonzero weights do you have?_**
> 
> 1 point
> 
> Enter answer here

      18
> 
> 4.
> 
> Question 4
> 
> We explore a wide range of l1_penalty values to find a narrow region of l1_penalty values where models are likely to have the desired number of non-zero weights (max_nonzeros=7).
> 
> **_What value did you find for l1_penalty_max?_**
> 
> **_If you are using Turi Create,_** **_enter your answer in simple decimals without commas (e.g. 1131000000), rounded to nearest millions._**
> 
> **_If you are using scikit-learn_****_, enter your answer in simple decimals without commas (e.g. 4313), rounded to nearest integer._**
> 
> 1 point
> 
> Enter answer here

      3792690191
> 
> 5.
> 
> Question 5
> 
> We then explore the narrow range of l1_penalty values between l1_penalty_min and l1_penalty_max.
> 
> **_What value of l1_penalty in our narrow range has the lowest RSS on the VALIDATION set and has sparsity equal to max_nonzeros?_**
> 
> **_If you are using Turi Create, enter your answer in simple decimals without commas (e.g. 1131000000), rounded to nearest millions._**
> 
> **_If you are using scikit-learn,_** **_enter your answer in simple decimals without commas (e.g. 4342), rounded to nearest integer._**
> 
> 1 point
> 
> Enter answer here

      3448968612
> 
> 6.
> 
> Question 6
> 
> **_Consider the model learned with the l1_penalty found in the previous question. Which of the following features has non-zero coefficients? (Choose all that apply)_**
> 
> 1 point
> 

      sqft_living 
> 
>  bedrooms_square 
> 
>  sqft_lot_sqrt 
> 

      bathrooms 
> 
>  floors
>
> -- https://www.coursera.org/learn/ml-regression/exam/qtNcq/using-lasso-to-select-features/attempt#Tunnel Vision Close
