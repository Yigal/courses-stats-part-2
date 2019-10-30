---
title: 'Covariance and Correlation'
description: 'Need to know the difference between the two, how to calculate the two (equations can help), advantages and disadvantages, when to use it and what for. Connection to causation.'
---

## Calculate covariance

```yaml
type: NormalExercise
key: 48671e7493
xp: 100
```

Typically, a data frame contains multiple variables. It is useful to know how those variables relate to each other. One method to identify this is to calculate [the covariance](https://en.wikipedia.org/wiki/Covariance). To calculate the covariance you use this expression:

$cov(X,Y) = E((X-E(X)) * (Y-E(Y)))$

Where $E(X)$ is the mean value of X, which is also called the expected value.

`@instructions`
You get three number lists of equal length (`X`, `Y`, and `Z`). Calculate the three covariances, and create a variable `result` which contains the tuple $(cov(X,Y), cov(X,Z), cov(Y,Z))$.

`@hint`


`@pre_exercise_code`
```{python}
length = 50

import random

random.seed(10)

X = []
Y = []
Z = []

for i in range(length):
  X.append(random.random()* 10)
  Y.append(X[i] + random.random())
  Z.append(random.random() * 20)
  
```

`@sample_code`
```{python}

```

`@solution`
```{python}
import statistics

def cov(X,Y):
  E_X = statistics.mean(X)
  E_Y = statistics.mean(Y)
  return statistics.mean(map(lambda x,y: (x-E_X)*(y-E_Y), X, Y))

result = (cov(X,Y), cov(X,Z), cov(Y,Z))
```

`@sct`
```{python}
Ex().check_object("result").has_equal_value()
```

---

## Covariance and addition

```yaml
type: PureMultipleChoiceExercise
key: 9895ce4388
xp: 50
```

What happens to the covariance if you add a five to every members of the first series?

`@hint`
Remember, $cov(X,Y) = E((X-E(X)) * (Y-E(Y)))$. What happens to the mean when you add a constant to the series? What happens to the difference between that mean and one of the values?

`@possible_answers`
- The covariance gets smaller by five
- [The covariance stays the same]
- The covariance gets bigger by five

`@feedback`


---

## Covariance and multiplication

```yaml
type: PureMultipleChoiceExercise
key: 0259ed5b29
xp: 50
```

What happens to the covariance if you multiply each member of the

`@hint`
Remember, $cov(X,Y) = E((X-E(X)) * (Y-E(Y)))$. What happens to the mean when you multiply a series by a constant? What happens to the difference between that mean and any of the values?

`@possible_answers`
- The covariance gets smaller (half as big)
- The covariance stays the same
- [The covariance gets bigger (twice as big)]

`@feedback`


---

## Correlation coefficient

```yaml
type: NormalExercise
key: 9d9558b371
xp: 100
```

Covariance measures the relationship between two variables. But that measurement is affected by a lot of other things, such as the [variance](https://en.wikipedia.org/wiki/Variance) of each variable. The [Pearson correlation coefficient](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient) lets us ignore the variance. If $a>0$, then when $y=ax$ the correlation coefficient is one. When $y=-ax$, the coefficient is minus one. The formula is:

$\rho\_{X,Y} = \frac{cov(X,Y)}{\sigma\_X \sigma\_Y}$

$\sigma\_X$ is the [standard deviation](https://en.wikipedia.org/wiki/Standard_deviation). It is defined as $\sqrt{E((x-E(X))^2)}$

`@instructions`
You get three number lists of equal length (`X`, `Y`, and `Z`). Calculate the three covariances, and create a variable `result` which contains a tuple: ( $\rho\_{X,Y}$, $\rho\_{X,Z}$, $\rho\_{Y,Z}$ )

`@hint`


`@pre_exercise_code`
```{python}
length = 50

import random

random.seed(10)

X = []
Y = []
Z = []

for i in range(length):
  X.append(random.random()* 10)
  Y.append(X[i] + random.random())
  Z.append(random.random() * 20)
  
```

`@sample_code`
```{python}
Ex().check_object("result").has_equal_value()
```

`@solution`
```{python}
import statistics
import math

def cov(X,Y):
  E_X = statistics.mean(X)
  E_Y = statistics.mean(Y)
  return statistics.mean(map(lambda x,y: (x-E_X)*(y-E_Y), X, Y))

def stdDev(X):
  E_X = statistics.mean(X)
  return math.sqrt(statistics.mean(map(lambda x: (x-E_X)**2, X)))

def rho(X,Y):
  return cov(X,Y)/(stdDev(X)*stdDev(Y))

result = (rho(X,Y), rho(X,Z), rho(Y,Z))
```

`@sct`
```{python}
# Examples of good success messages: https://instructor-support.datacamp.com/en/articles/2299773-exercise-success-messages.
```
