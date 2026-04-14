---
permalink: /R_and_Stan_code/
title: "R & Stan code"
---

# 1. Data organization
A central framework of data organization in R is the **tidyverse**, especially the **package dplyr**. Alongside it, **tidyr** focuses on reshaping data between wide and long formats, handling missing values, and ensuring that datasets follow the “tidy data” structure where each variable is a column and each observation is a row. For data import and string handling, packages like **readr** and **stringr** are commonly used, making it easier to read large datasets and clean textual variables in a consistent way. The design philosophy of the tidyverse is to make data preparation readable, chainable, and close to natural language through the pipe operator %>%. For large-scale data processing, packages like **data.table** are often preferred because they are faster and more memory-efficient, especially for big datasets.

These are functions ([Rcode]()) I often use:
- **filter()** means selecting a subset of observations based on conditions, such as keeping only patients older than 60 or only records from a specific time period.
- **select()** means choosing specific variables from a dataset, such as keeping only age, sex, and outcome while removing unnecessary columns.
- **group_by()** dividing data into subsets based on one or more categorical variables, such as grouping by gender.
- **summarize** means aggregating data within groups or across the entire dataset to compute statistics such as mean
- **mutate()** is used to create new variables or modify existing ones based on transformations of other columns. For example, you can compute a new risk score, log-transform a variable, or combine existing variables into a new feature.
- **drop_na()** is used to remove rows that contain missing values (NA).
- **is.na()** is used to detect missing values. It returns a logical vector indicating whether each element is NA, and is often used for filtering, counting missing values, or creating indicators of missingness.
- **which(!is.na(x))** is used to identify the positions of all elements in x that are not *NA*.
- [apply](https://stats.biopapyrus.jp/r/basic/apply.html) is a function used to perform an operation over the rows or columns of a matrix or array without writing explicit loops


# 2 Data Visualization
In R, there are several ways to create visualizations (e.g., ggblend, ggnewscale, gganimate), and ggplot2 is one of the most widely used and influential approaches ([guide book](https://ggplot2-book.org/)).
- For [distributional analysis](https://github.com/Hiroki-Ando1998/R/tree/main/ggplot2/1_DistributionAnalysis): histograms, density plots, frequency polygons, boxplots, violin plots, ridgeline plots, dot plots, and empirical cumulative distribution function (ECDF) plots, all of which help reveal the shape, spread, and skewness of data.
- For [relationships between variables](https://github.com/Hiroki-Ando1998/R/tree/main/ggplot2/2_relationship_betweem_variables): scatter plot, which can be extended into bubble charts by mapping size, regression lines, smoothing curves, and confidence bands, and create two-dimensional density plots, contour plots, and hexbin plots for large datasets.
- For [comparisons across categories](https://github.com/Hiroki-Ando1998/R/tree/main/ggplot2/3_comparison_across_categories): bar charts (count and summarized), grouped and stacked bar charts, proportional (100%) bar charts, lollipop charts, Cleveland dot plots, and mosaic plots (via extensions), all useful for comparing discrete groups.
- For [time series data](https://github.com/Hiroki-Ando1998/R/tree/main/ggplot2/4_time_series_data): line plots are the standard, but you can also create area charts, stacked area charts, streamgraphs (via extensions), and ribbon plots to show uncertainty intervals over time.
- For [multivariate visualization](https://github.com/Hiroki-Ando1998/R/tree/main/ggplot2/5_multivariate_visualization): heatmaps, tile plots, pairwise scatterplot matrices (via extensions like GGally), parallel coordinate plots, and faceted plots that split data into multiple panels for structured comparison across conditions.
- For [spatial data](https://github.com/Hiroki-Ando1998/R/tree/main/ggplot2/6_spatial_data): choropleth maps, point maps, path maps, polygon maps, and raster maps when combined with spatial packages, making it suitable for epidemiology, environmental science, and GIS applications.
- For [statistical summaries and uncertainty visualization](https://github.com/Hiroki-Ando1998/R/tree/main/ggplot2/7_statistical_summaries&uncertainty_visualization): error bar plots, pointrange plots, linerange plots, mean and median summary plots, and visualizations of confidence or credible intervals directly from data or model outputs.
- For displaying how quantities or effects move across categories: Sankey diagram and Alluvial plot can be used. Connections are shown as flowing bands, and the thickness of each band represents the magnitude, proportion, or strength of influence. Their smooth, wave-like appearance comes from the curved connections between nodes, making complex relationships intuitive to interpret.

ggplot2 supports specialized and less common visualizations, including QQ plots, PP plots, slope graphs, waterfall charts, funnel plots, dendrograms (via extensions), network visualizations (via packages like ggraph), and interactive-style layered graphics when combined with other tools.

To create a graph that matches your preferences, you need to adjust elements such as [colors](https://github.com/Hiroki-Ando1998/R/blob/main/ggplot2/1_colour_gradation.R), [plot styles](https://github.com/Hiroki-Ando1998/R/blob/main/ggplot2/2_shape.md), [how multiple plots are combined](https://github.com/Hiroki-Ando1998/R/blob/main/ggplot2/4_combined_figures.R), and [theme settings](https://ggplot2.tidyverse.org/reference/ggtheme.html).


---
# Modeling
In modern data analysis and machine learning, two fundamental requirements are generalization performance and reproducibility ([Ref](https://tjo.hatenablog.com/entry/2026/03/27/170000)), as they determine whether analytical results are both useful for prediction and trustworthy as scientific evidence. 
- **Generalization performance** refers to how well a model trained on observed data performs on unseen data, capturing the ability to extract true underlying patterns rather than overfitting noise. This concept is central in statistical learning, where techniques such as cross-validation are used to estimate out-of-sample predictive accuracy and ensure that models remain valid under future, unknown conditions.
- **Reproducibility** concerns whether an analysis produces the same results when the same data, code, and procedure are applied again, either by the original analyst or by others. It is a cornerstone of scientific reliability, ensuring that findings are not dependent on arbitrary choices, hidden preprocessing steps, or undocumented analytical decisions. In practice, reproducibility requires careful control of the entire analytical pipeline, including data selection, preprocessing, model specification, and evaluation criteria, all of which should be transparently documented and ideally automated.


# 3 Generalized linear model (GLM)
[GLM](https://en.wikipedia.org/wiki/Generalized_linear_model) is a flexible extension of ordinary linear regression that allows the response variable to follow different types of distributions.. 
By combining R with Stan, it becomes possible to extend GLMs into a fully Bayesian framework. This allows for full posterior distributions of parameters, more flexible modeling of uncertainty, and the incorporation of prior information.
- [Linear model]() is used when the outcome variable is continuous and approximately normally distributed. It assumes a linear relationship between predictors and the outcome and is appropriate when the goal is to explain or predict continuous measurements.
- [Logit-Binomial model]() is used when the outcome is binary or represents proportions, such as disease presence/absence, success/failure, or infection status.
- [Poisson regression model]() is used when the outcome is count data, such as the number of cases, events, or occurrences in a fixed time or space. It assumes that the variance is proportional to the mean and is commonly applied in epidemiology and event-rate modeling.



