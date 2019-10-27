---
title: Distributions
description: 'Chapter description goes here.'
---

## Distributions

```yaml
type: PureMultipleChoiceExercise
key: 840128d72b
xp: 50
```

The values of a quantitative variable are usually distributed in one of several ways, depending on the process that generates those values. [Click here to see different distributions](http://simple-tech.com/public_html/statistics/distributions.html).

Which of these distributions has mostly low values with a few high ones?

`@hint`


`@possible_answers`
- Normal
- [Exponential]
- Uniform
- Bernoulli

`@feedback`


---

## Uniform distribution

```yaml
type: PureMultipleChoiceExercise
key: b0025d5748
xp: 50
```

In a [uniform distribution](http://mathworld.wolfram.com/UniformDistribution.html) each value has an equal probability. For example, when you throw dice you have an equal chance of getting each value.

What is the chance of getting either one or six?

`@hint`
There are six possibilities uniformly distributed, so the chance of each is $\frac{1}{6}$. The two events, one and six, are mutually exclusive so the chance of either happening is the chance of one plus the chance of the other.

`@possible_answers`
- $0$, it cannot happen
- $\frac{1}{6}$
- [$\frac{1}{3}$]
- $\frac{1}{2}$
- $\frac{2}{3}$
- $\frac{5}{6}$
- $1$, it always happens

`@feedback`


---

## Adding uniformly distributed random variables

```yaml
type: MultipleChoiceExercise
key: 9ecf1e85b7
xp: 50
```

When you add multiple uniformly distributed variables, you get a distribution that has more entries in the middle than in the edges. For example, if you add the results of two dice throws, you get a graph like this one:

![Adding two dice](https://assets.datacamp.com/production/repositories/5515/datasets/7ea5ff962c69dcf1c150edeefb18b0be9b66ca75/two_dice.png)

Out of 36 possible results, there is only one that gives a sum of two ($1+1$) and only one that gives a sum of twelve ($6+6$). However, there are six possibilities for seven ($1+6, 2+5, ... , 6+1$). 

If we add three dice, we get this graph:

![Adding three dice](https://assets.datacamp.com/production/repositories/5515/datasets/91de587281abb23156c84c55fc4c34449c56c927/three_dice.png)

Use Python to calculate the chance that when you throw four dice you'll get a value of ten or less.

`@possible_answers`
- [Correct answer 1]
- Wrong answer 2
- Wrong answer 3

`@hint`
* You can simulate throwing a single die with `random.choice(range(1,6))`

`@pre_exercise_code`
```{python}
"""
import random

def die_throw():
	return random.choice(range(1,6))
  
  
def run_test():
	return die_throw()+die_throw()+die_throw()+die_throw() < 11
    
    
successes = 0
total_tests = 1000

for i in range(total_tests):
	if run_test():
    	successes++
        
print successses/total_tests
"""
```

`@sct`
```{python}

```
