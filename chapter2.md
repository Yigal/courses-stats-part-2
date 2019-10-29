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
# Examples of good success messages: https://instructor-support.datacamp.com/en/articles/2299773-exercise-success-messages.
```
