# Analyzing product sentiment
> 
> Total points 11
> 
>  1.Question 1
> 
> ### Out of the 11 words in _selected_words_, which one is most used in the reviews in the dataset?
> 
> 1 point 
> 
>  **awesome** 
> 
>  **love** 
> 
>  **hate** 
> 
>  **bad** 
> 

      **great** 
> 
>  2.Question 2
> 
> ### Out of the 11 words in _selected_words_, which one is least used in the reviews in the dataset?
> 
> 1 point 
> 

      **wow** 
> 
>  **amazing** 
> 
>  **terrible** 
> 
>  **awful** 
> 
>  **love** 
> 
>  3.Question 3
> 
> ### Out of the 11 words in _selected_words_, which one got the most positive weight in the _selected_words_model_?
> 
> ### (Tip: when printing the list of coefficients, make sure to use print_rows(rows=12) to print ALL coefficients.)
> 
> 1 point 
> 
>  **amazing** 
> 
>  **awesome** 
> 

      **love** 
> 
>  **fantastic** 
> 
>  **terrible** 
> 
>  4.Question 4
> 
> ### Out of the 11 words in _selected_words_, which one got the most negative weight in the _selected_words_model_?
> 
> ### (Tip: when printing the list of coefficients, make sure to use print_rows(rows=12) to print ALL coefficients.)
> 
> 1 point 
> 

      **horrible** 
> 
>  **terrible** 
> 
>  **awful** 
> 
>  **hate** 
> 
>  **love** 
> 
>  5.Question 5
> 
> ### Which of the following ranges contains the accuracy of the _selected_words_model_ on the _test_data_?
> 
> 1 point 
> 
>  **0.811 to 0.841** 
> 

      **0.841 to 0.871** 
> 
>  **0.871 to 0.901** 
> 
>  **0.901 to 0.931** 
> 
>  6.Question 6
> 
> ### Which of the following ranges contains the accuracy of the _sentiment_model_ in the IPython Notebook from lecture on the _test_data_?
> 
> 1 point 
> 
>  **0.811 to 0.841** 
> 
>  **0.841 to 0.871** 
> 
>  **0.871 to 0.901** 
> 

      **0.901 to 0.931** 
> 
>  7.Question 7
> 
> ### Which of the following ranges contains the accuracy of the majority class classifier, which simply predicts the majority class on the _test_data__?_
> 
> 1 point 
> 

      **0.811 to 0.843** 
> 
>  **0.843 to 0.871** 
> 
>  **0.871 to 0.901** 
> 
>  **0.901 to 0.931** 
> 
>  8.Question 8
> 
> ### How do you compare the different learned models with the baseline approach where we are just predicting the majority class?
> 
> 1 point 
> 
>  **They all performed about the same.** 
> 
>  **The model learned using all words performed _much better_ than the one using the only the _selected_words_. And, the model learned using the _selected_words_ performed much better than just predicting the majority class.** 
> 

      **The model learned using all words performed much better than the other two. The other two approaches performed about the same.** 
> 
>  **Predicting the simply majority class performed much better than the other two models.** 
> 
>  9.Question 9
> 
> ### Which of the following ranges contains the _‘predicted_sentiment’_ for the most positive review for _‘Baby Trend Diaper Champ’,_ according to the _sentiment_model_ from the IPython Notebook from lecture?
> 
> 1 point 
> 
>  **Below 0.7** 
> 
>  **0.7 to 0.8** 
> 
>  **0.8 to 0.9** 
> 
>  **0.9 to 1.0** 
> 
>  10.Question 10
> 
> ### Consider the most positive review for _‘Baby Trend Diaper Champ’_ according to the _sentiment_model_ from the IPython Notebook from lecture. Which of the following ranges contains the predicted_sentiment for this review, if we use the _selected_words_model_ to analyze it?
> 
> 1 point 
> 
>  **Below 0.7** 
> 
>  **0.7 to 0.8** 
> 
>  **0.8 to 0.9** 
> 

      **0.9 to 1.0** 
> 
>  11.Question 11
> 
> ### Why is the value of the _predicted_sentiment_ for the most positive review found using the _sentiment_model_ much more positive than the value predicted using the _selected_words_model_?
> 
> 1 point 
> 
>  **The _sentiment_model_ is just too positive about everything.** 
> 
>  **The _selected_words_model_ is just too negative about everything.** 
> 
>  **This review was positive, but used too many of the negative words in _selected_words_.** 
> 

      **None of the _selected_words_ appeared in the text of this review.**
>
> -- https://www.coursera.org/learn/ml-foundations/exam/lmpum/analyzing-product-sentiment/attempt#Tunnel Vision Close
