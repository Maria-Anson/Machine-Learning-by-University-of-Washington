## Implementing ridge regression via gradient descent
> 
> * * *
> 
> ## Regression Week 4: Ridge Regression Assignment 2
> 
> In this assignment, you will implement ridge regression via gradient descent. You will:
> 
> *   Convert an SFrame into a Numpy array (if applicable)
> *   Write a Numpy function to compute the derivative of the regression weights with respect to a single feature
> *   Write gradient descent function to compute the regression weights given an initial weight vector, step size, tolerance, and L2 penalty
> *   We will continue to use the House data from previous assignments. (In the next programming assignment for this module, you will implement your own ridge regression learning algorithm using gradient descent.)
> 
> ## If you are doing the assignment with Jupyter Notebook
> 
> An Jupyter Notebook has been provided below to you for this quiz. This notebook contains the instructions, quiz questions and partially-completed code for you to use as well as some cells to test your code.
> 
> ## What you need to download
> 
> ### If you are using Turi Create
> 
> *   Download the King County House Sales data In SFrame format:
> 
> [home_data.sframe.zip](https://d3c33hcgiwev3.cloudfront.net/00FsKOIoEemELQpo9cj5Ig_579152614f2b4a399ac90a939360749e_home_data.sframe.zip?Expires=1600819200&Signature=dKqGYdnBx8KC9~7DAbkOHKUxfWiUVVydnrHJcmA1nGtrlPLEnmLzxkeLfyY6BHHjAflblVf3Vz-GmMLt1hoB2Nb5tIjfwIIacXq1TgMkQ7YYt5p95RWfSmlWoPb-Kz3jOV~OEOROeV2uUb19bfat-ww8S60oO3bbHu~QzyLva0s_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the companion Jupyter Notebook:
> 
> [REG04-NB02.ipynb.zip](https://d3c33hcgiwev3.cloudfront.net/QSJnZOItEemx8A5HK6Ls8g_0759bf063ba4479688a48aa1e0e1401d_REG04-NB02.ipynb.zip?Expires=1600819200&Signature=NOGnr8OFhBvFmYx~M-bGYKIDKhHjAcCcUohjD-UzAwcWD5ERcSW87tGo4rOGkZu6bagsad3yzk7fTuiEHa~yHE9g7TsabTBZLJRBWgUHpBYRQeQN5N9xWWBZ7McpG6hMJNnzcbIxeavjkyjo~0qgS-mfUwKVCkLJfzeWeiUCXII_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Save both of these files in the same directory (where you are calling Jupyter notebook from) and unzip the data file.
> 
> ### If you are not using Turi Create
> 
> *   Download the King County House Sales data csv file:
> 
> [kc_house_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_46994807796a1213d2699c6d9a09667c_kc_house_data.csv.zip?Expires=1600819200&Signature=ale2jtwVUwkRsonEgolLzHgtEiNWGWE40lX2gqfANELWIq-OmMt07WNmDA~DInjF9YOwCmsCzAQKplLeyy4N7S7C6rSagRdQGHMHMq3X4Kxch7sHP~qREb5RFHqay7y-URrnhugYTOwDzPOpRdZXB~wVybNqrMZewzZIe0D~0bw_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the King County House Sales training data csv file:
> 
> [kc_house_train_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_46994807796a1213d2699c6d9a09667c_kc_house_train_data.csv.zip?Expires=1600819200&Signature=Y-u0~Byi4rXkLOrrSTbPcXJjQQcr5fInj9OzBSe6p9Td4HqdgL0-yBx-9v-sOHzXv29bKevIp35ana99FgGpjn2QFkNO~zlHPymB2otz9X1R7tunAN5CUODGHrklGn8eDCpekJ2WrmoZN-tmkDApA4MJ3MM2L8RlyUAnTWP92S4_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the King County House Sales testing data csv file:
> 
> [kc_house_test_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_46994807796a1213d2699c6d9a09667c_kc_house_test_data.csv.zip?Expires=1600819200&Signature=QqDuUeZqmDKNMbXkt~zl-gN9QoPrOksOI0wiZr9Plk7itxAM9n0FKcuZ4TwtrwyFbuPCoUMiHvdu6VMJZSmrG5qtC7OS0tiU2mduWOj9mashdfqkIgPjmnU47C3zKwez0PIb8zBQTl7Ad6ilWk93GuG1so1nWreZ2QFmjdzuaXI_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   **IMPORTANT: use the following types for columns when importing the csv files. Otherwise, they may not be imported correctly: [str, str, float, float, float, float, int, str, int, int, int, int, int, int, int, int, str, float, float, float, float]. If your tool of choice requires a dictionary of types for importing csv files (e.g. Pandas), use:**
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> dtype_dict = {'bathrooms':float, 'waterfront':int, 'sqft_above':int, 
> 
>   'sqft_living15':float, 'grade':int, 'yr_renovated':int, 'price':float, 
> 
>   'bedrooms':float, 'zipcode':str, 'long':float, 'sqft_lot15':float, 
> 
>   'sqft_living':float, 'floors':str, 'condition':int, 'lat':float, 'date':str, 
> 
>   'sqft_basement':int, 'yr_built':int, 'id':str, 'sqft_lot':int, 'view':int}
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> ## Useful resources
> 
> You may need to install the software tools described in the reading for Module 1.
> 
> If you are following the Jupyter Notebook and/or are new to numpy then you might find the following tutorial helpful:
> 
> [numpy-tutorial-py3.ipynb.zip](https://d3c33hcgiwev3.cloudfront.net/IvpyKP2LEei5Kg7DUflKxA_233c5c80fd8b11e891270765d8b4cf4e_numpy-tutorial-py3.ipynb.zip?Expires=1600819200&Signature=QtoFxkSBLluTB4I9ZSbobfbnfxnvTT11puPNAfggVGuSVWI0Z1wI-CYeH3SEhbFvbo11Ggh6PVVZrPW5hAPJ01uZhWH0S5kkL2uJXGsYkzfVzhi7LLqzeravIUTZxf0ejFNtK1J0Ss84jE7KR1Ucd~Xn10JS4-zPm6MaD5HqMBs_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> ## If you are using Turi Create and the companion Jupyter Notebook
> 
> Open the companion Jupyter notebook and follow the instructions in the notebook.
> 
> ## If instead you are using other tools to do your homework
> 
> You are welcome to write your own code and use any other libraries, like Pandas or R, to help you in the process. If you would like to take this path, follow the instructions below.
> 
> **1\.** If you’re using SFrame, import Turi Create and load in the house data as follows:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> sales = turicreate.SFrame('kc_house_data.gl/')      
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> Otherwise, load all the three csv files.
> 
> **2\.** If you’re using Python: to do the matrix operations required to perform a gradient descent we will be using the popular python library ‘numpy’ which is a computational library specialized for operations on arrays. For students unfamiliar with numpy we have created a numpy tutorial (see useful resources). It is common to import numpy under the name ‘np’ for short, to do this execute:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> import numpy as np
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> **3\.** Next, from Module 2, copy and paste the ‘get_numpy_data’ function (or equivalent) that takes a dataframe, a list of features (e.g. [‘sqft_living’, ‘bedrooms’]), to be used as inputs, and a name of the output (e.g. ‘price’). This function returns a ‘feature_matrix’ (2D array) consisting of first a column of ones followed by columns containing the values of the input features in the data set in the same order as the input list. It alsos return an ‘output_array’ which is an array of the values of the output in the data set (e.g. ‘price’).
> 
> e.g. in Python:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2
> 
> 3
> 
> def get_numpy_data(data_sframe, features, output):
> 
>     ...
> 
>     return (feature_matrix, output_array)
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> **4\.** Similarly, copy and paste the ‘predict_output’ function (or equivalent) from Module 2\. This function accepts a 2D array ‘feature_matrix’ and a 1D array ‘weights’ and return a 1D array ‘predictions’.
> 
> e.g. in Python:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2
> 
> 3
> 
> def predict_output(feature_matrix, weights):
> 
>     ...
> 
>     return predictions
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> **5\.** We are now going to move to computing the derivative of the regression cost function. Recall that the cost function is the sum over the data points of the squared difference between an observed output and a predicted output, plus the L2 penalty term.
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2
> 
> 3
> 
> Cost(w)
> 
> = SUM[ (prediction - output)^2 ]
> 
> + l2_penalty*(w[0]^2 + w[1]^2 + ... + w[k]^2).
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> Since the derivative of a sum is the sum of the derivatives, we can take the derivative of the first part (the RSS) as we did in the notebook for the unregularized case in Module 2 and add the derivative of the regularization part. As we saw, the derivative of the RSS with respect to w[i] can be written as:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2*SUM[ error*[feature_i] ]
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> The derivative of the regularization term with respect to w[i] is:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2*l2_penalty*w[i]
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> Summing both, we get
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2*SUM[ error*[feature_i] ] + 2*l2_penalty*w[i]
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> That is, the derivative for the weight for feature i is the sum (over data points) of 2 times the product of the error and the feature itself, plus 2*l2_penalty*w[i].
> 
> **IMPORTANT: We will not regularize the constant.** Thus, in the case of the constant, the derivative is just twice the sum of the errors (without the 2*l2_penalty*w[0] term).
> 
> Recall that twice the sum of the product of two vectors is just twice the dot product of the two vectors. Therefore the derivative for the weight for feature_i is just two times the dot product between the values of feature_i and the current errors, plus 2*l2_penalty*w[i].
> 
> **6\.** With this in mind write the derivative function which computes the derivative of the weight given the value of the feature (over all data points) and the errors (over all data points). To decide when to we are dealing with the constant (so we don't regularize it) we added the extra parameter to the call ‘feature_is_constant’ which you should set to True when computing the derivative of the constant and False otherwise.
> 
> e.g. in Python:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2
> 
> 3
> 
> def feature_derivative_ridge(errors, feature, weight, l2_penalty, 
> 
>   feature_is_constant):
> 
>     ...
> 
>     return derivative
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> **7\.** To test your feature derivative function, run the following:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2
> 
> 3
> 
> 4
> 
> 5
> 
> 6
> 
> 7
> 
> 8
> 
> 9
> 
> 10
> 
> 11
> 
> 12
> 
> 13
> 
> (example_features, example_output) = get_numpy_data(sales, ['sqft_living'], 
> 
>   'price')
> 
> my_weights = np.array([1., 10.])
> 
> test_predictions = predict_output(example_features, my_weights)
> 
> errors = test_predictions - example_output # prediction errors
> 
> # next two lines should print the same values
> 
> print feature_derivative_ridge(errors, example_features[:,1], my_weights[1], 1, 
> 
>   False)
> 
> print np.sum(errors*example_features[:,1])*2+20.
> 
> print ''
> 
> # next two lines should print the same values
> 
> print feature_derivative_ridge(errors, example_features[:,0], my_weights[0], 1, 
> 
>   True)
> 
> print np.sum(errors)*2.
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> **8\.** Now we will write a function that performs a gradient descent. The basic premise is simple. Given a starting point we update the current weights by moving in the negative gradient direction. Recall that the gradient is the direction of increase and therefore the negative gradient is the direction of decrease and we're trying to minimize a cost function.
> 
> The amount by which we move in the negative gradient direction is called the ‘step size’. We stop when we are ‘sufficiently close’ to the optimum. Unlike in Module 2, this time we will set a maximum number of iterations and take gradient steps until we reach this maximum number. If no maximum number is supplied, the maximum should be set 100 by default. (Use default parameter values in Python.)
> 
> With this in mind, write a gradient descent function using your derivative function above. For each step in the gradient descent, we update the weight for each feature before computing our stopping criteria. The function will take the following parameters:
> 
> *   2D feature matrix
> *   array of output values
> *   initial weights
> *   step size
> *   L2 penalty
> *   maximum number of iterations
> 
> To make your job easier, we provide a skeleton in Python:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2
> 
> 3
> 
> 4
> 
> 5
> 
> 6
> 
> 7
> 
> 8
> 
> 9
> 
> 10
> 
> 11
> 
> 12
> 
> 13
> 
> 14
> 
> def ridge_regression_gradient_descent(feature_matrix, output, initial_weights, 
> 
>   step_size, l2_penalty, max_iterations=100):
> 
>     weights = np.array(initial_weights) # make sure it's a numpy array
> 
>         #while not reached maximum number of iterations:
> 
>         # compute the predictions using your predict_output() function
> 
>         # compute the errors as predictions - output
> 
>         for i in xrange(len(weights)): # loop over each weight
> 
>             # Recall that feature_matrix[:,i] is the feature column associated 
> 
>               with weights[i]
> 
>             # compute the derivative for weight[i].
> 
>             #(Remember: when i=0, you are computing the derivative of the 
> 
>               constant!)
> 
>             # subtract the step size times the derivative from the current 
> 
>               weight 
> 
>               return weights
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> **9\.** The L2 penalty gets its name because it causes weights to have small L2 norms than otherwise. Let's see how large weights get penalized. Let us consider a simple model with 1 feature.
> 
> *   features: ‘sqft_living’
> *   output: ‘price’
> 
> **10\.** Split the dataset into training set and test set. If you are using Turi Create, call
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> train_data,test_data = sales.random_split(.8,seed=0)
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> Otherwise, please download the csv files from the download section.
> 
> **11\.** Convert the training set and test set using the ‘get_numpy_data’ function.e.g. in Python:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2
> 
> 3
> 
> 4
> 
> 5
> 
> simple_features = ['sqft_living']
> 
> my_output = 'price'
> 
> (simple_feature_matrix, output) = get_numpy_data(train_data, simple_features, 
> 
>   my_output)
> 
> (simple_test_feature_matrix, test_output) = get_numpy_data(test_data, 
> 
>   simple_features, my_output)
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> **12\.** First, let’s consider no regularization. Set the L2 penalty to 0.0 and run your ridge regression algorithm to learn the weights of the simple model (described above). Use the following parameters:
> 
> *   step_size = 1e-12
> *   max_iterations = 1000
> *   initial_weights = all zeros
> 
> Store the learned weights as
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> simple_weights_0_penalty
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> we’ll use them later.
> 
> **13.** Next, let’s consider high regularization. Set the L2 penalty to 1e11 and run your ridge regression to learn the weights of the simple model. Use the same parameters as above. Call your weights:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> simple_weights_high_penalty
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> we’ll use them later.
> 
> **14\.** If you have access to matplotlib, the following piece of code will plot the two learned models. (The blue line is for the model with no regularization and the red line is for the one with high regularization.)
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2
> 
> 3
> 
> 4
> 
> 5
> 
> import matplotlib.pyplot as plt
> 
> %matplotlib inline
> 
> plt.plot(simple_feature_matrix,output,'k.',
> 
>         simple_feature_matrix,predict_output(simple_feature_matrix, 
> 
>           simple_weights_0_penalty),'b-',
> 
>         simple_feature_matrix,predict_output(simple_feature_matrix, 
> 
>           simple_weights_high_penalty),'r-')
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> If you do not have access to matplotlib, look at each set of coefficients. If you were to plot ‘sqft_living’ vs the price, which of the two coefficients is the slope and which is the intercept?
> 
> **15\.** **_Quiz Question: What is the value of the coefficient for sqft_living that you learned with no regularization, rounded to 1 decimal place? What about the one with high regularization?_**
> 
> **16\.** **_Quiz Question: Comparing the lines you fit with the with no regularization versus high regularization, which one is steeper?_**
> 
> **17\.** Compute the RSS on the TEST data for the following three sets of weights:
> 
> *   The initial weights (all zeros)
> *   The weights learned with no regularization
> *   The weights learned with high regularization
> 
> **18\.** **_Quiz Question: What are the RSS on the test data for each of the set of weights above (initial, no regularization, high regularization)?_**
> 
> **19\.** Let us now consider a model with 2 features: [ ‘sqft_living’, ‘sqft_living_15’]. First, create Numpy version of your training and test data with the two features.
> 
> e.g. in Python:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2
> 
> 3
> 
> 4
> 
> model_features = ['sqft_living', 'sqft_living15']
> 
> my_output = 'price'
> 
> (feature_matrix, output) = get_numpy_data(train_data, model_features, my_output)
> 
> (test_feature_matrix, test_output) = get_numpy_data(test_data, model_features, 
> 
>   my_output)
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> **20\.** First, let’s consider no regularization. Set the L2 penalty to 0.0 and run your ridge regression algorithm. Use the following parameters:
> 
> *   initial_weights = all zeros
> *   step size = 1e-12
> *   max_iterations = 1000
> 
> Call the learned weights
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> multiple_weights_0_penalty
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> **21\.** Next, let’s consider high regularization. Set the L2 penalty to 1e11 and run your ridge regression to learn the weights of the simple model. Use the same parameters as above. Call your weights:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> multiple_weights_high_penalty
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> **22\.** **_Quiz Question: What is the value of the coefficient for ‘sqft_living’ that you learned with no regularization, rounded to 1 decimal place? What about the one with high regularization?_**
> 
> **23\.** Compute the RSS on the TEST data for the following three sets of weights:
> 
> *   The initial weights (all zeros)
> *   The weights learned with no regularization
> *   The weights learned with high regularization
> 
> **24\.** _**Quiz Question: What are the RSS on the test data for each of the set of weights above (initial, no regularization, high regularization)?**_
> 
> 25\. Predict the house price for the 1st house in the test set using the no regularization and high regularization models. (Remember that python starts indexing from 0.)
> 
> 26\. **_Quiz Question: What's the error in predicting the price of the first house in the test set using the weights learned with no regularization? What about with high regularization?_**
>
> -- https://www.coursera.org/learn/ml-regression/supplement/poz6z/implementing-ridge-regression-via-gradient-descent#main
