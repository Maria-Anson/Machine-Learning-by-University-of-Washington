# Installing Python and Turi Create

Please follow the installation instructions [here](https://www.coursera.org/learn/ml-foundations/supplement/5HQGl/reading-getting-started-with-python-jupyter-notebook-turi-create) before getting started:


## So far, we have
* Installed Python
* Started Jupyter Notebook

# Getting started with Python


```python
print('Hello World!')
```

    Hello World!


## Create some variables in Python


```python
i = 4  #int
```


```python
type(i)
```




    int




```python
f = 4.1  #float
```


```python
type(f)
```




    float




```python
b = True  #boolean variable
```


```python
type(b)
```




    bool




```python
s = "This is a string!"
```


```python
print(s)
```

    This is a string!


## Advanced python types


```python
l = [3,1,2]  #list
```


```python
print(l)
```

    [3, 1, 2]



```python
type(l)
```




    list




```python
d = {'foo':1, 'bar':2.3, 's':'my first dictionary'}  #dictionary
```


```python
print(d)
```

    {'foo': 1, 'bar': 2.3, 's': 'my first dictionary'}



```python
print(d['foo'])  #element of a dictionary
```

    1



```python
type(d)
```




    dict




```python
n = None  #Python's null type
```


```python
type(n)
```




    NoneType



## Advanced printing


```python
print("Our float value is %s. Our int value is %s." % (f,i))  #Python is pretty good with strings
```

    Our float value is 4.1. Our int value is 4.


## Conditional statements in python


```python
if i == 1 and f > 4:
    print("The value of i is 1 and f is greater than 4.")
elif i > 4 or f > 4:
    print("i or f are both greater than 4.")
else:
    print("both i and f are less than or equal to 4")

```

    i or f are both greater than 4.


## Conditional loops


```python
print(l)
```

    [3, 1, 2]



```python
for e in l:
    print(e)
```

    3
    1
    2


Note that in Python, we don't use {} or other markers to indicate the part of the loop that gets iterated.  Instead, we just indent and align each of the iterated statements with spaces or tabs. (You can use as many as you want, as long as the lines are aligned.)


```python
counter = 6
while counter < 10:
    print(counter)
    counter += 1
```

    6
    7
    8
    9


# Creating functions in Python

Again, we don't use {}, but just indent the lines that are part of the function.


```python
def add2(x):
    y = x + 2
    return y
```


```python
i = 5
```


```python
add2(i)
```




    7



We can also define simple functions with lambdas:


```python
square = lambda x: x*x
```


```python
square(5)
```




    25


