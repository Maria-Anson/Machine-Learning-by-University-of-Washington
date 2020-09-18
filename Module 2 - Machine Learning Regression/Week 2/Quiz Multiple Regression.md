## Multiple Regression
> 
> Total points 9
> 
> 1.
> 
> Question 1
> 
> Which of the following is **NOT** a **linear** regression model. _Hint: remember that a linear regression model is always linear in the parameters, but may use non-linear features._
> 
> 1 point
> 
>  y=w0+w1xy = w_0 + w_1 xy=w0​+w1​x 
> 
>  y=w0+w1x2y = w_0 + w_1 x^2y=w0​+w1​x2 
> 
>  y=w0+w1log⁡(x)y = w_0 + w_1 \log(x)y=w0​+w1​log(x) 
> 

      y=w0w1+log⁡(w1)xy = w_0 w_1 + \log(w_1)xy=w0​w1​+log(w1​)x 
> 
> 2.
> 
> Question 2
> 
> Your estimated model for predicting house prices has a large positive weight on 'square feet living'. This implies that if we remove the feature 'square feet living' and refit the model, the new predictive performance will be **worse** than before.
> 
> 1 point
> 
>  True 
> 

      False 
> 
> 3.
> 
> Question 3
> 
> _Complete the following:_ Your estimated model for predicting house prices has a positive weight on 'square feet living'. You then add 'lot size' to the model and re-estimate the feature weights. The new weight on 'square feet living' [_________] be positive.
> 
> 1 point
> 
>  will not 
> 
>  will definitely 
> 

      might 
> 
> 4.
> 
> Question 4
> 
> If you double the value of a given feature (i.e. a specific column of the feature matrix), what happens to the least-squares estimated coefficients for every **other** feature? (assume you have no other feature that depends on the doubled feature i.e. no interaction terms).
> 
> 1 point
> 
>  They double 
> 
>  They halve 
> 

      They stay the same 
> 
>  It is impossible to tell from the information provided 
> 
> 5.
> 
> Question 5
> 
> Gradient descent/ascent is...
> 
> 1 point
> 
>  A model for predicting a continuous variable 
> 

      An algorithm for minimizing/maximizing a function 
> 
>  A theoretical statistical result 
> 
>  An approximation to simple linear regression 
> 
>  A modeling technique in machine learning 
> 
> 6.
> 
> Question 6
> 
> Gradient descent/ascent allows us to...
> 
> 1 point
> 
>  Predict a value based on a fitted function 
> 

      Estimate model parameters from data 
> 
>  Assess performance of a model on test data 
> 
> 7.
> 
> Question 7
> 
> Which of the following statements about step-size in gradient descent is/are **TRUE** (select all that apply)
> 
> 1 point
> 
>  It's important to choose a very small step-size 
> 
>  The step-size doesn't matter 
> 

      If the step-size is too large gradient descent may not converge 
> 

      If the step size is too small (but not zero) gradient descent may take a very long time to converge 
> 
> 8.
> 
> Question 8
> 
> Let's analyze how many computations are required to fit a multiple linear regression model _using the closed-form solution_ based on a data set with 50 observations and 10 features. In the videos, we said that computing the inverse of the 10x10 matrix HTHH^T HHTH was on the order of D3D^3D3 operations. Let's focus on forming this matrix **prior** to inversion. How many multiplications are required to form the matrix HTHH^T HHTH?
> 
> Please enter a number below.
> 
> 1 point
> 
> Enter answer here
> 
> 9.
> 
> Question 9
> 
> More generally, if you have DDD features and NNN observations what is the total complexity of computing (HTH)−1(H^T H)^{-1}(HTH)−1?
> 
> 1 point
> 
>  O(D3)O(D^3)O(D3) 
> 
>  O(ND3)O(ND^3)O(ND3) 
> 

      O(ND^2 + D^3) 
> 
>  O(ND2)O(ND^2)O(ND2) 
> 
>  O(N2D+D3)O(N^2D + D^3)O(N2D+D3) 
> 
>  O(N2D)O(N^2D)O(N2D)
>
> -- https://www.coursera.org/learn/ml-regression/exam/qlNDi/multiple-regression/attempt#Tunnel Vision Close
