---
title: "C++ STL - 2 - 迭代器设计思路。萃取。"
slug: "STL2"
published: 2022-06-11T15:50:00-05:00
description: ""
tags: ["STL"]
category: "笔记"
draft: false
typora-root-url: ../../../public
---

# C++ STL - 2 - 迭代器设计思路。萃取。

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="330" height="86" src="//music.163.com/outchain/player?type=2&amp;id=410446173&amp;auto=1&amp;height=66"> </iframe>



# 什么是萃取？

**三个字：中间层**

我们这里先以侯捷老师的`iterator_traits`做为例子。

我们知道，`iterator`迭代器本身有五个属性。我们也知道迭代器是一个`class`。所以也就是迭代器类有五个`typedef`。分别是：

```c++
namespace std
{
    template <typename T>
    struct iterator_traits
    {
        typedef typename T::iterator_category   iterator_category;  //迭代器分类，比如正向迭代器，双向迭代器
        typedef typename T::value_type          value_type;  //迭代器指向的对应的数据类型，比如int string 等等
        typedef typename T::difference_type     difference_type; //用来表示两个迭代器之间的距离，因此也可以用来表示一个容器的最大容量
        typedef typename T::pointer             pointer; 
        typedef typename T::reference           reference; 
    };
}
```

算法组想通过迭代器访问容器数据。假设我们的算法组就一定要问你，迭代器指向的数据的类型是什么，我们可以轻易地像这样获取：

```c++
list<int>::iterator::value_type
```

它会回答你是一个`int`。

这样非常好。但是有一个问题。迭代器是一个泛化的指针。反过来说，指针就是一个退化的迭代器。

我们发现在迭代器萃取类内部有一大堆的`typedef`。我们正是通过这个来告诉外面你这个迭代器的`value_type`是个什么玩意。

举个小例子：

```c++
class test{
    public:
    test(){}
    typedef int inputtype;
};

int main(){
    test::inputtype x; //这句话等于告诉你 test类下面的inputtype这个东西是int 
}
```

**这里不需要加`typename`的原因是这不是模板类。类型是已经确定好的。后文会讲到。**

但是如果我们给算法传入的不是迭代器，而是一个指针怎么办？指针不是类，指针不是结构体，指针无法给自己弄一堆`typedef`。也就是你问一个指针，问他你的`value_type`是什么，他懵逼了，说我没有这玩意啊？怎么办

这就是萃取的意义。我们可以间接地获取类型。也就是利用模板的特化包装一层，让算法统一去问萃取层，这个东西的`value_type`是个什么玩意。

![QQ截图20220613172835](/assets/blog_res/2022-06-12-STL2.assets/QQ%E6%88%AA%E5%9B%BE20220613172835.png)

在图里，我们可以看见，如果传入的是迭代器，我们可以走到`1`里面，直接问迭代器的`value_type`是什么。

如果传入的是一个指针，我们可以走到`2`里面。人为地设定一个`value_type`。也就是把`T`提取出来。告诉算法组这个指向`T`类型的指针的`value_type`是`T`类型

举个例子：

```c++
template<typename T>
class pclass{
public:
    typedef T valuetype;
};

template<typename T>
class pclass<T*>{
public:
    typedef T valuetype;
};

int main(){
    pclass<int>::valuetype x; //x的类型是int
    pclass<int*>::valuetype x; //x的类型还是int。 可以看成T* = int*, 拿掉*就是 T = int 所以还是int。
    return 0;
}

```



整体代码：

