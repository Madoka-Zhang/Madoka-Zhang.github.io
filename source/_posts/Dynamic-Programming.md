---
title: Dynamic Programming
categories: 数据结构
tags:
  - 数据结构
  - 动态规划
abbrlink: 71b19194
date: 2021-04-19 18:59:24
mathjax: true
---

# Dynamic Programming

> 前世之不忘，后事之师
>
>     			————汉 刘向

<!--more-->

### How to design a DP method

+ Characterize an optimal solution
+ recursively define the optimal values
+ compute the values in some order
+ reconstruct the sloving strategy

最重要：

+ optimal substructure
+ overlapping sub-problems

---

+ recursion 递归
  + 怎样去找递归间的一个想法
+ 记忆化
+ DP
  + 递归
  + 子问题，不要重复计算
  + 记忆化

----

### Memorization

+ 存储已经算过的子问题的解值
+ 记忆化，自上而下
+ tabulation ： 迭代构造子问题的解构造一个表

---

+ 记忆化更好写
+ 记忆化可能会慢于table
+ 记忆化用栈可能会占用很大
+ table，smart remember subproblems

**某种意义上讲，动态规划就是没有重复的递归**

#### Matrix multiplication

+ n-by-n matrices X and Y

  $Z_{ij}\ =\ \sum\limits_{k=1}^{n}X_{ik}Y_{kj}$

  直接运算$O(N^3)$

+ **ordering matrix multiplication**

  $M_{1[10\times20]}*M_{2[20\times50]}*M_{3[50\times1]}*M_{4[1\times100]}$

  从右向左算，$50 \times 1 \times 100 + 20\times50\times100+10\times20\times100 = 125000$

  先算中间再左再右，$20\times50\times1+10\times20\times1+10\times1\times100=2200$

  问题就是如何找到最小的时间的一个order

+ 使用$b_n = $number\ of\ different ways to compute $M_1*M_2*......*M_n$

  上述$b_2=1,b_3=2,b_4=5$

  $M_{ij}=M_i....M_j \ \ \ Then M_{1n}=M_1....M_n=M_{1i}*M_{i-1\ n}$

  $b_n=\sum\limits_{i=1}^{n-1}b_ib_{n-i}$ where n>1 and b<sub>1</sub>=1

  $b_n=O(4^n/n\sqrt n)$

  suppose $M_i$ is an $r_{i-1}\times r_i$ matrix

  let $m_{ij}$  作为从i到j最有的计算路径
  $$
  m_{ij}=
  	\begin{cases}
  		0, & \text{if $i = j$}\\
  		\min\limits_{i\leq l<j}{m_{il}+m_{l+1\ j}+r_{i-1}r_lr_j}, & \text{if $j>i$}
  	\end{cases}
  $$

+ $T(N)=O(N^3)$

### Optimal Binary Search Tree

+ 不考虑增删的二叉搜索树的最好的搜索方法（有若干的节点，问怎样构造查找树）
+ 静态搜索  $T(N)=\sum\limits_{i=1}^Np_i\times(1+d_i)$
+ 使用表格$T(N)=O(N^3)$
+ 

---

### All-pairs shortest path

找到每个点之间的最短路径

+ Use single-source algorithm

  $O(n^3+n^2log\ n) = O(|V|^3)$  在稀疏图上非常快

+ define

  $D^k[i][j]=\min \{\text{length of path i} \rightarrow {l\leq k}\rightarrow j\}$

  and $D^{-1}[i][j]=Cost[i][j]$

  从点i到j的最短路径 $D^{N-1}[i][j]$

  k是最短路径$D^k[i][j]=D^{k-1}[i][k]+K^{k-1}[k][j]$

  $D^k[i][j] = \min \{D^{k-1}[i][j],  D^{k-1}[i][k]+K^{k-1}[k][j]\}$ 

---

未完