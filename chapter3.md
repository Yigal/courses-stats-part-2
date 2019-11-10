---
title: 'Hypothesis Testing'
description: 'Need to understand how to derive a hypothesis from a given problem, the difference between the null and the alternative hypothesis, what does the rejection region mean, types of errors including how to calculate it + explain their meaning, and know when to use each statistical test and calculate the critical value for each.'
---

## Hypothesis, null and otherwise

```yaml
type: DragAndDropExercise
key: c5122c99a7
xp: 100
```

One of the main uses of statistics is to test if a hypothesis, a testable theory, is correct. 

In most cases, we want to check if a treatment of some kind changes a measurable outcome. To do that, we create two populations: the treated population and the control group. We treat the first group but not the second, and then check between two possibilities:

* The [null hypothesis](https://en.wikipedia.org/wiki/Null_hypothesis) is that the treatment didn't affect the measured variable, or that a phenomena hasn't happened. This is the default position, which we accept unless the chance of it being true is very small.

* The [alternative hypothesis](https://en.wikipedia.org/wiki/Alternative_hypothesis), which is that the treatment did have an effect, or that a certain phenomena has happened.

`@instructions`
For each statement, classify whether it is a null hypothesis, an alternative hypothesis, or not a hypothesis at all.

`@hint`


`@solution`
```{python}
- id: Statements
  title: "Statements"

- id: nullHyp
  title: "Null Hypothesis"
  items: 
    - content: "After watching a ten minute commercial for candy, the ratio of people who prefer cheese to bread will be unchanged"
      id: commercialNull
    - content: "Patient A is not having a heart attack"
      id: Aneg

- id: alternative
  title: "Alternative Hypothesis"
  items: 
    - content: "After watching a ten minute commercial for candy, more people will prefer cheese to bread than in a control group that didn't watch the commercial"
      id: commercialCheese
    - content: "After watching a ten minute commercial for candy, more people will prefer bread to cheese than in a control group that didn't watch the commercial"
      id: commercialBread
    - content: "Patient A is having a heart attack"
      id: Apos

- id: notHypothesis
  title: "Not a Hypothesis"
  items:
    - content: "Cheese tastes better than bread"
      id: cheeseBetter
```

`@sct`
```{python}
checks: # Individual checks and custom messages per item. This is optional. Without it, it will check that the options are as in the solution code.
  - condition: check_target(cheeseBetter) == notHypothesis
    incorrectMessage: 'How do you objectively test if cheese tastes better than bread? If you cannot, it is not a hypothesis'
  - condition: check_target(commercialCheese) == alternative
    incorrectMessage: 'The hypothesis here is that a treatment (commercial for candy) will change preferences, that is an alternative hypothesis'
  - condition: check_target(commercialBread) == alternative
    incorrectMessage: 'The hypothesis here is that a treatment (commercial for candy) will change preferences, that is an alternative hypothesis'    
  - condition: check_target(commercialNull) == nullHyp
    incorrectMessage: 'The hypothesis here is that a treatment (commercial for candy) will not affect preferences, that is a null hypothesis'
  - condition: check_target(aNeg) == nullHyp
    incorrectMessage: 'The phenomena is that the patient is having a heart attack, the null hypothesis is that the patient does not have one'
  - condition: check_target(aPos) == alternative
    incorrectMessage: 'The phenomena is that the patient is having a heart attack, the alternative hypothesis is that the patient does have one'    
successMessage: "Congratulations" # Message shown when all is correct.
failureMessage: "Try again!" # Message shown when there are errors (and there is no specific error available).
isOrdered: false # Should the items in the zones be ordered as in the solution code?
```

---

## Identifying effects #1

```yaml
type: PureMultipleChoiceExercise
key: f5acaf39b1
xp: 50
```

Before throwing dice Gary the Gambler prays to [Fortuna](https://en.wikipedia.org/wiki/Fortuna), the Roman goddess of luck, for a high result. He gets a six. Based **only** on this information, is Fortuna real?

`@hint`


`@possible_answers`
- Yes, it wouldn't have happened otherwise
- [Maybe, but this result could have happened by chance ($\frac{1}{6} \approx 0.1667$). So we don't reject the null hypothesis that it was pure luck]
- No, Roman goddesses don't exist. That is a silly question

`@feedback`


---

## Identifying effects #2

```yaml
type: PureMultipleChoiceExercise
key: a94fd7d931
xp: 50
```

Gabi (the other gambler) throws the same dice five times, and gets six each time. Gary accuses her of cheating. What do you think?

`@hint`


`@possible_answers`
- Yes, the result she got is impossible without cheating
- [Yes, the result she got is possible but very unlikely ${(\frac{1}{6})^5} \approx 0.00012$]
- No, it could have happened randomly, so there is no reason to think the dice is not balanced

`@feedback`


---

## Statistical significance #1

```yaml
type: PureMultipleChoiceExercise
key: 616cad7432
xp: 50
```

As the previous two questions demonstrated, whether we reject the null hypothesis (it's all just chance) or not depends on how likely the result is to have happened randomly. If the chance of the result happening randomly is smaller than our chosen [significance level](https://en.wikipedia.org/wiki/Statistical_significance), we assume that the null hypothesis is incorrect and therefore accept the alternative hypothesis. In most fields, a significance level of 5% is considered sufficient. 

For example, imagine that we have a coin. We'll call one side of it "head" and the other "tail". The first we tossed it, it landed on head. How many more times does it need to land on head for us to conclude that the coin is weighed so it can only land on head with a significance level of 5%?

`@hint`
The null hypothesis is that the coin is fair, and lands on head half the time. Therefore, the chance of it landing repeatedly on head is:

| Tosses | Chance all heads under null hypothesis |
|---|---|
| 1 | 0.5 |
| 2 | 0.25 |
| 3 | 0.125 |
| 4 | 0.0625 |
| 5 | 0.03125 |

`@possible_answers`
- 1
- 3
- 4 
- [5]
- 6
- 7

`@feedback`


---

## Statistical significance #2

```yaml
type: PureMultipleChoiceExercise
key: a3691bf123
xp: 50
```

Let's get another coin. We suspect it is weighed to land on one side each time, but we're not sure which side. How many more times does it need to land on the same side for us to conclude that the coin is weighed so it can only land on that side with a significance level of 5%?

`@hint`
The null hypothesis is that the coin is fair, and lands on head half the time. Therefore, the chance of it landing repeatedly on the same side is:

| Tosses | Chance all heads under null hypothesis | Chance all tails under null hypothesis |
|---|---|---|
| 1 | 0.5 | 0.5 |
| 2 | 0.25 | 0.25 |
| 3 | 0.125 | 0.125 |
| 4 | 0.0625 | 0.0625 |
| 5 | 0.03125 | 0.03125 |
| 6 | 0.015625 | 0.015625 |

`@possible_answers`
- 1
- 3
- 4
- 5
- [6]
- 7

`@feedback`


---

## Danger with statistical significance

```yaml
type: MultipleChoiceExercise
key: 2a8c170496
xp: 50
```

Now we have a test for a weighed coin: toss the coin six times, and see if it lands on the same side on all six times. It works with a significance level of 0.05, because the chance of it happening randomly under the null hypothesis is $(1/2)^5 = 0.03125$.

If we had a hundred fair coins and used this test, how many false positives will we have? How many fair coins will we identify as weighed on the average? By the way, this type of mistake, rejecting the null hypothesis when it is correct, is also called a [Type I error](https://en.wikipedia.org/wiki/Type_I_and_type_II_errors). 

Note: select the correct range

`@possible_answers`
- <1
- 1-2
- 2-3
- [3-4]
- 4-5
- 5-6

`@hint`
The answer is the expected value of the [Bernoulli distribution](https://en.wikipedia.org/wiki/Bernoulli_distribution) times the number of experiments. Alternatively, you can use Python to calculate the answer.

`@pre_exercise_code`
```{python}
"""
import math

p = pow(0.5,5)
n = 100
k = range(n+1)   # Number of successes is anything from zero to n.
prob = [pow(p,k)*pow(1-p,n-k) for k in k]
binom = [math.factorial(n)/(math.factorial(k)*math.factorial(n-k)) for k in k]
expected = 0
for k in k:
	expected += k*prob[k]*binom[k]
    
print(expected)
"""
```

`@sct`
```{python}
# Check https://instructor-support.datacamp.com/en/articles/2375523-course-multiple-choice-with-console-exercises on how to write feedback messages for this exercise.
```

---

## What went wrong?

```yaml
type: PureMultipleChoiceExercise
key: 85051b2cb8
xp: 50
```

As you've seen, statistical significance can be tricky. The statistical significance has to be compared with the null hypothesis for the entire experiment, not applied to each part separately. The correct null hypothesis, in this case, is **none of the coins are weighed**. To reject this hypothesis, we need to be more than 95% sure that a specific coin is weighed. What probability do we need for each coin to reach an overall significance level of 0.05?

Note: Select the correct range

`@hint`
- If the probability of a type I error for a specific coin (the coin is considered weighed while it is fair) is $p$, the probability of correctly surmising the coin is fair is $1-p$.

- To accept the null hypothesis, we need it to be correct for all coins. The likelihood of that is $(1-p)^n$ where $n$ is the number of coins.

- Therefore, the chance we'll reject the null hypothesis erroneously is $1-(1-p)^n$. This is the significance level.

- From $1-(1-p)^{100} = 0.05$ you can get the value of $p$.

`@possible_answers`
-    0.01 - 0.001
- [ 0.001 - 0.0001]
-  0.0001 - 0.00001
- 0.00001 - 0.000001
- <         0.000001

`@feedback`
- If the probability of a type I error for a specific coin (the coin is considered weighed while it is fair) is $p$, the probability of correctly surmising the coin is fair is $1-p$. To accept the null hypothesis, we need it to be correct for all coins. The likelihood of that is $(1-p)^n$ where $n$ is the number of coins. Therefore, the chance we'll reject the null hypothesis erroneously is $1-(1-p)^n$. This is the significance level. $1-(1-p)^n = 0.05 \implies (1-p)^n = 0.95 \implies 1-p = 0.95^\frac{1}{n} \implies p = 1-0.95^\frac{1}{n} \implies p \approx 5.128 * 10^{-4}$

---

## Z-scores

```yaml
type: PureMultipleChoiceExercise
key: edf2016b74
xp: 50
```

A lot of variables behave according to the [normal distribution](https://en.wikipedia.org/wiki/Normal_distribution). When dealing with those variables, it is often useful to use the [z-score](https://en.wikipedia.org/wiki/Standard_score). The z-score is the number of standard deviations a value is from the mean. For example, if the mean is 100 and the standard deviation is 10, then 120's z-score is 2. The z-score for 95 is -0.5. 

The z-score also tells us how likely a result is. Except for the mean and standard deviation, all standard distributions are identical - and the z-score let us ignore those variables. Use a [calculator, such as this one](https://www.socscistatistics.com/pvalues/normaldistribution.aspx) to calculate the likelihood that a normally distributed value will have a z-score of 2 or more.

Note: Select the correct range.

`@hint`
- Enter the z-score
- The p value you get is the probability that a value will have that z-score or higher.

`@possible_answers`
- 0 - 0.01
- 0.01 - 0.02
- [0.02 - 0.04]
- 0.04 - 0.08
- 0.08 - 0.16

`@feedback`


---

## Z scores and blood sodium

```yaml
type: PureMultipleChoiceExercise
key: c56b953e7f
xp: 50
```

The normal ranges for most blood components were calculated using this method:

1. Measure the values for a lot of people
1. Verify that the values are normally distributed
1. Identify the bottom 5% of values and top 5% of values as abnormal, set the range between the 5'th percentile and the 95'th percentile.

In the case of blood sodium, the normal range is 135-145 $[\frac{mm}{L}]$. What is the standard deviation?

Note: Select the correct range

`@hint`
1. The normal distribution is symmetrical. The 5'th percentile and the 95'th percentile are an equal distance from the mean.
1. You can use [a z calculator](https://measuringu.com/zcalcp/) to identify the z score that corresponds to 5%. Note that it should be one tailed 5%, because they defined as out of the range both the bottom 5% and the top 5%. If you calculate a two tailed value, it is 10%, the total percent defined as abnormal.
1. $z = \frac{x-E(x)}{\sigma} \implies \sigma = \frac{x-E(x)}{z}$.

`@possible_answers`
- < 1.5 $[\frac{mm}{L}]$
- 1.5-2.5 $[\frac{mm}{L}]$
- [2.5-3.5 $[\frac{mm}{L}]$]

`@feedback`


---

## Standard deviation of mean value

```yaml
type: PureMultipleChoiceExercise
key: a684bbd7db
xp: 50
```

[Caucasian birth weight at a certain hospital had a mean of 3369 grams and a standard deviation of 567 grams](https://academic.oup.com/aje/article-abstract/141/12/1177/148415?redirectedFrom=fulltext). Imagine there's a new illegal drug, methacaine. 
We want to know if when women take methcaine in pregnancy it causes lower birth weight. In the last year a hundred Caucasian women gave birth while addicted to methacaine in that hospital.

To check if their mean birth weight is statistically significant, we need to know the standard distribution for a sample of a hundred birth weights. According to [this page](https://en.wikipedia.org/wiki/Standard_error#Standard_error_of_the_mean) the standard distribution of a sample mean is $\sigma\_{\bar{x}} = \frac{\sigma}{\sqrt(n)}$.

What is the standard deviation for the mean of a hundred Caucasian birth weights in this hospital? Select the correct range.

`@hint`


`@possible_answers`
-  0-25 gr
- 25-50 gr
- [50-75 gr]
- 75-100 gr

`@feedback`


---

## Z-test (known standard deviation)

```yaml
type: PureMultipleChoiceExercise
key: 5718b14ea7
xp: 50
```

This is the same scenario as the previous question. [Caucasian birth weight at a certain hospital had a mean of 3369 grams and a standard deviation of 567 grams](https://academic.oup.com/aje/article-abstract/141/12/1177/148415?redirectedFrom=fulltext). Imagine there's a new illegal drug, methacaine. We want to know if when women take methcaine in pregnancy it causes lower birth weight. 

In the last year a hundred Caucasian women gave birth while addicted to methacaine in that hospital. The mean birth weight for them was 2965 grams. With a statistical significance of 5%, can we say that methacaine causes lower birth weight?

`@hint`
- Under the null hypothesis we'd expect the mean of a sample of a hundred births to be the same as the population mean (3369 gr.), normally distributed at a standard deviation of $\sigma\_{mean} = \frac{\sigma\_{single}}{\sqrt{n}} = 56.7 gr$
- $z = \frac{\mu_{sample} - \mu\_{population}}{\sigma\_{mean}}$
- You can convert between z values and probabilities [here](https://www.socscistatistics.com/pvalues/normaldistribution.aspx).

`@possible_answers`
- [The alternative hypothesis is correct and methcaine causes lower birth weight]
- The null hypothesis is correct and methcaine does not cause lower birth weight

`@feedback`


---

## One tail and two tails

```yaml
type: PureMultipleChoiceExercise
key: dc62d7821c
xp: 50
```

Sometimes an experiment is to show change in a specific direction, such as low birth weight when the mother is on methacaine. At other times, we just want to identify if there's an effect, regardless of direction. For example, to show that a certain medicine is safe, we need to show it does not affect unrelated medical variables in either direction.

To do this, we look at both tails of the distribution, the high end and the low end. This is called a [two-tailed test](https://www.investopedia.com/terms/t/two-tailed-test.asp). The $p$ probability we are focusing on (also called $\alpha$) is the probability of a Type I error (a false positive, rejecting the null hypothesis when it is true). 

If the acceptable chance of a Type I error is $0.05$, what is the acceptable chance of the sample mean being too high?

`@hint`
If the null hypothesis is correct, the sample mean is expected to follow the normal distribution and be symmetrical around the mean value.

`@possible_answers`
- 0
- 0.01
- 0.2
- [0.025]
- 0.05
- 0.075
- 0.1

`@feedback`


---

## Estimating parameters from samples

```yaml
type: PureMultipleChoiceExercise
key: 001c9e3b1b
xp: 50
```

To calculate the z-score and check the hypothesis, we need two parameters for the original, untreated, population:

- The population mean 
- The population standard deviation

The population mean is relatively easy to approximate using the mean of a sample. But when the sample size is small, the standard deviation is biased to be different from the population standard deviation. In what way?

`@hint`
In the extreme case of a sample of one, the mean is equal to the sample value. What is the standard deviation then?

`@possible_answers`
- [The sample standard deviation is likely to be smaller than the real standard deviation]
- The statement above is untrue. The sample standard deviation is a good approximation of the population standard deviation
- The sample standard deviation is likely to be bigger than the real standard deviation

`@feedback`


---

## T-score

```yaml
type: MultipleChoiceExercise
key: dd5fa5603d
xp: 50
```

When we need to deal with an unknown standard deviation using 
a small sample (typically less than thirty values), we can use [Student's T-test](https://www.britannica.com/science/Students-t-test). The calculation is complex, so we [use a lookup table](http://www.ttable.org/student-t-value-calculator.html) instead, looking at the t-score rather than the z-score.

The t-score is calculated similarly to the z-score, but using sample values instead of population values. When the control sample is the same size as the treated sample, the t-score is calculated using this formula:

$t = \frac{\overline{x\_{treated}}-\overline{x\_{control}}}{s/\sqrt{n}}$

- $t$ is the t score
- $\overline{x\_{treated}}$ is the mean of the variable in the treated population
- $\overline{x\_{control}}$ is the mean of the variable in the control population. If the real population mean ($\mu$) is known, use that instead.
- $s$ is the standard deviation of the variable in the control population
- $n$ is the number of samples in the treated population

Note: When calculating the standard deviation of a sample, we use $N-1$ for reasons that are [explained here](https://www.khanacademy.org/math/ap-statistics/summarizing-quantitative-data-ap/more-standard-deviation/v/review-and-intuition-why-we-divide-by-n-1-for-the-unbiased-sample-variance)

You are given two lists of values: `treated` and `untreated`. From those two lists, calculate the t-score and select the correct range.

`@possible_answers`
- 0-0.5
- 0.5-1
- 1-1.5
- [1.5-2]
- 2-2.5

`@hint`


`@pre_exercise_code`
```{python}
import random

random.seed(10)

treated = []
untreated = []

for i in range(10):
  untreated.append(random.normalvariate(0,2))
  treated.append(random.normalvariate(1,1))
  

"""
import statistics
import math

diff = statistics.mean(treated)-statistics.mean(untreated)
meanSD = statistics.stdev(untreated)/math.sqrt(len(treated))
print (diff/meanSD)
"""
```

`@sct`
```{python}
# Check https://instructor-support.datacamp.com/en/articles/2375523-course-multiple-choice-with-console-exercises on how to write feedback messages for this exercise.
```
