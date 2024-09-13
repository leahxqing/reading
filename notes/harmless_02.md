---
title: '2 THE EXPERIMENTAL IDEAL'
date: 2023-09-24
toc: true
permalink: /posts/mostly_harmless_02/
tags:
  - Econometrics
  - Book Reading
  - Mostly Harmless
---

This is the second chapter *The Experimental Ideal* from *Mostly Harmless Econometrics*. You can also refer to my wechat account's post [here](https://mp.weixin.qq.com/s/ntU-3PRQWR4LuT98777-ig).


# The Experimental Ideal
## The Selection Problem
An example: studying a poor elderly population that uses hospital emergency rooms for primary care. Using NHIS data, where contains the information by asking "During the past 12 months, was the respondent a patient in a hospital overnight?" and also health status information.

By simply comparing the average health status by subtracting the mean health status of people go to hospital by the mean health status of people not go to hospital brings **selection bias**.

More precisely, think the treatment as described as a binary random variable. $$D_i = {0,1}$$. The outcome of health status is denoted as $$Y_i$$. So for any individual there are two potential health variables.

$$potential\ outcome = \left\{\begin{matrix}
Y_{1i}  & if\ D_i = 1\\
Y_{0i}  & if\ D_i = 0
\end{matrix}\right.$$

The observed outcome $Y_i$, can be written in the terms of potential outcomes as 

$$Y_i = \left\{ \begin{matrix}
    Y_{1i} &  if\ D_i = 1\\
    Y_{0i} &  if\ D_i = 0 
\end{matrix}
\right. 
\\ =Y_{0i}+(Y_{1i}-Y_{0i})D_i$$

Thus, the initial comparison, the observed difference in average health is:

$$
\begin{align}
    \mathop{E[Y_i|D_i=1]-E[Y_i|D_i=0]}\limits_{\textcolor{blue}{Observed\ difference\ in\ average\ health}}=& \mathop{E[Y_{1i}|D_i=1]-E[Y_{0i}|D_i=1]}\limits_{\textcolor{blue}{average\ treatment\ effect\ on\ the\ treated}} \\ 
    &+\mathop{E[Y_{0i}|D_i=0]-E[Y_{0i}|D_i=0]}\limits_{\textcolor{blue}{selection\ bias}}
\end{align}
$$

The term 

$$E[Y_{1i}|D_i=1]-E[Y_{0i}|D_i=1]=E[Y_{1i}-Y_{0i}|D_i=1]$$

is the *average causal affect of hospitalization on those who were hospitalized*.

The observed difference in health status however, adds to this causal effect a term called *selection bias*.

## Random Assignment Solves the Selection Problem
Random assignment of $D_i$ solves the selection problem because random assignment makes $D_i$ independent of potential outcomes:

$$
\begin{align}
    E[Y_{1i}|D_i=1]-E[Y_{0i}|D_i=1]&= E[Y_{1i}|D_i=1]-E[Y_{0i}|D_i=0] \\
    &= E[Y_{1i}|D_i=1]-E[Y_{0i}|D_i=0] \\
    &= E[Y_{1i}-Y_{0i}|D_i=1]\\
    &= E[Y_{1i}-Y_{0i}]
\end{align}
$$

The random assignment of $$D_i$$ eliminates the selection bias.

## Regression Analysis of Experiments
Suppose the treatment effect is the same for everyone, say $$Y_{1i}-Y_{0i}=\rho$$, a constant. We can write the outcome as

$$Y_i = \mathop{\alpha}\limits_{=E(Y_{0i})} + \mathop{\rho}\limits_{=Y_{1i}-Y_{0i}} D_i +\mathop{\eta_i}\limits_{=Y_{0i}-E(Y_{0i})}$$

where $$\eta_i$$ is the random part of $$Y_{0i}$$. Then

$$
\begin{align}
    E[Y_i|D_i=1]&=\alpha+\rho+E[\eta_i|D_i=1] \\
    E[Y_i|D_i=0]&=\alpha+E[\eta_i|D_i=0] \\
    E[Y_i|D_i=1]-E[Y_i|D_i=0]&=\mathop{\rho}\limits_{treatment\ effect} + \mathop{E[\eta_i|D_i=1]-E[\eta_i|D_i=0]}\limits_{selection\ bias}
\end{align}
$$
