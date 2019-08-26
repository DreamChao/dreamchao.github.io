---
layout: post
title: Microsoft Store 安装 OneNote 报错 0x800706D9
categories: Windows
description: 微软商店完美解决安装OneNote 报错 0x800706D9
keywords: windows, solution
comments: false
---  

遇到这个问题有好几次了，OneNote 打不开，然后只能将它卸载了重装，但是在重装的时候会报错，其中的一个错误就是 **0x800706D9**。今天在帖子中找到了最佳的解决方案，如下。

### Solution   
- 使用快捷键 “WIN+R” 打开 “运行”，并输入 “services.msc”。点击确认打开“服务”。     

  ![services](/images/posts/windows/services.png)     

  ![services1](/images/posts/windows/services1.png)   

- 找到 **Print Spooler**，将这个服务设置为自启动。     

  ![Print_Spooler](/images/posts/windows/Print_Spooler.png)  
  
- 然后再重新安装 OneNote， 问题解决。   


### Reference   
  [【完美解决】微软商店安装OneNote 报错 0x800706D9](https://blog.csdn.net/weixin_40040107/article/details/91053769)