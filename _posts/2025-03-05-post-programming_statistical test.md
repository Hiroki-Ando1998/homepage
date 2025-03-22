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


#### Step-wise method (should not be used)
```yaml

```


# 2.Logistic regression analysis


```yaml

```


# 3. Multiple impuation


```yaml

```



