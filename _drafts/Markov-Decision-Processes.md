---
layout: post
title: 马尔科夫决策过程(Markov Decision Processes)
categories: Stochastic-process
description: 机器学习算法简介
keywords: stochastic process, model 
comments: false
---  

## 概念
马尔科夫决策过程是基于马尔科夫论的随机动态系统的最优决策过程。它是马尔科夫过程与确定性的动态规划相结合的产物，故称为马尔科夫型随机动态规划，属于运筹学中数学规划的一个分支。     
马尔科夫决策过程具有**马尔可夫性**（无后效性，及系统的下一个状态只与当前状态信息有关，与更早的状态无关）,但不同的是 MDP 考虑了动作（action），即系统下个状态不仅和当前的状态有关，也和当前采取的动作有关。   

### 马尔科夫决策要求
 1. 能够检测到理想的状态。
 2. 可以多次尝试。
 3. 系统的下个状态只与当前状态信息有关，而与更早之前的状态无关。在决策过程中还和当前采取的动作有关。

 ## 定义    

 马尔科夫决策过程可以用五元组 $<S,A,P,R,\gamma >$ 来描述，其中：   

- $ S $ 为有限的状态集合(state)。
- $ A $ 为有限的动作集合(action)。
- $ P $ 为状态转移举证。$P_{ss^{^{\prime }}}^{a}=P[S_{t+1}=s^{^{\prime }}|S_{t}=s,A_{t}=a]$    
- $ R $ 为奖赏函数。表示通过动作 $ a $,状态$ s $转换到$s'$ 所带来的及时收益或回报(reward) 
- $\gamma $ 为折扣因子(discount factor),其中$\gamma \in \lbrack 0,1]$。表示未来收益和当前收益之间的差别，意味着当下的 reward 比未来反馈的 reward 更重要。    

## 策略  
策略(policy)是给定状态下的动作概率分布，即：$\pi (a|s)=P[A_{t}=a|S_{t}=a]$    

## 状态价值函数 & 最优状态价值函数    
给定策略 $ \pi $下状态 $ s $的状态价值函数(State-Value Function) $v_{\pi }(s)$ :     
    $$v_{\pi }(s)=E_{\pi }[G_{t}|S_{t}=s]$$
状态$ s $的最优状态价值函数(The Optimal State-Value Function) $v_{\ast }(s)$: 
$$v_{\ast }(s)=\underset{\pi }{\max }v_{\pi }(s)$$ 

## 动作价值函数 & 最优动作价值函数   
给定策略 $ \pi $,状态$ s $, 采取动作 $ a $的动作价值函数(Action-Value Function) $q_{\pi }(s,a)$:
$$q_{\pi }(s,a)=E_{\pi }[G_{t}|S_{t}=s,A_{t}=a]$$  
状态$ s $下采取动作$ a $的最优动作价值函数(The Optimal Action-Value Function) $q_{\ast }(s,a)$:
$$q_{\ast }(s,a)=\underset{\pi }{\max }q_{\pi }(s,a)$$

## 最优策略
如果策略$ \pi $优于策略$\pi ^{\prime }$:   
$$\pi \geqslant \pi ^{\prime }$ if $v_{\pi }(s)\geqslant v_{\pi ^{\prime}}(s),\forall s $$  
最优策略$v_{\ast }$满足:
- $v_{\ast }\geqslant \pi ,\forall \pi $
- $v_{\pi _{\ast }}(s)=v_{\ast }(s)$   
- $q_{\pi _{\ast }}(s,a)=q_{\ast }(s,a)$   

如何找到最优策略？可以通过最大化$q_{\ast }(s,a)$来找到最优策略：   
$v_{\ast }(a|s)=\{%
\begin{array}{c}
1\text{ if }a=\arg \max_{a\in A}q_{\ast }(s,a) \\ 
0\text{ otherwise}%
\end{array}%
$      
对于 MDP 而言，总存在一个确定的最优策略，而且一旦我们获得了$q_{\ast }(s,a)$，我们就能立即找到最优策略。  
