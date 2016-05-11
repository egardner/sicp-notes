# Structure and Interpretation of Computer Programs
## Chapter 1: Building Abstractions with Procedures

> The acts of the mind, wherein it exerts its power over simple ideas, are chiefly
> these three: 1. Combining several simple ideas into one compound one, and thus
> all complex ideas are made. 2. The second is bringing two ideas, whether simple
> or complex, together, and setting them by one another so as to take a view of
> them at once, without uniting them into one, by which it gets all its ideas of
> relations. 3. The third is separating them from all other ideas that accompany
> them in their real existence: this is called abstraction, and thus all its
> general ideas are made.

—John Locke, _An Essay Concerning Human Understanding_ (1690)

#### Programming in Lisp

Lisp was invented in the 1950s as a formalism for reasoning about _recursion
equations_ (logical expressions) as a model for computation. Stands for 
LISt Processing.

A key feature of Lisp is the ability to represent _procedures_ as _data_.
This allows the use of certain techniques which blur the boundaries between
"active" processes and "passive" data. This makes Lisp well-suited for writing
programs that must manipulate other programs, like compilers and interpreters.

### 1.1: The Elements of Programming

Every serious programming language must define the following:

- Primitive Expressions: `486`
- Means of Combination: `(+ 137 349)`
- Means of Abstraction: `(define size 2)`

Every programming language must deal with two kinds of elements:

- Procedures
- Data

Later the line between these two things will blur.

#### 1.1.1 Expressions

Primitive expressions like numbers: `486`
Compound expressions: `(+137 349)` (evaluates to 486)

These compound expressions are called _combinations_. 
Parentheses enclose an operator followed by one or more operands.

The convention of placing the operator on the left side is known as
_prefix notation_.

#### 1.1.2 Naming and the Environment

Naming variables in the Scheme dialect of Lisp works like this:

```lisp
(define size 2)
```

This is equivalent to `size = 2` in other languages.
Variables can be used like other values:

```lisp
(* 5 size)
;; 10
```

`define` is Lisp's simplest **means of abstraction**

#### 1.1.3 Evaluating Combinations

To evaluate a combination, first evaluate each element in the combination:
evaluation is _recursive_ by nature.

Example of recursive evaluation:

```lisp
(* (+ 2 (* 46)) (+ 3 5 7))
```

This expression could be viewed like a tree -- the separate branches of the 
individual nodes or elements merge into a "trunk" which is the complete value
of the statement. Values "percolate upward" in this analogy. This general
process is known as _tree accumulation_.

#### 1.1.4 Compound Procedures

Declaring a variable is a simple and limited means of abstraction.
A much more powerful abstraction technique is the _procedure definition_.

```lisp
(define (square x) (* x x))
```

The general form of a procedure definition is:

```
(define (<name> <formal parameters>) <body>)
```

A procedure can be used as a building block to construct new, higher-order procedures:

```lisp
(define (sum-of-squares x y)
  (+ (square x) (square y)))
```
