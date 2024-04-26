#Functions 
### Docstrings[](https://www.kaggle.com/code/colinmorris/functions-and-getting-help#Docstrings)

def least_difference(a, b, c):
    """Return the smallest difference between any two numbers
    among a, b and c.
    
    >>> least_difference(1, 5, -5)
    4
    """
    diff1 = abs(a - b)
    diff2 = abs(b - c)
    diff3 = abs(a - c)
    return min(diff1, diff2, diff3)

The docstring is a triple-quoted string (which may span multiple lines) that comes immediately after the header of a function. When we call `help()` on a function, it shows the docstring.

help(least_difference)

Help on function least_difference in module __main__:

least_difference(a, b, c)
    Return the smallest difference between any two numbers
    among a, b and c.
    
    >>> least_difference(1, 5, -5)
    4

> **Aside:** The last two lines of the docstring are an example function call and result. (The `>>>` is a reference to the command prompt used in Python interactive shells.) Python doesn't run the example call - it's just there for the benefit of the reader. The convention of including 1 or more example calls in a function's docstring is far from universally observed, but it can be very effective at helping someone understand your function. For a real-world example, see [this docstring for the numpy function `np.eye`](https://github.com/numpy/numpy/blob/v1.14.2/numpy/lib/twodim_base.py#L140-L194).

Good programmers use docstrings unless they expect to throw away the code soon after it's used (which is rare). So, you should start writing docstrings, too!