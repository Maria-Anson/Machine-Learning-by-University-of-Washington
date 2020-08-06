# Retrieving Wikipedia articles



In this module, we focused on using nearest neighbors and clustering to retrieve
documents that interest users, by analyzing their text.  We explored two
document representations: word counts and TF-IDF.  We also built an Jupyter
notebook for retrieving articles from Wikipedia about famous people.

In this assignment, we are going to dig deeper into this application, explore
the retrieval results for various famous people, and familiarize ourselves with
the code needed to build a retrieval system.  These techniques will be key to
building the intelligent application in your capstone project. 

Follow the rest of the instructions on this page to complete your program. When
you are done, **instead of uploading your code, you will answer a series of quiz
questions** (see the quiz after this reading) to document your completion of
this assignment. The instructions will indicate what data to collect for
answering the quiz.

### **Learning outcomes**

* Execute document retrieval code with the Jupyter notebook
* Load and transform real, text data
* Compare results with word counts and TF-IDF
* Set the distance function in the retrieval
* Build a document retrieval model using nearest neighbor search



### **Resources you will need**

You will need to install the software tools described in the Module 1 reading.
Instructions are provided
[here](https://www.coursera.org/learn/ml-foundations/item/5HQGl).

### Download the data and starter code

Before getting started, you will need to download the dataset and the starter
Jupyter notebook that we used in the module.

 *   Download the wikipedia dataset with articles on famous people here in SFrame format:
 
 [people_wiki.sframe.zip](https://d3c33hcgiwev3.cloudfront.net/-q2dp-IAEemnvhJSBz-0XA_9625a0851f91403da0239b66c8e2bed8_people_wiki.sframe.zip?Expires=1595548800&Signature=arx2r4mrGeZG~-0zdA0TxqI-FIZOe4GLOR87XdRey0wziN2aZ04RvwdXTbBkyj8Jujs1xDhWwTTNUXAXvmlgnhEzLAW-29zTKkM6QUvq4YNvGiX03WU8UaHGBBunVe0Pyb3VGi7y2Y5F9CWPSPmwLbs~YbzcUwj012FwkcNK9bI_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
 
 *   Download the document retrieval notebook from the module here:
 
 [FND04-NB01.ipynb.zip](https://d3c33hcgiwev3.cloudfront.net/rl6kn-JbEemJfgqR2HI2sA_8903e57518cc4e6b82a96ec033fe3a8c_FND04-NB01.ipynb.zip?Expires=1595548800&Signature=houmK0zLhDhXEA2M918~CSErH0eDliWKsvWjAIySfvZaXJgfAr6wHPlU1mibwTxYWA6DAzHBpTv0UiABcyvqZt9mhtqhthoGkCd3vOUay3Oxw1cY5-VMMSzFICqU~md3AAcRy1FemomGctwKmiZV-u0VgREhbqNC5ADCWg2T~Ic_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
 
 *   Save both of these files in the same directory (where you are calling Jupyter notebook from) and unzip the data file. **Not sure where to save the files? See** [**this guide**](https://www.coursera.org/learn/ml-foundations/supplement/kRD6B/where-should-my-files-go)**.**
 
 Now you are ready to get started!

 -- https://www.coursera.org/learn/ml-foundations/supplement/6DeQc/retrieving-wikipedia-articles-assignment#mai


### *Note:  If you would rather use other ML tools...*

You are welcome to use any ML tool for this course, such as
[scikit-learn](http://scikit-learn.org/stable/). Though, as discussed in the
intro module,* we strongly recommend you use Jupyter Notebook and Turi Create.
(Turi Create is free and open source.)*

If you are choosing to use other packages, we still recommend you use SFrame,
which will allow you to scale to much larger datasets than Pandas. (Though, it's
possible to use Pandas in this course, if your machine has sufficient memory.)
The SFrame package is available in [open-source under a permissive BSD
license](https://github.com/turi-code/SFrame). So, you will always be able to
use SFrames for free.

If you are not using SFrame, here is the dataset for this assignment in CSV
format, so you can use [Pandas](http://pandas.pydata.org/) or other options out
there: 
[people_wiki.csv](https://d396qusza40orc.cloudfront.net/phoenixassets/people_wiki.csv)



### Watch the video and explore the Jupyter notebook on retrieving wikipedia
articles

If you haven’t done so yet, before you start, we recommend you watch the video
where we go over the Jupyter notebook on retrieving documents from this module. 
You can then open up the Jupyter notebook we used and familiarize yourself with
the steps we covered in this example.

### What you will do

Now you are ready!  We are going do three tasks in this assignment.  There are
several results you need to gather along the way to enter into the quiz after
this reading.

1.  **Compare top words according to word counts to TF-IDF:**  In the notebook we
covered in the module, we explored two document representations: word counts and
TF-IDF.  Now, take a particular famous person, 'Elton John'. What are the 3
words in his articles with highest word counts?  What are the 3 words in his
articles with highest TF-IDF?   These results illustrate why TF-IDF is useful
for finding important words.  **Save these results to answer the quiz at the
end.**
1.  **Measuring distance:**  Elton John is a famous singer; let’s compute the
distance between his article and those of two other famous singers. In this
assignment, you will use the [cosine
distance](https://apple.github.io/turicreate/docs/api/generated/turicreate.toolkits.distances.cosine.html?highlight=cosine#turicreate.toolkits.distances.cosine),
which one measure of similarity between vectors, similar to the one discussed in
the lectures.  You can compute this distance using the
*turicreate.distances.cosine* function. What’s the cosine distance between the
articles on ‘Elton John’ and ‘Victoria Beckham’? What’s the cosine distance
between the articles on ‘Elton John’ and Paul McCartney’?  Which one of the two
is closest to Elton John?  Does this result make sense to you?  *Save these
results to answer the quiz at the end.*
1.  **Building nearest neighbors models with different input features and setting
the distance metric:**  In the sample notebook, we built a nearest neighbors
model for retrieving articles using TF-IDF as features and using the default
setting in the construction of the nearest neighbors model.  Now, you will build
two nearest neighbors models:

* Using word counts as features
* Using TF-IDF as features

In both of these models, we are going to set the distance function to cosine
similarity.  Here is how: when you call the function


add the parameter:


Now we are ready to use our model to retrieve documents.  Use these two models
to collect the following results:

* What’s the most similar article, other than itself, to the one on ‘Elton John’
using word count features?
* What’s the most similar article, other than itself, to the one on ‘Elton John’
using TF-IDF features?
* What’s the most similar article, other than itself, to the one on ‘Victoria
Beckham’ using word count features?
* What’s the most similar article, other than itself, to the one on ‘Victoria
Beckham’ using TF-IDF features?

*Save these results to answer the quiz at the end.*
