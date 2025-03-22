---
title: "Statistical test & epidemiological study designs (R code)"
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - Post Formats
  - readability
  - standard
---
# R packages


# 1.Linear regression model
1. Linear relationship of coefficients  
2. Normality of residuals (Shapilo wilk test, Q-Q plot, histogram)  
3. Homoscedasticity (statistical test, variance does not depend on level of X)  
4. Independent observation (i.e., no correlation between samples)

```yaml
#plot

```



#### Step-wise method (should not be used)
```yaml
lm_model <- lm(data = fev, logfev ~ Age + Hgt + sex + smoke)
 
ols_step_both_p(lm_model, pent = 0.05, prem = 0.051) #The P-value of 0.05 is the threshold.
ols_step_best_subset(lm_model)
```


# 2.Logistic regression analysis
1. Output is binary variable  
2. Linear relationship of coefficient  
3. Independent observations

```yaml

```


# 3. Multiple impuation
- library(mice)
- library(Amelia)  
- library (miceadds)  
- [R code](https://github.com/Hiroki-Ando1998/R/blob/main/Generalized%20linear%20model/3_A_Multiple%20imputation)  
詳しくは、"欠測データ処理 Rによる単一代入法と多重代入法, P97  

```yaml

```



