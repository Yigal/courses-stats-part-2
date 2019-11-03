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

## Hypothesis testing and z-tests

```yaml
type: MultipleChoiceExercise
key: 9458bac450
xp: 50
```

It is extremely common for the results of an experiment to be averaged together to form a mean value. If the experiment is repeated [these mean values tend to be distributed in a normal distribution](https://en.wikipedia.org/wiki/Central_limit_theorem).

For example, we know that a certain 

`@possible_answers`
- [Correct answer 1]
- Wrong answer 2
- Wrong answer 3

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- This is an example hint.
- This is an example hint.

`@pre_exercise_code`
```{python}

```

`@sct`
```{python}
# Check https://instructor-support.datacamp.com/en/articles/2375523-course-multiple-choice-with-console-exercises on how to write feedback messages for this exercise.
```

---

## Design a z-test experiment

```yaml
type: MultipleChoiceExercise
key: 29bd33f6fa
xp: 50
```



For example, take [the birth weight of babies in the UK](https://www.healthknowledge.org.uk/public-health-textbook/research-methods/1b-statistical-methods/statistical-distributions). It is a normal distribution with a mean of 3.39 kg and a standard distribution of 0.55 kg. Let's assume there is a new drug on the street, Methcaine. We want to show that Methcaine causes low birth weight.

The $H\_0$ (null hypothesis) is that Methcaine does not cause low birth weight. $H\_a$, the alternative hypothesis, is that it does. 

`@possible_answers`
- [Correct answer 1]
- Wrong answer 2
- Wrong answer 3

`@hint`


`@pre_exercise_code`
```{python}

```

`@sct`
```{python}

```
