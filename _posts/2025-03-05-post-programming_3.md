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
coming soon


### Modeling
1. General linear modeling
- Mass
- lme4 (liner mixed model)

### Linear regression model
```yaml
res_lm <- lm (Y ~ X + as.factor(D), data = d) 

#Regression and confidence interval
X_new <- data.frame(X = 23:60)
Conf <- predict(res_lm, X_new, interval = ‘confidence’, level = 0.95)
Conf <- predict(res_lm, X_new, interval = ‘prediction’, level = 0.95)
```




The following R code is used for logistic regression analysis:
```yaml
lo_f <- glm(disease ~ passive*personal, data = ex_1, family = binomial(link = “logit”))
summary(lo_1)
```

- miceadds (multiple imputation)  
The following R code is used for multiple imputation:

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

#詳しくは、"欠測データ処理 Rによる単一代入法と多重代入法, P97
```

### Logistic regression model
```yaml
#pin : プロット領域, par : 余白の指定
par(pin = c(3,3))
par(mar = c(3, 3, 3, 3))
p1 <- ggplot(data, aes(x = Clinical, y = WBE)) #WBE: 0 or 1
p1 <- p1+ geom_point(alpha = 0.4, shape = 21, size = 2, colour = "black", fill = "grey")  + scale_x_log10()

p1 <- p1 + stat_smooth(method = glm, method.args = list(family = binomial), fullrange = TRUE)
res = glm(WBE ~ Clinical, data, family=binomial)
summary(res)

```



