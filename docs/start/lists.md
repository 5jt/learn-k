# Lists


Much of the expressiveness of k derives from
the fact that most operations that operate
on single values (atoms) generalize nicely to lists.

The simplest list is simply a sequence of numbers separated by
spaces.  When you apply one of the arithmetic operations between an
atom and a list, k computes the result of the operation between each  item of
the list and the atom. For example

```kc
 1 2 3 4 * 10
10 20 30 40
```

You can also perform operations on the lists of the same length and k
will pair up the corresponding  items and apply the operation to
each pair.

```kc
 1 2 3 + 3 2 1
4 4 4
```

However, if the lengths don’t match, k will signal an error.

```ke
 1 2 3 + 3 2
1 2 3 + 3 2
      ^
length error
>
```

We will explain the meaning of error displays later, but for now
you just need to know that entering `\` at the
`>` prompt will clear the error and allow you to continue.


## Generating lists

Entering long lists into k soon becomes tedious. 

Let’s try generating numeric lists.

```kc
 &8  / Where
0 0 0 0 0 0 0 0 
```

What is Where doing? Test your definition with `&4`, `&4.4`, `&-4`, and `&3 4 5`. Look at the definition of [Where](../ref/where.md) in the Reference. 

Another way:

```kc
 !7  / Index
!7
 5+!7
5+!7
 0 0 0 0 0+!5
0 1 2 3 4
```

Again, write a comment defining what Index does. Test your definition with `!7.0` and `!-7`. Compare your definition to the [Reference for Index](../ref/index.md).

Adding 5 to `!7` does not require the summarized enumeration (of 0-9) to be expanded. Adding another list did, even when every item is 0. Can you find other ways to expand the enumeration?

??? "Expanding the enumeration"
    `1.0*!7  / float` 

Another way to generate numeric lists:

```kc
 rand 5
0.5 0.9078156 0.269656 0.5607996 0.5680352
 rand -5
1.291197 -0.7736368 1.811311 0.6372954 0.644298
```

Can you see what unary `rand` is doing? Test your conjecture with `asc rand 20`. 
(The definition of `rand` for negative integers is hard to guess.)
Compare your definition to the [Reference for `rand`](../ref/rand.md). 

```kc
 10 rand 50 / generate randomly with replacement (so there can be duplicates)
24 45 13 28 28 8 43 9 17 30
```

(Because of randomness, your result might not exactly match the above.)

```kc
 10 rand 10
1 8 6 8 2 5 2 0 1 0

 -10 rand 10 / generate randomly without replacement (no duplicates)
2 9 7 1 8 5 0 6 4 3
```

There are more advanced ways to generate random arrays:

```kc
 20 rand 100 / recall uniform random with replacement
44 11 0 55 17 36 50 73 85 62 93 16 58 75 81 81 72 36 90 21

 rand 6 / uniform random with replacement between 0 and 1
0.782244 0.3937393 0.4717788 0.2755357 0.1641728 0.9861826
```

==Others are on the way. (To be added)==


## Saving results

Once we have generated some data, we would want to save it and give it a name
by which it can be recalled later.  This is done by using an assignment
expression that in k is a colon.

```kc
 a: &12
```


## Cut and Reshape

From now on, `a` will refer to a list of 12 zeros until we reuse this name
by assigning it to something else.

From a simple list, k can create a list of sublists.

```kc
 a
0 0 0 0 0 0 0 0 0 0 0 0 
 0 2 6 _ a  / Cut
0 0
0 0 0 0
0 0 0 0 0 0
```

How does Cut work? Test your definition with different left arguments. Compare your definition to the [Reference on Cut](../ref/cut.md).

To cut a list into sublists of equal size, we use Reshape.

```kc
 3 4 # a  / Reshape
0 0 0 0
0 0 0 0
0 0 0 0
 10#!4
0 1 2 3 0 1 2 3 0 1
```

How does Reshape work?

Consider this example, and amend your definition of Reshape to fit.

```kc
 3 2 2 # a
