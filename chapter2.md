---
title: 'Confidence Interval'
description: 'Confidence Interval'
attachments:
    slides_link: 'https://s3.amazonaws.com/assets.datacamp.com/production/course_22798/slides/chapter2.pdf'
---

## Estimating a Population Proportion with Confidence

```yaml
type: VideoExercise
key: 0a8a472b30
xp: 50
```

`@projector_key`
4b39ac834b275b5b2b2680ebb26c34a3

---

## Understanding Confidence Intervals

```yaml
type: VideoExercise
key: 08a49a3f7c
xp: 50
```

`@projector_key`
6384527e6be7caa6e337e75734f88b42

---

## Demo: Seeing Theory

```yaml
type: VideoExercise
key: 36f03d7f23
xp: 50
```

`@projector_key`
d710976aaa4596ac14bb2aa99dc56582

---

## Confidence interval (known standard deviation)

```yaml
type: PureMultipleChoiceExercise
key: 601eb00119
xp: 50
```

Using the z-score we can calculate how likely it is that an observed value would fall in a specific range belongs to a specific normal distribution. For example, if $\mu=0, \sigma =1$ then there is a 0.05 probability of an observed value $|x| > 1.95996$. 1.95996 is the z-score for the probability 0.025 and we are looking at both tails.

The logic of z-scores goes both way. If the observed value is zero and we know that we are dealing with a normal distribution with $\sigma=1$, there is a 0.95 probability that the mean is in the $-1.95996 - 1.95996$ range.

We know that a certain variable is normally distributed, and that the normal distribution has a standard deviation of 100. Can we design an experiment that will let us know, with a 0.9 probability or more, that the mean of the distribution is within a range of less than 10?

You can use [this calculator] to obtain the z-score of a desired probability.

`@hint`
The mean value of a sample of $n$ measurements of a normally distributed variable is itself a normally distributed variable with these parameters:

- $\mu\_{mean of samples} = \mu\_{variable}$
- $\sigma\_{mean of samples} = \frac{\sigma\_{variable}}{\sqrt{n}}$

`@possible_answers`
- No, this is impossible to achieve
- Yes, you need to take at least 26 measurements and calculate the sample mean. There is a 0.9 probability that the variable mean is within 5 units of the mean of such a sample
- Yes, you need to take at least 33 measurements and calculate the sample mean. There is a 0.9 probability that the variable mean is within 5 units of the mean of such a sample
- Yes, you need to take at least 657 measurements and calculate the sample mean. There is a 0.9 probability that the variable mean is within 5 units of the mean of such a sample
- [Yes, you need to take at least 1083 measurements and calculate the sample mean. There is a 0.9 probability that the variable mean is within 5 units of the mean of such a sample]

`@feedback`


---

## Conservative Approach & Sample Size Consideration

```yaml
type: VideoExercise
key: c93174867b
xp: 50
```

`@projector_key`
3142b121e54383fbe7da7cf697111d1f

---

## Estimating a Difference in Population Proportions with Confidence

```yaml
type: VideoExercise
key: f64b82c94b
xp: 50
```

`@projector_key`
2edcb6505e048ade269de4a5dc98a3a9

---

## Interpretations & Assumptions for Two Population Proportion Intervals

```yaml
type: VideoExercise
key: 575f4e0906
xp: 50
```

`@projector_key`
92bca206647cfa6fca4636539dfdf9c6

---

## Assumptions for a Single Population Proportion Confidence Interval

```yaml
type: VideoExercise
key: 8eefbbc178
xp: 50
```

`@projector_key`
b700f500d75b3bf11868143ec9175753

---

## Confidence interval (unknown standard deviation)

```yaml
type: MultipleChoiceExercise
key: 626ca922d1
xp: 50
```

The z-score assumes we know the standard deviation. If we have a large enough sample (typically, over thirty measurements), we can usually assume that the standard deviation of the sample is close to the standard deviation of the population. 

When the sample size is smaller, we need to use the [t-score](https://www.statisticshowto.datasciencecentral.com/one-sample-t-test/). In the console there is a list of measurements, `measurements`, that were taken independently of one another. Calculate the 95% confidence interval for the mean of the population the samples were taken from.

`@possible_answers`
- 44.165 - 53.943
- 43.416 - 54.692
- 43.330 - 54.778
- 43.111 - 54.997
- [43.020 - 55.0879]

`@hint`
- The standard deviation of a sample is calculated using [`statistics.stdev`](https://docs.python.org/3/library/statistics.html#statistics.stdev). [It is a slightly different formula than a population's standard deviation](https://en.wikipedia.org/wiki/Bessel%27s_correction).
- You can get the t-score [using this calculator](https://stattrek.com/online-calculator/t-distribution.aspx). 
- Remember that the number of degrees of freedom is one less than the sample size in this case.
- $t = \frac{\bar{x}-\mu}{\frac{s}{\sqrt{n}}} \implies \bar{x}-\mu=\frac{t \times s}{\sqrt{n}}$

`@pre_exercise_code`
```{python}
import random

random.seed(0)
measurements = []

for i in range(10):
  measurements.append(random.normalvariate(50,10))
  
import math
import statistics  

sampleMean = statistics.mean(measurements)
sampleSD = statistics.stdev(measurements)
tScore = 2.262
diffOfMeans = tScore*sampleSD/math.sqrt(len(measurements))

print (sampleMean-diffOfMeans, sampleMean+diffOfMeans)

```

`@sct`
```{python}
# Check https://instructor-support.datacamp.com/en/articles/2375523-course-multiple-choice-with-console-exercises on how to write feedback messages for this exercise.
```

---

## Margin of error

```yaml
type: PureMultipleChoiceExercise
key: e4a49d1c8a
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

## Estimating a Population Mean with Confidence

```yaml
type: VideoExercise
key: 8016ec0d26
xp: 50
```

`@projector_key`
14c86b0a27e65a6d0e2e1801a3e3531e
