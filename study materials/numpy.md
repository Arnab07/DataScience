Parent Link: https://numpy.org/devdocs/user/quickstart.html

NumPy’s main object is the homogeneous multidimensional array. It is a table of elements (usually numbers), all of the same type, indexed by a tuple of non-negative integers. In NumPy dimensions are called axes.

NumPy’s array class is called `ndarray`. It is also known by the `alias array`. Note that numpy.array is not the same as the Standard Python Library class array.array, which only handles one-dimensional arrays and offers less functionality. The more important attributes of an ndarray object are:

###### For example, the coordinates of a point in 3D space [1, 2, 1] has one axis. That axis has 3 elements in it, so we say it has a length of 3. In the example pictured below, the array has 2 axes. The first axis has a length of 2, the second axis has a length of 3.

`[[ 1., 0., 0.],
 [ 0., 1., 2.]]`

~~~~~
ndarray.ndim
    the number of axes (dimensions) of the array.

ndarray.shape
    the dimensions of the array. This is a tuple of integers indicating the size of the array in each dimension. For a matrix with n rows and m columns, shape will be (n,m). The length of the shape tuple is therefore the number of axes, ndim.

ndarray.size
    the total number of elements of the array. This is equal to the product of the elements of shape.

ndarray.dtype
    an object describing the type of the elements in the array. One can create or specify dtype’s using standard Python types. Additionally NumPy provides types of its own. numpy.int32, numpy.int16, and numpy.float64 are some examples.

ndarray.itemsize
    the size in bytes of each element of the array. For example, an array of elements of type float64 has itemsize 8 (=64/8), while one of type complex32 has itemsize 4 (=32/8). It is equivalent to ndarray.dtype.itemsize.

ndarray.data
    the buffer containing the actual elements of the array. Normally, we won’t need to use this attribute because we will access the elements in an array using indexing facilities.

~~~~~


##Printing Arrays
When you print an array, NumPy displays it in a similar way to nested lists, but with the following layout:the last axis is printed from left to right,the second-to-last is printed from top to bottom,the rest are also printed from top to bottom, with each slice separated from the next by an empty line.

~~~~
np.arange(6)        //1d Array
    [0 1 2 3 4 5]

np.arange(12).reshape(4,3)  //2d Array
    [[ 0  1  2]
     [ 3  4  5]
     [ 6  7  8]
     [ 9 10 11]]

np.arange(24).reshape(2,3,4)   //3d Array
    [[[ 0  1  2  3]
      [ 4  5  6  7]
      [ 8  9 10 11]]
    
     [[12 13 14 15]
      [16 17 18 19]
      [20 21 22 23]]]
~~~~

###Basic Operations
Arithmetic operators on arrays apply elementwise. A new array is created and filled with the result.

~~~~
a = np.array( [20,30,40,50] )
b = np.arange( 4 )

Subtract: a-b
Sq Root: b**2
Sin: 10*np.sin(a)
Array Comparison a<35

the product operator * operates elementwise in NumPy arrays. The matrix product can be performed using the @ operator (in python >=3.5) or the dot function or method:
A = np.array( [[1,1],
               [0,1]] )
B = np.array( [[2,0],
               [3,4]] )

A * B           // elementwise product
array([[2, 0],
       [0, 4]])

A @ B           // matrix product
array([[5, 4],
       [3, 4]])

A.dot(B)      // matrix product
array([[5, 4],
       [3, 4]])

For inplace operation of same data-types:
a *= 3
b += a      //wont work if `b` is interger type and `a` is float type

When operating with arrays of different types, the type of the resulting array corresponds to the more general or precise one (a behavior known as upcasting).