```c++

//基本类

class FLOATtype{
public:
    float _val;
    FLOATtype(){}
    FLOATtype(float x):_val(x){};
    float retval (float& num){
        cout << _val*num << endl;
        return _val*num;
    }
    //我们假设FLOATtype没有自己的获取输入输出类型的部分
};

class INTtype{
public:
    int _val;
    INTtype(){}
    INTtype(int x):_val(x){};
    int retval (int& num){
        cout << _val*num << endl;
        return _val*num;
    }
    //我们假设INTtype没有自己的获取输入输出类型的部分
};


class fucktype{
public:
    int _val;
    fucktype(){}
    fucktype(int x):_val(x){};
    int retval (int& num){
        cout << _val*num << endl;
        return _val*num;
    }
    typedef fucktype rettype; //我们假设fucktype有自己的获取输入输出类型的部分。所以我们加了typedef。
    typedef int inputtype;
};




//萃取 模板特化
/*
这里的例子看起来非常脱裤子放屁。但是对于迭代器萃取来讲完全不是。
我们知道迭代器是泛化的指针，也就是说指针是退化的迭代器。
我们知道迭代器是一个class 所以他们有能力定义自己的associate type。
举个例子。我们知道迭代器类里面有自己的value_type。所以我们可以直接问 list<int>::iterator你的valuetype是什么，像这样 list<int>::iterator::value_type。它会回答你它是int。
但是如果我们给算法传入的不是迭代器，而是一个指针怎么办？指针不是类，指针不是结构体，指针无法给自己弄一堆typedef。怎么办
这就是萃取的意义。我们可以间接问。就是放入萃取机。
*/
template <typename T>
class testTraits{ //默认版本。直接问对应类的输入输出类型。如果有的话
    public:
        typedef typename T::rettype rettype; //注意这里一定要加typename告诉编译器 T::rettype是一个类型。
        typedef typename T::inputtype inputtype; //注意这里一定要加typename告诉编译器 T::rettype是一个类型。告诉编译器T类下的inputtype代表的不是变量，代表的是类型。
};

template<> //模板全特化。我们假设知道inttype不是类，不能放typename 就好比指针。所以我们在这里给他包一层，显式告知对应的输入输出类型是什么。让有人问的时候转到这里告诉他对应类型
class testTraits<INTtype>{
    public:
        typedef int rettype;
        typedef int inputtype;
};

template<>
class testTraits<FLOATtype>{ //和上面一样。
    public:
        typedef float rettype;
        typedef float inputtype;
};

//使用

/*
在这个例子里面。我们对照着迭代器萃取器的例子做一个总结。
假如我们有几个类是有inputtype的。到时候直接问那个类就可以。但是如果是一个普通变量或者指针，没有inputtype的怎么办？
就好比我们的fucktype。我们在fucktype类里面有自己的typedef。所以可以直接问。
但是INTtype和FLOATtype没有，不能直接问。我们就通过模板特化来加一个中间层。所以萃取其实就是中间层。
*/

template<typename T>
class test{
    public:
    //注意这里testTraits<T>::rettype是做为函数的返回类型。所以必须要加typename。不然编译器会认为rettype是一个在testTraits里的成员变量。但是因为是把testTraits类里的rettype成员变量对应的typedef的东西当做类型来看待。所以需要加typename
    typename testTraits<T>::rettype retvall(T& obj, typename testTraits<T>::inputtype input){
        return obj.retval(input);
    }
};

int main(){
    INTtype intnum(5);
    int INTarg = 5;
    test<INTtype> test1;
    test1.retvall(intnum, INTarg);

    FLOATtype floatnum(5.5f);
    float FLOATarg = 8.8f;
    test<FLOATtype> test2;
    test2.retvall(floatnum, FLOATarg);

    fucktype fucknum(10);
    int fuckarg = 5;
    test<fucktype> test3;
    test3.retvall(fucknum, fuckarg);
}

```



## 类作用域

在类外部访问类中的名称时，可以使用类作用域操作符，形如`MyClass::name`的调用通常存在三种：静态数据成员、静态成员函数和嵌套类型：

```c++
struct MyClass {
    static int A;
    static int B();
    typedef int C; //这里就是typedef 也就是嵌套类型
}
```

`MyClass::A`, `MyClass::B`, `MyClass::C`分别对应着上面三种。

## `typedef` 和作用域解析运算符`::` 和 嵌套类

我们很难把class和namespace联系起来，但是这两个在抽象层次上其实是一个概念。

作用域解析运算符::的作用就是制定某一个范围。但是一旦用在了嵌套类或者类内的typedef，我们就很难理解这层含义。

我们都知道**直接访问类静态成员必须使用作用域解析运算符`::`**

但是我们如果要通过作用域解析运算符访问非静态成员，可以吗？当然可以。只不过需要通过对象访问。

举个例子：

```c++
class test{
    public:
    class testinner{ //嵌套类
        public:
        int _val;
        testinner(){}
        testinner(int x):_val(x){}
    };
    test(){}
    typedef int testdef;


    int s;
};

int main()
{
    test::testinner tt1 = test::testinner(5); //OK
    test::testinner tt2; //OK 访问嵌套类
    test::testdef tt3 = 5; //OK 访问typedef。
    test::s = 5; //不行。直接访问的成员必须是静态成员。
    test t;
    t.test::s = 5; //OK 通过对象访问，但是还是脱裤子放屁加了作用域解析运算符。

    return 0;
}
```

这里我们可以理解为我们需要访问的`typede`f和嵌套类在`test`类的命名空间下。我们必须要告知编译器这东西在哪，所以需要通过作用域解析运算符去访问。

至于`typedef`和嵌套类是否是一个类的成员，我没有查到确切的说法。如果说他们不是成员吧，但是有成员的属性。要是说是成员吧，我们也可以直接访问。但是也有人说嵌套类的`static`是隐式的。也有人把嵌套类当做一个`namespace` 来看待。所以我的理解是**不要把嵌套类和`typedef`看做类成员。假设他们可以直接调用即可。**

**如果嵌套类没有在外部类中实例化，则实例化外部类的时候不会实例化嵌套类内容。**



## 最后说一下必须显式使用`typename`的情况。

