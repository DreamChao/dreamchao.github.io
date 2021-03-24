---
layout: post
title: IEEE Magazine 中 reference 的格式
categories: Research method
description: IEEE Magazine 中 reference 的格式修改
keywords: Research method, IEEE Magazine 
comments: false
---  

今天在修改 IEEE Magazine 中的 reference 格式中，遇到了一些困难。之前以为 reference 的格式都是一样的，但是当老板跟我提了这个问题的时候，我才意识到是自己知道的少了。于是回来就参考了别人 Magazine 中的 reference。刚开始一点头绪也没有，想着去看看 [IEEE Communications Magazine](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=35) 的主页，想着能不能找到一点参考。于是在about journal 中，看到 [For submission guidelines, please see](https://www.comsoc.org/publications/magazines/ieee-communications-magazine/author-guidelines/manuscript-submission)。点了进去，找到了[The IEEE Communications Society Publications Department Style Guide](https://www.comsoc.org/media/801/download),这是关于样式的手册，闲来无事可以看一看。找到 reference 那一节，看了一下大概的格式，于是就去 Google 请教前人。 搜"IEEE Magazine Reference", 出来一大堆，也看不出个啥。
我废话真多，上干货吧！
#### Journal 名称的缩写 
参考[LaTeX写文章过程中碰到的小问题总结](https://www.jianshu.com/p/16dfdc26a7c7)   

用JabRef, 将要处理的 .bib文件导入"library".菜单栏的“Options->Manage Journal Abbreviations”里面可以看到缩写方式库，里面如果有不够全的可以自己手动增加，基本上IEEE都是有的。然后，全选“Library”中所有的文献 -> 点击菜单栏“Quality-> Abbreviate Journal Names->default”即可。最后可以再“File->save library as”把改好的.bib文件导出来。
当然这个只能批量修改JabRef缩写库里有的，没有的期刊文章等要自己查找对应的规范简写之后自己再修改一下即可。具体简写可以查看这个ISO4 Abbreviation的网站：[Journal-Abbreviation-System](https://academic-accelerator.com/Journal-Abbreviation/System)  —— 为了省时间，我就直接copy了。

#### Conference 名称的缩写 
参考 [IEEE期刊参考文献中的会议缩写](https://blog.csdn.net/qq_35154082/article/details/103259213)  

[EI](https://www.engineeringvillage.com/search/quick.url)


#### 作者的省略
可以看到，格式中要求 一个作者 et al.
 所以我们就简单粗暴，只保留第一个作者，后面的全部用 and others 代替。比如 author = {Venkatesan, Suchitra and others}

 