---
title: "王道操作系统笔记-进程（5）--线程的实现方式和模型"
slug: "OS8"
published: 2022-05-12T01:20:00-05:00
description: ""
tags: ["操作系统"]
category: "笔记"
draft: false
typora-root-url: ../../../public
---

# 王道操作系统笔记-进程（5）--线程的实现方式和模型



### 线程的实现方式

#### 用户级线程（ULT)

![QQ截图20220512010637](/assets/blog_res/2022-05-12-OS8.assets/QQ%E6%88%AA%E5%9B%BE20220512010637.png)



![QQ截图20220512011115](/assets/blog_res/2022-05-12-OS8.assets/QQ%E6%88%AA%E5%9B%BE20220512011115.png)

#### 内核级线程（KLT）

![QQ截图20220512011509](/assets/blog_res/2022-05-12-OS8.assets/QQ%E6%88%AA%E5%9B%BE20220512011509.png)





### 多线程模型

#### 一对一模型



![QQ截图20220512011636](/assets/blog_res/2022-05-12-OS8.assets/QQ%E6%88%AA%E5%9B%BE20220512011636.png)





#### 多对一模型





![QQ截图20220512011745](/assets/blog_res/2022-05-12-OS8.assets/QQ%E6%88%AA%E5%9B%BE20220512011745.png)



#### 多对多模型



![QQ截图20220512012119](/assets/blog_res/2022-05-12-OS8.assets/QQ%E6%88%AA%E5%9B%BE20220512012119.png)



### 总结

![QQ截图20220512012129](/assets/blog_res/2022-05-12-OS8.assets/QQ%E6%88%AA%E5%9B%BE20220512012129.png)