![QQ截图20220613134505](/assets/blog_res/2022-06-12-STL2.assets/QQ%E6%88%AA%E5%9B%BE20220613134505-16551788472405.png)

来几个例子：

```c++
class test{
    public:
        struct obj{
            int _sb;
        };
        obj s;
        int _val;
        test(){}
        test(int x):_val(x){}
        test(int x, int y){
            _val = x;
            s._sb = y;
        }
};
template<typename T>
void func(){
    test t(5,8);
    typename T::obj* ptr = &t.s;
    //这里我们的意思是有一个指针ptr指向了T类里面的obj类型的对象。翻译成人话也就是ptr是一个T::obj类型的指针。但是如果有一个T类里面的obj是一个变量，如static int obj = 8
    //那么这就变成了变量乘法。会有歧义。所以使用typedef显式告知编译器 T::obj不是一个变量，而是一个类型。
    cout << ptr->_sb << endl;
} 
```



可能还不够？再来：

```c++
typedef iterator_traits<T>::value_type value_type_anothername; 
//这句话的意思是value_type_anothername是在模板类iterator_traits中的 变量 value_type的别名。

//所以如果有
value_type_anothername name = "foward_iterator";
//这样是不行的。因为value_type_anothername是一个变量不是类型。
//所以我们需要加typedef告知编译器这个是类型

typedef typename iterator_traits<T>::value_type value_type_anothername; 
//这句话的意思是value_type_anothername是iterator_traits<T>::value_type这个 类型 的别名。

//所以这样可以有
value_type_anothername name = "foward_iterator";
//因为value_type_anothername 是个类型。就好比int string这种。

```



还不够？再来：

这是我们前文的例子。但是为什么这里不需要加typedef呢？

```c++
class test{
    public:
    typedef int inputtype;
};

int main(){
    test::inputtype x = 4; //这句话等于告诉你 test类下面的inputtype这个东西是int 
}

```



先送上大佬文章一篇：https://feihu.me/blog/2014/the-origin-and-usage-of-typename/

由于`test`已经是一个完整的定义，因此编译期它的类型就可以确定下来，也就是说`test::inputtype`这些名称对于编译器来说也是已知的。

可是，如果是像`T::inputtype`这样呢？`T`是模板中的类型参数，它只有等到模板实例化时才会知道是哪种类型，更不用说内部的`inputtype`。通过前面类作用域一节的介绍，我们可以知道，`T::inputtype`实际上可以是以下三种中的任何一种类型：

- 静态数据成员
- 静态成员函数
- 嵌套类型





- `typename`的作用，简单理解就是强制告诉编译器 `namespace::objname`这个东西是一个类型名而不是变量名。

**所以在模板类中，如果想要告知编译器一个使用了`::`作用域解析运算符的东西是类型，而不是变量，就需要加`typename`**

- 如果直接把这个东西当做一个类型来进行变量的声明，那就不需要搭配`typedef`

- 如果需要把这个东西当做一个类型来赋予一个别名，那就需要使用`typedef`

所以，像这样就必须要加：

```c++
class test{
    public:
    test(){}
    typedef int inputtype;
};


template<typename T>
class test1{
    public:
    test1(){};
    typedef typename T::inputtype inputtype; //注意这里，T::inputtype是个类型。比如test::inputtype 就是 int类型
};

```



## 限定名、非限定名

限定名(qualified name)，故名思义，是限定了命名空间的名称。看下面这段代码，`cout`和`endl`就是限定名：

```c++
#include <iostream>

int main()  {
    std::cout << "Hello world!" << std::endl;
}
```

`cout`和`endl`前面都有`std::`，它限定了`std`这个命名空间，因此称其为限定名。

如果在上面这段代码中，前面用`using std::cout;`或者`using namespace std;`，然后使用时只用`cout`和`endl`，它们的前面不再有空间限定`std::`，所以此时的`cout`和`endl`就叫做非限定名(unqualified name)。



## 依赖名、非依赖名

依赖名(dependent name)是指依赖于模板参数的名称，而非依赖名(non-dependent name)则相反，指不依赖于模板参数的名称。看下面这段代码：

```c++
template <class T>
class MyClass {
    int i;
    vector<int> vi;
    vector<int>::iterator vitr;

    T t;
    vector<T> vt;
    vector<T>::iterator viter;
};
```

因为是内置类型，所以类中前三个定义的类型在声明这个模板类时就已知。然而对于接下来的三行定义，只有在模板实例化时才能知道它们的类型，因为它们都依赖于模板参数`T`。因此，`T`, `vector<T>`和`vector<T>::iterator`称为依赖名。前三个定义叫做非依赖名。

更为复杂一点，如果用了`typedef T U; U u;`，虽然`T`没再出现，但是`U`仍然是依赖名。由此可见，不管是直接还是间接，只要依赖于模板参数，该名称就是依赖名。
