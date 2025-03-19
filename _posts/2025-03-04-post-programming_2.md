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
[github_Hiroki Ando](https://github.com/Hiroki-Ando1998/R/tree/main/ggplot2)

### Visualization
- [ggplot2](https://r4ds.had.co.nz/data-visualisation.html)
- [gganimate](https://gganimate.com/)
- [ggblend](https://mjskay.github.io/ggblend/)
- ggnewscale

### plot type
```yaml
#Scatter plots
geom_point()

# Line, bar
ggplot(data, aes(x =factor(dose), y = length, colour = supp, group = supp) 
#group should be mentioned for geom line

geom_line(linetype = “dash”, size = 1, colour = “blue”) 
#linetype https://ggplot2.tidyverse.org/reference/aes_linetype_size_shape.html#:~:text=The%20linetype%20aesthetic%20can%20be,in%20consecutive%20positions%20in%20the

geom_bar(width = 1, position = position_dodge(0.7) #dodgeは横並び, position = “fill” 100%bar

#Area and interval
geom_area() + geom_line()  #position = “fill” 100%ba
geom_ribbon(aes(ymin = A, ymax =B), alpha = 0.2)

#dotplot and boxplot
ggplot(data, aes( x = interaction(A, B, C), y = D), #divided into several groups
geom_boxplot(outlier.color = NA)

geom_dotplot(binaxis = y, binwidth = 0.5, stackdir = “center”, fill = NA)
geom_violin(scale = “data$A”) #adjument of area with value of data$A

#histogram
geom_histogram(position = “identity”, binwidth = 4) #identity: overlap several histograms

#density
geom_density()
geom_line(stat = “density”)

ggplot(data, aes(x = A, y = ..density..)) + geom_histogram() + geom_density()

ggplot(data, aes(x = A, y = B) + geom_point() +
stat_density2d(aes(alpha = ..density..), geom = “raster”, contour = FALSE) 
#fill = density, geom = “tile

#heattmap (ヒートマップ stat_density2dでも)
geom_tile()
geom_raster()

#frequency line
geom_freqploy()

＃Empirical cumulative distribution function (累積分布)
ggplot(data, aes(x = A)) + stat_ecdf()

#Q-Qplot
p1 <- ggplot(data, aes(sample = MA_0_1)) + geom_qq(shape = 21, size = 2.3, colour = "black", fill = "grey") 
p1 <- p1 + geom_qq_line() + theme_bw()
p1


#correlation matrix
library(GGally)
ggpairs(data)

```

### Basic function
- [guide book](https://ggplot2-book.org/themes)
- [plot shape](https://www.sthda.com/english/wiki/ggplot2-point-shapes)
- [theme](https://r-charts.com/ggplot2/themes/) (title, axis, legend, facet title)
- [scale_xx_manual](https://ggplot2.tidyverse.org/reference/scale_manual.html) (fill, colour, shape, gradation, size)

### Scater plot
```yaml
library(scales)
plot <- ggplot(Data_GDP, aes(x = AA, y = BB, fill = factor(Dummy)))
plot <- plot + geom_point(shape = 21, size = 3.0, colour = "black")
plot <- plot + scale_fill_manual(values = c("lightskyblue3", "thistle1"))
plot <- plot + scale_y_log10(breaks = 10^(-7:-2), labels = trans_format("log10", math_format(10^.x)))

plot <- plot + scale_x_continuous(limits = c(1.5, 5.5), breaks = seq(2, 5, 1), label = NULL)
plot <- plot + theme_classic()
plot <- plot + theme_bw(
  axis.line = element_line(size = 1.0, lineend = "square"),
  text = element_text(colour ="black", size = 14),
  legend.position = "none",
  axis.ticks = element_line(linewidth = 1.5),
  axis.ticks.length = unit(-2, "mm"))
plot

ggsave(path = NULL, file = "file_name.svg", plot = plot, dpi = 600, width = 4, height = 3.2)
```

### Box plot
```yaml
plot <- ggplot(data_all_sample, aes(x = as.factor(COUNTY), y = adjust_cidm, fill = as.factor(sample))) + geom_boxplot() +
  labs(x = "County", y = "Concentration (ug/g or ug/L)")
plot <- plot + scale_fill_manual(values = c("lightblue", "orange", "red"))
plot <- plot + theme_classic()
plot <- plot + theme(
  axis.text.x = element_text(angle = 45, hjust = 1),
  axis.line = element_line(size = 1.0, lineend = "square"),
  text = element_text(colour ="black", size = 14),
  legend.position = c(0.28, 0.90), #"top
  legend.text = element_text(size = 14),
  legend.key.size = unit(3, "lines"),
  legend.direction = "horizontal",
  axis.ticks = element_line(linewidth = 1.5),
  axis.ticks.length = unit(-2, "mm"))
plot <- plot + guides(fill = guide_legend(title = NULL))
plot
```

