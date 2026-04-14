---
permalink: /R_and_Stan_code/
title: "R and Stan code"
---





# 2 Data Visualization
In R, there are several ways to create visualizations, and ggplot2 is one of the most widely used and influential approaches
- For distributional analysis: histograms, density plots, frequency polygons, boxplots, violin plots, ridgeline plots, dot plots, and empirical cumulative distribution function (ECDF) plots, all of which help reveal the shape, spread, and skewness of data.
- For relationships between variables: scatter plot, which can be extended into bubble charts by mapping size, regression lines, smoothing curves, and confidence bands, and create two-dimensional density plots, contour plots, and hexbin plots for large datasets.
- For comparisons across categories: bar charts (count and summarized), grouped and stacked bar charts, proportional (100%) bar charts, lollipop charts, Cleveland dot plots, and mosaic plots (via extensions), all useful for comparing discrete groups.
- For time series and longitudinal data: line plots are the standard, but you can also create area charts, stacked area charts, streamgraphs (via extensions), and ribbon plots to show uncertainty intervals over time.
- For multivariate visualization: heatmaps, tile plots, pairwise scatterplot matrices (via extensions like GGally), parallel coordinate plots, and faceted plots that split data into multiple panels for structured comparison across conditions.
- For spatial and geographic data: choropleth maps, point maps, path maps, polygon maps, and raster maps when combined with spatial packages, making it suitable for epidemiology, environmental science, and GIS applications.
- For statistical summaries and uncertainty visualization: error bar plots, pointrange plots, linerange plots, mean and median summary plots, and visualizations of confidence or credible intervals directly from data or model outputs.
- For displaying how quantities or effects move across categories: Sankey diagram and Alluvial plot can be used. Connections are shown as flowing bands, and the thickness of each band represents the magnitude, proportion, or strength of influence. Their smooth, wave-like appearance comes from the curved connections between nodes, making complex relationships intuitive to interpret.

In addition, ggplot2 supports specialized and less common visualizations, including QQ plots, PP plots, slope graphs, waterfall charts, funnel plots, dendrograms (via extensions), network visualizations (via packages like ggraph), and interactive-style layered graphics when combined with other tools.


# 3 Generalized linear model (GLM)
[GLM](https://en.wikipedia.org/wiki/Generalized_linear_model) is a flexible extension of ordinary linear regression that allows the response variable to follow different types of distributions.. 
In practice, GLMs are widely used for binary outcomes (logistic regression), count data (Poisson regression), and skewed continuous data. This framework is particularly important in epidemiology and public health, where outcomes are often not normally distributed.
By combining R with Stan, it becomes possible to extend GLMs into a fully Bayesian framework. Through packages such as rstan, users can specify the same linear predictor structure but estimate the model using Bayesian inference via Markov Chain Monte Carlo methods. This allows for full posterior distributions of parameters, more flexible modeling of uncertainty, and the incorporation of prior information.
- [Linear model]
- [logit-Binomial]()
- [Poisson regression model]()

In modern data analysis and machine learning, two fundamental requirements are generalization performance and reproducibility ([Ref](https://tjo.hatenablog.com/entry/2026/03/27/170000)), as they determine whether analytical results are both useful for prediction and trustworthy as scientific evidence. 
- **Generalization performance** refers to how well a model trained on observed data performs on unseen data, capturing the ability to extract true underlying patterns rather than overfitting noise. This concept is central in statistical learning, where techniques such as cross-validation are used to estimate out-of-sample predictive accuracy and ensure that models remain valid under future, unknown conditions.
- **Reproducibility** concerns whether an analysis produces the same results when the same data, code, and procedure are applied again, either by the original analyst or by others. It is a cornerstone of scientific reliability, ensuring that findings are not dependent on arbitrary choices, hidden preprocessing steps, or undocumented analytical decisions. In practice, reproducibility requires careful control of the entire analytical pipeline, including data selection, preprocessing, model specification, and evaluation criteria, all of which should be transparently documented and ideally automated.

