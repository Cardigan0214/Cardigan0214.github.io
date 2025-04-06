---
title: 多项分布与泊松分布
date: 2025-04-01 23:08:41
categories: ['概率论']
math: true
--- 
本文主要用途为测试一下MathJax插件hhh

# 多项分布
### 定义1（多项分布）
称 $(X_{1},\cdots,X_{r})$ 服从参数为 $(n;p_{1},\cdots,p_{r})$ 的多项分布，若
$$
    \mathbb{P}(X_{1}=k_{1},\cdots,X_{r}=k_{r})=\frac{n!}{k_{1}!\cdots k_{r}!}p_{1}^{k_{1}}\cdots p_{r}^{k_{r}}
$$
这里 $k_{1},\cdots,k_{r}$ 为非负整数，且满足 $k_{1}+\cdots+k_{r}=n,p_{1}+\cdots+p_{r}=1$ 实际上对于上式中的系数，我们有
\begin{align}
\binom{n}{k_{1}}\binom{n-k_{1}}{k_{2}}\cdots \binom{n-(k_{1}+\cdots+k_{r-1})}{k_{r}}& =\frac{n!}{k_{1}!(n-k_{1})!} \frac{(n-k_{1})!}{k_{2}!(n-k_{2})}\cdots \frac{(n-k_{1}-\cdots-k_{r-1})!}{(k_{r})!0!}\\
& =\frac{n!}{k_{1}!\cdots k_{r}!}
\end{align}
这表明 $(X_{1},\cdots,X_{r})$ 发生 $(k_{1},\cdots,k_{r})$ 次的事件共发生 $\frac{n!}{k_{1}!\cdots k_{r}!}$ 次

### 命题1
设称 $(X_{1},\cdots,X_{r})$ 服从参数为 $(n;p_{1},\cdots,p_{r})$ 的多项分布，则
$$
    X_{i}+X_{j}\sim B(n,p_{i}+p_{j})
$$

#### 证明：
为方便表示，我们不妨假设 $X_{i}+X_{j}=X_{1}+X_{2}$ ，因为
\begin{align}
    \mathbb{P}(X_{1}=k_{1},X_{2}=k_{2})& =\sum\limits_{k_{3}+\cdots+k_{r}=n-(k_{1}+k_{2})}\frac{n!}{k_{1}!\cdots k_{r}!}p_{1}^{k_{1}}\cdots p_{r}^{k_{r}}\\
    & =\frac{p_{1}^{k_{1}}p_{2}^{k_{2}}}{k_{1}!k_{2}!}\sum\limits_{k_{3}+\cdots+k_{r}=n-(k_{1}+k_{2})}\frac{n!}{k_{3}!\cdots k_{r}!}p_{3}^{k_{3}}\cdots p_{r}^{k_{r}}\\
    & =\frac{p_{1}^{k_{1}}p_{2}^{k_{2}}(1-p_{1}-p_{2})^{n-k_{1}-k_{2}}}{k_{1}!k_{2}!}\cdot \frac{n!}{(n-k_{1}-k_{2})!}\sum\limits_{k_{3}+\cdots+k_{r}=n-(k_{1}+k_{2})}\frac{(n-k_{1}-k_{2})!}{k_{3}!\cdots k_{r}!}\left (\frac{p_{3}}{1-p_{1}-p_{2}}\right )^{k_{3}}\cdots \left (\frac{p_{r}}{1-p_{1}-p_{2}}\right )^{k_{r}}\\
    & =\frac{n!}{k_{1}!k_{2}!(n-k_{1}-k_{2})!}p_{1}^{k_{1}}p_{2}^{k_{2}}(1-p_{1}-p_{2})^{n-k_{1}-k_{2}}
\end{align}
所以，对 $\forall 0\leq l\leq n$，我们有
\begin{align}
    \mathbb{P}(X_{1}+X_{2}=l)& =\sum\limits_{k=0}^{l}\mathbb{P}(X_{1}=k,X_{2}=l-k)\\
    & =\sum\limits_{k=0}^{l}\mathbb{P}(X_{1}=k)\mathbb{P}(X_{2}=l-k)\\
    & =\sum\limits_{k=0}^{l}\frac{n!}{k!(l-k)!(n-l)!}p_{1}^{k}p_{2}^{l-k}(1-p_{1}-p_{2})^{n-l}\\
    & =\sum\limits_{k=0}^{l}\frac{n!}{l!(n-l)!}\cdot \frac{l!}{k!(l-k)!}p_{1}^{k}p_{2}^{l-k}(1-p_{1}-p_{2})^{n-l}\\
    & =\binom{n}{l}(p_{1}+p_{2})^{l}(1-p_{1}-p_{2})^{n-l}\\
\end{align}
这就说明了$X_{1}+X_{2}\sim B(n,p_{1}+p_{2})$

### 推论1
设称 $(X_{1},\cdots,X_{r})$ 服从参数为 $(n;p_{1},\cdots,p_{r})$ 的多项分布，则对 $\forall 1\leq i_{1},\cdots,i_{k}\leq r$，均有
$$
    X_{i_{1}}+\cdots+X_{i_{k}}\sim B(n,p_{i_{1}}+\cdots+p_{i_{k}})
$$

#### 证明：
对 $k$ 进行归纳即可

# 泊松分布
### 定义2
称非负整数值离散型随机变量 $X$ 服从参数为 $\lambda>0$ 的泊松分布，是指 $X$ 的分布列为 
$$
    \mathbb{P}(X=k)=\frac{\lambda^{k}}{k!}e^{-\lambda},\quad \forall k\in \mathbb{N}
$$
记为$X\sim P(\lambda)$

### 命题2
设$X\sim P(\lambda_{1}),Y\sim P(\lambda_{2})$，且$X,Y$相互独立，则
$$
    X+Y\sim P(\lambda_{1}+\lambda_{2})
$$

#### 证明：
对$\forall n\in\mathbb{N}$
\begin{align}
    \mathbb{P}(X+Y=n)& =\sum\limits_{k=0}^{n}\mathbb{P}(X=k)\mathbb{P}(Y=n-k)\\
    & =\sum\limits_{k=0}^{n}\frac{\lambda_{1}^{k}}{k!}e^{-\lambda_{1}}\cdot \frac{\lambda_{2}^{n-k}}{(n-k)!}e^{-\lambda_{2}}\\
    & =e^{-(\lambda_{1}+\lambda_{2})}\cdot \frac{(\lambda_{1}+\lambda_{2})^{n}}{n!}\sum\limits_{k=0}^{n}\frac{n!}{k!(n-k)!}\left (\frac{\lambda_{1}}{\lambda_{1}+\lambda_{2}}\right )^{k}\left (\frac{\lambda_{2}}{\lambda_{1}+\lambda_{2}}\right )^{n-k}\\
    & =\frac{(\lambda_{1}+\lambda_{2})^{n}}{n!}e^{-(\lambda_{1}+\lambda_{2})}
\end{align}
这说明 $X+Y\sim P(\lambda_{1}+\lambda_{2})$