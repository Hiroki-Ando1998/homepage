---
title: "Data organization & Basic analysis"
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - Post Formats
  - readability
  - standard
---
coming soon
### Data modification
- dplyr
- tidyr
- plyr
- tidyverse

<!--more-->

This post has a manual excerpt `<!--more-->` set after the second paragraph. The following YAML Front Matter has also be applied:

### correlation & Statistical test
```yaml
#Correlation coefficient
cor.test(data_1$hospital, data_1$sapporo, method = "pearson")
cor.test(data_1$hospital, data_1$sapporo, method = "spearman") 


#t test 
t.test(data, data, var.equal=TRUE, paired = FALSE)

#Wilcoxson
library(exactRankTests)
wilcoxson(x = data, y = data, paired = T)

#χ2 test
chisq.test(matrix)

#Fisher exact test
matrix(c(103, 43, 33, 117), nrow=2, byrow = TRUE,
dimnames =list(Season = c("summer", "winter"), Test =c("Positive", "Negative")))
fisher.test(matrix)

#likelihood
lr.test(A, B)

#McNemar’s test
before <- c(89, 5)
after <- c(16, 90)
data_table <- matrix(c(before, after), nrow = 2, byrow = TRUE,
                     dimnames = list(Season = c("effective", "ineffective"),
                                     Test = c("effective", "ineffective")))
mcnemar.test(data_table)

#ANOVA, Krustical-wallis test
anova_result <- summary(aov(Bilsecpt ~ Hormone,data = data_3))
print(anova_result)

kruskal.test(adj ~ A, data = data)

#Effect size (https://www.statology.org/cohens-d-in-r/)
library(effsize)
cliff.delta(data, data)
cohens.d(data, data)
herges_g()

#effecti size for categorical data
condition1 <- c(30, 20, 50)
condition2 <- c(35, 30, 35)
x <- cbind( condition1, condition2 )
cramersV( x )
```


