---
layout: post
title: Group signature and Ring signature
categories: Cryptography
description: Introduction of group signature and ring signature
keywords: cryptography
comments: false
---   
最近学习了群签名(Group signature)和环签名(Ring signature),这里将其概念简单的总结一下。   

## 群签名（Group signature）

在一个群签名方案中，群体中的任意一个成员都可以以**匿名**的方式代表群体对消息进行签名。同样的，和其他**数字签名**一样，群签名是可以公开验证的，并且可以只用单个**群公钥**来进行验证。  

群签名方案的关键是“群管理员”，它负责添加群成员，并能够在发生争议的时候揭示签名者身份。在一些系统中，添加成员和 撤销签名匿名性的责任被分开，并分别赋予给**群管理员**和**撤销管理员**。   

### 历史   
1991年，Chaum 和 Heyst 首次提出群签名的概念。从那时起，越来越多的协议被引入，并在这个模型上加入了类似于数字签名的非伪造性的概念，当然也包括更具体的概念，如废除。直到Bellare, Micciancio 和 Warinschi 才提出了一个更精确的正式模型，这个模型如今被用于群签名方案的工程实现。  

### 群签名的一般流程  
群签名方案实现一般由以下四个可行的算法组成：初始化、签名、验证和打开。
1. 初始化过程  
 系统选取参数，输入安全参数 $ \lambda $ 和 $ \ N $, 返回公钥 $ gpk $ 和私钥 $ gsk $ ,以及私钥对 $ gsk[d] $,对应用户 $ d $ 的私钥和打开密钥 $ ok $. 
2. 成员加入  
在用户加入群的时候，群管理员颁发群证书（Group Certificate）给群成员。  
3. 签名过程
群成员利用获得的群证书签署文件，生成群签名。
输入密钥 $ gsk[d] $ 和消息 $ m $, 返回签名 $ \sigma $ 。
4. 验证过程  
验证者利用群公钥仅可以验证所得群签名的正确性，但是不能确定群中的正式签署者。      
以公钥 $ gpk $ ，消息 $ m $ 和 签名$ \sigma $ 作为输入，以布尔值返回验证结果。   
5. 打开过程  
群管理员利用群私钥可以对群成员生成的群签名进行追踪，并且暴露签名者身份。     
以打开密钥 $ ok $，消息 $ m $, 签名 $ \sigma $ 作为输入，返回用户身份 $ d $ 或者错误结果 *错误*。   
真实的消息签名的验证将返回 true，如下所示：    
$$ \forall m,(gpk,gsk)  \longleftarrow Init(\lambda,N):Verify(gpk,m,Sign(gsk[d],m))= true $$   
![Group signature](/images/posts/crypt/group-signature.png)   
### 安全性要求   
- **完整性(Soundness and completeness)**：群成员的有效签名始终验证正确，无效签名则始终验证失败。   
- **不可伪造性(Unforgeability)**： 只有群成员才能创建有效的群签名。   
- **匿名性(Anonymity)**： 给定一个群签名后，如果没有群管理员的密钥，则无法确定签名者的身份，至少在计算上是不可行的。   
- **可追踪性(Traceability)**：给定任何有效的签名，群管理员应该能够确定签名者的身份。（这也暗示了只有群管理员才能破坏其匿名性）  
- **不关联性(Unlinkability)**：给定两个消息及其签名，无法判断签名是否来自同一签名者。   
- **无框架(No framing)**：即使所有其他群成员相互串通（包括和管理员串通），他们也不能为非群成员伪造签名。   
- **不可伪造的跟踪验证(Unforgeable tracing verification)**： 撤销管理员不能错误地指责签名者创建了他本没有创建的签名。   
- **抗合谋攻击(Coalition-Resistance)**：即使所有群成员相互串通，他们也不能产生一个合法的不能被跟踪的群签名。     
  

## 环签名（Ring signature）   

2001年，Rivest, shamir和Tauman三位密码学家首次提出了环签名。**是一种简化的群签名，只有环成员没有管理者，不需要环成员间的合作**。环签名方案中签名者首先选定一个临时的签名者集合,集合中包括签名者。然后签名者利用自己的私钥和签名集合中其他人的公钥就可以独立的产生签名,而无需他人的帮助。签名者集合中的成员可能并不知道自己被包含在其中。   
环签名是一种特殊的群签名，没有可信中心，没有群的建立过程，对于验证者来说，签名人是完全正确匿名的。   
环签名提供了一种匿名泄露秘密的巧妙方法。环签名这种无条件匿名性在对信息需要长期保护的一些特殊环境中非常有用。例如：即使 RSA 被攻破也必须保护匿名性的场合。   
环签名因签名中参数$C_{i}(i=1,2,\ldots, n)$ 根据一定的规则首尾相连接组成环状而得名。其实就是实际的签名者用其他可能签名者的公钥产生一个带有断口的环，然后用私钥将断口连成一个完整的环。任何验证者利用环成员的公钥都可以验证一个环签名是否由某个可能的签名人生成。


