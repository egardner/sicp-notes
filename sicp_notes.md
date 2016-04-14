# Structure and Interpretation of Computer Programs

## Lecture 1 notes

**Declarative vs Imperative knowledge**: Declarative knowledge represents
high-level, abstract descriptions of relationships; the kind of knowledge that
can be expressed in a mathematical equation for example. This is a more "pure"
kind of knowledge. Imperative knowledge is more procedural and low-level,
describing how to arrive at a solution step by step instead of just stating the
solution.

**Fixed point mathematics**: A function `f()` can be said to have a fixed point
if when given some value `y`, `f(y) = y`. This is a very high-level way to
describe many other important mathematical relationships, such as square roots.
One "imperative" way to find the fixed point of a function is to continue
feeding the results of a function back into itself recursively; if the results
eventually stop changing, that is the fixed point.

### Course Topics

Overall goal: Controlling complexity in large programs
Ways to do this:

- Black Box Abstraction
- Conventional Interfaces
- Creation of new languages (metalinguistic abstraction)

### Introduction to LISP

When learning a new language, ask:

> What are the primitive elements?
> What are the means of combination?
> What are the means of abstraction?

#### Primitive Data

```lisp
3         ;numbers
17.4
+         ;operators

(+ 1 2 3) ;combinations
```

Combinations can be nested arbitrarily:

```
(+ 3 (* 5 6) 8 2)  ;=> Evaluates to 43
```

Lisp uses Prefix Operation (operators come first). It is also fully
parenthesized; everything gets wrapped up. Parentheses can never be left out;
they have a precise meaning.

Combinations can be thought of as trees, endlessly branching. 2-dimensional
structures represented as linear character strings.

#### Means of Abstraction

```lisp
(define a (* 5 5))
(* a a)  ;=> 25

;; let keyword is equivalent in clisp
```

Defining procedues:

```
(define (square x) (* x x))
(square 10) ;=> 100
```
