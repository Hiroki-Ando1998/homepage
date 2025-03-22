---
title: "Statistical test & epidemiological study designs (R code)"
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - Post Formats
  - readability
  - standard

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





# 2.Power test
- library(MESS)

```yaml
library(MESS)
#Grammer
Power_t_test(n = NULL, delta = NULL, sd = 1, sig.level = 0.05, power = NULL, ratio = 1,
  sd.ratio = 1, type = c("two.sample", "one.sample", "paired"), alternative = c("two.sided", "one.sided"),  df.method = c("welch", "classical"), strict = TRUE)
```
question:Plasma-glucose levels are used to determine the presence of diabetes. Suppose the mean ln (plasma-glucose) concentration (mg/dL) in 35- to 44-year-olds is 4.86 with standard deviation = 0.54. A study of 100 sedentary people in this age group is planned to test whether they have a higher or lower level of plasma glucose than the general population.  

```yaml
#If you want know unknown
d <- 0.1/0.54
pwr.t.test(n = 200, d = d, sig.level = 0.05, power = NULL)

# If you want to know sample size
d <- 0.1/0.54
pwr.t.test(n = NULL, d = d, sig.level = 0.05, power = 0.80)
```



# 3. Multiple impuation


```yaml

```



