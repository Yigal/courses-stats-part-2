---
title: 'Estimators and estimates'
description: 'Estimate values'
---

## Bayesian inference

```yaml
type: PureMultipleChoiceExercise
key: 8bb5ecff5e
xp: 50
```

[Bayesian inference](https://en.wikipedia.org/wiki/Bayesian_inference) specifies how we can update the estimated probability of an event given additional information. 

- $P(A)$ is the probability that event A happens (or that a certain hypothesis is true, etc.)
- $P(B)$ is the probability that event B happens
- $P(A|B)$ is the conditional probability of A, when we know that B is true
- $P(A \land B)$ is the probability that both A and B happen.

Bayes' rule is that 

$P(A|B) \times P(B) = P(A \land B) = P(B|A) \times P(A)$

For example, imagine that we throw a dice. 

- A is the event in which the result is 1,2, or 3.
- B is the event in which the result is even: 2,4, or 6.

$P(A) = P(B) = \frac{1}{2}$

$P(A \land B) = \frac{1}{6}$ (it only happens if we throw a two)

If we know that A happened, what is the chance of B?

$P(B|A) = \frac{P(A \land B)}{P(A)} = \frac{\frac{1}{6}}{\frac{1}{2}} = \frac{1}{3}$

For a more interesting example, imagine that we have a coin that may or may not be weighed. There are three possibilities:

1. $H\_0$ : The coin is fair ($)
1. $H\_H$ : The coin is weighed (75%) towards head ($p(H\_H) = 0.25$)
1. $H\_T$ : The coin is weighed (75%) towards tail ($p(H\_T) = 0.25$)

The initial probabilities are $p\_{t=0}(H\_0) = 0.5, p\_{t=0}(H\_H) = p\_{t=0}(H\_T) = 0.25$

After we throw the coin three times and get tail on each one, what is the probability that the coin is weighed towards tail? Select the correct range.

`@hint`
We can call the event of getting tail once T. The conditional probabilities are:

$P(T | H\_0) = 0.5$

$P(T | H\_H) = 0.25$

$P(T | H\_T) = 0.75$

By Bayes's rule:

$P(A|B) \times P(B) = P(B|A) \times P(A) \implies P(A|B) = \frac{P(B|A) \times P(A)}{P(B)}$

Therefore:

$P(H\_x | T) = \frac{P(T|H\_x) \times P(H\_x)}{P(T)}$

The probability that we get T is: $0.75 \times P(H\_T) + 0.5 \times P(H\_0) + 0.25 \times P(H\_H)$

For $t=0$ this gives up $P\_{t=0}(T) = \frac{3}{4}\times \frac{1}{4} + \frac{1}{2}\times \frac{1}{2} + \frac{1}{4}\times \frac{1}{4} = \frac{1}{2}$

$P\_{t=1}(H\_0) = P(H\_0 | T) = \frac{P(T|H\_0) \times P\_{t=0}(H\_0)}{P\_{t=0}(T)} = \frac{1}{2}$

$P\_{t=1}(H\_T) = P(H\_T | T) = \frac{P(T|H\_T) \times P\_{t=0}(H\_T)}{P\_{t=0}(T)} = \frac{0.75 \times 0.25}{0.5} = \frac{3}{8}$

$P\_{t=1}(H\_H) = P(H\_H | T) = \frac{P(T|H\_H) \times P\_{t=0}(H\_H)}{P\_{t=0}(T)} = \frac{0.25 \times 0.25}{0.5} = \frac{1}{8}$

Repeat the process two more times to get $P\_{t=3}(H\_T)$.

`@possible_answers`
- 0 - 0.2
- 0.2 - 0.4
- 0.4 - 0.6
- [0.6 - 0.8]
- 0.8 - 1

`@feedback`


---

## Margin of error

```yaml
type: PureMultipleChoiceExercise
key: eceb6353fc
xp: 50
```

The margin of error is half the size of the confidence interval. We run the experiment from the previous question with 2025 measurements. What is our margin of error for a 90% confidence interval?

Remember that $\sigma\_{variable} = 100$

Select the correct range

`@hint`
- $\sigma\_{mean of samples} = \frac{\sigma\_{variable}}{\sqrt{n}}$
- [This calculator](https://planetcalc.com/7803/) lets you calculate a Z-score from a probability

`@possible_answers`
- 0-1
- 1-2
- 2-3
- [3-4]
- 4-5
- 5-6

`@feedback`


---

## Maximum likelihood estimate

```yaml
type: MultipleChoiceExercise
key: 830d0b1967
xp: 50
```

Read [this explanation of maximum likelihood estimates](https://towardsdatascience.com/probability-concepts-explained-maximum-likelihood-estimation-c7b4342fdbb1). 

In the variable `measurements` we have data that we know follows the [exponential distribution](https://en.wikipedia.org/wiki/Exponential_distribution). Find the best value for $\lambda$, select the correct range

`@possible_answers`
- 0 - 0.5
- 0.5 - 1.5
- [1.5 - 2.5]
- 2.5 - 3.5

`@hint`
- The probability distribution for $x>0$ is $f(x; \lambda) = \lambda \times e^{-\lambda x}$
- The probability distribution of a set of $n$ measurements called $X$ is:

$f(X; \lambda) = \prod{\lambda e^{-\lambda x}} = \lambda^n \prod{e^{-\lambda x}} = \lambda^n e^{\sum -\lambda x} = \lambda^n e^{\lambda \sum -x}$

- To simplify, let's define $S \equiv \sum -x = - \sum x$ 

$f(X; \lambda) = \lambda^n e^{\lambda S}$

- The derivative is

$\frac{\partial f(X; \lambda)}{\partial \lambda}$
$= \lambda^n \frac{\partial e^{\lambda S}}{\partial \lambda} + e^{\lambda S}\frac{\partial \lambda^n}{\partial \lambda}$
$= \lambda^n S e^{\lambda S} + e^{\lambda S}n\lambda^{n-1}$
$= \lambda^{n-1} e^{\lambda S} (\lambda S + n)$

- In the extreme point (in this case, maximum $f(X; \lambda)$) the derivative is zero. Ignoring the possibility $\lambda = 0$, there is only one way for the derivative to be zero.

`@pre_exercise_code`
```{python}
import random

random.seed(10)

measurements = []

for i in range(100):
  measurements.append(random.expovariate(2))
  
  
"""
import statistics

print (1/statistics.mean(measurements))
"""

  

```

`@sct`
```{python}
# Check https://instructor-support.datacamp.com/en/articles/2375523-course-multiple-choice-with-console-exercises on how to write feedback messages for this exercise.
```
