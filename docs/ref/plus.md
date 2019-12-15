# `+` Add, Flip

## Add

Syntax: `x + y`

Where `x` and `y` are [conformable](../basics/glossary.md#conformable "Glossary") numeric or temporal atoms or lists, returns the sums of corresponding items.

Add is an [atomic](../basics/glossary.md#atomic "Glossary") verb. 

```kc
 2+3
5
 2+3 4 5
5 6 7
 2019-06-28 + 7*!4 / add 0 1 2 3 weeks
2019-06-28 2019-07-05 2019-07-12 2019-07-19
 12:34:56.789 + 1000 / add 1000 ms
12:34:57.789
```



## Flip

Syntax: `+ x`

Where `x` is

-   a list of [rank](../basics/glossary.md#rank) 2 or more, returns the transpose of `x`, padding with nulls as needed
-   a dictionary of which at least one value is a list, returns a table in which the dictionary keys are column names, and missing cells contain nulls
-   a dictionary of which all values are atoms of the same type, returns `x`
-   anything else, signals a `class` error

Lists: 

```kc
 +2 3#!6  / list rank 2
0 3
1 4
2 5

 a:"abcdefghijklmnopqrstuvwxyz"
 2 3 4#a  / list rank 3
("abcd";"efgh";"ijkl")
("mnop";"qrst";"uvwx")

 +2 3 4#a
("abcd";"mnop")
("efgh";"qrst")
("ijkl";"uvwx")

 +(`abc`def;24;"foo")  / non-rectangular 
(`abc;24;"f")
(`def;24;"o")
(`;24;"o")
```

Dictionaries:

```kc
 +{a:`x`y`z;b:3}  / values conform
a b
- -
x 3
y 3
z 3

 +{a:`x`y`z;b:3 2}  / values do not conform
a b
- --
x  3
y  2
z Ø

 +{a:2019-12-14;b:2019-11-27}  / values are atoms of same datatype
a|2019-12-14
b|2019-11-27
```

<i class="fas fa-book-open"></i>
[Errors](../basics/errors.md)
