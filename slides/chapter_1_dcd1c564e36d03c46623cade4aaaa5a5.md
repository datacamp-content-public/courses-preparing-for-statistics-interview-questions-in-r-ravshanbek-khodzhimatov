---
title: Insert title here
key: dcd1c564e36d03c46623cade4aaaa5a5

---
## Title Slide

```yaml
type: "TitleSlide"
key: "0a00cec9fd"
```

`@lower_third`

name: Ravshan S.K.
title: Statistical Consultant


`@script`



---
## Assumptions of Linear Regression

```yaml
type: "FullSlide"
key: "0256945d07"
```

`@part1`
1. Linearity in parameters{{1}}
2. Random sampling{{2}}
3. No perfect multicollinearity{{3}}
4. Zero conditional mean of error term: E(u|x) = 0{{4}}


What if they fail?{{5}}


`@script`



---
## When random sampling fails

```yaml
type: "TwoRows"
key: "374659e50c"
```

`@part1`
Selection biases:
1. Survivorship bias
2. Confirmation bias
3. Sample selection bias (job training)


`@part2`
```table(wagereg$MARR)
lm(log(WAGE) ~ SEX, data = subset(wagereg,MARR==1))
lm(log(WAGE) ~ SEX, data = wagereg[sample(500,350),])
```


`@script`



---
## Final Slide

```yaml
type: "FinalSlide"
key: "73cc65ec7d"
```

`@script`


