# Haskell Notes

## Chapter 1 - Intro to Lambda Calculus

### Terms:

Lambda has 3 basic components

1. Variable - identifier for an input or output.
2. Abstraction - a lambda function. Includes a head and a body, takes a single input and outputs a single output. Any computational logic can be written as a lambda abstraction (boolean, numbers, operations, etc.).
3. Expression - superset of all 3, can include any of them.

lambda expression - `λx.xy`

λx is the head. x is the parameter in the head.
xy is the body. x is bound to the x in the parameter in this case. y is a free identifier.

a lambda expression is anonymous - it has no name.

1. alpha equivalence

substantive equivalence rather than formalistic. When 2 functions will do the same operation on an input, they are substantively equivalent - or alpha equivalent.

λx.xx is ⍺ equivalent to λy.yy.
λx.x is alpha equivalent to λy.y.

2. beta equivalence / beta reduction

beta reduction means actually applying / reducing functions until they reach their normal form - i.e. a form that can not be reduced any further with the information that we know. To apply an argument, drop the lambda head and replace the bound variable with the applied parameter.


Order is:
1. Apply leftmost outermost arguments first.
2. When there are no more arguments left to apply, go to nested arguments.

```
(λx.x)2
reduces to
2
```

* Combinator = all variables are bound, none are free.

```
(λxy.x) or (λy.yyy)
```

* Divergence = infinite loop. e.g. `(λx.xx)(λx.xx)`

### Multiple arguments
First apply the leftmost argument, then continue onwards. 
Multiple arguments just appear adjacent to one another.

### Handling multiple parameters
Use currying to translate multiple parameters into single parameters.

```
λxy.xyz
-> λx.λy.xyz

λabc.a
-> λa.λb.λc.a
```

### Tips for successful beta reduction:

1. Make sure to differentiate between free and bound variables, even if they have the same name. Rename the bound variable to something else to make sure reduction is accurate.

```
(λx.(λy.xy))y
// 2 different y variables here. One is bound to λy and the one on the end is free.
// We'll rename the bound variable to `t` to make life easier.

-> (λx.(λt.xt))y
-> λt.yt
```

2. I like to write my currying down first (i.e. to simplify abstractions with multiple parameters in the head using currying) before proceeding. Then I apply all arguments, from left outermost to right.


