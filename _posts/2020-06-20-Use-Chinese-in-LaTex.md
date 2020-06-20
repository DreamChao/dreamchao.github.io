---
layout: post
title: How to Use Chinese in LaTex
categories: Solution
description: Some tips of using LaTex
keywords: LaTex, Solution
---   

最近在用 LaTex 写东西，但是写中文不是编译成乱码，就是编译错误，于是上网上查了一下如何配置中文环境。

#### 使用 CTEX 的 UTF8 选项


``` Tex
\documentclass{article} 
\usepackage[UTF8]{ctex} 
\begin{document}
   中文，English
\end{document}

```    
或者直接使用 ctexart   
``` Tex
\documentclass[UTF8]{ctexart}
\begin{document}
   中文，English
\end{document}
``` 
##### 参考
- [LaTex支持中文的三种方式](https://blog.csdn.net/z_feng12489/article/details/90449495)   
- [texstudio配置中文环境](https://blog.csdn.net/qizaijie/article/details/79564079)

