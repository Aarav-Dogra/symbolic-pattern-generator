# symbolic-pattern-generator

This code aims to enumerate potential functions to match the data-points you give it  (currently just (x_1,y_1)...(x_n,y_n)) in between some complexity bounds k_1 & k_2

I measure the complexity by what the minimum info required to describe the object is.

I do this from a repition operator and the successor functions, and vairables are also extra info.

examples:

Let K(v) be the 'complexity' of v

Let S(x) be the successor function = x+1, this has a complexity of 1

let O^b (a) mean O(O(O(... a))) which means like nested function composition repeated b times. This repition operator has a complexity of 1.

For example, A(a,b) = a+b = S^b (a) and a*b = A^b (0,a)

the complexity of A(a,b) is 4, because it requires the info that the repition operator is being applied(1), the input 'b' is being used for the repition operator (1), and the input 'a' (1) is used for the successor function (1). 1+1+1+1 = 4.

K(a*b) = 6, K(a^b) = 8 and K(a+b+c) = K((a+b)+c) = 4 + K(+c) = 4+3 coz K(+c) is K(x+y) (which = 4) but minus the info of x because we already have (a+b) as x, 4-1 = 3. 4+3 = 7.

example input & output:

%Run 'under complexity k generator 2.py'

data points (e.g., (1,1),(2,2),(3,3)): (1,0),(-1,0),(0,0),(2,6)

complexity min bound k1: 4

complexity max bound k2: 15

=== Streaming matches y = f(x) with K* in [4,15] ===

K*=9: y = ((x ^ 3) - x)

K*=11: y = (((x * x) - 1) * x)


**Why Should This Work?**
With addition -> multiplication -> exponentiation, we can analyse many things accurately without the need for special functions. If we choose the least minimum description length (least complexity) patterns for data, we oversimplify instead of overcomplicating things, which is computationally easier. Additionally, Solomonoff induction showed that the optimal predictor weights hypotheses by 2^(-K(h)) for K(h) is the Kolmogorov complexity, which means simpler explanations have exponentially higher prior probability. I have attempted to create a computable version of Kolmogorov complexity by assuming a repetition operator & the successor function are just 1 complexity point each. 

Also, this is slightly irrelevant, however the 'max_unique' variable is what allows ur computer to explore more variety/complexity (it's so ur computer finishes in time)
if you increase it alot, and you have lots of compute power/time, then it can even find things like data points of cos(x), as (e^(ix) - e^(ix))/2, so it's got potential!
