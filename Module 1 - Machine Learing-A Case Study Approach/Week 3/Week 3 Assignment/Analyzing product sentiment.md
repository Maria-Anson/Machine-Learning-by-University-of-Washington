# Analyzing product sentiment
> 
> In this module, we focused on classifiers, applying them to analyzing product sentiment, and understanding the types of errors a classifier makes. We also built an exciting Jupyter notebook for analyzing the sentiment of real product reviews.
> 
> In this assignment, we are going to explore this application further, training a sentiment analysis model using a set of key polarizing words, verify the weights learned to each of these words, and compare the results of this simpler classifier with those of the one using all of the words. These techniques will be a core component in your capstone project.
> 
> Follow the rest of the instructions on this page to complete your program. When you are done, _**instead of uploading your code, you will answer a series of quiz questions**_ (see the quiz after this reading) to document your completion of this assignment. The instructions will indicate what data to collect for answering the quiz.
> 
> ### Learning outcomes
> 
> *   Execute sentiment analysis code with the Jupyter notebook
> *   Load and transform real, text data
> *   Using the _.apply()_ function to create new columns (features) for our model
> *   Compare results of two models, one using all words and the other using a subset of the words
> *   Compare learned models with majority class prediction
> *   Examine the predictions of a sentiment model
> *   Build a sentiment analysis model using a classifier
> 
> ### **Resources you will need**
> 
> You will need to install the software tools described in the Module 1 reading. Instructions are provided [here](https://www.coursera.org/learn/ml-foundations/item/5HQGl).
> 
> ### Download the data and starter code
> 
> Before getting started, you will need to download the dataset and the starter Jupyter notebook that we used in the module.
> 
> *   Download the product review dataset here in SFrame format:
> 
> [amazon_baby.sframe.zip](https://d3c33hcgiwev3.cloudfront.net/y4OKQuIFEemJfgqR2HI2sA_43be9d356abf4561888105f8045995bf_amazon_baby.sframe.zip?Expires=1594339200&Signature=jEe4LPYrIKCC76gpg0E3xqmoh23~~K20uCswGQP0Db9l4RYyEhBpvatVRk2u4UI0KRuHnyZmaUZ1HnHepOuDWfCDys9vyXcKO-E4xwBI~KiuG3wIYleOqZK92mhPCcxEf7dkZlYeg6315O1Vp2YUOV-bncmqyw9dXEzItsCp2QQ_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Download the sentiment analysis notebook from the module here:
> 
> [FND03-NB01.ipynb.zip](https://d3c33hcgiwev3.cloudfront.net/SzUXweJcEemm5A4ynZyB2A_bd10e156b580492aa1f9f8a56521b169_FND03-NB01.ipynb.zip?Expires=1594339200&Signature=J6FzF31rsIcZC8PJALX8Vfe3zl3oIW-6k7H1UKghdruqD1PNy8-ENvoHVJB9hlecwg7Ru1iVUnRsh6Lxjb7mDpLT1DFMnmQfPB8UkrwRnIvf2JFJvLNt1R1tBKIVSrPCyDfhL8qKHq59pl~LOAPtK1oJw3F~kByZVjt3LFw~XyE_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
> 
> *   Save both of these files in the same directory (where you are calling Jupyter notebook from) and unzip the data file. **Not sure where to save the files? See** [**this guide**](https://www.coursera.org/learn/ml-foundations/supplement/kRD6B/where-should-my-files-go)**.**
> 
> Now you are ready to get started!
> 
> ### _**Note: If you would rather use other ML tools...**_
> 
> You are welcome to use any ML tool for this course, such as [scikit-learn](http://scikit-learn.org/stable/). Though, as discussed in the intro module, _we strongly recommend you use Jupyter Notebook and Turi Create. (Turi Create is free and open source.)_
> 
> If you are choosing to use other packages, we still recommend you use SFrame, which will allow you to scale to much larger datasets than Pandas. (Though, it's possible to use Pandas in this course, if your machine has sufficient memory.) The SFrame package is available in [open-source under a permissive BSD license](https://github.com/turi-code/SFrame). So, you will always be able to use SFrames for free.
> 
> If you are not using SFrame, here is the dataset for this assignment in CSV format, so you can use [Pandas](http://pandas.pydata.org/) or other options out there: [amazon_baby.csv](https://d396qusza40orc.cloudfront.net/phoenixassets/amazon_baby.csv)
> 
> ### Watch the video and explore the Jupyter notebook on analyzing sentiment
> 
> If you haven’t done so yet, before you start, we recommend you watch the video where we go over the Jupyter notebook on analyzing product sentiment using classifiers from this module. You can then open up the Jupyter notebook we used and familiarize yourself with the steps we covered in this example.
> 
> ### What you will do
> 
> Now you are ready! We are going do four tasks in this assignment. There are several results you need to gather along the way to enter into the quiz after this reading.
> 
> In the Jupyter notebook above, we used the word counts for all words in the reviews to train the sentiment classifier model. Now, we are going to follow a similar path, but only use this subset of the words:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> selected_words = ['awesome', 'great', 'fantastic', 'amazing', 'love', 'horrible'
> 
>   , 'bad', 'terrible', 'awful', 'wow', 'hate']
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> Often, ML practitioners will throw out words they consider “unimportant” before training their model. This procedure can often be helpful in terms of accuracy. Here, we are going to throw out all words except for the very few above. Using so few words in our model will hurt our accuracy, but help us interpret what our classifier is doing.
> 
> 1.  **Use .apply() to build a new feature with the counts for each of the selected_words:** In the notebook above, we created a column ‘word_count’ with the word counts for each review. Our first task is to create a new column in the products SFrame with the counts for each selected_word above, and, in the process, we will see how the method .apply() can be used to create new columns in our data (our features) and how to use a Python function, which is an extremely useful concept to grasp!
> 
> Our first goal is to create a column _products[‘awesome’]_ where each row contains the number of times the word _‘awesome’_ showed up in the review for the corresponding product, and 0 if the review didn’t show up. One way to do this is to look at the each row _‘word_count’_ column and follow this logic:
> 
> *   If _‘awesome’_ shows up in the word counts for a particular product (row of the products SFrame), then we know how often _‘awesome’_ appeared in the review,
> 
> *   if _‘awesome’_ doesn’t appear in the word counts, then it didn’t appear in the review, and we should set the count for _‘awesome’_ to 0 in this review.
> 
> We could use a for loop to iterate this logic for each row of the products SFrame, but this approach would be really slow, because the SFrame is not optimized for this being accessed with a for loop. Instead, we will use the _.apply()_ method to iterate the the logic above for each row of the _products[‘word_count’]_ column (which, since it’s a single column, has type SArray). [Read about using the .apply() method on an SArray here.](https://apple.github.io/turicreate/docs/api/generated/turicreate.SArray.apply.html?highlight=apply#turicreate.SArray.apply)
> 
> We are now ready to create our new columns:
> 
> *   First, you will use a Python function to define the logic above. You will write a function called _awesome_count_ which takes in the word counts and returns the number of times _‘awesome’_ appears in the reviews.
> 
> A few tips:
> 
> i. Each entry of the ‘word_count’ column is of [Python type dictionary](https://docs.python.org/3/tutorial/datastructures.html#dictionaries).
> 
> ii. If you have a dictionary called _dict_, you can access a field in the dictionary using:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> dict['awesome']
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> but only if _‘awesome’_ is one of the fields in the dictionary, otherwise you will get a nasty error.
> 
> iii. In Python, to test if a dictionary has a particular field, you can simply write:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> if 'awesome' in dict
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> In our case, if this condition doesn’t hold, the count of _‘awesome’_ should be 0.
> 
> Using these tips, you can now write the awesome_count function.
> 
> *   Next, you will use _.apply()_ to iterate _awesome_count_ for each row of _products[‘word_count’]_ and create a new column called _‘awesome’_ with the resulting counts. Here is what that looks like:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> products['awesome'] = products['word_count'].apply(awesome_count)
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> And you are done! Check the _products_ SFrame and you should see the new column you just create.
> 
> *   Repeat this process for the other 11 words in _selected_words_. (Here, we described a simple procedure to obtain the counts for each _selected_word_. There are other more efficient ways of doing this, and we encourage you to explore this further.)
> *   Using the _.sum()_ method on each of the new columns you created, answer the following questions: Out of the _selected_words_, which one is most used in the dataset? Which one is least used? _**Save these results to answer the quiz at the end.**_
> 
> 2\. **Create a new sentiment analysis model using only the selected_words as features:** In the Jupyter Notebook above, we used word counts for all words as features for our sentiment classifier. Now, you are just going to use the _selected_words_:
> 
> *   Use the same train/test split as in the Jupyter Notebook from lecture:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> train_data,test_data = products.random_split(.8, seed=0)
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> *   Train a logistic regression classifier (use _turicreate.logistic_classifier.create_) using just the _selected_words_. Hint: you can use this parameter in the _.create()_ call to specify the features used to be exactly the new columns you just created:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> features=selected_words
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> Call your new model: _selected_words_model_.
> 
> *   You will now examine the weights the learned classifier assigned to each of the 11 words in _selected_words_ and gain intuition as to what the ML algorithm did for your data using these features. In Turi Create, a learned model, such as the selected_words_model, has a field 'coefficients', which lets you look at the learned coefficients. You can access it by using:
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> selected_words_model['coefficients']
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> The result has a column called ‘value’, which contains the weight learned for each feature.
> 
> Using this approach, sort the learned coefficients according to the ‘value’ column using _.sort()_. Out of the 11 words in _selected_words_, which one got the most positive weight? Which one got the most negative weight? Do these values make sense for you? **_Save these results to answer the quiz at the end._**
> 
> 3\. **Comparing the accuracy of different sentiment analysis model:** Using the method
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> .evaluate(test_data)
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> What is the accuracy of the _selected_words_model_ on the _test_data_? What was the accuracy of the _sentiment_model_ that we learned using all the word counts in the Jupyter Notebook above from the lectures? What is the accuracy _majority_ class classifier on this task? How do you compare the different learned models with the baseline approach where we are just predicting the majority class? _**Save these results to answer the quiz at the end.**_
> 
> _Hint: we discussed the majority class classifier in lecture, which simply predicts that every data point is from the most common class. This is baseline is something we definitely want to beat with models we learn from data._
> 
> 4\. **Interpreting the difference in performance between the models:** To understand why the model with all word counts performs better than the one with only the _selected_words_, we will now examine the reviews for a particular product.
> 
> *   We will investigate a product named _‘Baby Trend Diaper Champ’_. (This is a trash can for soiled baby diapers, which keeps the smell contained.)
> *   Just like we did for the reviews for the giraffe toy in the Jupyter Notebook in the lecture video, before we start our analysis you should select all reviews where the product name is _‘Baby Trend Diaper Champ’_. Let’s call this table _diaper_champ_reviews_.
> *   Again, just as in the video, use the _sentiment_model_ to predict the sentiment of each review in _diaper_champ_reviews_ and sort the results according to their _‘predicted_sentiment’_.
> *   What is the _‘predicted_sentiment’_ for the most positive review for _‘Baby Trend Diaper Champ’_ according to the sentiment_model from the Jupyter Notebook from lecture? _**Save this result to answer the quiz at the end.**_
> *   Now use the _selected_words_model_ you learned using just the _selected_words_ to predict the sentiment most positive review you found above. _Hint: if you sorted the diaper_champ_reviews in descending order (from most positive to most negative), this command will be helpful to make the prediction you need:_
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> selected_words_model.predict(diaper_champ_reviews[0:1], output_type
> 
>   ='probability')
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> _**Save this result to answer the quiz at the end.**_
> 
> *   Why is the _predicted_sentiment_ for the most positive review found using the model with all word counts (_sentiment_model_) much more positive than the one using only the _selected_words (selected_words_model)_? _Hint: examine the text of this review, the extracted word counts for all words, and the word counts for each of the selected_words, and you will see what each model used to make its prediction.__**Save this result to answer the quiz at the end.**_
>
> -- https://www.coursera.org/learn/ml-foundations/supplement/phb1M/analyzing-product-sentiment-assignment#main
