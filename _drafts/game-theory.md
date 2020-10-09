---
layout: post
title: 博弈论的一些知识
categories: Game-theory
description: 关于博弈论中的一些知识
keywords: Game theory 
comments: false
---     


## Price of anarchy(PoA)      
Price of anarchy(PoA)：无政府状态的代价，是经济学和博弈论中的一个概念，用来衡量一个系统的效率如何因为 agent 的自私行为而降低。这是一个普遍的概念，可以扩展到各种系统和效率的概念。例如，考虑一个城市的交通系统，许多 agents 尝试着从某个初始位置(initial location)到达目的地(destination)，假设效率(efficiency)代表 agent 到达目的地的平均时间。在集中式(centralized)解决方案中，中央机构可以告诉每个 agent 采取哪一条路径，以最小化平均通行时间。在去中心化(decentralized)的方式中，每个 agent 选择自己的路径。PoA 衡量的是两种情况下平均通行时间的比率。     

系统通常被建模成一个 game，效率是结果的某种函数(网络的最大延迟、交通系统的拥塞程度、拍卖中的社会福利等)。不同的均衡概念可以用来对 agent 的自私行为进行建模，其中最常见的是 Nash equilibrium。不同的纳什均衡导致了 PoA 的概念的不同，比如 **Pure Price of Anarchy** (for deterministic equilibria)纯粹的 PoA(对于确定性均衡来说)、**Mixed Price of Anarchy** (for randomized equilibria)混合的 PoA (对于随机均衡)，和**Bayes–Nash Price of Anarchy** (for games with incomplete information)贝叶斯纳什 PoA（对于不完全信息博弈）。

通俗来讲，PoA就是如果参与者被迫进行协调时，最坏情况下的纳什均衡的系统成本(如最大完工时间、平均等待时间)超过最优系统成本。
