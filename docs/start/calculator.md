# Using k as a calculator




You can start using k as a powerful calculator: enter an expression at
the prompt, press Enter and k will evaluate the expression and print
the result.  Many available operations will look familiar, but you
will soon discover some features that are unique to k.

## Arithmetics

In k, `+`, `-`, and `*` work as the usual addition, subtraction and
multiplication operations, e.g.,

```kc
 3*4
12
```

but the division operator is `%` while `/` has several uses including
serving as a prefix for comments that k will ignore:

```kc
 10%3      / 10 divided by 3
3.333333
```

The next feature that may come as a surprise is that k does not use
the traditional order of operations.

```kc
 3*2+4     / addition is performed first
18
```

Instead of the (P)EMDAS order, k consistently evaluates its
expressions from right to left with only the parentheses having higher
precedence.

```kc
 (3*2)+4   / multiplication is performed first
10
```


## Elementary functions

As any good scientific calculator, k comes with a number of built-in
functions.  You can apply these functions by simply typing their names
before the argument separated by a space.

```kc
 sqrt 2
1.414214
```

Trigonometric functions operate on arguments in radians and you will
often need the π constant to convert from degrees.  The π constant is
built in in k and if you are using k on a Mac, you can type it using the
⌥-p key combination.

```kc
 sin π%2
1f
```

## Special values

Unlike some other languages that are quick to give up and report an error
when given invalid input, k tries hard to provide useful answers.  Thus
if the result of a function is infinite, k will return a special `∞` value
and indicate the sign of the infinity, and the invalid result may disappear
in the subsequent computations.

```kc
 log 0
-∞
 exp log 0
0f
```

When the result is completely undefined, k will return `ø`, which stands for
missing data.

```kc
 (log 0) + 1 % 0
ø
```

## Unary operators

In the previous sections, we have seen operators that take two numbers as
operands and functions that take one number as an argument.  From elementary
math, you are familiar with a unary `-` operator that takes a single operand
and returns its negation.  Not surprisingly, `-` does the same in k:

```kc
 - 42
-42
```

However, k takes this idea of the same operator having both binary and unary
forms to a whole new level.  Each operator in k has both unary and binary
forms.  For example, similar to `-`, the k division operator, `%`, has a unary
form that computes the inverse.

```kc
 % 3
0.3333333
```


## Whetting your appetite

As you experiment with k as a calculator, you will soon notice that it does not
complain about seemingly meaningless keystrokes.  Thus a `+` sign on its own or
following a number are simply echoed back by k

```kc
 +
+
 2+
2+
```

Entering the entire top row of shifted symbols is somehow understood by k as
a valid expression

```kc
 ~!@#$%^&*()_+
~:!:@:#:$:%:^:&:*:0#,""_+
```

We will explain what is happening here in future sections.

## Meet the Reference

On the [Reference Card](../ref/index.md) find the operators `+`, `-`, `*` and `%`. Try using each of them as a binary operator and confirm that you understand what it does. 

```kc
 2+3
5
 2-3
-1
 2*3
6
 2%3
0.6666667
```

See which of their unary forms you can explain. 

```kc
 (2 3;4 5)
2 3
4 5

 +(2 3;4 5)
2 4
3 5

 2 - 3
-1
 2 -3
2 -3

 *2 3
2

 %3
0.3333333
```

Evaluate k expressions to test your definitions. 

For each of the other operators explain what it does 

-   as a binary operator
-   as a unary operator

Write your English definitions as comments.
Evaluate k expressions to test your understanding of each. 

Follow the links from the [Reference Card](../ref/index.md) to see if your definitions are correct. 
