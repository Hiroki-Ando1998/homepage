---
permalink: /Textbook/
title: "Textbook"
---
I compiled a list of textbooks I used to study topics related to my research—such as epidemiology, statistics, and programming—for students who, like me, transitioned from an engineering background to public health. Many of these are Japanese textbooks; however, there are likely more comprehensive resources available in English, as well as other materials that may be easier to understand. Please use this list as a reference.

# Public helath
---
### Epidemiology
1. [疫学 医学的研究と実践のサイエンス](https://www.molcom.jp/products/detail/52131/) introduces the overall framework of epidemiology, covering basic measures, study designs, bias, and practical applications in public health
2. [Essential of Epidemiology in Public health](https://www.academia.edu/43690544/ESSENTIALS_OF_FOURTH_EDITION) focuses more on real-world applications, emphasizing how epidemiological methods are used in public health practice with many concrete examples.
3. [アドバンス分析疫学](https://www.medsi.co.jp/products/detail/3742) takes a more analytical approach, explaining statistical modeling, confounding adjustment, and methods for analyzing epidemiological data in greater depth
4. [現代疫学](https://www.gakujutsu.co.jp/product/978-4-7806-1245-5/) provides a more theoretical and rigorous treatment of epidemiology, particularly in causal inference and the formal understanding of bias and study design ([English](https://www.amazon.co.jp/Modern-Epidemiology-Kenneth-J-Rothman/dp/1451190050))


### Infectious disease epidemiology
1. [Modern infectious disease epidemiology](https://www.routledge.com/Modern-Infectious-Disease-Epidemiology/Giesecke/p/book/9781444180022?srsltid=AfmBOoqVT-OadjcUh9Vu4IVWE7S7OI1Dvvriyb9eknCtQIyvjmhBjNtb) provides a practical introduction to the epidemiology of infectious diseases, covering key concepts such as transmission dynamics, outbreak investigation, surveillance, immunity, and control measures, while linking epidemiological methods to real-world application
2. [感染症疫学のためのデータ分析入門](https://store.isho.jp/search/detail/productId/2105621490) focuses on how to analyze infectious disease data in practice, introducing statistical methods and computational approaches needed to handle real epidemiological datasets
3. [感染症の数理モデル](https://www.amazon.co.jp/%E6%84%9F%E6%9F%93%E7%97%87%E3%81%AE%E6%95%B0%E7%90%86%E3%83%A2%E3%83%87%E3%83%AB-%E7%A8%B2%E8%91%89-%E5%AF%BF/dp/4563011673) takes a more theoretical perspective, explaining how infectious disease dynamics can be described and understood using mathematical models, such as compartmental models, to study transmission mechanisms and predict epidemic behavior.



# Statistics and Modeling
---
I am learning statistics, following [this reference](https://qiita.com/ssugasawa/items/0e0d76de3ed92c7410e6)
### Theortical Statistics
01. [公式と例題で学ぶ数学の基礎](https://www.kyoritsu-pub.co.jp/book/b10123480.html) introduces the essential mathematical foundations, such as algebra and calculus, through formulas and worked examples, helping build the basic skills required for statistics
1. [データ分析に必須の知識・考え方　統計学入門](https://www.socym.co.jp/book/1319) focuses on intuitive understanding of statistical concepts, including how to summarize and interpret data, emphasizing practical thinking rather than formal theory
2. [統計学入門 東京大学出版](https://www.utp.or.jp/book/b300857.html) provides a more rigorous introduction to statistical inference, covering probability, estimation, and hypothesis testing in a systematic way
3. [データ解析のための数理統計入門](https://www.kyoritsu-pub.co.jp/book/b10033628.html) moves toward theoretical statistics, explaining the mathematical foundations behind inference methods and statistical models
4. [現代数理統計学の基礎](https://www.kyoritsu-pub.co.jp/book/b10003681.html) further deepens this theoretical perspective, offering a more formal and comprehensive treatment of statistical theory.
5. [標準ベイズ統計学](https://www.asakura.co.jp/detail.php?book_code=12267&srsltid=AfmBOookiaOnA332Yo92n3nYVIxSZejU-KBNujDbUkf5YifJy4G39KD8) introduces Bayesian thinking as a framework for updating beliefs with data, contrasting it with classical approaches ([English](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://sites.math.rutgers.edu/~zeilberg/EM20/Hoff.pdf))
6. [ベイズデータ解析](https://www.morikita.co.jp/books/mid/009703) provides a comprehensive and practical treatment of Bayesian methods, showing how to build models, perform inference, and apply Bayesian analysis to real-world problems using modern computational technique ([English](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://sites.stat.columbia.edu/gelman/book/BDA3.pdf))


### Modeling and Programming
1. [データ解析のための統計モデリング入門](https://www.iwanami.co.jp/book/b257893.html) introduces the core ideas of statistical modeling, emphasizing how to formulate models, interpret parameters, and connect data with underlying processes in an intuitive yet principled way
2. [RとStanではじめるベイズ統計モデリングによるデータ分析入門](https://www.kspub.co.jp/book/detail/5165362.html) provides a hands-on introduction to Bayesian modeling, showing how to implement models and perform inference using R and Stan, making abstract concepts computationally concrete
3. [StanとRでベイズ統計モデリング](https://www.kyoritsu-pub.co.jp/book/b10003786.html) builds on this foundation with more advanced models and deeper explanations, helping readers develop practical skills for real-world Bayesian data analysis.
4. [Rによる機械学習](https://www.shoeisha.co.jp/book/detail/9784798167343) expands beyond traditional statistics to cover machine learning methods, focusing on prediction, model evaluation, and algorithmic approaches using R
5. [Rではじめる地理空間データの統計解析入門](https://www.kspub.co.jp/book/detail/5273036.html) introduces statistical techniques for analyzing spatial and geographic data, including mapping, spatial correlation, and region-based modeling, which are particularly relevant for applications such as epidemiology and environmental studies.

### Causual inference
1. [欠測データ処理](https://www.kyoritsu-pub.co.jp/book/b10003896.html) explains how to handle missing data, which commonly arise in real datasets, by introducing methods such as single imputation and multiple imputation, along with their implementation in R, emphasizing that improper handling of missing values can lead to biased results
2. [効果検証入門](https://gihyo.jp/book/2020/978-4-297-11117-5) provides an accessible introduction to causal inference in practical settings, especially in business contexts, showing why simple comparisons can be misleading and how methods such as randomized controlled trials, propensity scores, and difference-in-differences can be used to estimate causal effects more appropriately
3. [統計的因果推論の理論と実装](https://www.kyoritsu-pub.co.jp/book/b10011781.html) offers a more rigorous and comprehensive treatment of causal inference, covering both theoretical foundations and practical implementation, including methods like matching, instrumental variables, regression discontinuity designs, and handling missing data within causal framework
4. [疫学・臨床研究のための因果推論: Robinsのg-methodsによる現実問題へのアプローチ](https://www.amazon.co.jp/%E7%96%AB%E5%AD%A6%E3%83%BB%E8%87%A8%E5%BA%8A%E7%A0%94%E7%A9%B6%E3%81%AE%E3%81%9F%E3%82%81%E3%81%AE%E5%9B%A0%E6%9E%9C%E6%8E%A8%E8%AB%96-Robins%E3%81%AEg-methods%E3%81%AB%E3%82%88%E3%82%8B%E7%8F%BE%E5%AE%9F%E5%95%8F%E9%A1%8C%E3%81%B8%E3%81%AE%E3%82%A2%E3%83%97%E3%83%AD%E3%83%BC%E3%83%81-%E7%AF%A0%E5%B4%8E-%E6%99%BA%E5%A4%A7/dp/4254123124/ref=pd_lpo_d_sccl_2/356-4230065-6534148?pd_rd_w=dDok3&content-id=amzn1.sym.855d8f70-df76-4181-80b0-56e48ae3bb9b&pf_rd_p=855d8f70-df76-4181-80b0-56e48ae3bb9b&pf_rd_r=FWM26WXBANKY1SA278J3&pd_rd_wg=p8zQp&pd_rd_r=a2437518-6616-4187-9d1a-6af7ecdbe13c&pd_rd_i=4254123124&psc=1)provides a rigorous and advanced treatment of causal inference in epidemiology and clinical research, focusing on Robins’ g-methods such as marginal structural models and g-computation. It explains how to properly estimate causal effects in the presence of time-varying confounding and complex longitudinal data, bridging theoretical foundations with practical applications to real-world epidemiological problems

