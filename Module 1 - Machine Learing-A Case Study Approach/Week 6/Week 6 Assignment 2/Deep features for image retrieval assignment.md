## Deep features for image retrieval assignment

*****



# Retrieving Images



This assignment focuses on using deep learning to create nonlinear features to
improve the performance of machine learning. You will see how transfer learning
techniques are applied to use deep features learned with one dataset to get
great performance on a different dataset. You will build models for image
retrieval and image classification tasks.

Follow the rest of the instructions on this page to complete your program.  When
you are done, instead of uploading your code, you will answer a series of quiz
questions (see the quiz after this reading) to document your completion of this
assignment.  The instructions will indicate what data to collect for answering
the quiz.

### Learning outcomes

* Load and transform real image data
* Use the Sketch method to view statistics of data
* Build image retrieval models using nearest neighbor search and deep features
* Compare the results of various image retrieval models
* Use the apply and sum methods to compute functions of the data

### Resources you will need

You will need to install the software tools described in the Module 1 reading.
Instructions are provided
[here](https://www.coursera.org/learn/ml-foundations/item/5HQGl).

### Download the data and starter code

Before getting started, you will need to download the dataset and the starter
Jupyter notebook that we used in the module.

*   Download the wikipedia dataset with training images here in SFrame format:
 
 [image_train_data.zip](https://d3c33hcgiwev3.cloudfront.net/_UfOzO0jEeiAgQrXx6bp4g_fd80e000ed2311e8a0546b27d475e197_image_train_data.zip?Expires=1596844800&Signature=LHA~Bm1iOqDnPZDl1W78qlh4YvIaZ3ST13IijP2fcazdTUCOBlcB1gHNWe3xDyRiF1lN6q0kVuGeDVw~rNIBKZWmQSrKK0v5Lv6URpKq5hGAvIub45u~XfUiFvb2OKi97fBN0pPpNP5yxliAvKLSG9srI5LE2kLsb6yV7ca3ARk_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
 
 *   Download the wikipedia dataset with test images herein SFrame format:
 
 [image_test_data.zip](https://d3c33hcgiwev3.cloudfront.net/_UcMSe0jEeiixgqCUDoEfA_fd7f3250ed2311e88507e367f09ac3a9_image_test_data.zip?Expires=1596844800&Signature=enCvvCLfCQrsNSVogN7ud-nowfIu6qAUkezmj77nqj8pTLiyu7d05Yr4uo~hDZuJGCqyIL-SMi-3lxGcuKD5SnEcW7BFU7hfiOY4DGgJsAkC1AoS09094k0h7~bTFCrHGG-yCZizo0gZxRCSFV-aMaTPgcq4SxHNoot4pvo81-c_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)


### **Programming Assignment: **

There are four tasks in this assignment. There are several results you need to
gather for the quiz that accompanies this module.

**Task 1: Compute summary statistics of the data**

Sketch summaries are techniques for computing summary statistics of data very
quickly. In Turi Create has a method **sketch** which computes summary
statistics. Using the training data, compute the sketch summary of the label
olumn and interpret the results by running this command.

sketch = turicreate.Sketch(image_data['label'])

Then look at the sketch object to see the summary statistics.

For more information on Sketch, see:

[https://apple.github.io/turicreate/docs/api/generated/turicreate.Sketch.html?highlight=sketch](https://apple.github.io/turicreate/docs/api/generated/turicreate.Sketch.html?highlight=sketch)

What is the least common category in the training data?

**Save this result to answer the quiz for this module.**

**Task 2: Create category-specific image retrieval models**

In most retrieval tasks, the data are unlabeled, thus you call these
unsupervised learning problems. This image dataset has labels, so you will use
them to create one model for each of the four image categories, dog, cat,
automobile, and bird.

Follow these steps:

1.  Split the training data into 4 different SFrame data structures. Each will
contain data for one of the four categories image categories. (Hint: If you use
a logical filter to select the rows where the label column equals ‘dog’, you can
create an SFrame that contains only the data for images labeled ‘dog’.)
1.  Similarly to the image retrieval notebook you downloaded, you will create a
nearest neighbor model using deep features. You will create one such model for
each category, using the corresponding subset of the training data. Call the
model with the dog images dog_model, the one with the cat images cat_model, as
so on.

You now have a nearest neighbors model, dog_model, that can find the nearest dog
to any image you give the model. Another model, cat_model, that can find the
nearest cat to any image you give it, and so on.

The following cat image is the first in the test data (image_test[0:1]):

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/jhu_hOJDEemELQpo9cj5Ig_9d4466a990ff605dc92f819a9e43eed6_first_image_test.png?expiry=1596844800000&hmac=R5S7-IgSjrSB7HtBoC_TbCQCmF6qlYjWyagZTZnubZE)

Using these models, answer the following questions.

* What is the nearest cat-labeled image in the training data to the cat image that
is the first image in the test data ?
* What is the nearest dog-labeled image in the training data to the cat image that
is the first image in the test data?

Hint: When you query your nearest neighbors model, it will return a result that
looks something like this:

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/Z6cf8eJEEemJfgqR2HI2sA_e2c19954217dac88fb5ecb5aaf6e8186_Table-1.png?expiry=1596844800000&hmac=nONSLmwlSWD8O-FWlO5oUgdFq68BvJQ12osSCHRrQFM)

To understand each column in this table, see this documentation:
[https://turi.com/learn/userguide/nearest_neighbors/nearest_neighbors.html](https://turi.com/learn/userguide/nearest_neighbors/nearest_neighbors.html).
The reference_label column is important, since it provides the index of the
nearest neighbors in the dataset used to train it. (In this case, the subset of
the training data labeled ‘cat’.)

**Save these results to answer the quiz for this module.**

**Task 3: Try a simple example of nearest-neighbors classification**

When you queried the nearest neighbors model, the distance column in the Task 2
showed the computed distance between the input and each of the retrieved
neighbors. In this task, you will use these distances for classification, using
a nearest-neighbors classifier.

* For the first image in the test data (image_test[0:1]), compute the mean
distance between this image at its five nearest neighbors that are labeled ‘cat’
in the training data (similar to what you did in the previous question).
* For the first image in the test data (image_test[0:1]), compute the mean
distance between this image at its five nearest neighbors that are labeled ‘dog’
in the training data (similar to what you did in the previous question).

On average, is the first image in the test data closer to its five nearest
neighbors in the ‘cat’ data or in the ‘dog’ data?

**Save these results to answer the quiz for this module.**

**Task 4: Compute nearest neighbors accuracy**

A nearest neighbor classifier predicts the label of a point as the most common
label of its nearest neighbors. In this task, you will measure the accuracy of a
1-nearest-neighbor classifier, i.e., predict the output as the label of the
nearest neighbor in the training data. Although there are simpler ways of
computing this result, this way introduces you to additional concepts in nearest
neighbors and SFrames, which will be useful in your future machine learning
education.

Use the four nearest neighbors models you trained previously on the training
data, the dog, cat, automobile, and bird models.

Just as you split the training data on label, you will now use the same
procedure to split the test data on the cat, dog, automobile, and bird labels.
Name the resulting SFrame data structures:

image_test_cat, image_test_dog, image_test_bird, image_test_automobile

Next you'll find nearest neighbors in the training set for each part of the test
set

Thus far you queried the nearest neighbors models with a single image as the
input, but you can actually query with a whole set of data. The query will find
the nearest neighbors for each data point. Note that the input index is stored
in the query_labelcolumn of the resulting SFrame.

Using this knowledge find the closest neighbor to the dog test data using each
of the trained models. For example, this code:

dog_cat_neighbors = cat_model.query(image_test_dog, k=1)

finds one neighbor (i.e., k=1) to the dog test images (image_test_dog) in the
cat portion of the training data.

Next, follow the same procedure for the other dog combinations: dog-automobile,
dog-bird, and dog-dog.

Create an SFrame with the distances from the dog test examples to the respective
nearest neighbors in each class in the training data.

The distance column in dog_cat_neighbors contains the distance between each
dog-labeled image in the test set and its nearest cat-labeled image in the
training set. The question to answer is: How many of the test set dog images are
closer to a dog in the training set than to a cat, automobile, or bird?

Next you will create an SFrame containing just these distances per data point.
The goal is to create an SFrame called dog_distances with 4 columns:

1.  dog_distances[‘dog-dog’]* ---- storing *dog_dog_neighbors[‘distance’]
1.  dog_distances[‘dog-cat’]* ---- storing *dog_cat_neighbors[‘distance’]
1.  dog_distances[‘dog-automobile’]* ---- storing
*dog_automobile_neighbors[‘distance’]
1.  dog_distances[‘dog-bird’] *---- storing *dog_bird_neighbors[‘distance’]

Hint: You can create a new SFrame from the columns of other SFrame structures by
creating a dictionary with the new columns, as shown in this example:

    news_frame = turicreate.SFrame({'foo': others_frame['foo'],'bar':
    some_others_frame['bar']})

The resulting SFrame will look similar to this:

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/RXrM6eJEEemnvhJSBz-0XA_0b5b7d3738895fae955350b054454238_Table-2.png?expiry=1596844800000&hmac=jr-WrqBhA0r8VyB3fzrBLsWYpq_fx0gkCtrH9QNWbRg)

Compute the number of correct predictions using 1-nearest neighbors for the dog
class.

Now that you have created dog_distances, you will use the apply method on this
SFrame to iterate through each row and compute the number of dog test examples
where the distance to the nearest dog image was lower than that to the other
image classes.

You will perform three steps:

1.  Consider one row of dog_distances and call this variable row. You can access
each distance by calling, for example, row['dog-cat'] which, in the previous
table, will have value equal to 36.4196077068 for the first row. Create a
function, def is_dog_correct(row):, that returns 1 if the value for
row[‘dog-dog’] is lower than that of the other columns, and 0 otherwise. That
is, returns 1 if this row is correctly classified by 1-nearest neighbors, and 0
if it is not.
1.  Using the function is_dog_correct(row), you can check if one row is correctly
classified. Next, you need to count how many rows are correctly classified. You
could use a for loop to iterate through each row and apply the function
is_dog_correct(row), but this method is extremely slow. An SFrame is not
optimized for this type of operation. Instead, use the apply method to iterate
the function is_dog_correct for each row.
1.  Compute the number of correct predictions for dog. You can now call the function
dog_distances.apply(is_dog_correct)which returns an SArray structure (a column
of data) with a value 1 for every correct row and a value 0 for every incorrect
one. You can call the sum method on the result to get the total number of
correctly classified dog images in the test set.

Using the work you did in this task, what is the accuracy of the 1-nearest
neighbor classifier at classifying dog images from the test set?

**NOTE:** If you are uncertain that your code is working correctly, you can
perform steps 1 and 2 to count the number of correctly classified cat images in
the test data. Your result should be 548. This verification will take you some
time, so you might do it only if you get the wrong answer on the quiz and can't
figure out why. 

**Save these results to answer the quiz for this module.**



*Note:  If you would rather use other ML tools...*

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
[image_train_data.csv](https://d396qusza40orc.cloudfront.net/phoenixassets/image_train_data.csv)
and 
[image_test_data.csv](https://d396qusza40orc.cloudfront.net/phoenixassets/image_test_data.csv)



### Watch the videos and explore the Jupyter notebooks on using deep features for
image classification and retrieval

If you haven’t done so yet, before you start, we recommend you watch the video
where we go over the Jupyter notebooks from this module.  You can then open up
the Jupyter notebook we used and familiarize yourself with the steps we covered
in these examples.

### What you will do

Now you are ready!  We are going do four tasks in this assignment.    There are
several results you need to gather along the way to enter into the quiz after
this reading.

1.  **Computing summary statistics of the data: ** Sketch summaries are techniques
for computing summary statistics of data very quickly.  In Turi Create, SArrays
include a method: 

    .summary()

which computes such summary statistics.  Using the training data, compute the
summary of the ‘label’ column and interpret the results.  What’s the least
common category in the training data?    **Save this result to answer the quiz
at the end.**

2.  **Creating category-specific image retrieval models:**  In most retrieval
tasks, the data we have is unlabeled, thus we call these unsupervised learning
problems.  However, we have labels in this image dataset, and will use these to
create one model for each of the 4 image categories,
{‘dog’,’cat’,’automobile’,bird’}.  To start, follow these steps:

* Split the SFrame with the training data into 4 different SFrames.  Each of these
will contain data for 1 of the 4 categories above.  *Hint: if you use a logical
filter to select the rows where the ‘label’ column equals ‘dog’, you can create
an SFrame with only the data for images labeled ‘dog’.*
* Similarly to the image retrieval notebook you downloaded, you are going to
create a nearest neighbor model using the 'deep_features' as the features, but
this time create one such model for each category, using the corresponding
subset of the training_data.  *You can call the model with the ‘dog’ data the
dog_model, the one with the ‘cat’ data the cat_model, as so on.*

You now have a nearest neighbors model that can find the nearest ‘dog’ to any
image you give it, the dog_model; one that can find the nearest ‘cat’, the
cat_model; and so on.  

Using these models, answer the following questions.  The cat image below is the
first in the *test data*:

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/5H_63k7OEeW17w7BjiD8oQ_1db702db5871b1c97627fdd5b367bebc_cat1.png?expiry=1596844800000&hmac=0UwLKKsFTqfrd0E1eQfU79pkp2DvsHLts_lAsL37WGI)

You can access this image, similarly to what we did in the Jupyter notebooks
above, with this command:

    image_test[0:1]

* What is the nearest ‘cat’ labeled image in the training data to the cat image
above (the first image in the test data)? **Save this result.**

*Hint: When you query your nearest neighbors model, it will return a SFrame that
looks something like this:*

[To understand each column in this table, see this
documentation](https://github.com/apple/turicreate/blob/master/userguide/nearest_neighbors/nearest_neighbors.md)[.](https://turi.com/learn/userguide/nearest_neighbors/nearest_neighbors.html)*
For this question, the ‘reference_label’ column will be important, since it
provides the index of the nearest neighbors in the dataset used to train it. 
(In this case, the subset of the training data labeled ‘cat’.)*

* What is the nearest ‘dog’ labeled image in the training data to the cat image
above (the first image in the test data)? **Save this result.**

**3.  A simple example of nearest-neighbors classification:** When we queried a
nearest neighbors model, the ‘distance’ column in the table above shows the
computed distance between the input and each of the retrieved neighbors.  In
this question, you will use these distances to perform a classification task,
using the idea of a nearest-neighbors classifier.  

* For the first image in the test data (image_test[0:1]), which we used above,
compute the mean distance between this image at its 5 nearest neighbors that
were labeled* ‘cat’* in the training data (similarly to what you did in the
previous question).  *Save this result.*
* Similarly, for the first image in the test data (image_test[0:1]), which we used
above, compute the mean distance between this image at its 5 nearest neighbors
that were labeled **‘dog’ **in the training data (similarly to what you did in
the previous question).  **Save this result.**
* On average, is the first image in the test data closer to its 5 nearest
neighbors in the ‘cat’ data or in the ‘dog’ data?  (In a later course, we will
see that this is an example of what is called a k-nearest neighbors classifier,
where we use the label of neighboring points to predict the label of a test
point.)

**4.  [Challenging Question]  Computing nearest neighbors accuracy using SFrame
operations: **A nearest neighbor classifier predicts the label of a point as the
most common label of its nearest neighbors.  In this question, we will measure
the accuracy of a 1-nearest-neighbor classifier, i.e., predict the output as the
label of the nearest neighbor in the training data.  Although there are simpler
ways of computing this result, we will go step-by-step here to introduce you to
more concepts in nearest neighbors and SFrames, which will be useful later in
this Specialization.  

* **Training models: ** For this question, you will need the nearest neighbors
models you learned above on the training data, i.e., the dog_model, cat_model,
automobile_model and bird_model.
* **Spliting test data by label:** Above, you split the train data SFrame into one
SFrame for images labeled ‘dog’, another for those labeled ‘cat’, etc.  Now, do
the same for the test data.  You can call the resulting SFrames

    image_test_cat, image_test_dog, image_test_bird, image_test_automobile

* **Finding nearest neighbors in the training set for each part of the test set:**
Thus far, we have queried, e.g.,

    dog_model.query()

our nearest neighbors models with a single image as the input, but you can
actually query with a whole set of data, and it will find the nearest neighbors
for each data point.  Note that the input index will be stored in the
‘query_label’ column of the output SFrame.  

Using this knowledge find the closest neighbor to each example the dog test data
using each of the trained models, e.g.,

    dog_cat_neighbors = cat_model.query(image_test_dog, k=1)

finds 1 neighbor (that’s what k=1 does) to each of the dog test images
(*image_test_dog*) in the cat portion of the training data (used to train the*
cat_model*).  

Now, do this for every combination of the labels in the training and test data. 


* **Create an SFrame with the distances from ‘dog’ test examples to the respective
nearest neighbors in each class in the training data: ** The ‘distance’ column
in *dog_cat_neighbors* above contains the distance between each ‘dog’ image in
the test set and its nearest ‘cat’ image in the* training set*.  The question we
want to answer is how many of the test set ‘dog’ images are closer to a ‘dog’ in
the training set than to a ‘cat’, ‘automobile’ or ‘bird’.  So, next we will
create an SFrame containing just these distances per data point.  The goal is to
create an SFrame called *dog_distances* with 4 columns:

i. *dog_distances[‘dog-dog’]* ---- storing  *dog_dog_neighbors[‘distance’]*

ii. *dog_distances[‘dog-cat’]* ---- storing  *dog_cat_neighbors[‘distance’]*

iii. *dog_distances[‘dog-automobile’] *---- storing 
*dog_automobile_neighbors[‘distance’]*

iv. *dog_distances[‘dog-bird’]* ---- storing  *dog_bird_neighbors[‘distance’]*

*Hint: You can create a new SFrame from the columns of other SFrames by creating
a dictionary with the new columns, as shown in this example:*

    new_sframe = turicreate.SFrame({'foo': other_sframe['foo'],'bar': some_other_sframe['bar']})

The resulting SFrame will look something like this:

* **Computing the number of correct predictions using 1-nearest neighbors for the
dog class:**  Now that you have created the SFrame *dog_distances*, you will
learn to use the method

    .apply()

on this SFrame to iterate line by line and compute the number of ‘dog’ test
examples where the distance to the nearest ‘dog’ was lower than that to the
other classes.  You will do this in three steps:

i.  Consider one row of the SFrame dog_distances.  Let’s call this variable row.
You can access each distance by calling, for example,

    row['dog-cat']

which, in example table above, will have value equal to *36.4196077068* for the
first row.  

Create a function starting with

    def is_dog_correct(row):

which returns 1 if the value for *row[‘dog-dog’]* is lower than that of the
other columns, and 0 otherwise.  That is, returns 1 if this row is correctly
classified by 1-nearest neighbors, and 0 otherwise.  

ii.  Using the function *is_dog_correct(row)*, you can check if 1 row is
correctly classified.  Now, you want to count how many rows are correctly
classified.  You could do a for loop iterating through each row and applying the
function *is_dog_correct(row)*.  This method will be really slow, because the
SFrame is not optimized for this type of operation.  

Instead, we will use the* .apply() *method to iterate the function
is_dog_correct for each row of the SFrame.  [Read about using the .apply()
method here. ](https://turi.com/learn/userguide/sframe/tabular-data.html)

iii. **Computing the number of correct predictions for ‘dog’: ** You can now
call:

    dog_distances.apply(is_dog_correct)

which will return an SArray (a column of data) with a 1 for every correct row
and a 0 for every incorrect one.  You can call:

    .sum()

on the result to get the total number of correctly classified ‘dog’ images in
the test set!

*Hint: To make sure your code is working correctly, if you were to do the steps
above in this question to computer 'cat distances' and count the number of
correctly classified ‘cat’ images in the test data, instead of ‘dog’, the result
would be 548. *

* **Accuracy of predicting dog in the test data: ** Using the work you did in this
question, what is the accuracy of the 1-nearest neighbor classifier at
classifying ‘dog’ images from the test set? **Save this result to answer the
quiz at the end.**


