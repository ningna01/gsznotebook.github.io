---
layout: post
author: ningna
title: "汉密尔顿时间序列分析 - 第五章"
date: 2026-01-04
categories: [Time Series Analysis]
tags: [时间序列, Time Series Analysis]
math: true
---

# Chapter 5 —— Maximum Likelihood Estimation

## 5.1 Introduction

在前面的章节当中，我们均基于一个重要的假设 —— ARMA 模型的总体参数(population parameters)已知，如$(c, \phi_1, \dots, \phi_p, \theta_1,\dots, \theta_q, \sigma^2)$ 。

基于这些总体参数，我们可以计算总体矩(population moments)和线性预测(linear forcasts)。

现在我们需要考虑：现在我们需要考虑已知样本数据时，如何估计上述未知的总体参数？这里介绍估计的核心——**极大似然估计(Maximum Likelihood Estimation / MLE)**。

令$\boldsymbol{\theta} \equiv (c, \phi_1, \dots, \phi_p, \theta_1,\dots, \theta_q, \sigma^2)^{\prime}$ 为总体参数向量，对于观测样本$(y_1, \dots , y_T)$ ，计算概率密度函数(probability density function)的方法如下：

$$
f_{Y_T, \dots , Y_1}(y_T, y_{T-1}, \dots , y_1; \boldsymbol{\theta})  \tag{5.1.1}
$$

极大似然估计即找到参数$\boldsymbol{\hat{\theta}}$ ，使得当前观测样本出现的概率最大，即：

$$
\boldsymbol{\hat \theta} = \arg \max _{\boldsymbol{\theta}} f_{Y_T, \dots , Y_1}(y_T, y_{T-1}, \dots , y_1; \boldsymbol{\theta})  \tag{5.1.2}
$$

MLE 通常要求$\varepsilon_t$ 为高斯白噪声(Gaussian white noise)：

$$
\varepsilon_t \sim \text{i.i.d.} \; N(0, \sigma^2)  \tag{5.1.3}
$$

> 尽管 “高斯分布” 是一个较强的假设，但对非高斯过程往往也具有合理性。
{: .prompt-tip }

MLE 通常分为两步，后面我们会依次介绍：

1. 计算似然函数(likelihood function)
2. 找到最大化似然函数的参数$\boldsymbol{\hat{\theta}}$ 