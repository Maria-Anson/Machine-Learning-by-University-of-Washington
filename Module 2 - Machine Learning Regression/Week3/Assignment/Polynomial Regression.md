## Polynomial Regression
> 
> * * *
> 
> ## Regression Week 3: Polynomial Regression Quiz
> 
> In this notebook you will compare different regression models in order to assess which model fits best. We will be using polynomial regression as a means to examine this topic. In particular you will:
> 
> *   Write a function to take an an array and a degree and return an data frame where each column is the array to a polynomial value up to the total degree.
> *   Use a plotting tool (e.g. matplotlib) to visualize polynomial regressions
> *   Use a plotting tool (e.g. matplotlib) to visualize the same polynomial degree on different subsets of the data
> *   Use a validation set to select a polynomial degree
> *   Assess the final fit using test data
> 
> ## If you are doing the assignment with Jupyter Notebook
> 
> A Jupyter Notebook has been provided below to you for this quiz. This notebook contains the instructions, quiz questions and partially-completed code for you to use as well as some cells to test your code.
> 
> ## What you need to download
> 
> ### If you are using Turi Create:
> 
> *   Download the King County House Sales data In SFrame format:
> 
> [home_data.sframe.zip](https://d3c33hcgiwev3.cloudfront.net/00FsKOIoEemELQpo9cj5Ig_579152614f2b4a399ac90a939360749e_home_data.sframe.zip?Expires=1600646400&Signature=aSMKGZP4O4pwZQaO5VeP6wcRp5lRLZmmFm2Ze3eqo7IItWpzM5n~3v8qVhecCp~W5dW~ddv9dYstOwR-EaUAZrqvmctzP0eJ7AYWD7b8rjHiIV7n~iKytQ9~2ry~mdrwNLGjd5yhofNM~6PE8XI4Sq8pNH-0QYpztm5Xor71b5M_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the companion Jupyter Notebook:
> 
> [REG03-NB01.ipynb.zip](https://d3c33hcgiwev3.cloudfront.net/i3YHfOIrEemJfgqR2HI2sA_57d4c573797843db9be3aa6c009d387b_REG03-NB01.ipynb.zip?Expires=1600646400&Signature=Oys~YtaBgU~UJyD95VyTfyeqO9BbnaUldiDnJzh58iC~aNL3ItqdfJrIiVodo4Mwe5bCngdEeN7L-JjUt1R-zbT03fadhfPa3ih~tY-pPTjppdO2cYmwMTBSBas0bGnNMwiwK~8qWHi4SK4FOpXv7cDL8v1VtWzthPcfKYIkkuM_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Save both of these files in the same directory (where you are calling Jupyter notebook from) and unzip the data file.
> 
> ### If you are not using Turi Create:
> 
> *   Download the King County House Sales data csv file:
> 
> [kc_house_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_46994807796a1213d2699c6d9a09667c_kc_house_data.csv.zip?Expires=1600646400&Signature=HE2giOaM6g6D-ECveck7hqho~-3AoUy3Ya~h153z0U9S8pSLgBlbEy-i6Z5uEPducOP0syWMh707yFQK-bwyAQidO8KrZM~6sqoEb5pQ~mZ27JXiegFedrmdLp5zUs732LF8a4-1oN-heT34dJdamy4hN~IJU95zAZymvTRh3VY_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> NOTE: The following files are different from weeks 1 and 2
> 
> *   Download the King County House Sales training data csv file:
> 
> [wk3_kc_house_train_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_f626f6faf3c1039d014563b39ede3037_wk3_kc_house_train_data.csv.zip?Expires=1600646400&Signature=ACp9fAB2J2-R6RjqQmmXEpUciZIz~u-2BWR-XhpeDoTRRaXAdx2Gw9hT0EvTr~KXbU33M~LGZyNDwom2UAkEGuU5cMFN1hQ7nIs0GN8njKsa5gcWKNxh1zGsEN558oKz40kasrqh74FcxBsCqQUGDYFqu6wJqc0pAb4GBVgx4Pc_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the King County House Sales validation data csv file:
> 
> [wk3_kc_house_valid_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_f626f6faf3c1039d014563b39ede3037_wk3_kc_house_valid_data.csv.zip?Expires=1600646400&Signature=j0uusdSOxHCMWTr8UlP-5Ajl6HuVep8CgHuvS-GvZjn-aeim53kH4t0ctPVkJedFfxQL89o4U086zfo8QmZfaHnyj1GXsnU6I7Ywi2F~bkQRnehdGcoO3fLvQ7XSA-OSlUq1RHzHZi6XwVEkcjCIYPIR6ozDyJUD5597I57xrGM_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the King County House Sales testing data csv file:
> 
> [wk3_kc_house_test_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_f626f6faf3c1039d014563b39ede3037_wk3_kc_house_test_data.csv.zip?Expires=1600646400&Signature=lD5vESgIPEZJyXMU9tCJGR-uNZXh1q6xlzWonO1sOJOWj2LvrpFz6lylyow0JXkD43DPiUJDIkQdJlEVontckSnVkAsbaWaFTF68zc3c4Y~HVqGNBYqze~oHkqSgdZgYnuCeVk2i9wffsizvmaSffvlmgarueLROGtvTxbEJrxA_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the King County House Sales subset 1 data csv file:
> 
> [wk3_kc_house_set_1_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_f626f6faf3c1039d014563b39ede3037_wk3_kc_house_set_1_data.csv.zip?Expires=1600646400&Signature=L-6tp-L4YhUcz-RSLPILeyfZWdrBXEJ6rEenOkuOS~SQt8WulcPCvxNcYljbQE57tbCwowBFpcbNVe95bvzS6d7B0SJHY9lOEOP~Mkji2k3sj0WThB~cS6KTBi7OjWvj66mnOf-WitvcfdWpur8v7lAEU9EAlgXs6rXWm4sWfhc_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the King County House Sales subset 2 data csv file:
> 
> [wk3_kc_house_set_2_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_f626f6faf3c1039d014563b39ede3037_wk3_kc_house_set_2_data.csv.zip?Expires=1600646400&Signature=EkSIUhogAJu4nAT4NAgk9JxLZmRlFRncxvNddqszlexelbDyeNd2Nzauo4jiQI0-Tza2CYrS6tZj~OYTC-yXV~7VzNvbAS7r3cxyo~0XTJQ~7gLkBw0FatM8NrOsC7~S5bRNKBPKkMkQhk12kPCcUJbo0S~qnMs-G3yQFLyCQ~o_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the King County House Sales subset 3 data csv file:
> 
> [wk3_kc_house_set_3_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_f626f6faf3c1039d014563b39ede3037_wk3_kc_house_set_3_data.csv.zip?Expires=1600646400&Signature=TqKll5drHtngfzmNIPAVzu5g10UiB~J16nV0B8jUv4vowoJY6WBbmxOJ-rm5iM5JqAtfQF6Qip~QSCI9iYwX34WMUzkviLkadsNyVJkkKkkxAZgx4rep3PTFppScQ1sNoNSKAfpVHWL2BbSQLsWfZ12cqtLCMfkvDDupAt-4EmI_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the King County House Sales subset 4 data csv file:
> 
> [wk3_kc_house_set_4_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_f626f6faf3c1039d014563b39ede3037_wk3_kc_house_set_4_data.csv.zip?Expires=1600646400&Signature=Ppi3HM1680EffsfpBoJg3QEH5ciYe3SNVzki917heAuY5afYMZ7LcSC1qX2pcQsO7pbeZ0~XEcuDZn5qyJd4AcSXCjTtnSLZ2hPmdDhEaL9gOzTZl8no5XwTheA8MWXIkmZ6y0wA5bP-zYdkcfoXvDdKBH9QLNRNVp39nUvGxCA_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
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
> [numpy-tutorial-py3.ipynb.zip](https://d3c33hcgiwev3.cloudfront.net/IvpyKP2LEei5Kg7DUflKxA_233c5c80fd8b11e891270765d8b4cf4e_numpy-tutorial-py3.ipynb.zip?Expires=1600646400&Signature=DVozYzoFwFJQHMmqaueCM28pgS97SzXjfx-nqS1xJg76L47kgjYSEpttLxkGAO9lJqheW6RWfn4T5RgLz4lewejtEmfGU1KA9Fuf1fy8Ux-Wlo9HKnp87yG2-OWIYTyl9TE5TKB1nOckdkPXUjrdG-VhoH3MZjnZNLjL62gSz9s_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> ## If instead you are using other tools to do your homework
> 
> You are welcome, however, to write your own code and use any other libraries, like Pandas or R, to help you in the process. If you would like to take this path, follow the instructions below.
> 
> **1\.** You’re going to write a function that adds powers of a feature to columns of a data frame. For those using SFrames:
> 
> Recall that if we have an SArray ‘tmp’ we can get a new SArray with all the values to the third power with:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> tmp_cubed = tmp.apply(lambda x: x**3)
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> We can create an empty SFrame with:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> my_SFrame = turicreate.SFrame()
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> And append the tmp to it with:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> my_SFrame['power_1'] = tmp
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> Where here ‘power_1’ will refer to the power our feature was raised to.
> 
> **2\.** Write your own function called ‘polynomial_sframe’ (or otherwise) which accepts an array ‘feature’ and a maximal ‘degree’ and returns an data frame (e.g. SFrame) with the first column equal to ‘feature’ and the remaining columns equal to ‘feature’ to increasing integer powers up to ‘degree’.
> 
> e.g. if you’re using SFrames, you can complete the following function:
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
> 15
> 
> def polynomial_sframe(feature, degree):
> 
>     # assume that degree >= 1
> 
>     # initialize the SFrame:
> 
>     poly_sframe = tuicreate.SFrame()
> 
>     # and set poly_sframe['power_1'] equal to the passed feature
> 
>     ...
> 
>     # first check if degree > 1
> 
>     if degree > 1:
> 
>         # then loop over the remaining degrees:
> 
>         for power in range(2, degree+1):
> 
>             # first we'll give the column a name:
> 
>             name = 'power_' + str(power)
> 
>             # assign poly_sframe[name] to be feature^power
> 
>             ...
> 
>     return poly_sframe
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> e.g. if you’re using Pandas, you can complete the following function:
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
> 15
> 
> def polynomial_dataframe(feature, degree): # feature is pandas.Series type
> 
>     # assume that degree >= 1
> 
>     # initialize the dataframe:
> 
>     poly_dataframe = pandas.DataFrame()
> 
>     # and set poly_dataframe['power_1'] equal to the passed feature
> 
>     ...
> 
>     # first check if degree > 1
> 
>     if degree > 1:
> 
>         # then loop over the remaining degrees:
> 
>         for power in range(2, degree+1):
> 
>             # first we'll give the column a name:
> 
>             name = 'power_' + str(power)
> 
>             # assign poly_dataframe[name] to be feature^power; use apply(*)
> 
>             ...
> 
>     return poly_dataframe
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> **3\.** For the remainder of the assignment we will be working with the house Sales data as in the previous notebooks. Load in the data and also sort the sales SFrame by ‘sqft_living’. When we plot the fitted values we want to join them up in a line and this works best if the variable on the X-axis (which will be ‘sqft_living’) is sorted. For houses with identical square footage, we break the tie by their prices.
> 
> e.g. if you’re using SFrames
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2
> 
> sales = turicreate.SFrame('kc_house_data.gl/')
> 
> sales = sales.sort(['sqft_living','price'])
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> e.g. if you're using Pandas
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2
> 
> sales = pandas.read_csv('kc_house_data.csv', dtype=dtype_dict)
> 
> sales = sales.sort(['sqft_living','price'])
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> **4\.** Make a 1 degree polynomial SFrame with sales[‘sqft_living’] as the the feature. Call it ‘poly1_data’.
> 
> **5\.** Add sales[‘price’] to poly1_data as this will be our output variable. e.g. if you’re using SFrames
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2
> 
> poly1_data = polynomial_sframe(sales['sqft_living'], 1)
> 
> poly1_data['price'] = sales['price']
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> **6.** Use `turicreate.linear_regression.create` (or another linear regression library) to compute the regression weights for predicting sales[‘price’] based on the 1 degree polynomial feature ‘sqft_living’. The result should be an intercept and slope. e.g if you’re using Turi Create:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> model1 = turicreate.linear_regression.create(poly1_data, target = 'price', 
> 
>   features = ['power_1'], validation_set = None)
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> _If you use `turicreate.linear_regression.create()` to estimate these models please ensure that you set validation_set = None. This way you will get the same answer every time you run the code._
> 
> **7.** Next use the produce a scatter plot of the training data (just square feet vs price) and add the fitted model. e.g. with matplotlib and SFrames:
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
> import matplotlib.pyplot as plt
> 
> %matplotlib inline
> 
> plt.plot(poly1_data['power_1'],poly1_data['price'],'.',
> 
> poly1_data['power_1'], model1.predict(poly1_data),'-')
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> The resulting plot should look like a cloud of points with a straight line passing through.
> 
> **8.** Now that you have plotted the results using a 1st degree polynomial, try it again using a 2nd degree and 3rd degree polynomial. Look at the fitted lines, do they appear as you would expect?
> 
> **9.** Now try a 15th degree polynomial. Print out the coefficients and look at the resulted fitted line. Do you think this degree is appropriate for these data? If we were to use a different subset of the data do you think we would get pretty much the same curve?
> 
> **10.** If you’re using SFrames then create four subsets as follows:
> 
> *   first split sales into 2 subsets with .random_split(.5) use seed = 0!
> *   next split these into 2 more subsets (4 total) using random_split(0.5) again set seed = 0!
> *   you should have 4 subsets of (approximately) equal size, call them set_1, set_2, set_3, and set_4
> 
> If you’re not using SFrames then please download the provided csv files for each subset.
> 
> **11.** Estimate a 15th degree polynomial on all 4 sets, plot the results and view the coefficients for all four models.
> 
> **12\. Quiz Question: Is the sign (positive or negative) for power_15 the same in all four models?**
> 
> **13\. Quiz Question: True/False the plotted fitted lines look the same in all four plots**
> 
> **14.** Since the “best” polynomial degree is unknown to us we will use cross validation to select the best degree. If you’re using SFrames then create a training, validation and testing subsets as follows:
> 
> *   First split sales into training_and_validation and testing with sales.random_split(0.9) use seed = 1!
> *   Next split training_and_validation into training and validation using .random_split(0.5) use seed = 1!
> 
> If you’re not using SFrames then please download the provided csv files for training, validation and test data.
> 
> **15.** Now for each degree from 1 to 15:
> 
> *   Build an polynomial data set using training_data[‘sqft_living’] as the feature and the current degree
> *   Add training_data[‘price’] as a column to your polynomial data set
> *   Learn a model on TRAINING data to predict ‘price’ based on your polynomial data set at the current degree
> *   Compute the RSS on VALIDATION for the current model (print or save the RSS)
> 
> _Hint: in turicreate.linear_regression.create() you can set verbose = False if you want to suppress the interim output of linear_regression.create()._
> 
> **16\. Quiz Question: Which degree (1, 2, …, 15) had the lowest RSS on Validation data?**
> 
> **17.** Now that you have selected a degree compute the RSS on TEST data for the model with the best degree from the Validation data.
> 
> **18\. Quiz Question: what is the RSS on TEST data for the model with the degree selected from Validation data? (Make sure you got the correct degree from the previous question)**
>
> -- https://www.coursera.org/learn/ml-regression/supplement/MhFOa/polynomial-regression#main
