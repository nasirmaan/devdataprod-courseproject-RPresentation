---
title       : MPG Prediction System
subtitle    : Motor Trend
author      : Nasir Mahmood
job         : Course Project - Developing Data Products
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Introduction

1. Mile per gallon (MPG) depends on car feature
2. Develop multivariable regression model for MPG prediction
2. Web-based MPG prediction application
3. Demonstrate the application
4. Summary

--- .class #id 

## Problem
A car's MPG depends on number of features;

1. Weight
2. Horse Power
4. Number of cylinders

Existing data shows reasonable relationship between above features and MPG. Therefore you can model this relations and can use it to build an effective MPG prediction system.

--- .class #id

## Method

Simple Multivariable Regresion Model with predictors:
  
  - Weight
  - Hourse Power
  - Cylinder

For concept validation, we used mtcars data;


```r
data(mtcars)
fit <- lm(mpg ~ wt + hp + cyl, data = mtcars)
summary(fit)$coeff
```

```
##             Estimate Std. Error t value  Pr(>|t|)
## (Intercept) 38.75179    1.78686  21.687 4.799e-19
## wt          -3.16697    0.74058  -4.276 1.995e-04
## hp          -0.01804    0.01188  -1.519 1.400e-01
## cyl         -0.94162    0.55092  -1.709 9.848e-02
```


--- .class #id

## Demo
On previous Correlation of predictors is significant except hp variable. We assume with large training data set, hp variable will also turn into a significant variable.

For prediction, a user will have to pride wight, horse power and cylinder values of his car. Base on model (fit), our MPG system will predict MPG and also give confidence interval e.g.


```r
newdata <- data.frame(wt = 4, hp = 100, cyl = 6)
predict(fit, newdata, interval = "predict")
```

```
##     fit   lwr   upr
## 1 18.63 13.15 24.11
```

Where 18.63 is predict MPG and [13.15, 24.11] its confidence interval.



--- .class #id

## Summary
- Regression Model for MPG prediction is simple and easily interpretable
- A robust model
- Weight and number of cylinders have significant correlations with MPG
- R's lm function used to build regression model for prediction
- Demo shows prediction results
- Model still has room for improvement

--- .class #id



