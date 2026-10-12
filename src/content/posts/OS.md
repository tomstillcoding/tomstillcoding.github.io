---
title: "王道操作系统笔记-操作系统的运行机制与体系结构"
slug: "OS"
published: 2022-05-02T16:50:00-05:00
description: ""
tags: ["操作系统"]
category: "笔记"
draft: false
typora-root-url: ../../../public
---

# 王道操作系统笔记-操作系统的运行机制与体系结构

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="330" height="86" src="//music.163.com/outchain/player?type=2&amp;id=32574583&amp;auto=1&amp;height=66"> </iframe>

## 操作系统特征：并发，共享，虚拟，异步。

其中，共享分为__互斥共享方式(摄像头设备的共享使用)__ 和 __同时共享方式(硬盘资源的共享使用)__

虚拟分为__空分复用(虚拟储存技术)__ 和 __时分复用(虚拟处理器技术)__

## CPU指令分为特权指令和非特权指令

特权指令如内存清零指令

非特权指令如普通运算指令

## 处理器状态分为用户态和核心态

处理器处于用户态的时候 CPU只能执行非特权指令

处理器处于核心态的时候 CPU可以执行非特权指令和特权指令

## 所以程序内核程序和应用程序

内核程序可以执行特权指令和非特权指令。所以内核程序运行在核心态

应用程序仅可以执行非特权指令。所以引用程序运行在用户态

![QQ截图20220502185501](/assets/blog_res/2022-05-02-OS.assets/QQ%E6%88%AA%E5%9B%BE20220502185501.png)

![QQ截图20220502185640](/assets/blog_res/2022-05-02-OS.assets/QQ%E6%88%AA%E5%9B%BE20220502185640.png)

![QQ截图20220502185958](/assets/blog_res/2022-05-02-OS.assets/QQ%E6%88%AA%E5%9B%BE20220502185958.png)

