### Ridge Regression
> 
> Total points 9
> 
> 1.
> 
> Question 1
> 
> **Which of the following is NOT a valid measure of overfitting?**
> 
> 1 point
> 

      Sum of parameters (w1+w2+...+wnw_1+w_2+...+w_nw1​+w2​+...+wn​) 
> 
>  Sum of squares of parameters (w12+w22+…+wn2w_1^2 + w_2^2 + … +w_n^2w12​+w22​+…+wn2​) 
> 
>  Range of parameters, i.e., difference between maximum and minimum parameters 
> 
>  Sum of absolute values of parameters (∣w1∣+∣w2∣+…+∣wn∣|w_1| + |w_2| + … + |w_n|∣w1​∣+∣w2​∣+…+∣wn​∣) 
> 
> 2.
> 
> Question 2
> 
> **In ridge regression, choosing a large penalty strength λ\lambdaλ tends to lead to a model with (choose all that apply):**
> 
> 1 point
> 

      High bias 
> 
>  Low bias 
> 
>  High variance 
> 

      Low variance 
> 
> 3.
> 
> Question 3
> 
> **Which of the following plots best characterize the trend of bias, variance, and generalization error (all plotted over λ\lambdaλ)?**
> 
> 1 point
> 
>  ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/g8gDgJatEeW3hApy-CjURQ_9a7e2c25068ef3705b0494637cc489cd_Untitled-1.png?expiry=1600819200000&hmac=Dcy_iBI-2HXgdint2dHRONijpQ2uKl-cuA45Gv6KAuk) 
> 
>  ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/isJbzJatEeWZJxK6sR1SHQ_bb04d8424c2a0dbc690f04a70d09a6f0_Untitled-2.png?expiry=1600819200000&hmac=__AX5J2DzC4KRg1qejTZoXcae1JFbgWU0h4t3mNpEX4) 
> 
>  ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/kwzbFZatEeWnUgr3Wf2uiQ_8885f6a27f89f4f7f067c51984c5ffcc_Untitled-3.png?expiry=1600819200000&hmac=yvoPi8gUfz4agNbSEk1RdzGgqAan1E6qpfxyotNKQso) 

      3
> 
> 4.
> 
> Question 4
> 
> **In ridge regression using unnormalized features, if you double the value of a given feature (i.e., a specific column of the feature matrix), what happens to the estimated coefficients for every other feature? They:**
> 
> 1 point
> 
>  Double 
> 
>  Half 
>
>  Stay the same 
> 

      Impossible to tell from the information provided 
> 
> 5.
> 
> Question 5
> 
> **If we only have a small number of observations, K-fold cross validation provides a better estimate of the generalization error than the validation set method.**
> 
> 1 point
> 

      True 
> 
>  False 
> 
> 6.
> 
> Question 6
> 
> **10-fold cross validation is more computationally intensive than leave-one-out (LOO) cross validation.**
> 
> 1 point
> 
>  True 
> 

      False 
> 
> 7.
> 
> Question 7
> 
> **Assume you have a training dataset consisting of NNN observations and DDD features. You use the closed-form solution to fit a multiple linear regression model using ridge regression. To choose the penalty strength** **λ\lambdaλ****, you run leave-one-out (LOO) cross validation searching over LLL values of λ\lambdaλ****. Let Cost(N,D)\mbox{Cost}(N,D) be the computational cost of running ridge regression with NNN data points and DDD features. Assume the prediction cost is negligible compared to the computational cost of training the model. Which of the following represents the computational cost of your LOO cross validation procedure?**
> 
> 1 point
> 
>  LN⋅Cost(N,D)L N \cdot \mbox{Cost}(N,D) 
> 

      LN⋅Cost(N−1,D)
> 
>  LD⋅Cost(N−1,D)L D \cdot \mbox{Cost}(N-1,D) 
> 
>  LD⋅Cost(N,D)L D \cdot \mbox{Cost}(N,D) 
> 
>  L⋅Cost(N−1,D)L\cdot\mbox{Cost}(N-1,D) 
> 
>  L⋅Cost(N,D)L\cdot \mbox{Cost}(N,D) 
> 
> 8.
> 
> Question 8
> 
> **Assume you have a training dataset consisting of 1 million observations. Suppose running the closed-form solution to fit a multiple linear regression model using ridge regression on this data takes 1 second. Suppose you want to choose the penalty strength λ\lambdaλ** **by searching over 100 possible values. How long will it take to run leave-one-out (LOO) cross-validation for this selection task?**
> 
> 1 point
> 
>  About 3 hours 
> 
>  About 3 days 
> 

      About 3 years 
> 
>  About 3 decades 
> 
> 9.
> 
> Question 9
> 
> **Assume you have a training dataset consisting of 1 million observations. Suppose running the closed-form solution to fit a multiple linear regression model using ridge regression on this data takes 1 second. Suppose you want to choose the penalty strength λ\lambdaλ** **by searching over 100 possible values. If you only want to spend about 1 hour to select λ\lambdaλ****, what value of k should you use for k-fold cross-validation?**
> 
> 1 point
> 
>  k=6 
> 

      k=36 
> 
>  k=600 
> 
>  k=3600
>
> -- https://www.coursera.org/learn/ml-regression/exam/REIRy/ridge-regression/attempt#Tunnel Vision Close
