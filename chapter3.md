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

## Statistical significance

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
- [5]
- 7

`@feedback`
