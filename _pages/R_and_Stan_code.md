---
permalink: /R and Stan code/
title: "R and Stan code"
---





2 Data Visualization
In ggplot2, you can create an extremely wide range of visualizations, covering almost all standard statistical graphics and many specialized plots, because it is based on the Grammar of Graphics and allows flexible layering and extension.

- For distributional analysis, ggplot2 supports histograms, density plots, frequency polygons, boxplots, violin plots, ridgeline plots, dot plots, and empirical cumulative distribution function (ECDF) plots, all of which help reveal the shape, spread, and skewness of data.
- For relationships between variables, the most common is the scatter plot, which can be extended into bubble charts by mapping size. You can also overlay regression lines, smoothing curves, and confidence bands, and create two-dimensional density plots, contour plots, and hexbin plots for large datasets.
- For comparisons across categories, ggplot2 provides bar charts (count and summarized), grouped and stacked bar charts, proportional (100%) bar charts, lollipop charts, Cleveland dot plots, and mosaic plots (via extensions), all useful for comparing discrete groups.
- For time series and longitudinal data, line plots are the standard, but you can also create area charts, stacked area charts, streamgraphs (via extensions), and ribbon plots to show uncertainty intervals over time.
- For multivariate visualization, ggplot2 enables heatmaps, tile plots, pairwise scatterplot matrices (via extensions like GGally), parallel coordinate plots, and faceted plots that split data into multiple panels for structured comparison across conditions.
- For spatial and geographic data, ggplot2 can produce choropleth maps, point maps, path maps, polygon maps, and raster maps when combined with spatial packages, making it suitable for epidemiology, environmental science, and GIS applications.
- For statistical summaries and uncertainty visualization, you can create error bar plots, pointrange plots, linerange plots, mean and median summary plots, and visualizations of confidence or credible intervals directly from data or model outputs.

In addition, ggplot2 supports specialized and less common visualizations, including QQ plots, PP plots, slope graphs, waterfall charts, funnel plots, dendrograms (via extensions), network visualizations (via packages like ggraph), and interactive-style layered graphics when combined with other tools.

A key strength of ggplot2 is that these plots are not isolated types but composable elements, meaning you can combine geometries, statistical transformations, scales, and facets to construct highly customized visualizations. In this sense, ggplot2 is not just a library of predefined charts but a general framework for designing visual representations of data.
