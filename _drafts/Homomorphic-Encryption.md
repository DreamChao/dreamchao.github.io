---
layout: post
title: Homomorphic Encryption
categories: cryptography
description: 密码学的一些知识
keywords: cryptography
comments: false
---  
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>   
> **Homomorphic encryption** is a form of encryption that allows computation on ciphertexts, generating an encrypted result which, when decrypted, matches the result of the operations as if they had been performed on the plaintext.          
                   --Cite from [wikipedia](https://en.wikipedia.org/wiki/Homomorphic_encryption)   

--- 
## 基本概念      
同态加密是一种支持在密文上进行计算的加密方式，对在密文上计算得到的结果进行解密后得到的内容与直接在明文上计算得到的结果相同。    

传统的加密就是将消息或者原始信息用一种方式打乱，得到密文，然后将其保存或者传递给接收者，接收者接收到密文后，用另一种方式对密文进行解密并读取它。这样在一定程度上增加了数据的安全性，因为只有授权的用户才能够读取消息。当然，这种加密方式只有在数据被加密时能保证其安全性，加密的数据只能进行存储或者共享，在云计算飞速发展的今天，这无疑是一个限制。我们知道，云计算为用户提供了许多服务，包括对大数据的存储和计算。然而，要利用云计算，用户就必须信任云服务提供商并与之共享数据。确保数据的隐私性的一种方法就是在上传到云端之前对数据进行加密。但是当用户希望对数据进行计算的时候，就必须下载数据并对数据进行解密，这降低了云服务的优势。所以，在不受信任的公共云上提供安全云计算的一个解决方案就是使用同态加密。   


    






---
## 参考     
- [Homomorphic encryption](https://en.wikipedia.org/wiki/Homomorphic_encryption)