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


```yaml
R code
#並列計算するにはstan関数やstan_model関数とsampling関数を呼ぶ前に以下のコードを書く
rstan_options(auto_write = TRUE)
options(mc.cores = parallel::detectCores())
```

# Regression model
- [Git hub](https://github.com/Hiroki-Ando1998/R/blob/main/Generalized%20linear%20model/2_E_Outlinear_ROC%20curve)

### Linear regression model
R code
```yaml
data_list_ww <- list(N = sample_size, x = data$infected, y = concentation)

rstan_options(auto_write = TRUE)
options(mc.cores = parallel::detectCores())

mcmc <- stan(
  file = "linear_regression.stan", 
  data = data_list_ww,
  seed = 1,
  chain = 4,
  iter = 10000,
  warmup = 5000,
  thin = 4
)
```

stan file (name: linear_regression.stan
```yaml
data {
  int<lower=0> N;      // サンプル数
  vector[N] x;         // 説明変数
  vector[N] y;         // 目的変数
}

parameters {
  real alpha;          // 切片
  real beta;           // 回帰係数
  real<lower=0> sigma; // 誤差の標準偏差
}

model {
  // Priors
  alpha ~ normal(0, 10);
  beta ~ normal(0, 10);
  sigma ~ normal(0, 10);

  // Likelihood
  y ~ normal(alpha + beta * x, sigma);
}
```

### Trace plots, WAIC, and loo
```yaml
R code
print(mcmc, pars = c("c1", "intercept"), probe = c(0.025, 0.50, 0.975))

#Traceplot
library(bayesplot)
mcmc_combo(mcmc, pars = c("alpha", "beta", "sigma"))

traceplot(mcmc, inc_warmup = T)

#Extract log-likelihood produced from generated block
library(loo)
log_lik <- extract_log_lik(mcmc, parameter_name = "log_lik", merge_chains = TRUE)

waic(log_lik)
loo(log_lik)
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
- 収束しないときは、ベクトル化と各パラメータのスケールを調整する再パラメータ化する。事前分布が全てnorm(0, 1) にすると収束しやすくなる。

