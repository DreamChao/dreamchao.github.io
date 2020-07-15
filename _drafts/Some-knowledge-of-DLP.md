---
layout: post
title: Some Knowledge of DLP
categories: Cryptography
description: 离散对数困难问题中的一些知识
keywords: cryptography，DLP，Diffie-Hellman
comments: false
---   

这篇 blog 主要是为了介绍离散对数困难问题中的一些常见的知识点。   

## The Discrete Logarithm Problem (DLP)
 假设 $ G $ 是一个交换群，




## 什么是群（Group）    
**群 (Group)**： 如果一个集合 $ G $ 的元素在某个操作下满足以下几个代数性质，那么集合 $ G $构成了一个群(Group):          

- **封闭性(Closure)**：$G$ 中的任意两个元素 $a$, $b$, 以及操作 $\cdot $ ,有 $a\cdot b$ 也属于 $G$。
- **结合性(Associativity)**：$G$ 中的三个元素 $a$, $b$, $c$, 以及操作 $\cdot $， 有 $(a\cdot b)\cdot c=a\cdot (b\cdot c)$。
- **单位元(Identity)**：如果存在 $e$, 使得 $G$ 中任何元素 $a$, 有 $e\cdot a = a \cdot e = a$。
- **逆元(Inverse)**：$G$ 中任意元素 $a$, 存在元素 $b$, 使得 $a \cdot b = b \cdot a = e$。   


**阿贝尔群（Abelian group）**: 如果一个集合 $G$ 构成了一个群，并且还满足交换性质，则 $G$ 构成了一个阿贝尔群(Abelian group).

- **交换性(Commutativity)**：$G$ 中任意元素 $a$, $b$, 有 $a \cdot b = b \cdot a$ 。 

- **有限循环群**：如果一个群 $G=\{g^{0},g^{1},\cdots \U{ff0c} g^{k},\cdots ,g^{n}\}$ ，则 $G$ 是由 $g$ 生成的阶(order)为 $n$ 的有限循环群。    

