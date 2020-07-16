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
给定 $n,g,x$, 其中 $x = ind_g(a)$, 可以很快的计算出 $a=g^{ind_g(a)} mod n$， 但是给定 $n,g,a$时，要计算相应指数 $ind_g(a)$，即$x$ 则是非常困难的。这就是离散对数问题。


## D-H（Diffie-Hellman 密钥交换协议）  

基于 DLP (离散对数问题)的困难性。     

#### 描述  
> 1. Alice 和 Bob 协商一个有限循环群 $G$, 和它的一个生成元 $g$   
>2. Alice 选择一个随机自然数 $a$, 并且将 $g^{a}  mod  p$ 发送给 Bob。  
>3. Bob 选择一个随机自然数b， 并且将 $g^{b} mod p$ 发送给 Alice。  
>4. Alice 计算 $(g^{b})^{a} mod p$。
>5. Bob 计算 $(g^{a})^{b} mod p$。    

这样，Alice 和 Bob就同时协商出群元素 $g^{ab}$， 它可以被用作共享秘密。其中 $(g^{b})^{a}$ 和 $(g^{a})^{b} $ 因为群是乘法交换的。

![Diffie-Hellman](/images/posts/crypt/Diffie-Hellman-Schlüsselaustausch.svg.png)
  
## CDH（Computational Diffie-Hellman）Problem

给定有限循环群 $G$ , $G$ 的生成元 $g$ , 元素 $g^{u}. g^{v} \in G$, 求 $g^{uv} \in G$。

 
 ## DDH（Decisional Diffie-hellman）Problem   

给定有限循环群 $G$, $G$ 的生成元 $g$, 元素$g^{u},g^{v} \in G$, 判定 $g^{w} = g^{uv}$是否成立。

## BDDH 和 BCDH
- **BDDH**（Bilinear Decisional Diffie-Hellman）：给出任意的（a,b,c,d）, 有多项式时间算法能$g^{a},g^{b},g^{c},g^{abc}$ 和 $g^{a},g^{b},g^{c},g^{d}$ 两者区分开来。    

- **BCDH**（Bilinear Computational Diffie-Hellman problem ）：任意选取(a,b,c)，在多项式时间内计算出$g^{abc}$ 。



## 什么是群（Group）    
**群 (Group)**： 如果一个集合 $ G $ 的元素在某个操作下满足以下几个代数性质，那么集合 $ G $构成了一个群(Group):          

- **封闭性(Closure)**：$G$ 中的任意两个元素 $a$, $b$, 以及操作 $\cdot $ ,有 $a\cdot b$ 也属于 $G$。
- **结合性(Associativity)**：$G$ 中的三个元素 $a$, $b$, $c$, 以及操作 $\cdot $， 有 $(a\cdot b)\cdot c=a\cdot (b\cdot c)$。
- **单位元(Identity)**：如果存在 $e$, 使得 $G$ 中任何元素 $a$, 有 $e\cdot a = a \cdot e = a$。
- **逆元(Inverse)**：$G$ 中任意元素 $a$, 存在元素 $b$, 使得 $a \cdot b = b \cdot a = e$。   


**阿贝尔群（Abelian group）**: 如果一个集合 $G$ 构成了一个群，并且还满足交换性质，则 $G$ 构成了一个阿贝尔群(Abelian group).

- **交换性(Commutativity)**：$G$ 中任意元素 $a$, $b$, 有 $a \cdot b = b \cdot a$ 。 

- **有限循环群**：如果一个群 $G=\{g^{0},g^{1},\cdots g^{k},\cdots ,g^{n}\}$ ，则 $G$ 是由 $g$ 生成的阶(order)为 $n$ 的有限循环群。    

