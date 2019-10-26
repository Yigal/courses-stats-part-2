---
title: Distributions
description: 'Chapter description goes here.'
---

## Standard normal distribution

```yaml
type: TabExercise
key: 51c7ad2f89
xp: 100
```

A distribution is the ideal shape that a quantitative variable's graph would take if we had an infinite number of values. In this chapter you learn about the most common distributions: normal, exponential, etc.

`@pre_exercise_code`
```{python}

```

***

```yaml
type: NormalExercise
key: f0bf5942ee
xp: 100
```

`@instructions`
The [normal distribution](http://mathworld.wolfram.com/StandardNormalDistribution.html) appears when a variable is the sum of uniformly distributed random values.

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- This is an example hint.
- This is an example hint.

`@sample_code`
```{python}

```

`@solution`
```{python}
import random

def sum_of_randoms(n):
  if (n == 0):
    return 0
  else:
    return random.uniform(-1,1)+sum_of_randoms(n-1)
  
  
print (sum_of_randoms(100))
```

`@sct`
```{python}
# Examples of good success messages: https://instructor-support.datacamp.com/en/articles/2299773-exercise-success-messages.
```
