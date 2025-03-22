---
title: "Data visualization"
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - Post Formats
  - readability
  - standard
---


### Data overview
```yaml
#Histogram
ggplot(data, aes(x = values)) +
  geom_histogram(binwidth = 0.5, fill = "blue", color = "black", aes(y = ..density..)) +
  geom_density(alpha = 0.2, fill = "orange") +
  labs(title = "Histogram of Random Data", x = "Values", y = "Density")

#Boxplot and dotplot
RR_plot <- ggplot(data_fil_1_1, aes(x = 1, y = change))
RR_plot <- RR_plot + geom_boxplot(notch = FALSE, width = 0.9)
RR_plot <- RR_plot + geom_dotplot(binaxis = "y", binwidth = 1.0, stackdir = "center", alpha = 0.5) 
RR_plot <- RR_plot + theme_bw() + theme(
  axis.line = element_line(size = 1.0, lineend = "square"),
  text = element_text(colour ="black", size = 14),
  legend.position = "none",
  axis.ticks = element_line(linewidth = 1.5),
  axis.ticks.length = unit(-2, "mm"))
RR_plot
```

### t-test & Wilcoxson
P-value and effect size should be calculated.
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





# Power test
- library(MESS)
- [github](https://github.com/Hiroki-Ando1998/R/tree/main/Statistical%20tests%20&%20epidemiological%20study%20design)

```yaml
library(MESS)
#Grammer
Power_t_test(n = NULL, delta = NULL, sd = 1, sig.level = 0.05, power = NULL, ratio = 1,
  sd.ratio = 1, type = c("two.sample", "one.sample", "paired"), alternative = c("two.sided", "one.sided"),  df.method = c("welch", "classical"), strict = TRUE)
```
Question:Plasma-glucose levels are used to determine the presence of diabetes. Suppose the mean ln (plasma-glucose) concentration (mg/dL) in 35- to 44-year-olds is 4.86 with standard deviation = 0.54. A study of 100 sedentary people in this age group is planned to test whether they have a higher or lower level of plasma glucose than the general population.  

```yaml
#If you want know unknown
d <- 0.1/0.54
pwr.t.test(n = 200, d = d, sig.level = 0.05, power = NULL)

# If you want to know sample size
d <- 0.1/0.54
pwr.t.test(n = NULL, d = d, sig.level = 0.05, power = 0.80)
```

### Cohort study
Power for comparing two independent proportions (two sample study, cohort study)
Assume that 5% of the non-smokers will develop coronary heart disease during the study. You would like your study to have adequate power to detect a relative risk of 2.0. 
```yaml
#P2 = 0.05%
#P1 = 0.10 % given that relative risk of 2.0
#Given a prevalence of smoking 0.25 (This is assumption from literature review), which represents k = 3 ((1-0.25)/0.25). K is ratio of exposure group to non exposure group.

power_prop_test(n = NULL, p1 =0.1, p2 = 0.05, sig.level = 0.05, power = 0.9, ratio = 3, alternative = “one.sided”) 
#p1 and p2 already known
```


### Case-Control study
Assume that approximately 30% of women of child-bearing age will have an exposure to oral contraceptives. You would like your case-control study to have 90% power to detect an odds ratio of 3.0 at the a = 0.05 level. How many women are needed assuming a 1:1 ratio of cases to controls?  
```yaml
#P2 = 0.3
#Odd = P1*(1-P1)(P2*(1-P2)
#P1 = 0.5625

power_prop_test(n = NULL, p1 =0.5625, p2 = 0.05, sig.level = 0.05, power = 0.9, ratio = 1, alternative = “one.sided”)
```


### Case-Control (Matching) study
Suppose we are interested in comparing the effectiveness of two different antibiotics, A and B, in treating gonorrhea. Each person receiving antibiotic A is matched with an equivalent person (age within 5 years, same gender), to whom antibiotic B is given. These people are asked to return to the clinic within 1 week to see if the gonorrhea has been eliminated. Suppose the results are as follows: (a) for 40 pairs of people, both antibiotics are successful; (b) for 20 pairs of people, antibiotic A is effective whereas antibiotic B is not; (c) for 16 pairs of people, antibiotic B is effective whereas antibiotic A is not; (d) for 3 pairs of people, neither antibiotic is effective. How many matched pairs should be enrolled in a future study if we wish to conduct a two-sided test with  = 0.05 and power = 0.80?
```yaml
P12 <- 20/79 (79 is total pair sample) = 0.2025
P21 <- 16/79 = 0.2532
power.mcnemar_test(n = NULL, paid =0.2025, psi = 0.2532/0.2025, sig.level = 0.05, power = 0.9, ratio = 1, alternative = “two.sided”, method = “normal)
```

# Third variable
- For testing the association between a risk factor and disease adjusting for other factors, stratified analysis should be the first step in the analysis plan.  
- Testing the interaction (MH test of Homogeneity, P < 0.10)  
- If being no interaction, report average (adjusted) odds ratio  

Approach (The similar analysis can be done with logistic regression model)
1.Test whether there is interaction, using woolf’s test (P-value, crude and adjusted odds ratio are shown in R program).
2.If not, check confounding by comparing adjusted and crude odds ratios.
3. Test whether there is association, using the Mantel-Haenszel test (assume no interaction). 

[github](https://github.com/Hiroki-Ando1998/R/blob/main/Statistical%20tests%20%26%20epidemiological%20study%20design/3_A_Third%20variable.R)
```yaml
# Create matrix
data <- c(rep(c(0, 1, 1), 120), rep(c(0, 1, 0), 80), rep(c(0, 0, 1), 111), rep(c(0, 1, 0), 155),
rep(c(1, 1, 1), 161), rep(c(1, 1, 0), 130), rep(c(0, 0, 1), 117), rep(c(0, 1, 0), 124)
data <- matrix(data, ncol = 3, byrow = TRUE)
data <- data.frame(data)
colnames(data) <- c(“personal”, “passive”, “disease”)
 
library(EpiStats)
library(dplyr)
library(knitr)

#Odds ratio stratified 
res1 <- CC(data[data$personal == 0, ], cases = “disease”, exposure = “passive”, exact = TRUE, full = TRUE)
kable(res1$df1, align = “r”)
kable(res1$df2, align = res1$df2.align)
res2 <- CC(d1[d1$personal == 1, ], cases = “disease”, exposure = “passive”, exact = TRUE, full = TRUE)
kable(res2$df1, align = “r”)
kable(res2$df2, align = res2$df2.align)

# Test for whether the two odds ratios differ (Woolf’s test for interaction)
# CCinter: Case-control interaction
res <- CCInter(data, cases = ”disease”, exposure = “passive”, by = “personal”, full = TRUE)
kable(res$df2)

#Test for association assuming no interaction (Mantel-Haenszel χ2 test)
The test should be used only when if the variance V > 5 (χ2 test)
#行列の作成
data <- array(c(98, 832, 169, 3520, + 54, 227, 55, 686, + 11, 85, 61, 926, + 7, 102, 90, 1936), + dim = c(2, 2, 4), + dimnames = list( + Exposure = c("1", "0"), + Response = c("1", "0"), + Race.Level = c("1", "2", "3", "4"))) 
mantelhaen.test(data, correct = FALSE)
 
res4 <- CC(d2, cases = “bw”, exposure = “smoking”, exact = TRUE, full = TRUE)
kable(res4$df2, align = res4$df2.align)
```


### Test Odds trend (linear trend in odds ratio across levels)
Approach 
1. Test homogeneity of odds (all odds ratio is equivalent)
2. If rejected, test for trend

[github](https://github.com/Hiroki-Ando1998/R/blob/main/Statistical%20tests%20%26%20epidemiological%20study%20design/3_B_trend_odds_test.R)
```yaml
#χ2 test (used only if variance is >5) Homogeneity 

disease <- c(320, 1206, 1011, 463, 220)
no_disease <- c(1422, 4432, 2893, 1092, 406)
n <- c(1742, 5683, 3904, 1555, 626)
m <- as.table(cbind(no_disease, disease))
damnames(m) <- list(age = c(“1”, “2”, “3”, “4”, “5”)), + disease = c(“N”, “Y”)
chisq.test(m)
 
# test for trend
prop.trend.test(disease, n, score = seq_along(disease))

#Since p < 0.001, we reject the null hypothesis and conclude that there is a linear trend in the odds
```

Maternal extension test
Goal is to determine whether there is a linear trend in the odds ratios across levels of an (ordinal) risk factor after controlling for a confounder.
```yaml
mantelhaen(table)
```

