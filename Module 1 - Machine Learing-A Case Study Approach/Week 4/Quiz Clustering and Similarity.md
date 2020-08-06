# Clustering and Similarity
> 
> Total points 6
> 
>  1.Question 1
> 
> ### A country, called _Simpleland_, has a language with a small vocabulary of just _“the”_, _“on”_, _“and”_, _“go”_, _“round”_, _“bus”_, and _“wheels”_. For a word count vector with indices ordered as the words appear above, what is the word count vector for a document that simply says _“the wheels on the bus go round and round.”_
> 
> ### Please enter the vector of counts as follows: If the counts were [_"the"_=1, _“on”_=3, _"and"_=2, _"go"=_1, _"round"=_2, "_bus"=_1, "_wheels"=_1], enter 1321211.
> 

    2111211
> 1 point 
> 
>  2.Question 2
> 
> ### In _Simpleland_, a reader is enjoying a document with a representation: [1 3 2 1 2 1 1]. Which of the following articles would you recommend to this reader next?
> 
> 1 point 
> 
>  **[7 0 2 1 0 0 1]** 
> 

    **[1 7 0 0 2 0 1]** 
> 
>  **[1 0 0 0 7 1 2]** 
> 
>  **[0 2 0 0 7 1 1]** 
> 
>  3.Question 3
> 
> ### A corpus in _Simpleland_ has 99 articles. If you pick one article and perform **1-nearest neighbor search** to find the closest article to this query article, how many times must you compute the similarity between two articles?
> 
> 1 point 
> 

      **98** 
> 
>  **98*2 = 196** 
> 
>  **98/2 = 49** 
> 
>  **(98)^2** 
> 
>  **99** 
> 
>  4.Question 4
> 
> ### For the TF-IDF representation, does the relative importance of words in a document depend on the base of the logarithm used? For example, take the words "_bus_" and "_wheels_" in a particular document. Is the ratio between the TF-IDF values for "_bus_" and "_wheels_" different when computed using log base 2 versus log base 10?
> 
> 1 point 
> 
>  Yes 
> 

    No 
> 
>  5.Question 5
> 
> ### Which of the following statements are **true?** (_Check all that apply_):
> 
> 1 point 
> 

      **Deciding whether an email is _spam_ or _not spam_ using the text of the email and some _spam_ / _not spam_ labels is a supervised learning problem.** 
> 
>  **Dividing emails into two groups based on the text of each email is a supervised learning problem.** 
> 

      **If we are performing clustering, we typically assume we either do not have or do not use class labels in training the model.** 
> 
>  6.Question 6
> 
> ### Which of the following pictures represents the **_best_** k-means solution? (_Squares represent observations, plus signs are cluster centers, and colors indicate assignments of observations to cluster centers_.)
> 
> 1 point 
> 
>  ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/7xfZwlvUEeWhtQ48PjS6Pw_dc04a86c61327011232ba029923cc6a5_Clust5a.png?expiry=1595548800000&hmac=JX8G5FZiRxPceyiKPlpkxhjmxVvOZmFspvwDlGUw8Vs) 
> 
>  ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/AW6FxVvVEeWzLwrzeFOkAw_3e7caa843845e525f9275753265c0900_Clust5b.png?expiry=1595548800000&hmac=01nRIQQX5aZ-vkPBKDLECLAg0nySm6c49QflsxGD-Ak) 
> 
>  ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/DgUts1vVEeWhtQ48PjS6Pw_42c5de5cdd81069ab89feb8ab852f8c3_Clust5c.png?expiry=1595548800000&hmac=jfbZciIKDYwg7aUui0mE1Lc6m4swrsg0GQwzscwGao0)
>

    2
> -- https://www.coursera.org/learn/ml-foundations/exam/ubkwg/clustering-and-similarity/attempt#Tunnel Vision Close
