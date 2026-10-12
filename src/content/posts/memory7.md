---
title: "C++内存管理- 17"
slug: "memory7"
published: 2022-06-06T09:50:00-05:00
description: ""
tags: ["内存管理"]
category: "笔记"
draft: false
typora-root-url: ../../../public
---

# C++内存管理 - 17 

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="330" height="86" src="//music.163.com/outchain/player?type=2&amp;id=410446173&amp;auto=1&amp;height=66"> </iframe>

# 此笔记需要等待更新和确认。





## std::alloc 源码剖析

视频14~27没什么难度。略

## 源码剖析8

![QQ截图20220606193011](/assets/blog_res/2022-06-04-memory7.assets/QQ%E6%88%AA%E5%9B%BE20220606193011.png)

有几个要点需要注意

248行的`chunk`已经是`char*`*类型了。所以260行**直接**将其`+n`后转为`obj*`类型。259~261行的要点是，首先261行的for循环是从1开始的。因为切割出来后将第一块直接返回回去。不需要再放回去切割。所以259行直接将分配过来的内存转为`obj*`后返回。然后260行直接进行指针移动到第一个区块末尾。所以现在的空闲链表头是从`*my_free_list`开始的。

