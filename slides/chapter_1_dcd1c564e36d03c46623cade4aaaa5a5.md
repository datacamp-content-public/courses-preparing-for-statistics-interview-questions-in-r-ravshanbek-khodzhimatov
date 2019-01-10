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
In this lesson, we are going to review the Linear Regression assumptions and see what happens if they fail.


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
So, firstly, the regression equation should be linear in parameters as we have discussed this before.

The sample should be random for statistics to work.

There should be no perfect multicollinearity between variables, meaning no two explanatory variables should mean the same thing.

The conditional error should have an average of 0.

So, let's see what they mean and why are they important.


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
So, all of our statistics depends on the random sampling assumption. Otherwise, our models would fail.

You might have heard of survivorship bias, when people interviewed the ship wreck survivors who told that the reason they are alive is that they didn't give up, implying that dead people gave up, which we don't know.

In this code, we can see that there are 350 married people. The coefficients differ if we select those 350 randomly or based on their status.


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
Collinearity happens when two variables carry exactly the same information. Like weight in kilograms and weight in pounds, or age and birthyear.

R detects this automatically, and deactivates one of the variables. You can see that in code below.


---
## Non-zero mean error

```yaml
type: "FullSlide"
key: "e359492d6d"
```

`@part1`
- u means "error term" and "unobserved variables" (mother's maiden name, color of jeans){{1}}
- E[y|x] = E[xb+u|x] = xb + E[u|x]{{2}}
- If E[u|x]>0, then we have omitted an important variable.{{3}}

```
> summary(lm(log(WAGE) ~ SEX + AGE + SECTOR, data=wagereg))
             Estimate Std. Error t value Pr(>|t|)    
(Intercept)  1.809693   0.073882  24.494  < 2e-16 ***
SEX         -0.245413   0.044573  -5.506 5.73e-08 ***
AGE          0.009675   0.001873   5.164 3.42e-07 ***
SECTOR       0.020861   0.041277   0.505    0.614
```{{4}}
```
> summary(lm(log(WAGE) ~ SEX + AGE + SECTOR + EDUCATION, data=wagereg))
             Estimate Std. Error t value Pr(>|t|)    
(Intercept)  0.526584   0.128647   4.093 4.92e-05 ***
SEX         -0.236854   0.039828  -5.947 4.97e-09 ***
AGE          0.012350   0.001689   7.310 9.90e-13 ***
SECTOR       0.099452   0.037492   2.653  0.00823 ** 
EDUCATION    0.089025   0.007661  11.620  < 2e-16 ***
```{{5}}


`@script`
u is called error term, but it's more correct to call it unobserved effects. This includes billions of variables irrelevant to our model. Like, in our regression, the color of your jeans or the maiden name of your mom, the planet that you live in - are all omitted but they make zero affect on average.

But if, on average, the unobserved term makes nonzero effect, then we have omitted an important variable.

You can see in the code that SECTOR of work is not important to WAGE and insignificant, but when you EDUCATION, it becomes much more controlled for - because education does affect wages.


---
## Measurement error

```yaml
type: "FullSlide"
key: "64c03e877a"
center_content: false
```

`@part1`
- Y = xb + u, where Y = y - e => y = xb + (u+e) : fine, just greater variance
- y = Xb + u, where X = x + e => y = xb + (be + u), and E[be+u|x]>0, biased and inconsistent.


`@script`



---
## Final Slide

```yaml
type: "FinalSlide"
key: "73cc65ec7d"
```

`@script`


