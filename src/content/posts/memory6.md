---
title: "C++内存管理- 16"
slug: "memory6"
published: 2022-06-04T09:50:00-05:00
description: ""
tags: ["内存管理"]
category: "笔记"
draft: false
typora-root-url: ../../../public
---

# C++内存管理 - 16

# 此笔记需要等待更新和确认。





## New Handler

当使用`new`申请内存失败时会抛出`"bad alloc"`异常，此前会调用一个由`std::set_new_handler()`指定的错误处理函数（"new-handler"）。

如下是一个最简单的形式

```c++
void outOfMem(){
    std::cout<<"Unable to alloc memory";
    std::abort();
}
int main(){
    std::set_new_handler(outOfMem);
    int *p = new int[100000000L];
}
```

当`new`申请不到足够的内存时，它会**不断地**调用`outOfMem`。因此一个良好设计的系统中`outOfMem`函数应该做如下几件事情之一：

- 使更多内存可用；

- 安装一个新的"new-handler"；

- 卸载当前"new-handler"，传递`null`给`set_new_handler`即可；

- 抛出`bad_alloc`（或它的子类）异常；

- 不返回，可以`abort`或者`exit`。

关于`abort`, `exit`, `terminate`的区别：`abort`会设置程序非正常退出，`exit`会设置程序正常退出，当存在未处理异常时C++会调用`terminate`， 它会回调由`std::set_terminate`设置的处理函数，默认会调用`abort`。

![QQ截图20220604101541](/assets/blog_res/2022-06-04-memory6.assets/QQ%E6%88%AA%E5%9B%BE20220604101541.png)
