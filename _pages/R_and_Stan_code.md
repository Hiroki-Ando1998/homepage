---
permalink: /R and Stan code/
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

