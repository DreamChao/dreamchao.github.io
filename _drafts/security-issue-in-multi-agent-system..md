### A survey of security issue in multi-agent systems
由于agent的自动，主动以及能够动态地解决问题的行为，使得multi-agent system引起了研究人员的注意。这篇论文调研了multi-agent system中的安全性相关的研究工作。特别是对于访问控制（access control）和和信任（trust/reputation）问题, 然后给出了自己的研究分析，还提出了现有问题并讨论未来的研究挑战。
#### Keywords 
 intelligent agents， Multi-agent system, Security, Access control, Trust, Reputation

#### Introduction 
 agent 是一个自治（autonomous）且面向目标（goal-oriented）的软件实体，他可以与其他软件实体或人类进行协作和通信。目前，agent有很多种定义，但是对于agent来说，最为普通的特点就是自治（autonomy），社交能力（social-ability），反应性（reactivity）和积极性（pro-activity）。由于这些特性，使得agent 范式已经成为在开放、分布式和异构的环境中开发应用程序最有前途的技术。实际上，基于agent 的系统已经在开放的分布式环境中得到了广泛的开发，尤其是在电子商务、移动计算、网络管理和信息检索领域。    
 在基于agent 的系统中，agent 可能会尝试着从其他agent 获取信息或者向远程提供服务的代理来获得访问权限，以实现其目标。但是在开放的环境中，agent是可以自由行动的，因为很难知道哪些agent 是可信的，哪些外部访问是没有危害的，因此，agent的一些行动是不安全和不可靠的。如果没有适当的解决方案来解决这类问题，那么就会泄露某些敏感信息，或者破坏系统。特别的，对于一些关键性的交易来说，例如与银行和个人医疗健康系统有关的交易，必须要保证安全。然而，agent的自主性、异构性和开放等特性，使得很难保证这些系统的安全性。但是，为了能够充分受益于agent技术，确保MAS 的安全是非常重要的。我们通过不同的机制（例如身份验证[authentication]、授权[authorization]、信任管理[trust management]等）来保证关键的安全属性，例如机密性(confidentiality)、完整性(integrity)、可用性(availability)、问责制(accountability)和不可否认性(non-repudiation)等。  

 近年来，研究人员已经尝试着解决基于agent 的系统中的安全问题，他们分析了安全漏洞并且确定了安全需求和挑战。另外，对于一些可能的南拳攻击已经研究，并且提出了适用于攻击的安全技术。还提出了各种安全模型，中间件和安全服务。在各种安全问题中，移动智能体系统的安全性是许多研究人员的主要研究方向。移动agent是一种特殊的agent类型，它能够从一个主机（host）迁移到另一个主机，并在那里继续执行(Borselius 2002)。agent的可移动性并不是一个强制性的特征，但由于其自身的优点，近年来引起了人们的关注。使用移动代理的最大好处是，它们可以帮助减少网络流量和克服网络延迟(Chess等，1996年)。此外，如果我们能够解决与移动代理相关的安全问题，那么这些解决方案就可以很容易地应用于解决任何类型的基于代理的系统的安全问题(Ghanea-Hercock和Gifford 2001)。除了一般针对移动代理安全的研究外，一些研究人员还针对特定的访问控制和信任管理需求研究了解决方案。此外，还分析了许多现有的安全解决方案，以确定它们是否适用于基于agent的系统。除了基于agent 的系统的安全考虑外，一些研究人员还提出使用代理来提供安全服务;在本文中不讨论这些。    
 在本文中，介绍了基于agent的系统的安全需求分析和安全解决方案的现有工作，特别是访问控制和信任模型。还讨论了它们的局限性和未来的挑战。论文的其余部分组织如下。第2节介绍了通过分析相关威胁和漏洞来解决多代理系统(MASs)安全需求的研究。在第三节中，提出了现有的安全解决方案，以抵御各种威胁。第4节介绍了适合于大规模使用的认证技术和访问控制模型，包括用于分布式访问控制的信任管理解决方案。第5节介绍了关于大众信任和声誉的现有研究。最后，在第六部分，我们总结并提出未来的研究方向。

 #### Security requirements in MAS

 在这一节中，首先定义MAS的特点，然后描述了基于agent特征的安全漏洞，并确定了安全需求。

 ##### Multi-agent systems
 对于agent 和 MAS 的定义有很多，在本文中，使用了普遍接受的定义(Jennings et al. 1998):
 > An agent is a software entity, situated in some environment, that is capable of flexible, autonomous action in order to meet its design objectives.  
 > 一个agent是一个软件实体，它位于环境中，能够灵活、自主地行动以满足它的设计目标。     

