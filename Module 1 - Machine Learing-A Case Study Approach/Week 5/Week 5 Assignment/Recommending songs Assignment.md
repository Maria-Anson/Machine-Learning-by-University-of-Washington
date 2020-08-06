# Recommending songs



In this module, we focused on building recommender systems to find products,
music and movies that interest users.  We also built an exciting Jupyter
notebook for recommending songs, which we compared the simple popularity-based
recommendation with a personalized model, and which showed the significant
improvement provided by personalization.

In this assignment, we are going to explore the song data and the
recommendations made by our model.  In the process, you are going to learn how
to use one of the most important data manipulation primitives: *groupby*.

Follow the rest of the instructions on this page to complete your program.  When
you are done, **instead of uploading your code, you will answer a series of quiz
questions** (see the quiz after this reading) to document your completion of
this assignment.  The instructions will indicate what data to collect for
answering the quiz.

### Learning outcomes

* Execute song recommendation code with the Jupyter notebook
* Load and transform real, song data
* Build a song recommender model
* Use the model to recommend songs to individual users
* Use *groupby* to compute aggregate statistics of the data



### **Resources you will need**

You will need to install the software tools described in the Module 1 reading.
Instructions are provided
[here](https://www.coursera.org/learn/ml-foundations/item/5HQGl).

 [FND05-NB01.ipynb.zip](https://d3c33hcgiwev3.cloudfront.net/HzNgAeJcEemELQpo9cj5Ig_9bb707e80221427a9ca4bd23e2181a74_FND05-NB01.ipynb.zip?Expires=1596499200&Signature=OXCegQSC0AV1LN~-yab~Sn5Yj2wkdVsmxtEMtZiczGDDVb2bjUquGHzAM5NMov96DF7rHq2a2~FRCHyo-rFmQiLyGxlUZ8mMEX3ew3LLI6TGAskYTXwbZEa6Psh-OGeF5J8cfAGSp0q35Rp3qIjb~8RZnrDdAzOkedYO0il~ACs_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
 
 [song_data.sframe.zip](https://d3c33hcgiwev3.cloudfront.net/dIBuXeIiEemm5A4ynZyB2A_749ef60351624a8d83beedd5ef23367e_song_data.sframe.zip?Expires=1596499200&Signature=b9jh-bTfD-ytmNEAXlIijQHXxBlKwd0naAQB79td2OaTlQ1pWo0BOKcxN5BrUImf3o0D-b~XN8-DAko-FcNMFT9EvcmtlXR21AUw5YX74lG4fGkkYHAzFWdppPJ7JtNVO-eoJYBUsMQJgyT~UPuI~P0K2HX95nsljuhJluHd6YQ_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)



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
[song_data.csv](https://d396qusza40orc.cloudfront.net/phoenixassets/song_data.csv)

### Watch the video and explore the Jupyter notebook on recommending songs

If you haven’t done so yet, before you start, we recommend you watch the video
where we go over the Jupyter notebook on song recommendation from this module. 
You can then open up the Jupyter notebook we used and familiarize yourself with
the steps we covered in this example.

### What you will do

Now you are ready!  We are going do three tasks in this assignment.  There are
several results you need to gather along the way to enter into the quiz after
this reading.

1.  **Counting unique users: ** The method *.unique()* can be used to select the
unique elements in a column of data. In this question, you will compute the
number of unique users who have listened to songs by various artists.  For
example, to find out the number of unique users who listened to songs by 'Kanye
West', all you need to do is select the rows of the song data where the artist
is 'Kanye West', and then count the number of unique entries in the ‘user_id’
column.  Compute the number of unique users for each of these artists:  'Kanye
West', 'Foo Fighters', 'Taylor Swift' and 'Lady GaGa'.  **Save these results to
answer the quiz at the end. **
1.  **Using groupby-aggregate to find the most popular and least popular artist:** 
each row of *song_data* contains the number of times a user listened to
particular song by a particular artist.  If we would like to know how many times
any song by 'Kanye West' was listened to, we need to select all the rows where
‘artist’=='Kanye West' and sum the ‘listen_count’ column.  If we would like to
find the most popular artist, we would need to follow this procedure for each
artist, which would be very slow.  Instead, you will learn about a very
important method:

     .groupby()


You can read the [documentation about groupby
here](https://turi.com/products/create/docs/generated/graphlab.SFrame.groupby.html#graphlab.SFrame.groupby).
The *.groupby* method computes an aggregate (in our case, the sum of the
‘listen_count’) for each distinct value in a column (in our case, the ‘artist’
column).  

Follow these steps to find the most popular artist in the dataset: 

* The *.groupby* method has two important parameters:

i.  *key_columns*, which takes the column we want to group, in our case,
‘artist’

ii.  *operations*, where we define the aggregation operation we using, in our
case, we want to sum over the ‘listen_count’.  

* With this in mind, the following command will compute the sum* listen_count* for
each artist and return an SFrame with the results:

    song_data.groupby(key_columns='artist', operations={'total_count': turicreate.aggregate.SUM('listen_count')})


the total number of listens for each artist will be stored in *‘total_count’*.

* Sort the resulting SFrame according to the *‘total_count’*, and find the artist
with the most popular and least popular artist in the dataset.  **Save these
results to answer the quiz at the end.**

3. **[OPTIONAL] Using groupby-aggregate to find the most recommended songs:** 
Now that we learned how to use *.groupby() *to compute aggregates for each value
in a column, let’s use to find the song that is most recommended by the
*personalized_model *model we learned in the Jupyter notebook above.  Follow
these steps to find the most recommended song:

* Split the data into 80% training, 20% testing, using *seed=0*, as was done in
the Jupyter notebook above.
* Train an* item_similarity_recommender*, as done in the Jupyter notebook, using
the training data.
* Next, we are going to make recommendations for the users in the test data, but 
there are over 200,000 users (58,628 unique users) in the test set.  Computing
recommendations for these many users can be slow in some computers.  Thus, we
will use only the first 10,000 users only in this question.  Using this command
to select this subset of users:

      subset_test_users = test_data['user_id'].unique()[0:10000]

* Let’s compute one recommended song for each of these test users.  Use this
command to compute these recommendations:

      subset_test_users = test_data['user_id'].unique()[0:10000]

* Finally, we can use *.groupby() *to find the most recommended song!  :)  When we
used *.groupby() *in the previous question, we summed up the total
*‘listen_count’* for each artist, by setting the parameter SUM in the
aggregator:

       operations={'total_count': turicreate.aggregate.SUM('listen_count')}

For this question, we simply want to count how often each song is recommended,
so we will use the COUNT aggregator instead of SUM, and store the results in a
column we will call ‘count’ by using:
 
       operations={'total_count': turicreate.aggregate.SUM('listen_count')}


And, since we want to use the song titles as the key to the aggregator instead
of of the ‘artist’, we use:

       key_columns='song'

* By sorting the results, you will find out the most recommended song to the first
10,000 users in the test data! **Due to randomness in train-test split, the most
recommended song may come out differently for different people. This is why we
chose not to assign a quiz question for this section.**
