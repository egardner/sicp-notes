# Structure and Interpretation of Computer Programs

## Lecture 2 Notes

A very simple program that computes the sum of the squares of two numbers:

```lisp
(define (SOS x y)
  (+ (SQ x) (SQ y)))
(define (SQ x)
  (* x x))
  
;; (SOS 3 4) => 25
```

### The Substitution Model

This is the simplest model to represent a process running in a computer program.

