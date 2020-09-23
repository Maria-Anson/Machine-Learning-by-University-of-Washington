## Using LASSO to select features
> 
> * * *
> 
> ## Regression Week 5: LASSO Assignment 1
> 
> In this assignment, you will use LASSO to select features, building on a pre-implemented solver for LASSO (using Turi Create, though you can use other solvers). You will:
> 
> *   Write a function to normalize features
> *   Implement coordinate descent for LASSO
> *   Explore effects of L1 penalty
> 
> In the second assignment, you will implement your own LASSO solver, using coordinate descent.
> 
> ## IMPORTANT: Choice of tools
> 
> **For the purpose of this assessment, you may choose between Turi Create and scikit-learn (with Pandas). You are free to experiment with other tools (e.g. R or Matlab), but they may not produce correct numbers for the quiz questions.**
> 
> *   If you are using Turi Create, download the Jupyter notebook and follow the instructions contained in the notebook.
> *   If you are using Pandas+scikit-learn combination, follow through the instructions in this reading.
> 
> ## What you need to download
> 
> ### If you are using Turi Create:
> 
> *   Download the King County House Sales data In SFrame format:
> 
> [home_data.sframe.zip](https://d3c33hcgiwev3.cloudfront.net/00FsKOIoEemELQpo9cj5Ig_579152614f2b4a399ac90a939360749e_home_data.sframe.zip?Expires=1600992000&Signature=PhJ4WMoAgzuFUnLhRknly6o5uCQikH37VA77P4wvvPV5esYWBN8BIVrpbxRSYbfC~DiK3PR5XHQOkb1vrZD3zvsCmTC-KGQIJezyfxerOxKBib6hqIHmuiS0dh32qtvLT3m1a-GZDJGVgVX5wOK9KFbqon-Yi2KxvdIY4mp8xps_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the companion Jupyter Notebook:
> 
> [REG05-NB01.ipynb.zip](https://d3c33hcgiwev3.cloudfront.net/SR-fUeIvEemnvhJSBz-0XA_d7341e6fd20445b6a97ccd646dfd9ec1_REG05-NB01.ipynb.zip?Expires=1600992000&Signature=Fz1Knw9t6sgBV4~DqAMmrVlOxgEq5PqWMOKqSzs36gIuQd2HdNYwCWQPjawN8Y~Kt6I1GWuQMZAexScjzf2CYIkp4UzEQZkJeb5BA4QTmTk~TCDp~Uxg5snAQdBXx8C57ACxPZjfjTrQJVQ9yPmVpGNNPO-SmPGlyYSddz-UQXU_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Save both of these files in the same directory (where you are calling Jupyter notebook from) and unzip the data file.
> 
> ### If you are using scikit-learn with Pandas:
> 
> *   Download the King County House Sales data csv file:
> 
> [kc_house_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_46994807796a1213d2699c6d9a09667c_kc_house_data.csv.zip?Expires=1600992000&Signature=iM71IUkxP9kjRmuGzfc3Nvqw578QtW3hw8X0~cVrGBkjcu-KiVgGWKcr9A2CBKoGcfpMcQWm7fCCFifFq7pwY0lTJZgAm-tUDdqr2YRxoZkpfQv8~oWyNlI~BcvCF-j1so6KGVVh6BzEFPSWHtSO-sphudd6NOwpW0ljtpEmIoI_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the King County House Sales training data csv file:
> 
> [wk3_kc_house_train_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_f626f6faf3c1039d014563b39ede3037_wk3_kc_house_train_data.csv.zip?Expires=1600992000&Signature=dagupmB2BDbH3u0UpQVBzYYqaxw7tyTRNxJbVumSudLQVLQmoaSGE9nS2aJENC-TDjj8kUbkDvxqT94kH9n1lYSe8-Qgj776KHU7FTVDwA42ZZiK8Fxm5weL6vBHBYvnAzQqxLPhV2ctM7YohvUr66y-zp7kCOpYhSFLaFedMHc_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the King County House Sales validation data csv file:
> 
> [wk3_kc_house_valid_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_f626f6faf3c1039d014563b39ede3037_wk3_kc_house_valid_data.csv.zip?Expires=1600992000&Signature=TrClpJKJ5i7ZqWN4JrG9fIDYkeKqFJqk2CRv~BWZVbvxDj-3vVJLPxhMogZyOtc~dV5Pydt7UrxxFUNs8Mpk6fu7YK8cSIXPuFxzD0q7czCVQkZYqIQyDgfBGOUdzaNg5wBbHCpEEFYPD-T1CxcM1OHQmznetkyUVpQ20ekKHWk_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the King County House Sales testing data csv file:
> 
> [wk3_kc_house_test_data.csv.zip](https://d3c33hcgiwev3.cloudfront.net/_f626f6faf3c1039d014563b39ede3037_wk3_kc_house_test_data.csv.zip?Expires=1600992000&Signature=DV4uW8lIocHTU2oTZhuGJ33TqZRrLhrU7WbiiicpT7KNkQhcnR5fA30aIKFi-8oaQdWGCOKzvgMOeWtS9CH45hLIHBI5V~elWdqEzu0rqSPsw-VoqqDhiOVLtCOdve-PxViBKvngXmFnoiLAjwkRaI74YzEsRFvC4IeqWH3k~iQ_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> ## Useful resources
> 
> You may need to install the software tools described in the reading for Module 1 (Simple Regression).
> 
> If you are following the Jupyter Notebook and/or are new to numpy then you might find the following tutorial helpful:
> 
> [numpy-tutorial-py3.ipynb.zip](https://d3c33hcgiwev3.cloudfront.net/IvpyKP2LEei5Kg7DUflKxA_233c5c80fd8b11e891270765d8b4cf4e_numpy-tutorial-py3.ipynb.zip?Expires=1600992000&Signature=H6NFa1-WVWsahArH1zPQXf3NDgyWJm9vRkL9JGUoKhIcxFIo1o~NkA1cWdk1ECS~Dlm4xGNpXgatsShZASnyfOvr4Mg1vsnTQFaclX6Ggzf9o31wobPSFpt-sNdsD1bW6ETFp50WmEIVW7uKE-mk5pirjcNpoyAOnYP0jkww~Lg_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> ## If you are using Turi Create and the companion Jupyter Notebook
> 
> Open the companion Jupyter notebook and follow the instructions in the notebook.
> 
> ## If you are using scikit-learn with Pandas:
> 
> The instructions may apply to other tools, but the set of parameters are specific to scikit-learn.
> 
> **0**. Load the sales dataset using Pandas:
> 
> <pre contenteditable="false" style="opacity: 1;" tabindex="0">
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
> import pandas as pd
> 
> dtype_dict = {'bathrooms':float, 'waterfront':int, 'sqft_above':int, 
> 
>   'sqft_living15':float, 'grade':int, 'yr_renovated':int, 'price':float, 
> 
>   'bedrooms':float, 'zipcode':str, 'long':float, 'sqft_lot15':float, 
> 
>   'sqft_living':float, 'floors':float, 'condition':int, 'lat':float, 'date':str, 
> 
>   'sqft_basement':int, 'yr_built':int, 'id':str, 'sqft_lot':int, 'view':int}
> 
> sales = pd.read_csv('kc_house_data.csv', dtype=dtype_dict)
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> **1\.** Create new features by performing following transformation on inputs:
> 
> <pre contenteditable="false" style="opacity: 1;" tabindex="0">
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
> from math import log, sqrt
> 
> sales['sqft_living_sqrt'] = sales['sqft_living'].apply(sqrt)
> 
> sales['sqft_lot_sqrt'] = sales['sqft_lot'].apply(sqrt)
> 
> sales['bedrooms_square'] = sales['bedrooms']*sales['bedrooms']
> 
> sales['floors_square'] = sales['floors']*sales['floors']
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> *   Squaring bedrooms will increase the separation between not many bedrooms (e.g. 1) and lots of bedrooms (e.g. 4) since 1^2 = 1 but 4^2 = 16\. Consequently this variable will mostly affect houses with many bedrooms.
> *   On the other hand, taking square root of sqft_living will decrease the separation between big house and small house. The owner may not be exactly twice as happy for getting a house that is twice as big.
> 
> **2\.** Using the entire house dataset, learn regression weights using an L1 penalty of 5e2\. Make sure to add "normalize=True" when creating the Lasso object. Refer to the following code snippet for the list of features.
> 
> **Note.** From here on, the list 'all_features' refers to the list defined in this snippet.
> 
> <pre contenteditable="false" style="opacity: 1;" tabindex="0">
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
> from sklearn import linear_model  # using scikit-learn
> 
> all_features = ['bedrooms', 'bedrooms_square',
> 
>             'bathrooms',
> 
>             'sqft_living', 'sqft_living_sqrt',
> 
>             'sqft_lot', 'sqft_lot_sqrt',
> 
>             'floors', 'floors_square',
> 
>             'waterfront', 'view', 'condition', 'grade',
> 
>             'sqft_above',
> 
>             'sqft_basement',
> 
>             'yr_built', 'yr_renovated']
> 
> model_all = linear_model.Lasso(alpha=5e2, normalize=True) # set parameters
> 
> model_all.fit(sales[all_features], sales['price']) # learn weights
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> **3\. Quiz Question: Which features have been chosen by LASSO, i.e. which features were assigned nonzero weights?**
> 
> **4\.** To find a good L1 penalty, we will explore multiple values using a validation set. Let us do three way split into train, validation, and test sets. Download the provided csv files containing training, validation and test sets.
> 
> <pre contenteditable="false" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2
> 
> 3
> 
> testing = pd.read_csv('wk3_kc_house_test_data.csv', dtype=dtype_dict)
> 
> training = pd.read_csv('wk3_kc_house_train_data.csv', dtype=dtype_dict)
> 
> validation = pd.read_csv('wk3_kc_house_valid_data.csv', dtype=dtype_dict)
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> Make sure to create the 4 features as we did in #1:
> 
> <pre contenteditable="false" style="opacity: 1;" tabindex="0">
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
> testing['sqft_living_sqrt'] = testing['sqft_living'].apply(sqrt)
> 
> testing['sqft_lot_sqrt'] = testing['sqft_lot'].apply(sqrt)
> 
> testing['bedrooms_square'] = testing['bedrooms']*testing['bedrooms']
> 
> testing['floors_square'] = testing['floors']*testing['floors']
> 
> training['sqft_living_sqrt'] = training['sqft_living'].apply(sqrt)
> 
> training['sqft_lot_sqrt'] = training['sqft_lot'].apply(sqrt)
> 
> training['bedrooms_square'] = training['bedrooms']*training['bedrooms']
> 
> training['floors_square'] = training['floors']*training['floors']
> 
> validation['sqft_living_sqrt'] = validation['sqft_living'].apply(sqrt)
> 
> validation['sqft_lot_sqrt'] = validation['sqft_lot'].apply(sqrt)
> 
> validation['bedrooms_square'] = validation['bedrooms']*validation['bedrooms']
> 
> validation['floors_square'] = validation['floors']*validation['floors']
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> **5\.** Now for each l1_penalty in [10^1, 10^1.5, 10^2, 10^2.5, ..., 10^7] (to get this in Python, type np.logspace(1, 7, num=13).)
> 
> *   Learn a model on TRAINING data using the specified l1_penalty. Make sure to specify normalize=True in the constructor:
> 
> <pre contenteditable="false" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> model = linear_model.Lasso(alpha=l1_penalty, normalize=True)
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> *   Compute the RSS on VALIDATION for the current model (print or save the RSS)
> 
> Report which L1 penalty produced the lower RSS on VALIDATION.
> 
> **6\. Quiz Question: Which was the best value for the l1_penalty, i.e. which value of l1_penalty produced the lowest RSS on VALIDATION data?**
> 
> 7\. Now that you have selected an L1 penalty, compute the RSS on TEST data for the model with the best L1 penalty.
> 
> **8\. Quiz Question: Using the best L1 penalty, how many nonzero weights do you have? Count the number of nonzero coefficients first, and add 1 if the intercept is also nonzero.** A succinct way to do this is
> 
> <pre contenteditable="false" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2
> 
> np.count_nonzero(model.coef_) + np.count_nonzero(model.intercept_)
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> where 'model' is an instance of linear_model.Lasso.
> 
> **9\.** What if we absolutely wanted to limit ourselves to, say, 7 features? This may be important if we want to derive "a rule of thumb" --- an interpretable model that has only a few features in them.
> 
> You are going to implement a simple, two phase procedure to achieve this goal:
> 
> *   Explore a large range of ‘l1_penalty’ values to find a narrow region of ‘l1_penalty’ values where models are likely to have the desired number of non-zero weights.
> *   Further explore the narrow region you found to find a good value for ‘l1_penalty’ that achieves the desired sparsity. Here, we will again use a validation set to choose the best value for ‘l1_penalty’.
> 
> **10\.** Assign 7 to the variable ‘max_nonzeros’.
> 
> **11\.** Exploring large range of l1_penalty
> 
> For l1_penalty in np.logspace(1, 4, num=20):
> 
> *   Fit a regression model with a given l1_penalty on TRAIN data. Add "alpha=l1_penalty" and "normalize=True" to the parameter list.
> 
> <pre contenteditable="false" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> model = linear_model.Lasso(alpha=l1_penalty, normalize=True)
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> *   Extract the weights of the model and count the number of nonzeros. Take account of the intercept as we did in #8, adding 1 whenever the intercept is nonzero. Save the number of nonzeros to a list.
> 
> **12\.** Out of this large range, we want to find the two ends of our desired narrow range of l1_penalty. At one end, we will have l1_penalty values that have too few non-zeros, and at the other end, we will have an l1_penalty that has too many non-zeros.
> 
> More formally, find:
> 
> *   The largest l1_penalty that has more non-zeros than ‘max_nonzeros’ (if we pick a penalty smaller than this value, we will definitely have too many non-zero weights)Store this value in the variable ‘l1_penalty_min’ (we will use it later)
> *   The smallest l1_penalty that has fewer non-zeros than ‘max_nonzeros’ (if we pick a penalty larger than this value, we will definitely have too few non-zero weights)Store this value in the variable ‘l1_penalty_max’ (we will use it later)
> 
> Hint: there are many ways to do this, e.g.:
> 
> *   Programmatically within the loop above
> *   Creating a list with the number of non-zeros for each value of l1_penalty and inspecting it to find the appropriate boundaries.
> 
> **13\. Quiz Question: What values did you find for l1_penalty_min and l1_penalty_max?**
> 
> **14\.** Exploring narrower range of l1_penalty
> 
> We now explore the region of l1_penalty we found: between ‘l1_penalty_min’ and ‘l1_penalty_max’. We look for the L1 penalty in this range that produces exactly the right number of nonzeros and also minimizes RSS on the VALIDATION set.
> 
> For l1_penalty in np.linspace(l1_penalty_min,l1_penalty_max,20):
> 
> *   Fit a regression model with a given l1_penalty on TRAIN data. As before, use "alpha=l1_penalty" and "normalize=True".
> *   Measure the RSS of the learned model on the VALIDATION set
> 
> Find the model that the lowest RSS on the VALIDATION set and has sparsity equal to ‘max_nonzeros’. (Again, take account of the intercept when counting the number of nonzeros.)
> 
> **15\. Quiz Question: What value of l1_penalty in our narrow range has the lowest RSS on the VALIDATION set and has sparsity equal to ‘max_nonzeros’?**
> 
> **16\. Quiz Question: What features in this model have non-zero coefficients?**
>
> -- https://www.coursera.org/learn/ml-regression/supplement/qsV5O/using-lasso-to-select-features#main
