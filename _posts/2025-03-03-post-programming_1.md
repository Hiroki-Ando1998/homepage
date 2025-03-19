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

### Data treatment
```yaml
# NA Remove
A <- Data %>% drop_na(data$column)

#Replace (A列のNAを5, ｂ列のNAを3にする。)
replace_na(data_name, list(column_a = 5, column_b = 3)

#Coversion
mutate(data_name, new_column_name = na_if(column_name, 4)

#detection of NA
is.na(x)

#Filter and select
Filter: A <- Data_name %>% filter(Column_name =="urban" )
Filter: A <- Data_name %>% filter(Column_name,  X < 0 | X 1> 12 ) #or
data_2 <- data_1 %>% mutate(anxiousyoga = if_else(Q7 == 5 | Q7 == 6, 1, 0))
#!= 4 (not equal), AかつB: X < 0 & X 1> 12

Select: A <- Select (Data, column name, column name)

# Addition of work column
A <- data_name %>% mutate(column_name = “cold”)

# lag and behind column
A <- mutate(data_name, new_column_name = lag(column_name, 3, defalt = 0)
# 0 will be put to column moved

Multiplication
mutate(data_name, new_column_name = column_name * 3)

#Replacement values  in one condition
mutate(data_name, new_column_name = if_else (x1 > 3, 4, x1)

#Change of values in multiple conditions (https://www.sharpsightlabs.com/blog/case-when-r/)
mutate(new_column_name = case_when(
Column_name == 0 & column == “A” ~ 1,
Column_name == 0 & column == “B” ~ 1,
True ~ 0) #それ以外の値は0

#Change of column name
colnames(data) <- c("name”, “name”, "name”, “name”)
Data <- data %>% rename(length = len)

#Change of categorical data name
fct_recode(data$A, S = “small”, M = “medium”, L = “large”)

#Change of order of categorical data
size <- factor(data$A, levels = c(“small”, “medium”, “large)

Rearrangement of row
#Countryのアルファベット順に並び替え
Data_GDP <- Data_GDP %>% arrange(Country)

#GDPの小さい順に並べ替え 
Data <- data %>% order(dataset$Weight, decreasing = TRUE))

#Combine row or column
Data <- rbind(data, data)
Data <- cbind(data, data)


```


### Basic statistics & data overview
```yaml
head(data, 5)
#Number of row and column
nrow(data_name)
ncol(data_name)

#Name of row and column
names(data_name) 
colnames(data_name)

#Table 
Table(data$col)

#Summary
summary(data$col)

#quantile
quantile(data$A, c(0.025, 0.5, 0.975))

#Histogram
ggplot(data, aes(x = values)) +
  geom_histogram(binwidth = 0.5, fill = "blue", color = "black", aes(y = ..density..)) +
  geom_density(alpha = 0.2, fill = "orange") +
  labs(title = "Histogram of Random Data", x = "Values", y = "Density")

#Boxplot and dotplot
RR_plot <- ggplot(data_fil_1_1, aes(x = 1, y = change))
RR_plot <- RR_plot + geom_boxplot(notch = FALSE, width = 0.9)
RR_plot <- RR_plot + geom_dotplot(binaxis = "y", binwidth = 1.0, stackdir = "center", alpha = 0.5) 
RR_plot <- RR_plot + theme_classic() + theme(
  axis.line = element_line(size = 1.0, lineend = "square"),
  text = element_text(colour ="black", size = 14),
  legend.position = "none",
  axis.ticks = element_line(linewidth = 1.5),
  axis.ticks.length = unit(-2, "mm"))
RR_plot

mean(data$aA, na.rm = TRUE) #exclude NA
median()
mode()
max()
min()

# unbiased variance 
var()
sd(data, na.rm = FALSE)

covariance <- cov(c1, c2)


```

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


