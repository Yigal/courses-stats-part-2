---
title: 'Covariance and Correlation'
description: 'Need to know the difference between the two, how to calculate the two (equations can help), advantages and disadvantages, when to use it and what for. Connection to causation.'
attachments:
    slides_link: 'https://s3.amazonaws.com/assets.datacamp.com/production/course_22798/slides/chapter1.pdf'
---

## Looking at Associations with Multivariate Categorical Data

```yaml
type: VideoExercise
key: d388985d36
xp: 50
```

`@projector_key`
9a0dc36c27277778e25aaba8cfc271a8

---

## Calculate covariance

```yaml
type: NormalExercise
key: 48671e7493
xp: 100
```

Typically, a data frame contains multiple variables. It is useful to know how those variables relate to each other. One method to identify this is to calculate [the covariance](https://en.wikipedia.org/wiki/Covariance). To calculate the covariance you use this expression:

$cov(X,Y) = E((X-E(X)) * (Y-E(Y))) $

Where $E(X)$ is the mean value of X, which is also called the expected value.

`@instructions`
You get three number lists of equal length (`X`, `Y`, and `Z`). Calculate the three covariances, and create a variable `result` which contains the tuple $(cov(X,Y), cov(X,Z), cov(Y,Z))$.

`@hint`
$E(X)$ is the mean value of X, which is also called the expected value. Therefore, 

$ cov(X,Y) = \frac{1}{N}\sum\_1^N(x\_n-E(X))(y\_n-E(Y)) = $
$\frac{1}{N}\sum\_1^N(x\_n-\frac{1}{N}\sum\_1^Nx\_i)(x\_n-\frac{1}{N}\sum\_1^Ny\_i)$

Alternatively, you can use the [`statistics.mean`](https://docs.python.org/3/library/statistics.html#statistics.mean) function.

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

Covariance measures the relationship between two variables. But that measurement is affected by a lot of other things, such as the [variance](https://en.wikipedia.org/wiki/Variance) of each variable. The [Pearson correlation coefficient](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient) lets us ignore the variance. If $a>0$, then when $y=ax$ the correlation coefficient is one. When $y=-ax$, the coefficient is minus one. If there is absolutely no correlation, the coefficient is zero.

The formula is:

$\rho\_{X,Y} = \frac{cov(X,Y)}{\sigma\_X \sigma\_Y}$

$\sigma\_X$ is the [standard deviation of $X$](https://en.wikipedia.org/wiki/Standard_deviation). It is defined as $\sqrt{E((x-E(X))^2)}$, where $E(X)$ is the mean of $X$.

`@instructions`
You get three number lists of equal length (`X`, `Y`, and `Z`). Calculate the three correlation coefficients, and create a variable `result` which contains a tuple: ( $\rho\_{X,Y}$, $\rho\_{X,Z}$, $\rho\_{Y,Z}$ )

`@hint`
$\sigma\_X$ is the [standard deviation of $X$](https://en.wikipedia.org/wiki/Standard_deviation). It is defined as $\sqrt{E((x-E(X))^2)}$, where $E(X)$ is the mean of $X$. In other words,

$\sigma\_X = \sqrt{E((x-E(X))^2)} = \sqrt{\frac{1}{N}\sum\_{1}^{N}(x\_n-E(x))^2} = $
$\sqrt{\frac{1}{N}\sum\_{1}^{N}(x\_n-\frac{1}{N}\sum\_{1}^{N}x\_n)^2} = \sqrt{cov(X,X)}$

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

---

## Correlation with a non linear relationship

```yaml
type: MultipleChoiceExercise
key: 5ab1b266d6
xp: 50
```

Can you use the correlation coefficient to check for non linear relationships? 

Use the function `rho(X,Y)` to get the correlation coefficient between two series.

`@possible_answers`
- Yes, you can still use the correlation coefficient
- [No, the correlation coefficient is only useful for relationships that behave similar to linear ones]

`@hint`
What is the correlation coefficient between $x$ and $x^2$ when the range is $(-a,a)$? 

Does it mean there is no relationship between $x$ and $x^2$?

`@pre_exercise_code`
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


"""
X = list(range(-20,20))
Y = list(map(lambda x:x**2, X))

print (rho(X,Y))
"""
```

`@sct`
```{python}

```

---

## Correlation and causation

```yaml
type: PureMultipleChoiceExercise
key: 2426449fc6
xp: 50
```

What do you think is the correlation between amount of medicine taken each day and the chance of dying from a disease?

`@hint`


`@possible_answers`
- [Positive, people who take a lot of medicine are more likely to die of disease]
- Negative, medicine saves lives

`@feedback`


---

## Correlation and causation 2

```yaml
type: PureMultipleChoiceExercise
key: 940e1f5024
xp: 50
```

Does this correlation between medicine and dying mean that medicine is actually harmful?

`@hint`


`@possible_answers`
- Yes, if the correlation is positive it means medicine causes people to die
- No, that result is accidental
- No. **Correlation does not equate causation**. In this case, there is no causal relationship.
- [No, because both variables are caused by a third variable, how sick a person is. Sicker people get more medicine and are more likely to die,]

`@feedback`
