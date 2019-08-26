---
layout: post
title: Homomorphic Encryption
categories: Cryptography
description: 密码学的一些知识
keywords: cryptography
comments: false
---  
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>   
---
同态加密是一种支持在密文上进行计算的加密方式，对在密文上计算得到的结果进行解密后得到的内容与直接在明文上计算得到的结果相同。    

> **Homomorphic encryption** is a form of encryption that allows computation on ciphertexts, generating an encrypted result which, when decrypted, matches the result of the operations as if they had been performed on the plaintext.          
                                                       --Cite from [wikipedia](https://en.wikipedia.org/wiki/Homomorphic_encryption)   

--- 

传统的加密就是将消息或者原始信息用一种方式打乱，得到密文，然后将其保存或者传递给接收者，接收者接收到密文后，用另一种方式对密文进行解密并读取它。这样在一定程度上增加了数据的安全性，因为只有授权的用户才能够读取消息。当然，这种加密方式只有在数据被加密时能保证其安全性，加密的数据只能进行存储或者共享，在云计算飞速发展的今天，这无疑是一个限制。我们知道，云计算为用户提供了许多服务，包括对大数据的存储和计算。然而，要利用云计算，用户就必须信任云服务提供商并与之共享数据。确保数据的隐私性的一种方法就是在上传到云端之前对数据进行加密。但是当用户希望对数据进行计算的时候，就必须下载数据并对数据进行解密，这降低了云服务的优势。所以，在不受信任的公共云上提供安全云计算的一个解决方案就是使用同态加密。   

以下这张图解释了同态是如何用于加密的。加密过程始于明文  m ，他可能是计算机系统中的一个用户名，比如 “john”，目标就是对它执行一些操作，比如将字母大写。这个操作当然是可以实现的，但是在执行操作之前先对数据加密 *enc* 会更加安全，因为这样就不会有人知道John这个名字。 因此这个明文被加密成密文 178672 ，然后，它通过 $$ f(x)= x + 127 $$ 来计算，例如，输出为 178799 ，是另外一个完全加密的消息。那么这个消息可以被解密为 “John”。
![homomorphism and encryption](/images/posts/crypt/homomorphism%20and%20encryption.png)   

目前的同态加密有两种，**部分同态加密(Partial Homomorphic Encryption)**和**完全同态加密(Fully Homomorphic Encryption)**。部分同态加密只允许对加密数据进行某些操作，通常是乘法或除法，并且已经存在多年。完全同态加密允许对加密数据进行所有的操作，30 年以来一直是密码学中一个未解的问题，最终在 2009 年得到了解决。它通常是可取的，因为它允许系统将所有在加密数据上执行的多个操作链接在一起，以避免暴露未加密的数据。

## 概览 (Overview)            
 
同态加密是在 20 世纪 70 年代首次被提出的，其概念是，应该可以对加密的数据执行数学操作，而不必解密其中的任何部分。这显然对现代计算有着巨大的影响。   
在一个典型的同态密码系统中，有些信息是公共的，有些信息是私有的。例如，在上面的例子中，执行 *enc* 函数所需的信息可能是公开的。这样，任何人都可以加密消息。更重要的是，执行 *decrypt* 函数所需的信息是私有的。这样，就没有攻击者窃取评估函数 *enc(f(m))* 并为自己解密。 这就是 RSA 加密方案的基础。  

--- 
在密码学中，假定两个人之间有某种通信，分别叫做 Alice 和 Bob ,Alice 想要给 Bob 一个装满钱的手提箱，让他数一数再还给她。Alice 把手提箱给 Bob ，Bob 向 Alice 索要钥匙来打开它。 Alice 不想把钥匙交给 Bob ，因为她不是很信任他。对于 Bob 来说，如果 Alice 不把钥匙交给他，他就不能打开箱子，也就不知道如何来数箱子里的钱。 因此，这两个人有两个选择：   
1. Alice 可以给 Bob 钥匙，这当然可行。然而，可能会有一个攻击者 Eve ，他想要偷钱。 她可能会假扮 Bob，或者她会从 Bob 那里偷走手提箱和钥匙。
2. 设计一种新的锁，这种锁比需要钥匙的手提箱更好。这种锁不让任何不是 Alice 的人拿到钱，甚至不让他们知道里面有多少钱。但是它将允许任何有权利的人来计算它。这就是同态加密背后的概念，也是它如此强大的原因。  

---  

## 特点 (Properties)  
* 延展性(malleability).    
同态加密在设计上是具有延展性的。具有延展性的密码  系统指的是任何人都可以拦截密文，将其转换为另外一个密文，然后将其解密为有意义的明文。在密码系统中，延展性通常被认为是不受欢饮的。举个例子，如果你想给你喜欢的人发一句 “I love you”, 有一天你终于有勇气说出这句话，你把它加密发给她。但是这个密文信息在中途被你的情敌给拦截了，当然，他看到的只是密文。但是当你喜欢的人试图解密时，就解密成了 “I hate you ”，这就是为什么延展性通常是不需要的。   

![A malleable crypto-system](/images/posts/crypt/A malleable crypto-system.png)      
  
然而，同态加密应该是具有延展性的。举个例子，也许你想要构建一个系统，无论你给你的朋友发送什么，只要在后面加上叹号就可以了。但是由于机密性，你不想让系统知道你发给你朋友的是什么。你加密这个消息并将其发给系统，系统看见的也只是密文，因此，它不知道你在说些什么，但是它可以转换这个密文。它将密文转化为相同的明文消息，加上一个感叹号。他看起来是这样的：   

![another malleable crypto-system](/images/posts/crypt/another malleable crypto-system.png)    

具有延展性的系统允许多方操作数据，特别是在基于云计算的环境下，无需公开数据。另一方面，从延展性的角度, 同态加密方案比非同态的方案在安全特性上更弱.   
  
---  

## 部分同态加密 (Partially homomorphic cryptosystems)   

在接下来的例子中，我们用符号 $$ \varepsilon (x) $$ 表示对消息 $$ x $$ 加密。 


### Unpadded RSA 
If the RSA public key is modulus $$ n $$ and exponent $$ e $$, then the encryption of a message $$ x $$ is given by $$ \varepsilon (x)=x^{e} $$ $$ mod $$ $$ n $$. The homomorphic property is then   

  $$ \varepsilon (x_{1})\cdot \varepsilon (x_{2})=x_{1}^{e}x_{2}^{e} \  mod \  n \  =(x_{1}x_{2})^{e} \  mod \  m = \varepsilon (x_{1} \cdot x_{2} )$$


### ElGamal   

In the [ElGamal cryptosystem](https://en.wikipedia.org/wiki/ElGamal_encryption), in a cyclic group $$ G $$ of order $$ q $$ with generator $$ g $$, if the public key is $$ (G,q,g,h) $$, where $$ h=g^{x}$$ , and $$x$$ is the secret key, then the encryption of a message $$ m $$ is $$\varepsilon(m)=(g^{r},m\cdot h^{r}) $$, for some random $$ r \in $$ {$$1,...,q-1$$}. The homomorphic property is then        

   $$ \varepsilon (x_{1})\cdot \varepsilon (x_{2})=(g^{r_{1}},m_{1}\cdot h^{r_{1}})(g^{r_{2}},m_{2}\cdot h^{r_{2}}) $$     

   $$ =(g^{r_{1}+r_{2}},(m_{1}\cdot m_{2})h^{r_{1}+r_{2}})=\varepsilon (m_{1}\cdot m_{2}). $$
  
### Paillier    
In the [Paillier cryptosystem](https://en.wikipedia.org/wiki/Paillier_cryptosystem), if the public key is the modulus $$ m $$ and the base $$ g $$,then the encryption of a message $$ x $$ is $$\varepsilon(x) = g^{x}r^{m} \  mod \  m^{2}$$, for some random $$ r \in $$ {$$0,...,m-1$$}.  The homomorphic property is then   

  $$ \varepsilon (x_{1})\cdot \varepsilon (x_{2})= (g^{x_{1}}r_{1}^{m})(g^{x_{2}}r_{2}^{m})\  mod \ m ^{2}=g^{x_{1}+x_{2}}(r_{1}r_{2})^{m} \  mod \  m^{2}=\varepsilon (x_{1}+x_{2}) $$   

### Other partially homomorphic cryptostsyems    

- [Goldwasser–Micali cryptosystem](https://en.wikipedia.org/wiki/Goldwasser%E2%80%93Micali_cryptosystem)  
- [Benaloh cryptosystem](https://en.wikipedia.org/wiki/Benaloh_cryptosystem)
- [Okamoto–Uchiyama cryptosystem](https://en.wikipedia.org/wiki/Okamoto%E2%80%93Uchiyama_cryptosystem)  
- [Naccache–Stern cryptosystem](https://en.wikipedia.org/wiki/Naccache%E2%80%93Stern_cryptosystem)   
- [Damgård–Jurik cryptosystem](https://en.wikipedia.org/wiki/Damg%C3%A5rd%E2%80%93Jurik_cryptosystem)  
- Sander–Young–Yung encryption scheme
- Boneh–Goh–Nissim cryptosystem
- Ishai–Paskin cryptosystem
- Castagnos–Laguillaumie cryptosystem       


## 完全同态加密 (Fully Homomorphic Encryption)   

支持在密文上进行任意计算的密码系统成为完全同态加密(FHE)。这样的方案可以为任何需要的功能构建程序，这些功能都可以在加密的输入上运行，从而生成加密的结果。因为这样的程序永远不需要解密它的输入，所以它可以由任何不受信任的一方运行，而不需要暴露它的输入和内部状态。完全同态密码系统在私有外包计算中具有重要的现实意义，例如：云计算。

---
## 应用 (Applications)    

同态加密技术在分布式计算环境下的密文数据计算方面具有比较广泛的应用领域，比如云计算、多方保密计算、匿名投票等

#### 安全云计算与委托计算
同态技术在该方面的应用可以使得我们在云环境下，充分利用云服务器的计算能力，实现对明文信息的运算，而不会有损私有数据的私密性。例如医疗机构通常拥有比较弱的数据处理能力，而需要第三方来实现数据处理分析以达到更好的医疗效果或者科研水平，这样他们就需要委托有较强数据处理能力的第三方实现数据处理（云计算中心），但是医院负有保护患者隐私的义务，不能直接将数据交给第三方。在同态加密技术的支持下，医疗机构就可以将加密后的数据发送至第三方，待第三方处理完成后便可返回给医疗结构。整个数据处理过程、数据内容对第三方是完全透明的。

#### 文件存储与密文检索
用户可以将自己的数据加密后存储在一个不信任的远程服务器上，日后可以向远程服务器查询自己所需要的信息，存储与查询都使用密文数据，服务器将检索到的密文数据发回。用户可以解密得到自己需要的信息，而远程服务器却对存储和检索的信息一无所知。此种方法同样适用于搜索引擎的数据检索。

#### 安全多方计算协议设计的工具
所谓安全多方计算就是分别持有私有数据 x1,x2,…,xn的 n 个人，在分布式环境中协同计算函数f (x1,x2,…,xn) 而不泄露各方的私有数据。以同态技术加密的密文数据计算不仅可以满足安全多方计算协议设计中保护各方隐私的需要，还能避开不经意传输协议而大大提升协议效率。

#### 电子选举
基于同态加密技术设计的电子选举方案，统计方可以在不知道投票者投票内容的前提下，对投票结果进行统计，既保证了投票者的隐私安全，有能够保证投票结果的公证。
 
---
## 参考     
- [Homomorphic encryption](https://en.wikipedia.org/wiki/Homomorphic_encryption)  
- [同态加密技术总结](https://blog.csdn.net/weixin_41564401/article/details/82777335 )  
- [Homomorphic Encryption](https://brilliant.org/wiki/homomorphic-encryption/)