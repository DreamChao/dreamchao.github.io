## 前提   
 Agent 主要与理性的行为有关，在理想的状态下， agent 需要采取一个在其所处的环境中使其性能度量最大化的行动(action)。 追求尽可能好的行为表现是 agent 的目标。  
## Agent 与环境   
 Agent 是通过传感器(sensors) 来对外部环境进行感知，并通过执行器(actuator) 来对环境做出反应。   

 **感知(Percept)** 表示任何给定时刻 agent 从外部环境得到的感知输入。 这个感知输入的完整历史数据称为这个agent到此刻为止的**感知序列(Percept Sequence)**。   
 
 Agent 的**行动(action)** 依赖于到此刻为止的感知序列。   

 感知序列到行动的映射关系被定义为这个 Agent 的 Agent 函数(agent function)。   

 Agent 的感知序列是**无穷**的。因此，Agent 函数只能通过 Agent 程序实现。   
 Agent 函数是抽象的数学描述，Agent 程序是具体实现 Agent 函数的方法。   

## 如何判断一个行为的好坏？—— 理性的概念
### 性能度量  
行为的好坏需要一个具体的、量化的评价，才能达成理性的目标。我们希望 Agent 的行动可以导致环境向一个好的方向变化。 这种“希望”需要通过**性能度量(Performance measure)** 表述以来评估行为。 为了达到客观理性，性能度量基于对**环境状态**的变化而不是对 Agent 自身的状态变化。合适的性能度量应该基于想要达成的环境状态来进行目标定制。

### 理性的判断   
性能度量只是理性判断的一个方面。理性的判断基于4个方面：
1. 定义成功标准的**性能度量**。
2. Agent 对环境的**先验知识**。  
3. Agent 可以完成的**行动**。  
4. Agent 截止到此时的**感知序列**。  

综上所述，我们得出理性 Agent 的定义：   
**理性 Agent**
> 对每一个可能的感知序列，根据已知的感知序列提供的证据和Agent具有的先验知识，理性Agent应该选择使其性能度量最大化的行动。





















## A Variety of Definitions  
* Accommodate new problem solving rules incrementally.   逐渐顺应新的问题求解规划。   
* Adapt online and in real time.  适合在线与实时    
* Able to analyze itself in terms of behavior, error and success. 能够从行为、错误与成功等方面进行自我分析。   
* Learn and improve through interaction with the environment.  能够通过与环境交互来进行学习和改善。   
* Learn quickly from large amounts of data. 迅速从大量的数据中学习。   
* Have memory-based exemplar storage and retrieval capacities.   具有基于内存的样本存储和检索能力。   
* Have parameters to represent short and long term memory, forgetting, etc. 具有表示短期和长期记忆、遗忘等参数。   

## What is a Rational Agent   
 * It is one that does the **right thing** - every entry in the table for the agent function is filled out correctly. 是一个做正确事的 agent ,可以认为是在这个 agent 的功能表中的每个条目都是正确填写的。     

## What is the Right Thing 
 * An agent in an environment generates a sequence of actions according to the percepts.     
 一个智能体在一个环境中依据感知生成一系列动作。   
 * Those actions causes the environment to go through a sequence of states.   
这些动作经由一系列状态而引起环境发生变化。   
 * If the sequence is desirable, then the agent has performed well.   
 如果该系列变化是所期望的，则该智能体表现良好。 

 ## Right Thing = Rational Action   

* Rational 
   exploration, learning, autonomy.   理性： 探索、学习、自主   
* Rational action    
  Maximize the expected value of performance measure given the percept sequence.   
  理性动作： 对给定的感知序列，能使期望的性能指标最大化。   
  > Rational = Best    理性 = 最佳
  Rational = Optimal   理性 = 最优
  Rational != Omniscience   理性 != 全知全能 
  Rational != Clairvoyant   理性 != 明察秋毫
  Rational != Successful    理性 != 百战百胜  

## Concept of Rationality    

* Rationality depends on four things:   理性依赖于四件事：

> * The performance measure that defines the criterion of success.  定义成功标准的性能标准。   
> * The agent's prior knowledge of environment.   智能体对环境的先验知识。  
> * The actions that the agent can perform.   智能体能够完成的动作。     
> * The agent's percept sequence to  date.   智能体最新的感知序列。    

## Different Environment Types    