虽然没有一个普遍接受的定义，但是大多数研究人员都同意agent 的共同特征是情境性(situatedness)、自主性(autonommy)和灵活性(flexibility)(Franklin and Graesser 1996;Jansen 2000;Jennings等人(1998)将agent 范式与其他软件范式区分开来。

- 情境性是指 agent 根据从环境中接收到的感官输入来感知自身的具体情况。
- 自主性是指行为人能够控制自己的行为和内部状态，而不需要人类或其他行为人的直接干预。
- 灵活性是指能够适应不断变化的情况，并持续地执行操作以实现代理的目标的能力。 灵活性有三个属性:反应性(responsiveness)、主动性(proactiveness)和社交能力(scial-ability)。
 响应性意味着代理可以执行更改环境的操作，或者在它们意识到其环境时作为响应提供反馈。
 主动性意味着行为主体不只是对环境做出反应; 相反，他们能够表现出目标导向（goal-directed）的行为(FranklinandGraesser1996)。
社交能力是指agent 为了解决自己的问题或帮助他人而与其他agent 和人类相互作用的能力。
此外，还有其他的特征，如机动性(mobility)、理性(rationality)、诚实的(veracity)和善良的(benevolence)。
如上所述，mobile agent是一种具有移动特征的 agent，即能够跨网络和在不同主机之间迁移(Greenberg et al. 1998)。
尽管agent system 可以从 agent 的移动性中获得显著的好处，但是agent的移动性也会带来重大的安全问题。mobile agent system的安全问题一直是许多研究人员关注的焦点。本文中将在以下几节中详细描述这些问题和现有的解决方案。

请注意，如上所述，MAS是一个由相互作用的 agent 组成的基于agent 的系统(Ferber 1999)。一般来说，MASs 有一些复杂的问题需要agent 之间的合作来解决。此外，许多 MASs 没有全局控制，它们的数据通常是分散的。为了使 MAS 安全，我们应该处理跨系统发生的问题以及单个 agent 中的安全问题。

##### Vulnerabilities and security requirements 
agent范式已经被证明是开发智能(intelligence)、异构(heterogeneous)和开放系统(open systems)的一种有前景的方法，因为它具有诸如自治(autonomy)、灵活性(flexibility)和协作解决问题的行为(cooperative problem solving behavior)等特性。然而，这样的特性使得确保 MASs 的安全变得更加困难。如今，许多MASs应用程序正在开发，甚至在安全关键领域，如在线商务、银行和医疗服务领域。许多研究人员已经认识到 MASs 攻击的安全漏洞，并确定了可能的攻击。   
在Borselius(2002)、Mouratidis等人(2003)中，作者提出了基于agent特征的 MASs 的安全需求。在情境性特征方面，**信息来源的验证(verification of origin of information)**是一个关键问题。如果环境信息来自一个代理的主机，那么安全问题可能是最小的。然而，如果agent 从互联网上获取信息，就应该检查这些信息是否可信。基本上，agent 应该知道它所使用信息的来源和可信度。这些问题与信息的认证和完整性有关。 agent 的自治性也可能会存在一些严重的安全问题，因为恶意的agent 能够在不需要其他 agent 或人的任何请求的情况下传播(Mouratidis等，2003年)。因此，代理应该能够防止或修复由未经授权的访问可能造成的损害;一个MAS应该被保护免受其他自治代理的恶意入侵。就社会能力而言，我们应该能够确保agent之间以及agent与人之间的安全通信。为了做到这一点，我们需要大量地保证几个安全目标，如保密性、完整性、可用性、可靠性和不可抵赖性。此外，agent 的移动性可能会导致严重的安全问题。主机(host)可能被恶意的mobile agent 破坏。另一方面，恶意主机可能会破坏移动代理的安全性。因此，需要有同时保护主机和移动代理的安全解决方案。为了保证移动代理的安全性，需要注意与其他恶意代理和用户以及恶意主机之间的交互。此外，agent 之间的合作可能会导致更严重的安全问题。为了实现它们的目标，有时候agent可能需要访问其他人维护和拥有的资源，或者了解其他代理的内部状态。如果在没有适当的身份验证和授权机制的情况下允许合作，那么可能会出现严重的安全问题。   
除了确定与代理特征相关的特定漏洞外，文献中还研究了针对MASs的其他可能的攻击。Poslad等人(2002)讨论了与抽象MAS体系结构相关的安全攻击。这项工作分析了智能物理代理( Intelligent Physical Agents，FIPA)体系结构的基础。
FIPA抽象架构(FIPA2002a)定义了如何在一个抽象的层次上注册和交换信息，从而进行彼此的扫描和通信。
为此，定义了一种结构元素及其之间的关系。
在这些元素中，Poslad等人重点关注服务发现模型、消息传输互操作性、代理通信语言(ACL)表示、内容语言和多目录服务表示。
它们描述了与FIPA MAS体系结构的名称服务、目录服务和通信服务相关的几个威胁。
名称服务组件可能允许代理在消息交换或服务请求中伪造身份。
在提供目录服务时，可能会出现拒绝服务(DoS)或未经授权的修改。
在MAS中实体之间的通信中，关键的问题是被传输数据的窃听或损坏。
作者分析了与FIPA抽象架构相关的可能的攻击，但是没有提供这些攻击的解决方案。
 
 

#### Key security properties should be guaranteed
- confidentiality,
- integrity, 
- availability, 
- accountability 
- non-repudiation 
Among a variety of security issues, the security for
mobile agent systems has been the main focus of many researchers. 