(0 0;0 0)
(0 0;0 0)
(0 0;0 0)
```

Test your definition with some other left arguments to Reshape. 
Compare your definition to the [Reference on Reshape](../ref/reshape.md).

!!! tip "Typing in 3D"

    If k had a 3D display, it could show this as a stack of 2×2
    matrices, but because we only have two dimensions, k shows stacked matrices
    in a linear notation.  The same notation can be used for input.

    <pre><code class="kc">
     (1 2;3 4)
    1 2
    3 4
    </code></pre>

```kc
 4 4#1,&4
1 0 0 0
0 1 0 0
0 0 1 0
0 0 0 1
```

You probably guessed that in the above example `1,` prepends `1` to the following list.  
We will discuss Join (`,`) next.


## Enlist and Join

K’s simple syntax for writing lists has one drawback.  How do you
write lists with zero or one items?  In fact, k offers no literal syntax 
for that: such lists have to be generated.  

You already know one method: simply
reshape an atom to a list using `0#` or `1#`.  When you create a list of one item, you will see that it is displayed as follows:

```kc
 1#42
,42
```

The `,` in front of the number is the Enlist operator. It turns its argument (
in this case the number `42`) into a 1-item list.  When applied to a list, `,` 
turns it into a 1-item list containing a list.  Note the difference between

```kc
 2#1 2 3    / take first 2  items
1 2
```

and

```kc
 2#,1 2 3   / repeat twice
1 2 3
1 2 3
```

In the first case, `2#` reshape gets a 3-item list and cuts it to length 2, but
in the second case it gets a 1-item list, so it recycles the first item (the list `1 2 3`) and makes a 2×3 matrix.

As a binary, `,` is the Join operator. Placed between two lists, or between a list and an atom, it joins its arguments together.

```kc
 (1,2 3 4;1 2,3 4;1 2 3,4)
1 2 3 4
1 2 3 4
1 2 3 4
```

The Index operator applies to negative integers.

```kc
 !-4
1 0 0 0
0 1 0 0
0 0 1 0
0 0 0 1
```

Joining lists of lists joins the rows:

```kc
 x,x: !-3
1 0 0
0 1 0
0 0 1
1 0 0
0 1 0
0 0 1
```

To join columns, we can use Join Each  `,'`. The [Each](../ref/each.md) adverb modifies how Join works.

```kc
 x,'x: !-3
1 0 0 1 0 0
0 1 0 0 1 0
0 0 1 0 0 1
```

To flatten a list of lists, use Join Over `,/`. The [Over](../ref/accumulatoirs.md#scan-over) adverb modifies how Join works. 

```kc
 ,/(1;2 3;4 5 6)
1 2 3 4 5 6
```

To recursively flatten a nested list, use Join Over Converge `,//`. 
The [Converge](../ref/accumulators.md#converge) adverb modifies how Join Over works.
Compare

```kc
  ,/(1;!-2)      / Join Over
1
1 0
0 1

 ,/  ,/(1;!-2)   / Join Over Join Over
1 1 0 0 1
  ,//(1;!-2)     / Join Over Converge
1 1 0 0 1
```

Much iteration in k is implicit, e.g. `2+3 4 5`. Adverbs are fast and powerful tools for explicit iteration. We shall return to them in ==FIXME==.


## Lists from atoms and back

We can split integers into digits

```kc-err
 10\:123456789
1 2 3 4 5 6 7 8 9
```

and put them back together

```kc
 10/:1 2 3 4 5 6 7 8 9
123456789
```

using the Vector from Scalar (`\:`) and Scalar from Vector (`/:`) operators.

For binary expansion just use 2 instead of 10.

```kc-err
 2\:42
1 0 1 0 1 0
```

Review the Reference articles for [Vector from Scalar](../ref/vector-from-scalar.md) (`\:`) and [Scalar from Vector](../ref/scalar-from-vector.md) (`/:`) and try the following exercise.

??? "Exercise: Split 12345 seconds into days, hours and minutes – then back into seconds."
    <pre><code class="kc">
     24 60 60\:12345
    3 25 45
     24 60 60/:3 25 45  / and back again
    12345
    </code></pre>

