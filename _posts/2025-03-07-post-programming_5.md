---
title: "Bayesian modeling (R code)"
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - Post Formats
  - readability
  - standard
---
Baysian modeling and time-series analysis
- [Rstan](https://mc-stan.org/docs/2_19/stan-users-guide/index.html)
- 管理者権限でアクセスしているか確認する。 
- R4.3.2でRstanが動かなくなった→R4.2.3にすることで動いた。  
- StanはNAを取り扱えないから、あらかじめ除去しておく。  


# Regression model
- [Git hub](https://github.com/Hiroki-Ando1998/R/blob/main/Generalized%20linear%20model/2_E_Outlinear_ROC%20curve)

### Linear regression model
```yaml
excerpt_separator: "<!--more-->"
```

### Logistic regression model
Stan code
```yaml
data {
  int<lower=0> n_cd;
  vector[n_d] ww;
  int<lower=0> n_count[n_cd];
  int row_cd[n_cd];
}

parameters {
  real<lower=-4, upper=4> c1_raw;
  real<lower=-4, upper=4> c2_raw;
}

transformed parameters{
    real c1;
     c1 = -22 + 5*c1_raw;
  
    real c2;
    c2 = exp(1+c2_raw);

}

model {
  // Priors
  c1_raw ~ normal(0, 1);
  c2_raw ~ normal(0, 1);
  
  // Compute probabilities using the logistic function and likelihood for Bernoulli observations
    vector[n_cd] p;
    for (k in 1:n_cd) {
      p[k] = inv_logit(c1 + c2 * ww[row_cd[k]]);
      nd[k] ~ binomial(n_count[k], p[k]); 
    } 
}
```
- ロジスティック回帰分析をするときは、intで値を指定する
- Index()の中身は整数型でなければならない (e.g., int<lower=0> na, int pick_colum [na];)
- intだけ指定の仕方が違う

