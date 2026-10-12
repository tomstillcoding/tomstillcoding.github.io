---
title: "C++内存管理- 9~11"
slug: "memory3"
published: 2022-05-31T04:50:00-05:00
description: ""
tags: ["内存管理"]
category: "笔记"
draft: false
typora-root-url: ../../../public
---

# C++内存管理 - 9~11

# 此笔记需要等待更新和确认。

## 重载 operator new， operator delete

![微信图片_20220531035654](/assets/blog_res/2022-05-31-memory3.assets/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20220531035654.png)

**注意红色的是较为常见的重载成员函数中的operator new。绿色的是不常见的重载全局函数的operator new**



### 重载全局operator new， operator delete

![微信图片_20220531040706](/assets/blog_res/2022-05-31-memory3.assets/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20220531040706.png)

- 一定要注意，全局的`::operator new`下面是`malloc`。全局的`::operator delete`下面是`free`。所以全局`::operator new`不构造对象，全局`::operator delete`也不析构对象。






## 注意事项

重载`operator new`的时候一定要注意 **它的返回类型必须是`void*`。**

**请注意，任何指针都可以赋值给`void`指针。不需要转换。只获得变量/对象地址而不获得大小。 如以下代码：**

```c++
void* test(int* a){
    *a = 4;
    return a;
}
int main(){
    int s = 1;
    int* b = &s;
    test(b);
    cout << s << endl;
}
//输出结果为4
```

![QQ截图20220531044057](/assets/blog_res/2022-05-31-memory3.assets/QQ%E6%88%AA%E5%9B%BE20220531044057-16539902288687.png)





### 重载局部（某个类内）operator new， operator delete

![QQ截图20220531041338](/assets/blog_res/2022-05-31-memory3.assets/QQ%E6%88%AA%E5%9B%BE20220531041338.png)



## 注意重载局部operator new， operator delete必须要设置为静态函数

**注意重载局部operator new， operator delete必须要设置为静态函数。因为为对象分配内存的时候是正在创建对象，而没有对象无法调用类非静态成员。所以为了用类的函数进行内存分配，必须要把new和delete设置为类的静态函数这样可以在没有创建对象之前就调用。**

**任何类内的内存分配函数必须要声明为静态函数 static **

**静态成员函数即使在类对象不存在的情况下也能被调用，静态函数只要使用类名加范围解析运算符 :: 就可以访问。new对象时，对象还没有，设置成类非静态成员函数是没意思的，隐藏的this指针无从下手，所以要声明为static函数。**

- 此时，如果想使用全局的`operator new`则需要加作用域访问运算符`:`指定全局作用域

- 这里多提一嘴。看一下这个的[内存池实现](https://blog.csdn.net/K346K346/article/details/49538975) 和 [这个](https://blog.csdn.net/baidu_41388533/article/details/105648119)





# more effective c++ 条款8 了解new operator 和 operator new 的区别

**注意，重载的类内operator new 和 delete是在我们使用`new` （这个`new`叫做 new operator）的时候，编译器在`new`的底下会调用我们重载的operator new。我们本身如果直接调用`operator new`不会调用构造函数，因为我们此时不能手动调用对象初始化所必须的构造函数。**

**`new` operator会执行底层的`operator new`，然后如memory1中提到的帮助我们转型和构造。**

**`delete` operator会执行底层的`operator delete`，然后如memory1中提到的帮助我们析构。**

- **所以，如果想分配内存并构造对象，则依旧使用`new`。如果只想分配内存，不构造对象，则可以手动调用`operator new`**

- **所以，直接调动全局的`::operator new`不会调用构造函数。因为它的下面只是`malloc`。直接调用全局的`::operator delete`不会调用析构函数。因为它的下面只是`free`。**


### **顺便一提，根据标准，针对单**对象或数组的分配函数（也就是局部`operator new` 和 `operator new[]`）对这些函数不需要使用关键词 `static`。不管是否显式使用（声明分配函数为静态），分配函数都是静态成员函数。

![QQ截图20221217071624](/assets/blog_res/2022-05-31-memory3.assets/QQ%E6%88%AA%E5%9B%BE20221217071624.png)


### 重载 operator new() delete()。这个地方指的是重载placement new

重载operator new() 的时候一定要注意，有多个版本的时候每一个重载版本都要有**独特的不一样的参数列表**。而且参数列表的第一个参数必须是`size_t` 剩下的参数必须不一样。 而且 **它的返回类型必须是void***，并不必须重载operator delete()。**查看discord频道笔记。关键字new()**

**记住笔记二中说的，placement new 是operator new的一种特殊形式**

![QQ截图20220531042442](/assets/blog_res/2022-05-31-memory3.assets/QQ%E6%88%AA%E5%9B%BE20220531042442.png)

