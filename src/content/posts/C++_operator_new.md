---
title: "C++ 重载 Operator new() delete()"
slug: "C++_operator_new"
published: 2022-05-07T20:30:00-05:00
description: ""
tags: ["C++"]
category: "笔记"
draft: false
typora-root-url: ../../../public
---

# 重载 Operator new() delete()

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="330" height="86" src="//music.163.com/outchain/player?type=2&amp;id=1342840047&amp;auto=1&amp;height=66"> </iframe>

![QQ截图20220507233819](/assets/blog_res/2022-05-07_C++_operator_new.assets/QQ%E6%88%AA%E5%9B%BE20220507233819.png)

### 重载operator new（）

重载operator new() 的时候一定要注意，有多个版本的时候每一个重载版本都要有独特的不一样的参数列表。而且参数列表的第一个参数必须是__size_t__ 

剩下的参数必须不一样。![QQ截图20220507233809](/assets/blog_res/2022-05-07_C++_operator_new.assets/QQ%E6%88%AA%E5%9B%BE20220507233809-16519848048475.png)

如上图所示。有四个版本的operator new()重载。每一个版本的第一个参数都是size_t。剩余的参数都是不一样的参数。

### 重载Operator delete()

这一步不是必须的。因为不会被delete调用。主要是释放未能完全创建成功的对象所占用的内存。也就是构造函数出现异常的时候。
