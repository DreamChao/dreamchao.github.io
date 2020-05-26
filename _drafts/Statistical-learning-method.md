---
layout: post
title: Some knowledge point of the Statistical Learning Method
categories: AI, Mathematics
description: something about the Statistical Learning Method
keywords: artificial intellegence, statistical learning method
---    


### Hoeffding不等式与泛化误差上界

#### Hoeffding 不等式   
##### 简述    
 在概率论中，霍夫丁不等式给出了随机变量的和与其期望值偏差的概率上限，是由 Wassily Hoeffding 于1963年提出并证明。 霍夫丁不等式是一个Azuma-Hoeffding不等式的特例，并且他比Sergei Bernstein于1923年证明的Bernstein不等式更加具有广泛性。这几个不等式都是McDiarmid’s不等式的特例。这样，我们基本就把这几个不等式的关系理清楚了。


##### 伯努利随机变量的特例    
 霍夫丁不等式经常被应用于一些独立分布的伯努利随机变量的重要特例中，所以这个不等式在计算机科学以及组合数学中很常见。在抛硬币时，假设正面向上的概率为 p ,则背面向上的概率为 1-p， 投掷 n 次之后，正面朝上次数的期望值为 np。 我们进一步可以知道，正面朝上的次数不超过 k 次的概率能够被下面的表达式完全确定： 
  ![1](/images/posts/statisticalLearning/1.webp)       
 其中，H(n)是n次投掷中，正面朝上的次数。   
 对某一ε>0,有k=(p−ε)n，上述不等式确定的霍夫丁上界将会按照指数级变化:   
 ![2](/images/posts/statisticalLearning/2.webp)     
 相似的,对某一ε>0,当k=(p+ε)n，霍夫丁不等式的概率边界同样可以确定为：    
 ![3](/images/posts/statisticalLearning/3.webp)      
  由上面两个式子，我们可以得到：       
 ![4](/images/posts/statisticalLearning/4.webp)     
现在令：   
 ![5](/images/posts/statisticalLearning/5.webp)    
 就可以得到：   
 ![6](/images/posts/statisticalLearning/6.webp)   
   那么上式即为霍夫丁不等式的伯努利随机变量特例。    

##### 一般形式    
现在令X1，X2，…，Xn为[0,1]的独立随机变量，即0<=Xi<=1。我们定义这些变量的经验均值为：    
![7](/images/posts/statisticalLearning/7.webp)  
在1963年霍夫丁提出该不等式，其中霍夫丁定理一中的一个不等式为：   
![8](/images/posts/statisticalLearning/8.webp) 

当知道Xi严格的边界范围ai，bi（即Xi属于[ai,bi]）时，霍夫丁定理二更加广泛：
![9](/images/posts/statisticalLearning/9.webp)    

这个不等式也可以写成和的形式：   
![10](/images/posts/statisticalLearning/10.png)     
其中：  
![11](/images/posts/statisticalLearning/11.png)      

需要注意的是对于Xi为不放回的抽样该等式依然成立；在这样的例子中这些随机变量不在是独立的了。这种情形的证明可以看Hoeffding在1963年发表的论文。如果需要一个在无放回抽样的例子中更好的边界，可以查看Serfling在1974年发表的论文。

##### 证明   
在这里，给出霍夫丁不等式的证明，该证明使用了霍夫丁引理。   