### 定义   
假定有 $ n $ 个用户，每一个用户 $ u_{i} $ 拥有一个公钥$ y_{i} $ 和与之对应的私钥$ x_{i} $。环签名是一个能够实现签名者无条件匿名的签名方案，主要由以下算法组成：   
1. **密钥生成过程(Gen)**: 一个概率多项式时间(PPT)算法，输入安全参数 $ k $,输出为公钥和私钥。这里假定 Gen 为每一个用户 $ u_{i} $, 产生一个公钥$ y_{i} $和私钥$x_{i}$,并且不同的用户的公私钥可能来自不同的公钥体制，如有来自 RSA, 有的来自 DL。
2. **签名过程(Gign)**:一个 PPT 算法，在输入消息 $ m $和 $ n $个环成员的公钥$L=\{y_{1},y_{2},\ldots ,y_{n}\}$ 以及其中一个成员的私钥$x_{s}$ 后，对消息 $m$产生一个签名 $R$, 其中 $R$中的某个参数根据一定的规则呈环状。   
3. **验证过程(Verify)**:一个确定性算法，在输入$(m,R)$后，若$R$为$m$的环签名，则输出"**True**", 否则输出 "**False**"。
环签名因为其签名隐含的某个参数按照一定的规则组成环状而得名。在之后提出的方案中，不要求签名的构成结构成环状，只要签名的形成满足自发性、匿名性和群特性，也称之为环签名。   
![Ring signature](/images/posts/crypt/ring-signature.png)   

### 安全性要求  
- **无条件匿名性**：攻击者即使非法获取了所有可能签名者的私钥，他能确定出真正的签名者的概率不超过$1/n$ ,这里$n$为环成员的个数。  
- **不可伪造性**：外部攻击者在不知道任何成员私钥的情况下，即使能够从一个产生环签名的随机预言机那里得到任何消息$m$的签名，他成功伪造一个合法签名的概率也是可以忽略的。  
- **环签名具有良好的特征**：可以实现签名者的无条件匿名，签名者可以自由指定自己的匿名范围；构成优美的环形逻辑结构；可以实现群签名的主要功能但无需可信第三方或群管理员等。    

    - 正确性：如果按照正确的签名步骤对消息进行签名，并且在传播过程中签名没有被篡改，那么环签名满足签名验证等式。   
    - 无条件匿名性：攻击者即使非法获取了所有可能签名者的私钥，他能确定出真正的签名者的概率不超过$1/n$ ,这里$n$为环成员的个数。
    - 外部攻击者在不知道任何成员私钥的情况下，即使能够从一个产生环签名的随机预言机那里得到任何消息$m$的签名，他成功伪造一个合法签名的概率也是可以忽略的。

## 两者比较  
1. **匿名性**: 都是一种个体代表群体签名的体制，验证者能验证签名为群体中某个成员所签，但并不能知道为哪个成员，以达到签名者匿名的作用。
2. **可追踪性**: 群签名中，群管理员的存在保证了签名的可追踪性。群管理员可以撤销签名，揭露真正的签名者。环签名本身无法揭示签名者,除非签名者本身想暴露或者在签名中添加额外的信息。提出了一个可验证的环签名方案,方案中真实签名者希望验证者知道自己的身份,此时真实签名者可以通过透露自己掌握的秘密信息来证实自己的身份。
3. **管理系统**: 群签名由群管理员管理，环签名不需要管理，签名者只有选择一个可能的签名者集合，获得其公钥，然后公布这个集合即可，所有成员平等。

## 参考  
- [简书-环签名与群签名](https://www.jianshu.com/p/e0104dd841fb)   
- [维基百科-群签名](https://zh.wikipedia.org/wiki/%E7%BE%A4%E7%AD%BE%E5%90%8D)  
- [群签名与环签名](https://blog.csdn.net/lovely_girl1126/article/details/79128788)
- [环签名](https://baike.baidu.com/item/%E7%8E%AF%E7%AD%BE%E5%90%8D/22448429#:~:text=%E7%8E%AF%E7%AD%BE%E5%90%8D(ring%20signature)%E6%98%AF,%E7%8E%AF%E6%88%90%E5%91%98%E9%97%B4%E7%9A%84%E5%90%88%E4%BD%9C%E3%80%82)   
- [什么是环签名](https://www.jinse.com/blockchain/241175.html)    
