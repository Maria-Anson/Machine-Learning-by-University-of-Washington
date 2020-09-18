## Exploring different multiple regression models for house price prediction
> 
> * * *
> 
> ## Regression Week 2: Multiple Linear Regression Assignment 1
> 
> Predicting House Prices (Multiple Variables)
> 
> In this notebook you will use data on house sales in King County to predict prices using multiple regression. The first assignment will be about exploring multiple regression in particular exploring the impact of adding features to a regression and measuring error. In the second assignment you will implement a gradient descent algorithm. In this assignment you will:
> 
> *   Use SFrames to do some feature engineering
> *   Use built-in Turi Create (or otherwise) functions to compute the regression weights (coefficients)
> *   Given the regression weights, predictors and outcome write a function to compute the Residual Sum of Squares
> *   Look at coefficients and interpret their meanings
> *   Evaluate multiple models via RSS
> 
> ## If you are doing the assignment with Jupyter Notebook
> 
> An Jupyter Notebook has been provided below to you for this assignment. This notebook contains the instructions, quiz questions and partially-completed code for you to use as well as some cells to test your code.
> 
> ## What you need to download
> 
> ### If you are using Turi Create:
> 
> *   Download the King County House Sales data In SFrame format:
> 
> [home_data.sframe.zip](https://d3c33hcgiwev3.cloudfront.net/00FsKOIoEemELQpo9cj5Ig_579152614f2b4a399ac90a939360749e_home_data.sframe.zip?Expires=1600560000&Signature=YCtUXbI0gjV8wfPP8J3TS7jOF~1~w46kULdZppatY8CSLQmVChyEkYhT~8VP3Lkc5bYvJCBIUezgGwOWVji3TTKIpHO3xCtU-b0tZtREzYq6fscwcLjw73E1nNnBwKli7o-98KUVqwNYbfSz465YOIEY950meaFk3q3l~FEojAM_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the companion Jupyter Notebook:
> 
> [REG02-NB01.ipynb.zip](https://d3c33hcgiwev3.cloudfront.net/qzJWO-IpEemx8A5HK6Ls8g_e3ace897972f4d0e870c765241ca0804_REG02-NB01.ipynb.zip?Expires=1600560000&Signature=TTALNNCcyL7snMZdnGFB~rKSQyh-Yc~EXqUM9TJG7WNDuQlAQ0tp1eNBinpBCfPVoBscRb6p18LSQt3aX9etl2-SF5XDLtvDtpfXxE9~8dyTRQysyKUZh7A7eV-sC~Vz42KNPlW0web45R5gmZqpNHgLTO80ynftpgLzWkeCQtk_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Save both of these files in the same directory (where you are calling Jupyter notebook from) and unzip the data file.
> 
> ### If you are not using Turi Create:
> 
> *   Download the King County House Sales data csv file:
> 
> [kc_house_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_46994807796a1213d2699c6d9a09667c_kc_house_data.csv.zip?Expires=1600560000&Signature=J7goqwM6YWLj-mMsQ-agrGHPFbfwvWY8vlYq5LOKF7CSPFs6iwZ5loZDdIoxGhRhZTgy-lwlYUeRqmosHGFyQKTXp8nWAZvU40gPQrRSA0f4uA804pPBzHg2IVWevKlfpUspqtY735ScsjJS-Z55j5rOz66nuKFWsl1iopJfv40_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the King County House Sales training data csv file:
> 
> [kc_house_train_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_46994807796a1213d2699c6d9a09667c_kc_house_train_data.csv.zip?Expires=1600560000&Signature=LR9~NkG6PTKZASV~2Q913IgnFmy7Zwn~w47Fqpb-wX4f5c~4hYw7PB0qIEafBTtkwbMljGbTAtPsu537r~klA1ko2-P6S5UUfIUvzuDQNuDNTxmIAZEcOKhGXC4Wqaft4CEhodblHRE0EWQ8fnjlnS3Tn8Tr3QSxzxeSoo8hdqo_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the King County House Sales testing data csv file:
> 
> [kc_house_test_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_46994807796a1213d2699c6d9a09667c_kc_house_test_data.csv.zip?Expires=1600560000&Signature=dSKb4~d6DkbXAFBzCZ3xc3t8eLHR3uCWxGYqX~9GyYIJ7K9t6oYUfWxj9i1E9MBO6D6HmspkU5KRZmbJlk2i2MDmbuN1eqbjCf9rvGWRMcB6m9gV74evg-PbuvrZK-qbfWyGmi69m5MDITcT1-T8758-N6c-Xmp6MKZesWL1TqE_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
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
> ## If instead you are using other tools to do your homework
> 
> You are welcome, however, to write your own code and use any other libraries, like Pandas or R, to help you in the process. If you would like to take this path, follow the instructions below.
> 
> **1.** If you are using SFrame, import turicreate and load in the house data, otherwise you can also download the csv. (Note that we will be using the training and testing csv files provided) e.g in python with SFrames:
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
> **2.** Split into training and test data Use this command to set the same seed for everyone: e.g. in python with SFrames:
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
> For those students not using SFrames please download the training and testing data csv files.
> 
> From now on we will train the models using train_data. It will be important that we use the same split here to ensure the results are the same.
> 
> **3.** Although we often think of multiple regression as including multiple different features (e.g. # of bedrooms, square feet, and # of bathrooms) but we can also consider transformations of existing variables e.g. the log of the square feet or even "interaction" variables such as the product of bedrooms and bathrooms. Add 4 new variables in both your train_data and test_data.
> 
> *   ‘bedrooms_squared’ = ‘bedrooms’*‘bedrooms’
> *   ‘bed_bath_rooms’ = ‘bedrooms’*‘bathrooms’
> *   ‘log_sqft_living’ = log(‘sqft_living’)
> *   ‘lat_plus_long’ = ‘lat’ + ‘long’
> 
> Before we continue let’s explain these new variables:
> 
> *   Squaring bedrooms will increase the separation between not many bedrooms (e.g. 1) and lots of bedrooms (e.g. 4) since 1^2 = 1 but 4^2 = 16\. Consequently this variable will mostly affect houses with many bedrooms.
> *   Bedrooms times bathrooms is what's called an "interaction" variable. It is large when both of them are large.
> *   Taking the log of square feet has the effect of bringing large values closer together and spreading out small values.
> *   Adding latitude to longitude is non-sensical but we will do it anyway (you'll see why)
> 
> For those students not using SFrames you should first download and import the training and testing data sets provided and then add the four new variables each to both data sets (training and testing)
> 
> **4\. Quiz Question: what are the mean (arithmetic average) values of your 4 new variables on TEST data? (round to 2 digits)**
> 
> **5.** Use `turicreate.linear_regression.create()` (or any other regression library/function) to estimate the regression coefficients/weights for predicting ‘price’ for the following three models:(In all 3 models include an intercept -- most software does this by default).
> 
> *   Model 1: ‘sqft_living’, ‘bedrooms’, ‘bathrooms’, ‘lat’, and ‘long’
> *   Model 2: ‘sqft_living’, ‘bedrooms’, ‘bathrooms’, ‘lat’,‘long’, and ‘bed_bath_rooms’
> *   Model 3: ‘sqft_living’, ‘bedrooms’, ‘bathrooms’, ‘lat’,‘long’, ‘bed_bath_rooms’, ‘bedrooms_squared’, ‘log_sqft_living’, and ‘lat_plus_long’
> 
> You’ll note that the three models here are “nested” in that all of the features of the Model 1 are in Model 2 and all of the features of Model 2 are in Model 3\.
> 
> _If you use `turicreate.linear_regression.create()` to estimate these models please ensure that you set validation_set = None. This way you will get the same answer every time you run the code._
> 
> _Learn all three models on the TRAINING data set. Save your model results for quiz questions later._
> 
> **6\. Quiz Question: What is the sign (positive or negative) for the coefficient/weight for ‘bathrooms’ in Model 1?**
> 
> **7\. Quiz Question: What is the sign (positive or negative) for the coefficient/weight for ‘bathrooms’ in Model 2?**
> 
> **8\.** Is the sign for the coefficient the same in both models? Think about why this might be the case.
> 
> **9\.** Now using your three estimated models compute the RSS (Residual Sum of Squares) on the Training data.
> 
> **10\. Quiz Question: Which model (1, 2 or 3) had the lowest RSS on TRAINING data?**
> 
> **11.** Now using your three estimated models compute the RSS on the Testing data
> 
> **12\. Quiz Question: Which model (1, 2, or 3) had the lowest RSS on TESTING data?**
> 
> **13.** Did you get the same answer for 9 and 11? Think about why this might be the case.
>
> -- https://www.coursera.org/learn/ml-regression/supplement/7xN9c/exploring-different-multiple-regression-models-for-house-price-prediction#main
