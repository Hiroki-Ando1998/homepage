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
Memo
[github_Hiroki Ando](https://github.com/Hiroki-Ando1998/R/tree/main/ggplot2)

### Visualization
- [ggplot2](https://r4ds.had.co.nz/data-visualisation.html)
- [gganimate](https://gganimate.com/)
- [ggblend](https://mjskay.github.io/ggblend/)
- ggnewscale

### Basic function
- [guide book](https://ggplot2-book.org/themes)
- [plot shape](https://www.sthda.com/english/wiki/ggplot2-point-shapes)
- [theme](https://r-charts.com/ggplot2/themes/) (title, axis, legend, facet title)
- [scale_xx_manual](https://ggplot2.tidyverse.org/reference/scale_manual.html) (fill, colour, shape, gradation, size)

### Colour 
- [Colour_github](https://github.com/Hiroki-Ando1998/R/blob/main/ggplot2/ggplot2_Colour.R)
- [Colour code](https://rpubs.com/nishikosh/308337)
- scale_fill_viridis_d() #色覚障碍者でも認識可能
- scale_fill_brewer(palette = “Spectral”)

```yaml
#Gradation
library(RcolorBrewer)
display.brewer.all
scale_fill_brewer(palette = “Spectral”)

scale_fill_gradient(low = “black”, high = “white)

ggplot(data, aes(x = data$A, y = data$B, fill = data$C)) + 
scale_fill_gradient(low = “black”, high = “white”, limits = c(0, 6000), breaks = seq(70, 170, by = 20), guide =guide_legend()
#離散的な凡例。連続値は、breaks以降を削除

#n個のgradation
scale_fill_gradientn(fill = c(“darked”, “orange”, “yellow”, “white”
```

### Axis 
- [Colour_github](https://github.com/Hiroki-Ando1998/R/blob/main/ggplot2/ggplot2_Colour.R)
- [Colour code](https://rpubs.com/nishikosh/308337)
- scale_fill_viridis_d() #色覚障碍者でも認識可能
- scale_fill_brewer(palette = “Spectral”)

```yaml
#Adjustment of axis
library(scales)
plot <- plot + scale_y_continuous(limits = c(0,100), breaks = seq(0, 100, 20), label = NULL, name = “Age in years”)
plot <- plot + scale_y_log10(breaks = 10^(-7:-2), labels = trans_format("log10", math_format(10^.x)))
plot <- plot + scale_x_continuous(limits = c(1.5, 5.5), breaks = seq(2, 5, 1), label = NULL)
#limitの方向を逆転すれば、軸が逆転する

#% axis
scale_y_continuous(labels = scales::percent)

#change of order
scale_x_discrete(limits = c(“A”, “B”, “C”)
scale_x_discrete(limits = rev(levels(data$A)

#flip of axis
ggplot() + geom_boxplot() + coord_flip() + scale_x_discrete(limits = rev(levels(data$A)

Change order of value
ggplot(data_name, aes(x = reorder(column_1, column_2), y = column_3)
# Based on value of column_2, change the order of column_1
#change of order of more than 2 factor data
#sorted by B and then by C
order_change <- data$A[order(B, C)
data2 <- factor[data$A, order_change)

scale_x_discrete(limits = c(“A”, “B”, “C”)
scale_x_discrete(limits = rev(levels(data$A)
```

### Plot types
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

### Labeling plots
```yaml
ggplot(data, aes(x = data$A, y = data$B, fill = data$C)) + geom_col(position = position_dodge())
geom_text(aes(label = data$B), vjust = 1.5, colour = “white”, size = 3, position = position_dodge(0.9))

#add name to plots
library(ggrepel)
ggplot(data, aes(x = A, y = B)) + geom_point() +
geom_text_repel(aes(label = C), size = 3)

#Other options is use of geom_text()
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
ggsave(path = NULL, file = "file_name.svg", plot = plot, dpi = 600, width = 4, height = 3.2)
```

### Line up figures
```yaml
library(cowplot)
Plot_grid(figure_1, figure_2, ncol = 1, nrow = 2, rel_heights = c(2, 3))
#2行1列に並べる。上下の図の高さの比 2:3

library(devtools)
library(patchwork)
plot1 + plot2 + plot(col = 2, heights = c(1, 4)) #nrow, 高さ1:4の比


library(gridExtra)
# 2つのプロットを横に並べる
grid.arrange(
  plot,
  plot_ww,
  ncol = 2  # 2列のレイアウトを指定
)
```

### Facets
```yaml
#縦並び
ggplot(data, aes(x = A)) + geom_histogram(fill = “white”, colour = “black”) +
facet_grid(race ~., scales = “free”) +
theme(strip.text = element_text(face = “bold”, size = rel(1.5)), +
strip.background = element_rect(fill = “lightblue”, colour = “black”, size = 1)

# other version (横並びと自由に並べる)
face_grid(.~race)
facet_wrap(~class, nrow = 2) # or ncol = 4
```


