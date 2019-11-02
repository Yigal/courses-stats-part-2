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

* The [null hypothesis](https://en.wikipedia.org/wiki/Null_hypothesis) is that the treatment didn't affect the measured variable. This is the default position, which we accept unless the chance of it being true is very small (usually less than 0.05, but for medical experiments typically 0.01).

* The alternative hypothesis, which is that the treatment does have an effect



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
      
- id: alternative
  title: "Alternative Hypothesis"
  items: 
    - content: "After watching a ten minute commercial for candy, more people will prefer cheese to bread than in a control group that didn't watch the commercial"
      id: commercialCheese
    - content: "After watching a ten minute commercial for candy, more people will prefer bread to cheese than in a control group that didn't watch the commercial"
      id: commercialBread      

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
successMessage: "Congratulations" # Message shown when all is correct.
failureMessage: "Try again!" # Message shown when there are errors (and there is no specific error available).
isOrdered: false # Should the items in the zones be ordered as in the solution code?
```
