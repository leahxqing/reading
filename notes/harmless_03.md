---
title: '3 MAKING REGRESSION MAKE SENSE'
date: 2023-09-24
permalink: /posts/mostly_harmless_03/
tags:
  - Econometrics
  - Book Reading
  - Mostly Harmless
---

This is the third chapter *Making Regression Make Sense* from *Mostly Harmless Econometrics*. You can also refer to my wechat account's post [here](https://mp.weixin.qq.com/s/0NsDNFkb6Y-MQvDDNy0E4A).


# Making Regression Make Sense

## Regression Fundamentals
The mechanical properties of regression estimates (universal features of the population regression vector and its sample analog that have nothing to do with a researcher's interpretation of his output):
- the intimate connection between the population regression function and the conditional expectation function
- how and why regression coefficients change as covariates are added or removed from the model
- the close link between regression and other "control strategies" such as matching
- the sampling distribution of regression estimates

### Economic Relationships and the Conditional Expectation Function
CEF (conditional expectation function): $$E[Y_i|X_i]$$ is a function of $$X_i$$, also a random variable

$$ E[Y_i|X_i=x]=\int tf_y(t|X_i=x)dt $$

$$ E[Y_i|X_i=x]=\sum_t tf_y(t|X_i=x) $$

An important complement to the CEF: the law of iterated expectations:

$$E[Y_i]=E\{E[Y_i|X_i]\}$$ 

**Theorem 3.3.1 The CEF-Decomposition Property**

$$ Y_i=E[Y_i|X_i]+\epsilon_i $$

where $$ \epsilon_i $$ is mean-independent of $$ X_i $$, i.e., 
$$ E[\epsilon_i|X_i]=0 $$ 
and, therefore, 
$$ \epsilon_i $$ 
is uncorrelated with any function of 
$$ X_i $$

This theorem says that any random variable, $$Y_i$$ can be decomposed into a piece that's "explained by $$X_i$$", i.e., the CEF, and a piece left over which is orthogonal to (i.e., uncorrelated with) any function of $$X_i$$.

**Theorem 3.1.2 The CEF-Prediction Property**

Let $$m(X_i)$$ be any function of $$X_i$$, the CEF solves

$$E[Y_i|X_i]=\mathop{\mathbf{argmin}}\limits_{m(X_i)}E[(Y_i-m(X_i))^2]$$

so it is the MMSE (*Minimum Mean Square Error*) predictor of $$ Y_i $$ given $$ X_i $$

**Theorem 3.1.3 The ANOVA Theorem**

$$V(Y_i)=V(E[Y_i|X_i])+E[V(Y_i|X_i)]$$

where $$ V(\cdot) $$ denotes variance and 
$$ V(Y_i|X_i) $$ 
is the conditional variance of 
$$ Y_i $$ 
given 
$$ X_i $$
.

### Linear Regression and the CEF

$$\beta_k=\frac{Cov(Y_i,\tilde{x}_{ki})}{V(\tilde{x}_{ki})}$$

where $$\tilde{x}_{ki}$$ is the residual from a regression of $$x_{ki}$$ on all the other covariates.

That is, $$E[X_iX_i']E[X_iY_i]^{-1}$$ is the $$K\times 1$$ vector with k-th element $$\dfrac{Cov(Y_i,\tilde{x}_{ki})}{V(\tilde{x}_{ki})}$$ 

**Theorem 3.1.4 The Linear CEF Theorem (Regression-justification I)**

Suppose the CEF is linear. Then the population regression function is it.

**Theorem 3.1.5 The Best Linear Predictor Theorem (Regression-justification II)**

The function 
$$X_i' \beta $$ 
is the best linear predictor of 
$$Y_i$$ 
given 
$$X_i$$ 
in a MMSE sense.

**Theorem 3.1.6 The Regression-CEF Theorem (Regression-justification III)**

The function $$ X_i' \beta $$ provides the MMSE linear approximation to 
$$ E[Y_i|X_i] $$
, that is 

$$\beta=\mathop{\mathbf{argmin}}\limits_{b}E\{(E[Y_i|X_i]-X_i'b)^2\}$$

### Asymptotic OLS Inference
The *Ordinary Least Squares (OLS)* estimator

$$\hat{\beta}=[\sum_i X_i X_i']^{-1} \sum_i X_iY_u$$

It is derived as a method of moments estimator.

**The general asymptotic asymptotic distribution theory:**

**The Law of Large Numbers:** Sample moments converge in probability to the corresponding population moments. In other words, the probability that the sample mean is close to the population mean can be made as high as you like by taking a large enough sample.

**The Central Limit Theorem:** Sample moments are asymptotically Normally distributed (after subtracting the corresponding population moment and multiplying by the square root of the sample size). The covariance matrix given by the variance of the underlying random variable. In other words, in large enough samples, approximately normalized sample moments are approximately Normally distributed.

**Slutsky's Theorem:**
- Consider the sum of two random variables, one of which converges in distribution and the other converges in probability to a constant: the asymptotic distribution of this sum is unaffected by replacing the one that converges to a constant by this constant. Formally, let $$ a_N $$ be a statistic with a limiting distribution and let $$ b_N $$ be a statistic with probability limit b. Then $$ a_N +b_N $$ and $$ a_N+b $$ have the same limiting distribution.
- Consider the product of two random variables, one of which converges in distribution and the other converges in probability to a constant: the asymptotic distribution of this product is unaffected by replacing the one that converges to a constant by this constant. This allows us to replaces some sample moments by population moments (i.e, by their probability limits) when deriving distributions. Formally, let $$ a_N $$ be a statistic with a limiting distribution and let $$ b_N $$ be a statistic with probability limit b. Then $$ a_Nb_N $$ and $$ a_N b $$ have the same asymptotic distribution.


**The Continuous Mapping Theorem:** Probability limits pass through continuous functions.For example, the probability limit of any continuous function of a sample moment is the function evaluated at the corresponding population moment. Formally, the probability limit of h(bx) is h(b)where plim $$ b_n=b $$ and $$ h(\cdot) $$ is continuous at b.

**The Delta Method:** Consider a vector-valued random variable that is asymptotically Normally distributed. Most scalar functions of this random variable are also asymptotically Normally distributed with covariance matrix given by a quadratic form with the covariance matrix of the random variable on the inside and the gradient of the function evaluated at the probability limit of the random variable on the outside. Formally, the asymptotic distribution of $$ h(b_n) $$ is Normal with covariance matrix $$ \bigtriangledown h(b)'\bigtriangledown h(b) $$ where plim $$ b_N = b $$, $$ h(\cdot) $$ is continuously differentiable at b with gradient $$ \bigtriangledown h(b) $$, and $$ b_N $$ has asymptotic covariance matrix $$\Omega$$.

**The asymptotic distribution of $$ \hat{\beta} $$:**

The first way using **Delta Method**, since $$\hat{\beta}$$ is a function of sample moments, and is therefore asymptotically Normally distributed. 

An easier and more instructive derivation uses the **Slutsky and central limit theorems** shows that $$ \hat{\beta} $$ has an asymptotically Normal distribution, with probability limit $$ \beta $$, and covariance matrix 

$$E[X_iX_i']^{-1}E[X_iX_i'e_i^2]E[X_iX_i']^{-1}$$

The standard errors used to construct t-statistics are the square roots of the diagonal elements of this matrix. In practice these standard errors are estimated by substituting sums for expectations, and using the estimated residuals, $$ \hat{e}_i=Y_i-X_i'\hat{\beta} $$ to form the empirical fourth moment, $$ \sum[X_iX_i\hat{e}_i^2]/N $$. 

Asymptotic standard errors computed in this way are known as heteroskedasticity-consistent standard errors, also "robust" standard errors.

### Saturated Models, Main Effects, and Other Regression Talk
Saturated regression models are regression models with discrete explanatory variables, where the model includes a separate parameter for all possible values taken on by the explanatory variables. Suppose, for example, that 

$$ S_i=0,1,2,...,\tau $$. A saturated model for $$ S_i $$ is 

$$
Y_i=\beta_0+\beta_1 d_{1i}+\beta_2 d_{2i}+...+\beta_{\tau}d_{\tau i}+\epsilon_i
$$

where $$ d_{ji}=1[s_i=j] $$ is a dummy variable indicating schooling level-j, and $$ \beta_j $$ is said to be the jth-level effect. 

Note that 

$$
\beta_j=E[Y_i|S_i=j]-\beta_j=E[Y_i|S_i=0]
$$ 

while 
$$ \beta_0=E[Y_i|S_i=0] $$
.

A regression model is saturated as long as it has one parameter for every possible j in 
$$ E[Y_i|S_i=j] $$
. Saturated models fit the CEF perfectly because the CEF is linear in the dummy regressors used to saturate.

If there are two explanatory variables, say one dummy indicating college graduates and one dummy indicating sex, the model is saturated by including these two dummies, their product, and a constant. The coefficients on the dummies are known as **main effects**, while the product is called an **interaction term**. This is not the only saturated parameterization: any set of indicators (dummies) that can be used to identify each value taken on by the covariates produces a saturated model. 

It is natural to start with saturated model because this fits the CEF. On the other hand, saturated models generate a lot of interaction terms, many of which may be uninteresting or imprecise.

## Regression and Causality
### The Conditional Independence Assumption
A regression is causal when the CEF it approximates is causal.

Conditional independence assumption (CIA), also called selection-on-observables because the covariates to be held are assumed to be known and observed.

Consider the *education-income* example. Given the CIA, conditional-on-$$ X_i $$ comparisons of average earnings across schooling levels have a causal interpretation. 

$$
E[Y_i|X_i,C_i=1]-E[Y_i|X_i,C_i=0]=E[Y_{1i}-Y_{0i}|X_i]
$$

Using the individual-specific notation, 

$$
Y_{si}\equiv f_i(s)
$$

The CIA in a more general setup becomes 

$$
Y_{si}\amalg S_i|X_i
$$

Conditional on $$ X_i $$, the average causal effect of a one year increase in schooling is 
$$ E[f_i(s)-f_i(s-1)|X_i] $$
, while the average casual effect of a 4-year increase in schooling is 
$$ E[f_i(s)-E[f_i(s-4)]|X_i] $$
. Given CIA, conditional-on-$$ X_i $$ comparisons of average earnings across schooling levels have a causal interpretation.

$$
E[Y_i|X_i,S_i=s]-E[Y_i|X_i,S_i=s-1]=E[f_i(s)-f_i(s-1)|X_i]
$$

The elimination of selection bias.

Regression provides an easy-to-use empirical strategy that automatically turns the CIA into causal effects. Two routes can be traced from the CIA to regression, One assumes that $$ f_i(s) $$ is both linear in s and the same for everyone except for an additive error term, in which case linear regression is a natural tool to estimate the features of $$ f(s) $$. A more general but somewhat longer route recognizes that $$ f_i(s) $$ almost certainly differs for different people. and, moreover, need not be linear in s. Even so. allowing for random variation in $$ f_i(s) $$ across people, and for non-linearity for a given person, regression can be thought of as strategy for the estimation of a weighted average of the individual-specific difference, $$ f_i(s) - f_i(s - 1) $$. In fact, regression can be seen as a particular sort of matching estimator, capturing an average causal effect.

The first route, a linear constant-effects causal model. Suppose that 

$$
f_i(s)=\alpha+\rho s+\eta_i
$$

The equation says that the linearity and the functional relationship of interest is the same for everyone.

Suppose now the CIA holds given a vector if observed covariates, $$ X_i  $$. We decompose the random part of potential earnings, $$ \eta_i $$, into a linear function of observable characteristics, $$ X_i $$, and an error term, $$ v_i $$: 
$$
\eta_i=X_i'\gamma+v_i
$$

where $$ \gamma $$ is a vector of population regression coefficients that is assumed to satisfy 
$$ E[\eta_i|X_i]=X_i'\gamma $$
. Because $$ \gamma $$ is defined by the regression of $$ \eta_i $$ on $$ X_i $$, the residual $$ v_i $$ and $$ X_i $$ are uncorrelated by construction. Moreover, by virtue of the CIA, we have 

$$
E[f_i(s)|X_i,S_i]=E[f_i(s)|X_i]=\alpha+\rho s+E[\eta_i|X]=\alpha+\rho s+X_i'\gamma
$$

Because mean-independence implies orthogonality, the residual in the linear causal model 

$$
Y_i=\alpha+\rho S_i+X_i'\gamma+v_i
$$

is uncorrelated with the regressors, $$ S_i $$ and $$ X_i $$, and the regression coefficient $$ \rho $$ is the causal effect of interest. It bears emphasizing once again that the key assumption here is that the observable characteristics, $$ X_i $$, are the only reason why $$ \eta_i $$ and $$ S_i $$ (equivalently, $$ f_i(s) $$ and $$ S_i $$) are correlated. The \textit{selection-on-observables assumption}.

### The Omitted Variables Bias Formula
To paraphrase, the OVB formula says: *Short equals long plus the effect of omitted times the regression of omitted on included*

Control for covariates can make the CIA more plausible.

### Bad Control
Bad controls are variables that are themselves outcome variables in the notional experiment at hand. That is, bad controls might just as well be dependent variables too. Good controls are variables that we can think of as having been fixed at the time the regressor of interest was determined.

The essence of the bad control problem is a version of selection bias, albeit somewhat more subtle.

A formal illustration of the bad control problem in the college/occupation example (the effects of a college degree on earnings that people can work in one of two occupations, while collar and blue collar. And the occupation is highly correlated with both education and pay, thus is better to look at the effect college on wages within an occupation).

Let $$ W_i $$ be a dummy variable that denotes white collar workers and $$ Y_i $$ denote earnings. The realization of these variables is determined by college graduation status and potential outcomes that are indexed against $$ C_i $$. We have 

$$
    Y_i=C_iY_{1i}+(1-C_i)Y_{0i} \\
    W_i=C_iW_{1i}+(1-C_i)W_{0i} 
$$

where $$ C_i=1 $$ for college graduates and is zero otherwise. Assuming that $$ C_i $$ is randomly assigned, it is independent of all potential outcomes. Thus, the causal effect of $$ C_i $$ on either $$ Y_i $$ or $$ W_i $$ since independence gives:

$$
    E[Y_i|C_i=1]- E[Y_i|C_i=0]= E[Y_{1i}-Y_{0i}] \\
    E[W_i|C_i=1]- E[W_i|C_i=0]= E[W_{1i}-W_{0i}]
$$

Bad control means that a comparison of earnings conditional on $$ W_i $$ does not have a causal interpretation. 

$$
E[Y_{1i}|W_{1i}=1]-E[Y_{0i}|W_{0i}=1] \\
= E[Y_{1i}-Y_{0i}|W_{1i}=1]+E[Y_{0i}|W_{1i}=1]-E[Y_{0i}|W_{0i}=1]
$$

A second version of bad control scenario involves *proxy control*, that is, the inclusion of variables that might partially control for omitted factors, but are themselves affected by the variable of interest.

One moral of both the bad-control and the proxy-control stories is that when thinking about controls, timing matters. Variables measured before the variable of interest was determined are generally good controls. In particular, because these variables were determined before the variable of interest, they cannot themselves be outcomes in the causal nexus.
