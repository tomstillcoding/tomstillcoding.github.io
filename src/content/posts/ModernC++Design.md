---
title: "Modern C++ Design 笔记"
slug: "ModernC++Design"
published: 2023-03-03T01:55:00-05:00
description: ""
tags: ["C++"]
category: "笔记"
draft: false
typora-root-url: ../../../public
---

这本书有点儿老，好多和模板相关的都是脱裤子放屁

# 第一章 策略类

整个这一章讲的都是策略类的使用。这一部分分散在模板笔记当中。包括设计模式目前没有整理，后续会整理。

核心要点就是让类可以定制化。当把一个类拆分为多个策略的时候，首先要把设计的功能模块抽离。同时要注意寻找正交的策略，也就是彼此之间无交互，可以独立更改的策略。



# 第二章 技术

## 2.5 型别对型别的映射 （就是到底用不用SFINAE）

其实就是使用类似`enable_if`来激活SFINAE。

假设我们需要对`myobj`对象进行特殊处理，如果使用嵌入式`enable_if`会是这样：

```c++
struct myobj{

};
template<typename T, typename U, typename = typename enable_if<is_same<U, myobj>::value>::type>
void create(const T& obj, const U& arg){
    std::puts(__PRETTY_FUNCTION__);
    cout <<"myobj special" << endl;
}
template<typename T, typename U, typename = typename enable_if<!is_same<U, myobj>::value>::type, typename = int>
void create(const T& obj, const U& arg){
    std::puts(__PRETTY_FUNCTION__);
    cout <<"normal" << endl;
}
int main(){
    create(2,3);
    create(2,myobj{});
}
```

还是老规矩，分析下过程。

针对第一个，模板参数`T`和`U`被推导为`int`和`int`。然后发现`int`和`myobj`不同，所以第一个模板被SFINAE掉（因为为`false`后`enable_if`没有`type`定义）。然后看第二个模板，第二个模板发现可以，所以选择第二个模板。

针对第二个，一个道理。

我们发现使用起来比较麻烦，如果我们能自己实现一个类似的呢？

```c++
struct myobj{
};

template<typename T>
struct typewrapper{
    using objtype = T;
};

template<typename T, typename U>
void anothercreate(const T& obj, typewrapper<U>){
    std::puts(__PRETTY_FUNCTION__);
    //void anothercreate(const T&, typewrapper<U>) [with T = int; U = int]
    cout <<"normal" << endl;
}
template<typename T>
void anothercreate(const T& obj, typewrapper<myobj>){
    std::puts(__PRETTY_FUNCTION__);
    //void anothercreate(const T&, typewrapper<myobj>) [with T = int]
    cout <<"myobj special" << endl;
}
int main(){
    anothercreate(2,typewrapper<int>{});
    anothercreate(2,typewrapper<myobj>{});
}
```

老规矩，分析一下。

- 这里没用到SFINAE。只是单纯的重载匹配。我们说过了SFINAE的三个要素：推导语境，失败和其他可行选项。

第一个调用，模板参数`T`和`U`被推导为`int` 和`int`。匹配至第一个。**因为第二个明显不符合类型要求。压根不存在SFINAE的情况，因为第二个重载模板从未被考虑过。因为第二个重载模板的第二个函数形参不在推导语境内。不在推导语境内，也没有错误发生，就不可能是SFINAE**

第二个调用，由于第二个重载模板比第一个更特化，所以调用第二个。针对第一个重载模板，此时虽然有推导语境，但是没有错误发生。所以也不存在SFINAE。
