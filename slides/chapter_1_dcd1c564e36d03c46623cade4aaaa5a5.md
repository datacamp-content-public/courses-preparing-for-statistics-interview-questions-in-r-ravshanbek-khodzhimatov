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
## Non-random sampling

```yaml
type: "TwoRows"
key: "374659e50c"
```

`@part1`
Selection biases (survivorship bias, confirmation bias, sample selection bias).
```
> table(wagereg$MARR)
  0   1 
184 350 
> lm(log(WAGE) ~ SEX, data = subset(wagereg,MARR==1))
Coefficients:
(Intercept)          SEX  
     2.2665      -0.3358  
> (lm(log(WAGE) ~ SEX, data = wagereg[sample(500,350),]))
Coefficients:
(Intercept)          SEX  
     2.1361      -0.1798  
```


`@part2`



`@script`



---
## Collinearity

```yaml
type: "FullSlide"
key: "6f562a200b"
```

`@part1`
No meaning, infinitely many answers, R omits. Same with (0,1).

```
> wagereg$BIRTHYEAR <- 2019 - wagereg$AGE
> lm(log(WAGE) ~ SEX + AGE, data=wagereg)
Coefficients:
(Intercept)          SEX          AGE  
   1.814098    -0.249419     0.009761  
> lm(log(WAGE) ~ SEX + BIRTHYEAR, data=wagereg)
Coefficients:
(Intercept)          SEX    BIRTHYEAR  
  21.521221    -0.249419    -0.009761  
> lm(log(WAGE) ~ SEX + AGE + BIRTHYEAR, data=wagereg)
Coefficients:
(Intercept)          SEX          AGE    BIRTHYEAR  
   1.814098    -0.249419     0.009761           NA  
```


`@script`



---
## Non-zero mean error

```yaml
type: "FullSlide"
key: "e359492d6d"
```

`@part1`
E[u|x] = 0


`@script`



---
## Measurement error

```yaml
type: "FullSlide"
key: "64c03e877a"
```

`@part1`
32


`@script`



---
## Final Slide

```yaml
type: "FinalSlide"
key: "73cc65ec7d"
```

`@script`


