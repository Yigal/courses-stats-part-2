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




`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- This is an example hint.
- This is an example hint.

`@possible_answers`
- [Correct answer 1]
- Wrong answer 2
- Wrong answer 3

`@feedback`
<!-- Examples of good feedback messages: https://instructor-support.datacamp.com/en/articles/2299773-exercise-success-messages.  -->
- Perfect!
- Error message answer 2
- Error message answer 3
