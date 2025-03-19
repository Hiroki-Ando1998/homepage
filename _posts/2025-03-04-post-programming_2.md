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
coming soon
### Visualization
- [ggplot2](https://r4ds.had.co.nz/data-visualisation.html)
- [gganimate](https://gganimate.com/)
- [ggblend](https://mjskay.github.io/ggblend/)
- ggnewscale


### basic function
- [guide book](https://ggplot2-book.org/themes)
- [plot shape](https://www.sthda.com/english/wiki/ggplot2-point-shapes)
- [theme](https://r-charts.com/ggplot2/themes/)

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

