---
title       : Does transmission affect mileage (Using mtcars Dataset)
subtitle    : Coursera Data Products Project
author      : Murtuza Attarwala
job         : Data Insight Provider
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : github        # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---
## Executive Summary

This application looks at the dataset for 32 different car models (1973-74) from *Motor Trend* magazine and attempts to answer the question  

  - Does automatic/manual transmission have any impact on mpg

By looking at the data, we see that it has normal distribution, so we use linear regression to attempt to answer this question  

The application computes **lm(mpg ~ am, data=mtcars)** model by default, and allows users to add other predictor variables, like weight, number of cylinders and horse power alongwith transmission(am)  

Users can compare the default model with the model computed using additional predictors, which will give them insight into our question, as to whether transmission really does affect mpg or are other factors more important than transmission

---
## How to use the app
- The app has four tabs
  - An about tab briefly describing the app
  - A model summary tab, which shows the summary of the model
  - A model comparison tab, which let's users compare the model with the default model using anova function
  - The residuals plot tab, which plots the residuals vs the predicted values
  
- On the left panel is the set of predictors that the user can select to add to the model, alongside default predictor of transmission(am)

- User can look at the p-value in the model comparison tab, to see if the new model is significantly better than the default

- By looking at the residuals plot the user can verify if there is any heteroskedasticity, and whether linear model will work well for the data or not

--- .smallcode
## Example

- A quick look at the fuel efficiency based on on transmission alone suggests that on average manual transmission gives 7 more miles per gallon

```r
fit1 <- lm(mpg~am, data=mtcars)
summary(fit1)$coeff
##             Estimate Std. Error t value  Pr(>|t|)
## (Intercept)   17.147      1.125  15.247 1.134e-15
## am             7.245      1.764   4.106 2.850e-04
```
- Now let's see what happens when we add other confounding variables like wt, which we suspect can impact mpg

```r
fit2 <- lm(mpg~am+wt, data=mtcars)
summary(fit2)$coeff
##             Estimate Std. Error  t value  Pr(>|t|)
## (Intercept) 37.32155     3.0546 12.21799 5.843e-13
## am          -0.02362     1.5456 -0.01528 9.879e-01
## wt          -5.35281     0.7882 -6.79081 1.867e-07
```

---
## Example Contd.
- We can see that each 1000 pounds of wt decreases the mpg by about 5 miles, and the higher p-value suggests that there is no evidence that transmission type affects mileage, other things being equal

- User can play with different confounding variables to see what affect it has on mileage

--- {
 tpl: thankyou
}

## Thank You
