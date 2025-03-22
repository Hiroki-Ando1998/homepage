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

t-test & Wilcoxson
```yaml
#t test 
t.test(data, data, var.equal=TRUE, paired = FALSE)

#Wilcoxson
library(exactRankTests)
wilcoxson(x = data, y = data, paired = T)

#Effect size (https://www.statology.org/cohens-d-in-r/)
library(effsize)
cliff.delta(data, data)
cohens.d(data, data)
herges_g()
```
- [Chi-square & Fisher-exact & McNemar](https://github.com/Hiroki-Ando1998/R/blob/main/Statistical%20tests%20%26%20epidemiological%20study%20design/1_B_Chi_Fisher_Mcneman.R)
- [ANOVA & Krustical-wallis](https://github.com/Hiroki-Ando1998/R/blob/main/Statistical%20tests%20%26%20epidemiological%20study%20design/1_C_ANOVA_Krustical-wallis.R)


#### Step-wise method (should not be used)
```yaml

```


# 2.Logistic regression analysis


```yaml

```


# 3. Multiple impuation


```yaml

```



