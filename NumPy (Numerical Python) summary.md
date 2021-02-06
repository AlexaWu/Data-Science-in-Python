> Python library/package for scientific computing, contains multidimensional array and matrix data structures. It provides **ndarray** object, a homogeneous n-dimensional array object.

**[Array creation routines](#create)**
- [Placeholders](#place)
    
**[Arrays Properties](#props)**
      
**[Mathematics](#maths)**
- [Arithmetic Operations](#ops)
- [Comparison](#comparison)
- [Basic Statistics](#stats)
- [More](#more)
    
**[Slicing and Subsetting](#ss)**
    
**[Tricks](#tricks)**

</br>

## Array creation routines <a name="create"></a>

>The essential difference between *lists* and *NumPy arrays* is functionality and speed. *lists* give you basic operation, but *NumPy* adds FFTs, convolutions, fast searching, basic statistics, linear algebra, histograms, etc.</br>

| Operator     | Description   | Reference|
| :------------- | :------------- | :--------|
|`np.array([1,2,3])`|create 1 dimensional array|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.array.html#numpy.array)|
|`np.array([(1,2,3),(4,5,6)])`|create 2 dimensional array|same above|
|`np.arange(start,stop,step)`|create array with a sequence of numbers, not include stop|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.arange.html)|

#### Examples
```python
import numpy as np

# 1 dimensional
>>> x = np.array([1,2,3])

# 2 dimensional
>>> y = np.array([(1,2,3),(4,5,6)])

>>> x = np.arange(3)
array([0, 1, 2])

>>> y = np.arange(3.0)
array([ 0.,  1.,  2.])

>>> x = np.arange(3,7)
array([3, 4, 5, 6])

>>> y = np.arange(3,7,2)
array([3, 5])
```

### Placeholders <a name="place"></a>
| Operators | Description |Reference|
| :------------- | :------------- |:---------- |
|`np.linspace(0,2,9)`|generate a sequence of floats with evenly spaced values, include stop|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.linspace.html)|
|`np.zeros((2,3))`|Create 2 rows 3 columns array with float zeros|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.zeros.html)|
|`np.ones((2,4))`|Creates 2 rows 4 columns with float ones|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ones.html#numpy.ones)|
|`np.random.random((5,5))`|Creates 5 rows 5 columns random float array|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.random.random.html)|

#### Examples
```python
>>> np.linspace( 0, 2, 15 )
array([0.        , 0.14285714, 0.28571429, 0.42857143, 0.57142857,
       0.71428571, 0.85714286, 1.        , 1.14285714, 1.28571429,
       1.42857143, 1.57142857, 1.71428571, 1.85714286, 2.        ])

>>> d = np.zeros((2,3))
>>> print(d)
[[0. 0. 0.]
 [0. 0. 0.]]

>>> e = np.ones((2,3))
>>> print(e)
[[1. 1. 1.]
 [1. 1. 1.]]

>>> np.random.rand(2,3)
array([[0.63814812, 0.10556618, 0.80024855],
       [0.45082757, 0.84823512, 0.28658515]])
```

</br>

## Array Properties <a name="props"></a>
|Syntax|Description|Reference|
|:-------------|:-------------|:-----------|
|`array.shape`|check dimensions (Rows,Columns), which returns a tuple|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.shape.html)|
|`len(array)`|check length of Array|[link](https://docs.python.org/3.5/library/functions.html#len)|
|`array.ndim`|check number of Array Dimensions|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.ndim.html)|
|`array.dtype`|check data Type|[link](https://docs.scipy.org/doc/numpy/reference/arrays.dtypes.html)|
|`array.astype(type)`|Converts Data Type|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.astype.html)|

## Mathematics <a name="maths"></a>

### Operations <a name="ops"></a>
| Operator | Description     |Reference|
| :------------- | :------------- |:---------|
|`np.add(x,y)`|x + y|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.add.html)|
|`np.substract(x,y)`|x - y|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.subtract.html#numpy.subtract)|
|`np.divide(x,y)`|x / y|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.divide.html#numpy.divide)|
|`np.multiply(x,y)`|x @ y|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.multiply.html#numpy.multiply)|
|`np.sqrt(x)`|Square Root|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.sqrt.html#numpy.sqrt)|

>NumPy array operations work element-wise. If a 1d array is added to a 2d array (or the other way), NumPy chooses the array with smaller dimension and adds it to the one with bigger dimension

#### Example
```python
>>> a = np.array([1, 2, 3])
>>> b = np.array([(1, 2, 3), (4, 5, 6)])
>>> print(np.add(a, b))
[[2 4 6]
 [5 7 9]]
```

### Comparison
| Operator | Description | Reference |
| :------------- | :------------- |:---------|
|`==`|Equal|[link](https://docs.python.org/2/library/stdtypes.html)|
|`!=`|Not equal|[link](https://docs.python.org/2/library/stdtypes.html)|
|`<`|Smaller than|[link](https://docs.python.org/2/library/stdtypes.html)|
|`>`|Greater than|[link](https://docs.python.org/2/library/stdtypes.html)|
|`<=`|Smaller than or equal|[link](https://docs.python.org/2/library/stdtypes.html)|
|`>=`|Greater than or equal|[link](https://docs.python.org/2/library/stdtypes.html)|
|`np.array_equal(x,y)`|Array-wise comparison|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.array_equal.html)|

#### Example
```python
# Using comparison operators will create boolean NumPy arrays
>>> z = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
>>> c = z < 6
>>> print(c)
[ True  True  True  True  True False False False False False]
```
### Basic Statistics <a name="stats"></a>
| Operator | Description    |Reference |
| :------------- | :------------- |:--------- |
|`np.mean(array)`|Mean|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.mean.html#numpy.mean)|
|`np.median(array)`|Median|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.median.html#numpy.median)|
|`array.corrcoef()`|Correlation Coefficient|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.corrcoef.html#numpy.corrcoef)|
|`np.std(array)`|Standard Deviation|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.std.html#numpy.std)|

#### Example
```python
# Statistics of an array
a = np.array([1, 1, 2, 5, 8, 10, 11, 12])

# Standard deviation
>>> print(np.std(a))
4.2938910093294167

# Median
>>> print(np.median(a))
6.5
```

### More <a name="more"></a>
| Operator | Description    | Reference |
| :------------- | :------------- |:--------- |
|`array.sum()`|Array-wise sum|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.sum.html)|
|`array.min()`|Array-wise minimum value|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.min.html)|
|`array.max(axis=0)`|Maximum value of specified axis||
|`array.cumsum(axis=0)`|Cumulative sum of specified axis|[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.cumsum.html)|

## Slicing and Subsetting <a name="ss"></a>
|Operator|Description|Reference|
| :------------- | :------------- | :------------- |
|`array[i]`|1d array at index i|[link](https://docs.scipy.org/doc/numpy/reference/arrays.indexing.html)|
|`array[i,j]`|2d array at index[i][j]|see above|
|`array[i<4]`|Boolean Indexing, see [Tricks](#tricks)|see above|
|`array[0:3]`|Select items of index 0, 1 and 2|see above|
|`array[0:2,1]`|Select items of rows 0 and 1 at column 1|see above|
|`array[:1]`|Select items of row 0 (equals array[0:1, :])|see above|
|`array[1:2, :]`|Select items of row 1|see above|
[comment]: <> (|`array[1,...]`|equals array[1,:,:]|see above|)
|`array[ : :-1]`|Reverses `array`|see above|


#### Examples
```python
>>> b = np.array([(1, 2, 3), (4, 5, 6)])

# The index *before* the comma refers to *rows*,
# the index *after* the comma refers to *columns*
>>> print(b[0:1, 2])
[3]

>>> print(b[:len(b), 2])
[3 6]

>>> print(b[0, :])
[1 2 3]

>>> print(b[0, 2:])
[3]

>>> print(b[:, 0])
[1 4]

>>> c = np.array([(1, 2, 3), (4, 5, 6)])
>>> d = c[1:2, 0:2]
>>> print(d)
[[4 5]]

```

</br>

## Tricks <a name="tricks"></a>

```python
# Index trick when working with two np-arrays
>>> a = np.array([1,2,3,6,1,4,1])
>>> b = np.array([5,6,7,8,3,1,2])

# Only saves a at index where b == 1
other_a = a[b == 1]

#Saves every spot in a except at index where b != 1
other_other_a = a[b != 1]
```

```python
>>> x = np.array([4,6,8,1,2,6,9])
>>> y = x > 5
>>> print(x[y])
[6 8 6 9]

# Even shorter
>>> x = np.array([1, 2, 3, 4, 4, 35, 212, 5, 5, 6])
>>> print(x[x < 5])
[1 2 3 4 4]

```

[NumPy / SciPy / Pandas Cheat Sheet](https://s3.amazonaws.com/quandl-static-content/Documents/Quandl+-+Pandas,+SciPy,+NumPy+Cheat+Sheet.pdf)
