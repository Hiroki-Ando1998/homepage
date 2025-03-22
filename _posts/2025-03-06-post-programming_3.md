---
title: "Generalized linear model (R code)"
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - Post Formats
  - readability
  - standard
---
# R packages
- car
- Mass
- lme4 (liner mixed model)

# 1.Linear regression model
1. Linear relationship of coefficients  
2. Normality of residuals (Shapilo wilk test, Q-Q plot, histogram)  
3. Homoscedasticity (statistical test, variance does not depend on level of X)  
4. Independent observation (i.e., no correlation between samples)

```yaml
#plot
RR_plot <- ggplot(data, aes(x = X, y = Y, colour = males))
RR_plot <- RR_plot + geom_point()
RR_plot <- RR_plot + scale_colour_brewer(palette = "Set1")
RR_plot <- RR_plot + geom_smooth(method = "lm", formula = y ~ x, aes(col = “lift”))
RR_plot <- RR_plot + labs(title = "Linear regression", x = "Number of drivers (log10)", y = "deaths (log10)")
RR_plot <- RR_plot + theme_classic() + theme(
  axis.line = element_line(linewidth = 1.0, lineend = "square"),
  text = element_text(colour ="black", size = 14),
  legend.position = "none",)

#linear model
res_lm <-  lm(Y ~ X + males + X*males, data = data) 
summary(res_lm)

#Regression and confidence interval
X_new <- data.frame(X = 23:60)
Conf <- predict(res_lm, X_new, interval = ‘confidence’, level = 0.95)
Conf <- predict(res_lm, X_new, interval = ‘prediction’, level = 0.95)
```
- [Normality & Homoscedasticity](https://github.com/Hiroki-Ando1998/R/blob/main/Generalized%20linear%20model/1_B_Normality_Homoscedasticity.R)
- [Outliners](https://github.com/Hiroki-Ando1998/R/blob/main/Generalized%20linear%20model/1_C_Detecion%20of%20outliers.R)
- [Collinearity](https://github.com/Hiroki-Ando1998/R/blob/main/Generalized%20linear%20model/1_D_Collinearity.R)
- Coversion of variables  
  Interaction  
- Confounding  
- Fitness or predictive performance  

Conversion of varaibles, interaction, confunding could be identified with likelihood test.(But Baysian modeling is better) 
1. Fit the model containing the variables we want to test and save the log-likelihood.
2. Fit the model removing the variables we want to test and save the log-likelihood.
3. Compare the two log-likelihoods to perform the likelihood ratio test (e.g., testing whether interaction is present)
4. Compute the odds ratio


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
#pin : プロット領域, par : 余白の指定
par(pin = c(3,3))
par(mar = c(3, 3, 3, 3))
p1 <- ggplot(data, aes(x = Clinical, y = WBE)) #WBE: 0 or 1
p1 <- p1+ geom_point(alpha = 0.4, shape = 21, size = 2, colour = "black", fill = "grey")  + scale_x_log10()
p1 <- p1 + stat_smooth(method = glm, method.args = list(family = binomial), fullrange = TRUE)


lo_1 <- glm(disease ~ passive, data = ex_1[ex_1$personal ==0, ], family = binomial(link = “logit”))
summary(lo_1)

#compute the odds ratio
library(oddsratio)
or_glm(ex_1, lo_1, incr = list(passive = 1))
```
- [likelihood ratio test](https://github.com/Hiroki-Ando1998/R/blob/main/Generalized%20linear%20model/2_A_logistic_likelihood.R)
- [Interaction](https://github.com/Hiroki-Ando1998/R/blob/main/Generalized%20linear%20model/2_B_Interaction.R)
- [Confounding](https://github.com/Hiroki-Ando1998/R/blob/main/Generalized%20linear%20model/2_C_Confounding.R)
- [Goodness of fit (Hosmer-Lemeshow test)](https://github.com/Hiroki-Ando1998/R/blob/main/Generalized%20linear%20model/2_D_Hosmer-Lemeshow_test.R)
- [Goodness of fit (Outlinear & ROC curve)](https://github.com/Hiroki-Ando1998/R/blob/main/Generalized%20linear%20model/2_E_Outlinear_ROC%20curve)


# 3. Multiple impuation
- library(mice)
- library(Amelia)  
- library (miceadds)  
- [R code](https://github.com/Hiroki-Ando1998/R/blob/main/Generalized%20linear%20model/3_A_Multiple%20imputation)  
詳しくは、"欠測データ処理 Rによる単一代入法と多重代入法, P97  

```yaml
library(mice)
library(miceadds)　#library(Amelia)を使用するのもよい

# 例となるデータの作成 (# 一部の値を欠損させる)
set.seed(123)
mydata <- data.frame(
  y = rbinom(100, 1, 0.5),            # 応答変数（0か1の二項変数）
  x1 = rnorm(100),                    # 説明変数1
  x2 = rnorm(100),                    # 説明変数2
  x3 = rnorm(100)                     # 説明変数3
)
mydata[sample(1:100, 20), "x1"] <- NA
mydata[sample(1:100, 20), "x2"] <- NA


# 欠損値を多重代入で補完（mice）
imp <- mice(mydata, m = 5, method = "pmm", seed = 500)

# 補完されたデータセットでロジスティック回帰モデルをフィッティング
logit_model <- with.mids(imp, glm(y ~ x1 + x2 + x3, family = binomial()))
pooled_results <- pool(logit_model)
summary(pooled_results)
```



