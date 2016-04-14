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

```lisp
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

```lisp
(define (square x) (* x x))
(square 10) ;=> 100
```

This can also be written as:

```lisp
(define square (lambda (x) (* x x)))
```

Lambda is Lisp's way of saying "make a procedure"

Case analysis / conditional statements:

```lisp
(define (abs x)
  (cond ((< x 0) (- x))
        ((= x 0) 0)
        ((> x 0) x)))
```

A more restricted case analysis: 

```lisp
(define (abs x)
  (if (< x 0)
      (- x)
      x))
```

#### Basic algorithm

Based on Heron of Alexandria's algorithm for finding squares:

> To find an approximation of the square root of x
> Make a guess, G
> Improve the guess by averaging G and x / G
> Keep improving the guess until it is good enough
> Use 1 as the initial guess

How to write this in lisp?

```lisp
;; Here is the final procedure made up of higher-order functions
;; The "dependencies" utilized are:
;; improve and good-enough?
;; Importantly, the procedure also calls itself recursively.

(define (sqrt-iter guess x)
  (if (good-enough? guess x)
      guess
      (sqrt-iter (improve guess x) x)))


;; The improve procedure is defined in terms of average

(define (improve guess x)
  (average guess (/ x guess)))

;; The average procedure

(define (average x y) 
  (/ (+ x y) 2))

;; The good-enough? procedure - value depends on how accurate we need to be

(define (good-enough? guess x)
  (< (abs (- (square guess) x)) 0.001))

;; Finally, call the function and use 1 as initial value

(define (sqrt x)
  (sqrt-iter 1.0 x))

```

Other languages would use a `while` or `for` loop to solve this sort of problem.
In lisp, the preferred approach is to rely on **recursion** instead.
