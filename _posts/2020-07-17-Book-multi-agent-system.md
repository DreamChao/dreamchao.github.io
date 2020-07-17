---
layout: post
title: Reading notes ——《An Introduction to Multi Agent Systems》
categories: Multi-agent system, Reading notes
description: 读《An Introduction to Multi Agent Systems》的笔记
keywords: Multi-agent system, Reading notes
comments: false
---    

# 《An Introduction to MultiAgent Systems》    

### About Author     

[Michael Wooldridge](http://www.cs.ox.ac.uk/people/michael.wooldridge/) 是牛津大学 Hertford College(赫特福德学院) 的 Senior Research Fellow(高级研究员), 牛津大学计算机科学系的教授及系主任。主要的研究方向是 Multi-agent system。   

### About This Book    
这本书主要是从理论和实践的角度来介绍 multi agent system(多智能体系统)。多智能体系统是由多个相互作用的 agent（智能体）组成的系统 。agent 具有自主性(autonomous)和交互性(interactivity)的能力。其中，自主性是指 agent 能够自己决定他们需要做什么来满足他们的目标。交互性是指 agent 能够与其他 agent 或者人类互动，不仅仅是交换数据，还有合作(cooperation)、协调(coordination)、谈判(negotiation)等。       

相关的 Lecture Slides 和 Videos 可以在这本书的[课程主页](http://www.cs.ox.ac.uk/people/michael.wooldridge/pubs/imas/IMAS2e.html)上找到。
 
## Introduction      

这本书是关于多智能体的，主要解决的是一下两个关键的问题：  

> - How do we build agents that are capable of independent, autonomous action in order to successfully carry out the tasks that we delegate to them?   
> - How do we build agents that are capable of interacting (cooperating, coordinating, negotiating) with other agents in order to successfully carry out the tasks that we delegate to them, particularly when the other agents cannot be assumed to share the same interests/goals? 

也就是说，第一个解决的是如何构建一个独立、自主行动的 agent ，以便能够完成我们委托给他们的任务。第二个解决的是如何构建能够与其他 agent 进行交互(合作、协调、谈判)的 agent，以便能够成功地执行委托给他们的任务，特别是在 其他agent不能够共享相同的利益或目标的时候。
第一个问题是 agent 设计(agent design)问题，第二个问题是 社会设计(society design)问题。   
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

在设计和实现多智能体系统的时候，必须要借鉴分布式或并发式系统的优点，因此，在实现多智能体系统时，需要考虑诸如共享资源互斥、死锁等问题。   
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


