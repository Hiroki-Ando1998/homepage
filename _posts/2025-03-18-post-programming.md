---
title: "2. R programming & Packages"
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - Post Formats
  - readability
  - standard
---
備忘録兼落書きです。
### Data modification
- dplyr
- tidyr
- plyr
- tidyverse

### Visualization
- [ggplot2](https://r4ds.had.co.nz/data-visualisation.html)
- [gganimate](https://gganimate.com/)
- [ggblend](https://mjskay.github.io/ggblend/)
- ggnewscale

### Modeling
1. General linear modeling
- Mass
- lme4 (liner mixed model)

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

2. Baysian modeling and time-series analysis
- [Rstan](https://mc-stan.org/docs/2_19/stan-users-guide/index.html)
