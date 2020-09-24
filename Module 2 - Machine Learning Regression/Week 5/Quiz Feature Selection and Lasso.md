## Feature Selection and Lasso
> 
> Total points 7
> 
> 1.
> 
> Question 1
> 
> **The best fit model of size 5 (i.e., with 5 features) always contains the set of features from best fit model of size 4.**
> 
> 1 point
> 
>  True 
> 

      False 
> 
> 2.
> 
> Question 2
> 
> **Given 20 potential features, how many models do you have to evaluate in the all subsets algorithm?**
> 
> 1 point
> 
> Enter answer here

      1048576
> 
> 3.
> 
> Question 3
> 
> **Given 20 potential features, how many models do you have to evaluate if you are running the forward stepwise greedy algorithm? Assume you run the algorithm all the way to the full feature set.**
> 
> 1 point

      210
> 
> Enter answer here
> 
> 4.
> 
> Question 4
> 
> **Which of the plots could correspond to a lasso coefficient path? Select ALL that apply.**
> 
> Hint: notice **λ=∞\lambda=\inftyλ=∞** in the bottom right of the plots. How should coefficients behave eventually as λ\lambdaλ goes to infinity?
> 
> 1 point
> 
>  ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/MedPIZbOEeW3hApy-CjURQ_a85a1d3a8c894051dacf249d0354b3b7_Untitled-1.png?expiry=1601078400000&hmac=rTAUF9rMoG4giliyX83O1F_GmCpp0pOE2rwFpLhbXgU) 
> 
>  ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/N5wvCpbOEeWZJxK6sR1SHQ_eb16c320cae86ffe1199a27505e042b4_Untitled-2.png?expiry=1601078400000&hmac=Zz0rSVsWjv4zs5-VZLHX55fcO5x2ccx0mQEpyGb1S5Q) 
> 
>  ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/gTyaW5bOEeWZJxK6sR1SHQ_1366dbe76f0fb3d80c9953b325e5514e_Untitled-3.png?expiry=1601078400000&hmac=AC2ldFpog4q5JAKgrPCuf9F-2WP6Z4K-qtvztLR60gE) 
> 
>  ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/SivFNJbOEeWnUgr3Wf2uiQ_be6f036fd2f02c6ab54fbeeda03fb8dc_Untitled-4.png?expiry=1601078400000&hmac=Rbh1KUL52E4e351VSDszGGX3jWCNF4Dy6j2dwluDubE) 
>

      2 & 3
> 
> 5.
> 
> Question 5
> 
> **Which of the following statements about coordinate descent is true? (Select all that apply.)**
> 
> 1 point
> 
>  A small enough step size should be chosen to guarantee convergence. 
> 

      To test the convergence of coordinate descent, look at the size of the maximum step you take as you cycle through coordinates. 
> 
>  Coordinate descent cannot be used to optimize the ordinary least squares objective. 
> 
>  Coordinate descent is always less efficient than gradient descent, but is often easier to implement. 
> 
> 6.
> 
> Question 6
> 
> **Using normalized features, the ordinary least squares coordinate descent update for feature j has the form (with ρj\rho_jρj​ defined as in the videos):**
> 
> 1 point
> 

      w^j=ρj
> 
>  w^j=(ρj)2\hat{w}_j = (\rho_j)^2w^j​=(ρj​)2 
> 
>  w^j=ρj−λ\hat{w}_j = \rho_j - \lambdaw^j​=ρj​−λ 
> 
>  w^j=ρj/2−λ\hat{w}_j = \rho_j / 2 - \lambdaw^j​=ρj​/2−λ 
> 
> 7.
> 
> Question 7
> 
> **Using normalized features, the ridge regression coordinate descent update for feature j has the form (with ρj\rho_jρj​** **defined as in the videos):**
> 
> 1 point
> 
>  w^j=ρj−λ\hat{w}_j = \rho_j - \lambdaw^j​=ρj​−λ 
> 
>  w^j=ρj/2−λ\hat{w}_j = \rho_j / 2 - \lambdaw^j​=ρj​/2−λ 
> 

      w^j=ρj/(λ+1)
> 
>  w^j=ρj\hat{w}_j = \rho_jw^j​=ρj​
>
> -- https://www.coursera.org/learn/ml-regression/exam/uifj6/feature-selection-and-lasso/attempt#Tunnel Vision Close
