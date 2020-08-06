---
layout: post
title: Reading notes-《An Introduction to Multi Agent Systems》
categories: Multi-agent system, Reading notes
description: 读《An Introduction to Multi Agent Systems》的笔记
keywords: Multi-agent system, Reading notes
comments: false
---    

# An Introduction to MultiAgent Systems   

### About Author     

[Michael Wooldridge](http://www.cs.ox.ac.uk/people/michael.wooldridge/) 是牛津大学 Hertford College(赫特福德学院) 的 Senior Research Fellow(高级研究员), 牛津大学计算机科学系的教授及系主任。主要的研究方向是 Multi-agent system。   

### About This Book    
这本书主要是从理论和实践的角度来介绍 multi agent system(多智能体系统)。多智能体系统是由多个相互作用的 agent（智能体）组成的系统 。agent 具有自主性(autonomous)和交互性(interactivity)的能力。其中，自主性是指 agent 能够自己决定他们需要做什么来满足他们的目标。交互性是指 agent 能够与其他 agent 或者人类互动，不仅仅是交换数据，还有合作(cooperation)、协调(coordination)、谈判(negotiation)等。       

相关的 Lecture Slides 和 Videos 可以在这本书的[课程主页](http://www.cs.ox.ac.uk/people/michael.wooldridge/pubs/imas/IMAS2e.html)上找到。
 
## Introduction      

这本书是关于多智能体的，主要解决的是一下两个关键的问题：  

> - How do we build agents that are capable of independent, autonomous action in order to successfully carry out the tasks that we delegate to them?   
> - How do we build agents that are capable of interacting (cooperating, coordinating, negotiating) with other agents in order to successfully carry out the tasks that we delegate to them, particularly when the other agents cannot be assumed to share the same interests/goals? 

也就是说，第一个解决的是如何构建一个独立、自主行动的 agent ，以便能够完成我们委托给他们的任务。第二个解决的是如何构建能够与其他 agent 进行**交互(合作、协调、谈判)**的 agent，以便能够成功地执行委托给他们的任务，特别是在 其他agent不能够共享相同的利益或目标的时候。
第一个问题是 **agent 设计(agent design)**问题，第二个问题是 **社会设计(society design)**问题。   
把之前的问题分解一下：

> - How can cooperation emerge in societies of self-interested agents? 
> - What sorts of common languages can agents use to communicate their beliefs and aspirations, both to people and to other agents? 
> - How can self-interested agents recognize when their beliefs, goals, or actions conflict, and how can they reach agreements with one another on matters of self-interest, without resorting to conflict? 
> - How can autonomous agents coordinate their activities so as to coopera- tively achieve goals?    

- 在自私自利的社会中，合作是如何出现的？
- agent 可以使用哪些通用语言来向人们和其他 agent 传达他们的信念和愿望？   
- 当他们的信仰、目标或行为发生冲突时，自利的 agent 如何识别，他们如何在不诉诸冲突的情况下就自身利益问题达成一致？
- 自主 agent 如何协调他们的活动以协同实现目标？   

虽然这些问题在一定程度上是由其他学科（特别是经济学和社会科学）来解决的，但是多智能体系统领域的独特之处在于它强调所讨论的主体是**计算的(computational)、信息处理(information processing)的实体**。（重点）     

### Objections to Multiagent Systems   

对于多智能体系统，一些人对它保持怀疑态度，因此，作者在这里对一些常见的反对意见予以回应。   

####  Is it not all just distributed/concurrent systems?      

在设计和实现多智能体系统的时候，必须要借鉴分布式或并发式系统的优点，因此，在实现多智能体系统时，需要考虑诸如**共享资源互斥、死锁**等问题。   
因为 agent 是自治的，它能够独立决定如何做才能满足他们的设计目标，因此，我们需要允许 agent 在运行时同步和协调其活动的机制。另外，agent 主要关心的是自己的利益。因此由于以上两种原因，多智能体系统领域所研究的问题会与在分布式/并发式系统中研究的问题有很大的不同。在这里，我们关注的问题应该包括 agent 如何通过谈判就共同关心的问题达成一致，以及 agent 如何与目标或动机未知的 agent 动态协调。    

#### Is it not all just artificial intelligence (AI)?    

多年来，多智能体系统领域与 AI 领域有着密切的关系。事实上，直到最近，人们才普遍认为多智能体系统是人工智能的一个子领域。     
> 首先,AI 在很大程度上关注智力的核心要素：学习、计划、理解图像的能力等等。相比之下，agent 领域关注的是集成这些组件，以便实现一台能够做出独立决策的机器。因此，为了构建一个 agent，我们需要解决 AI 本身的所有问题，比如规划问题，学习问题等。但是事实并非如此，当我们构建一个 agent 在某个环境中执行任务时，我们很可能利用 AI 的某种技术，但我们所做的大部分将是标准的计算机科学和软件工程。简而言之，我们也许会用到 AI 中的某些技术来构建 agent，但是我们并不需要解决 AI 的所有问题来构建 agent。   
另外，经典的 AI 在很大程度上忽略了 agent 的社会属性。有一点需要清除，作为地球上的一个物种，我们独一无二的原因不仅仅是因为我们的学习能力和解决问题的能力，而是我们与同龄人交流、合作和达成协议的能力。这些社交能力渗透在我们日常生活中，因此，对于 agent 来说，也是重要的组成，就好像计划和学习能力一样重要。

#### Is it not all just economics/game theory?   

Game Theory（博弈论）是研究自利的 agent 之间相互作用的数学理论。近年来，博弈论的工具和技术在计算型多智能体系统的研究中得到了广泛的应用，特别是在谈判等问题上。关于多智能体系统是否被恰当地视为经济学/博弈论的一个子领域，有两点需要指出：  
> 首先，许多在博弈论中发展起来的解决方案的概念 （比如纳什均衡）是在没有考虑到计算的情况下发展起来的。它们往往是描述性的概念，告诉我们一个适当的、最佳的解决方案。此外，计算一个解的问题往往在计算上非常困难(例如 NP 完全问题等)。多智能体系统的研究突出了这些问题，并使得我们能够利用计算机科学的工具(如计算复杂性理论等)来解决这些问题。       
> 另外, 一些研究学者质疑博弈论为了得出结论所作的假设。特别地，在多智能体系统领域中，关于博弈论中建模的理性(rational)智能体的概念是否有效或者对于理解人类或人工智能社会是否有用展开了争论。     

**请注意，所有的这些都不应该理解为对博弈论的批评，博弈论无疑是多智能体系统中一个非常有价值并且重要的工具，在未来可能会得到广泛的应用。**    

#### Is it not all just social science?      
 
社会科学主要研究人类社会的行为。一些社会科学家对(计算的)多智能体系统感兴趣，因为它们提供了一种模拟人类社会的实验工具。此外，设计多智能体系统（即人类社会）的一个明显方法是研究人类社会中某个特定功能的工作方式，并尝试以同样的方式构建多智能体系统。这里可以用人工智能的方法进行类比，研究人类如何获得某种特定的智能，然后尝试在计算机程序中对此进行建模，这是相当常见的。因此，多智能体系统领域是否只是社会科学的一个子集呢？        
虽然我们可以从人类社会中汲取有益的见解和类比，但这并不意味着我们可以用完全相同的方式来建立人工社会。众所周知，要精确地模拟人类社会的行为是非常困难的，因为它们依赖于如此多不同的参数。此外，尽管通过借鉴和利用人类社会的类比和隐喻来设计多智能体系统是完全合法的，但这并不意味着这将是设计多智能体系统的最佳方式。还有其他工具（比如博弈论）。 
在作者看来，多智能体系统和社会科学有很多关联，多智能体系统为建模和理解社会提供了一个强大而新颖的工具，而社会科学代表了理解和构建多智能体系统的丰富概念库，但它们是截然不同的学科。

 —— 2020年7月17日  

---   
   
##  Intelligent Agents     

当我们想要了解多智能体系统时，我们首先要先了解什么是 agent。但遗憾的是，目前对于 agent 没有一个普遍接受的定义，并且在这个问题上存在很多争议。虽然人们普遍认为 autonomy(自治性)是 agent 的核心，但除此之外几乎没有达成一致意见。这种现象的原因在于，agent 所具有的不同的属性对于不同的领域来说，其重要性也不相同。

> An agent is a computer system that is situated in some environment, and that is capable of autonomous action in this environment in order to meet its design objectives.  
> agent 是位于某个环境中的一个计算机系统，它能够在该环境中自主地活动，以实现其设计目标。        
>      —— Wooldridge and Jennings (1995)      


![agent](/images/posts/agent/agent.png)         

如上图，agent 在它所处的环境中，它能够从环境中获取感应信息，并产生影响环境的输出动作。这种互动是一种持续的、非终结性的互动。   
图给出了 agent 的抽象视图。在这个图中，我们可以看到 agent 为了影响其环境而生成的动作输出。在大多数具有合理复杂性的领域中，agent 不能完全控制其环境。它最多只能有部分控制，因为它可以影响环境。从行为人的角度来看，这意味着在明显相同的情况下执行了两次相同的动作，可能会出现完全不同的效果，特别是可能无法达到预期的效果。因此，除了最微小的环境之外，所有环境中的 agent 都必须为可能出现的故障做好准备。我们可以把这种情况正式地总结为环境通常被假定为不确定性。     
通常，agent 会有一系列可用的操作。这组可能的操作表示 agent 的反射能力:它改变环境的能力。注意，并不是所有的操作都可以在所有的情况下执行。例如，一个动作“lift table”只适用于重量足够小的情况，agent 可以举起它。同样，如果资金不足，“购买一辆法拉利”的行动也会失败。因此，动作具有与之关联的先决条件，这些先决条件定义了可以应用它们的可能位置。      
agent 所面临的关键问题是决定它应该执行哪些操作，以便最好地满足其设计目标。agent 体系结构，实际上是嵌入到环境中的 decision-making system。比如控制系统(control system) 可以看作是一个 agent。这样的系统可以是一个恒温器(thermostat)，它通过传感器去检测室内的温度，传感器是直接嵌入到环境中的，它将产生两个信号中的一个作为输出，一个表示温度过低，一个表示温度正常。恒温器可用的操作是"加热打开"或"加热关闭"。操作通常会产生提高室内温度的效果。但是这不能保证效果，比如在门窗都打开的情况下，打开加热器可能没有任何效果。因此，恒温器是一种简单的 decision-making 系统。他执行一下规则：
> too cold ——> heating on    
> temperature OK ——> heating off    

当然，更复杂的环境控制系统有更丰富的决策结构，例如自主空间探测器、无人机、核反应堆控制系统等。    

总而言之，agent 就是能够在某些环境中自主行动已达到其设计目标的计算机系统。一个 agent 通常会感知他的环境，并拥有一系列可以执行的操作来修改环境。      

### Environments   

Russell 和 Norvig 建议对环境的特点做以下分类：     
- **Accessible versus inaccessible** : 可访问环境是指 agent 可以获得有关环境状态的完整、准确、最新的信息。大多数现实世界的环境（包括，例如，每天的物理世界和互联网）在这个意义上是不可访问的。    
- **Deterministic versus non-deterministic** : 确定性环境是指任何动作都有一个单一的保证效果的环境，在这种环境中，执行某个动作所产生的状态没有不确定性。     
- **Static versus dynamic** : 静态环境可以假定为保持不变，除非 agent 执行操作。相比之下，动态环境是一个有其他进程在其上运行的环境，因此它以超出 agent 控制的方式发生变化。物理世界是一个高度动态的环境，互联网也是如此。   
- **Discrete versus continuous** : 如果有一个固定的、有限的动作和感知存在，那么这个环境是固定的。

我们从可访问性来进行讨论。首先，物理世界中的环境大多是都是不可访问的。当一个环境越容易访问，那么构建在其中有效运行的 agent 就越简单。举个例子，一个“好”的经纪人是做出“正确”决定的人。agent 所能做出的决策的质量显然取决于它所能或得的信息的质量，如果可用的信息很少或不准确，那么 agent 的决策可能就会很差。随着信息的完善和精确，agent
做出一个好的决定的可能性会增加。       

对于确定性来说，如果执行的任何操作的结果都是唯一定义的，则环境是确定的，否则是不确定的。例如，我们通常把软件环境想象成由精确的规则管理的，这是确定性的范例。非确定性主要有以下几个重要方面：首先，行动者的影响范围是有限的，他们最多只能部分地控制他们的环境。另外，操作通常是由 agent 执行的，目的是为了实现某些所需的事务状态，但是非确定性使得行动可能无法得到预期的结果。   

显然，从代理设计者的角度来看，确定性环境比非确定性环境更可取。如果某一特定行动的结果从来没有任何不确定性，那么代理人就永远不必停下来确定某一特定行动是否有特定的结果，从而决定它是否需要重新考虑它的行动方针。特别是，在一个确定的环境中，代理设计者可以假设代理执行的操作总是成功的：它们永远不会失败，以实现预期的效果。
不幸的是，正如Russell和Norvig(1995)所指出的，如果一个环境足够复杂，那么它实际上是确定性的这一事实并没有多大帮助。从所有的意图和目的来看，它可能是不确定的。在实践中，几乎所有的现实环境都必须从行为人的角度来看是非确定性的。    
    
非决定论与**动态论(dynamism)**密切相关。早期关于行动选择的人工智能的研究主要集中在**规划算法(planning algorithms)**上，这些算法描述了环境的初始状态、agent 可用的操作及其效果和目标状态，将生成一个计划（即一系列行动），这样当从初始环境状态开始执行时，该计划将保证目标的实现（Allen et a/，1990）。然而，这些规划算法隐含地假设执行计划的环境是静态的(static)，除非通过 agent 执行操作，否则不会发生变化。显然，许多环境（包括软件环境，如计算机操作系统，以及物理环境，如真实世界）并不适用这一特性—它们是动态的(dynamic)，许多进程同时运行，以 agent 无法控制的方式修改环境。     

从 agent 的角度来看，动态环境至少有两个重要的属性。首先，如果agent 在 $t_{0}$ 
 





















## Reference   
[An Introduction to Multi Agent Systems](/files/An Introduction to Multi Agent Systems.pdf)