* Fully observable vs. partially observable   完全可观测与部分可观测    
 An agent sensors give it access to the complete state of the environment at each point in time, then the task environment  is fully observable.      
 一个智能体的传感器在每个时间点上可访问环境的完整状态，则该任务环境是完全可观测的。
     
 * Single agent vs. multi-agent  单智能体与多智能体   
 An agent operating by itself in an environment, then it is fully single agent.      
 一个智能体在一个环境内自运作，则他就是一个单智能体。   

 * Deterministic VS. stochastic   确定性与随机性    
 The next state of the environment is completely determined by the current state and the action executed by the agent, then the environment is deterministic.     
 环境的下一个状态完全由当前的状态和由该智能体执行的动作所决定，则该环境是确定性的。  

 * Episodic VS. Sequential    阵发性与连续性  
 The agent's experience is divided into atomic episodes, and the choice of action in each episode depends only on the episode itself.   
 智能体的动作过程被分为原子的片段，并且每个片段的动作选择仅仅依赖于片段本身。   

 * Dynamic VS. Static   动态与静态   
 If the environment can change while an agent is delibereting, then the environment is dynamic for that agent; otherwise it is static.   
 如果环境随智能体的行为而改变，则该智能体的环境是动态的；否则是静态的。   
  > Semi-dynamic: If the environment itself does not change with the passage of time but the agent's performance score does.      
  半动态：如果环境本身不随时间的推移而改变，但该智能体的性能发生改变。   

 * Known VS. Unknown    已知与未知   
 In the  known environment, the outcomes for all actions are given.    
 在一个已知的环境下，所有动作的结果是给定的。     
 > Obviously, if the environment is unknown, the agent will have to learn how it works in order to make good decisions.    
   显然，如果环境是未知的，则该智能体将需要学习如何行动，以便做出正确的决策。   


## Agent Function 
 The agent function is an abstract concept, it could incorporate various principles of secision making.    
 智能体函数是一个抽象的概念，它可以包含将各种决策制定的原则。  
 >  calculation of utility  of individual options.    单个选项的效用计算。
 deduction over logic rules.   贯穿逻辑规则的推论。   
 fuzzy logic.    模糊逻辑。  
 lookuo table.   查找表。   

## Agent Programs   
An agent program implements an agent function, It take the current percept as input from the sensors, and return an action to the actuators.     
一个智能体程序实现一个智能体功能。它将感受器的输入作为当前的感知，然后返回一个动作给执行器。   

> **function** TABLE-DRIVEN-AGENT(*percept*) **returns** an action  
   **persistent**: percepts, a sequence, initially empty *table*, a table of actions, initially none append *percept* to the end of *percepts*
   action <- LOOKUO(*percepts,table*)                  （表驱动的agent算法） 
   **return** *action*   

The agent program returns an action by lookup table each time.  该智能体程序通过查找表返回一个动作。   
## The Structure of Agents 
> Agent = platform + agent program  
Platform = computing device + sensors + actuators   
agent program 包含 agent function    

### Hierarchies of agents 
* Intelligent agents today are normally gathered in a hierarchical structure  containing many "**sub-agents**".   
智能体通常表现为一个分层的结构，它包含许多子智能体。
* Intelligence sub-agents process and perform lower level functions.  
子智能体处理和执行较低级的功能。   
* Intelligence agent and sub-agents create a complete system that can accomplish difficult tasks with behaviors and responses.   
智能体和子智能体构建一个完整的系统，它可以通过行为和反应来完成艰巨的任务。   

## Type Classes of Agents  
* The classification  is based on their degree of perceived intelligence and capability.  
该分类是基于他们感知的智能和能力的程度。   
* Here we will introduce five kinds of agents that embody the principles underlying almost  all intelligent systems.   
这里我们将介绍5种类型的智能体，体现几乎所有智能系统的基本原理。  
> Simple reflex agents   简单反射智能体
Model-based reflex agent  基于模型的反射智能体 
Goal-based reflex agents  基于目标的智能体
Utility-based agents   基于效用的智能体
Learning agents    学习智能体      
 










http://www.sohu.com/a/194982925_390227



















## 关于我
**年龄**：95年，射手座
**身高**：178
**家乡**：宁夏，准备留西安，独生子
**学历**：西电在读博士，毕业想留高校
**爱好**：偏运动，骑行（经常出去，进山，进城），跑步（去年10月份西安半马完赛），打羽毛球。平时也在办公室养养花，也喜欢猫和狗，也喜欢拍照。
**性格**：认识的人都说性格挺好的。
**对于感情**：如果不喜欢，一点也不会考虑。但只要对对方动了心，定会“所爱隔山海，山海皆可平”。

## 关于她
希望对方身高在160以上，体重正常就好。因为我毕业还得四年，博士期间不会考虑结婚，所以更想找一个能同步的人，比如她也读博或者比我小个几岁。希望她是一个孝顺，温柔体贴，有自己思想的人，比较看重这些。比较在意眼缘，可以互换照片。真心希望能够找到可以携手一生的另一半。

![1.jpg](/images/1.jpg)