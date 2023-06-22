# K for Python Programmers
Python is a popular programming language in the fields of data science and machine learning, and a popular general-purpose scripting language for general purpose computing.
Python is notable for its "batteries included" approach which encourages solving problems by composing modules together.

## Similarities to K
Both languages are dynamically typed and come with a read-eval-print-loop (REPL) interpreter which facilitates interactive use.
Python and K both have powerful built-in list and dictionary container data types.

### Lists
We can create a list of numbers in Python:
```python
mylist = [1, 2, 3]
```

And a similar list of numbers in K:
```kc
mylist: 1 2 3
```

Creating a two-dimensional array is accomplished in the same way in both K and Python.
Namely, we create a list of lists.

In Python:
```python
my2d = [[1,2,3], [4,5,6]]
```

And in K:
```kc
my2d: (1 2 3;4 5 6)
```

### Dictionaries
Similarly, both languages have syntax for writing a literal dictionary value.

Python uses curly braces and JSON-like delimiters between keys and values:
```python
mydict = {"key1":23, "key2":46}
```

K has a similar method to create a dictionary:
```kc
mydict: ["key1":23; "key2":46]
```

### Functions
Functions are handled a little differently between the two languages.

Python has two different kinds of functions (named or anonymous):
```python
# a named function
def func1(a,b):
    return a+b
    
lambda x,y: x+y           # anonymous function
func2 = lambda x,y: x+y   # anonymous function, saved to the name "func2"
```

K has one kind of function, which is similar to Python's `lambda`:

```kc
{x+y}         / anonymous function
func2: {x+y}  / anonymous function, saved to the name "func2"
```

Did you notice that the parameter names `x` and `y` were only mentioned once in the K version?
That's because in K, user-defined functions can use default names `x`, `y`, and `z` for the first, second, and third parameters, respectively.

If you prefer to give names to function parameters (or if you have more than 3), no problem:

```kc
func3: {[a;b] a+b}  / same as func2, but with user-defined names for the first 2 parameters
```

As in the Python `lambda` function, in K there is no explicit `return` keyword.
Instead, functions return the value of their last expression.

### Control Flow
Python has ways of handling conditional and iterative computations similar to those in K:
```python
x = 2 if condition else 3  # x gets 2 if condition is true, otherwise x gets 3
```

In K, we would use a `cond` expression to accomplish the same task:
```kc
x: $[condition;2;3]
```

Python has "comprehension" forms for performing operations on collections like lists and dictionaries:
```python
result = [x+1 for x in [1,2,3]]  # result gets [2,3,4]
```

In K, operators like `+` implicitly map to each element in a list:
```kc
result: 1 + 1 2 3
```

## Differences from K
As we just saw, operators in K implicitly work on collections, so adding an atom to a list uses the same syntax as adding an atom to another atom:

```kc
atom: 2+3             / atom gets 5
foo: 2 + 100 200 300  / foo gets 102 202 302
```

The third-party module [NumPy](https://numpy.org/) (short for Numeric Python) adds similar functionality to Python, although it requires more syntax:

```python
import numpy as np
atom = 2+3                         # atom gets 5
foo = 2 + np.array([100,200,300])  # foo gets array([102, 202, 302])
```
