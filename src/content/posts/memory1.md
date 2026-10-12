---
title: "C++内存管理- 1~6"
slug: "memory1"
published: 2022-05-29T19:55:00-05:00
description: ""
tags: ["内存管理"]
category: "笔记"
draft: false
typora-root-url: ../../../public
---

# C++内存管理 - 1~6 

# 此笔记需要等待更新和确认。最好搭配深度探索6.1一起看



![QQ截图20220529201640](/assets/blog_res/2022-05-29-memory1.assets/QQ%E6%88%AA%E5%9B%BE20220529201640.png)



![QQ截图20220529201640](/assets/blog_res/2022-05-29-memory1.assets/QQ%E6%88%AA%E5%9B%BE20220529201640-16538734497572.png)

![QQ截图20220529201724](/assets/blog_res/2022-05-29-memory1.assets/QQ%E6%88%AA%E5%9B%BE20220529201724.png)

### 我们由上图可以看出malloc和free是比new delete更底层的东西。malloc和free属于c函数，而new和delete属于c++表达式。



## 内存分配方式：

![QQ截图20220529202032](/assets/blog_res/2022-05-29-memory1.assets/QQ%E6%88%AA%E5%9B%BE20220529202032-16538736739556.png)

1. 使用`malloc`分配特定大小的内存。使用`malloc`会返回一个未定类型的指针。

   **类型决定了指向的内存空间的大小. 编译器依靠指针类型来决定到底读取到哪一个字节。因为你只能确定开始地址，如果不给指针类型，编译器不知道你要读取1个字节还是100个字节为止**

2. 使用`new`分配特定大小的内存。使用`new`需要指定其类型。一般后接class名称指定类型。返回一个该类型的指针。

​	**注意： 如代码`A *a = new A()` ，此处不仅仅分配了内存，而且调用了构造函数**

![微信图片_20220530014049](/assets/blog_res/2022-05-29-memory1.assets/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20220530014049.png)



3. 使用`::operator new `分配特定大小的内存。`::operator new`其实就是包装过的`malloc`。一样返回一个未定类型指针。

​	**记住。free和delete释放的是指针指向的地址，而不是指针本身。指针本身依旧存在。因此，指针会指向释放过的地址，可能引发错误。所以记得要将指针本身置空。**

在如如下代码中

```c++
A *a = new A();
delete a;
```

`delete` 会先调用析构函数，再释放内存

![QQ截图20220530014703](/assets/blog_res/2022-05-29-memory1.assets/QQ%E6%88%AA%E5%9B%BE20220530014703.png)



## 总结

- **new的原理**
  1. 调用operator new函数申请空间
     1. operator new还会调用malloc
  2. **会用static_cast把malloc返回的void*强转为对应类型。**
  3. 在申请的空间上执行构造函数（通过这个指针调用构造函数），完成对象的构造
  4. **不要看到重载`operator new`返回`void*`就懵逼了。因为`new expression`不仅会寻找对应的`operator new()`分配内存，还要构造对象并返回对应类型的指针。后面的两个步骤是编译器做的。**
  
- **delete的原理**
  
  1. 在空间上执行析构函数，完成对象中资源的清理工作
  2. 调用operator delete函数释放对象的空间
     1. operator delete还会调用free
  
  ***delete会发生隐式类型转换！！！详细看一下智能指针章节的最后一块***
  
  > .....对于第一种（非数组）形式，*表达式* 必须是指向对象类型的指针或可以按语境隐式转换到这种指针的类类型.........
  
- **new T[N]的原理** 这个叫array new
  1. 调用operator new[]函数，在operator new[]中实际调用operator new函数完成N个对象空间的申请
  1. 在申请的空间上执行N次构造函数
  1. array new 的时候 内存块会记录你这个具体[]括号里面的是几。看一下下一篇。
  1. 进阶：一般来说，如果new一个数组，数组里面储存的对象没有定义默认构造函数，则不需要调用对象的构造函数。


- **delete[] T的原理**
  1. 在释放的对象空间上执行N次析构函数，完成N个对象中资源的清理
  1. 调用operator delete[]释放空间，实际在operator delete[]中调用operator delete来
  1. 进阶：一般来说，如果new一个数组，数组里面储存的对象没有定义默认析构函数，则不需要调用对象的析构函数。


### malloc/free和new/delete的区别:

**共同点是:**

都是从堆上申请空间，并且需要用户手动释放。

**不同的地方是:**

1. **malloc和free是函数，new和delete是操作符（operator new(), operator delete())**
2. malloc申请的空间不会初始化，new可以初始化
3. malloc申请空间时，需要手动计算空间大小并传递，new只需在其后跟上空间的类型即可，因为他帮你包了一层
4. malloc的返回值为void*, 在使用时必须强转，new不需要，因为new后跟的是空间的类型 ，因为他帮你包了一层
5. **malloc申请空间失败时，返回的是NULL，因此使用时必须判空，new不需要，但是new需要捕获异常**
6. **申请自定义类型对象时，malloc/free只会开辟与销毁空间，不会调用构造函数与析构函数，而new在申请空间后会调用构造函数完成对象的初始化，delete在释放空间前会调用析构函数完成空间中资源的清理**
7. new/delete比malloc和free的效率稍微低点，因为new/delete的底层封装了malloc/free

**new申请的内存，能用free吗？**

- 不可以，new对应delete不可以张冠李戴。（malloc/free,new/delete必需配对使用）
- 对于非内部数据类型的对象而言，光用malloc/free无法满足动态对象的要求。对象在创建的同时要自动执行构造函数，对象在消亡之前要自动执行析构函数。由于malloc/free是库函数而不是运算符，不在编译器控制权限之内，不能够把执行构造函数和析构函数的任务强加于malloc/free。因此c++语言需要一个能完成动态内存分配和初始化工作的运算符new，以及一个能完成清理与释放内存工作的`delete`

## 注意不要double-free

- 对一个已经调用过`delete`或`free`清理过的区块再次调用`delete`或`free`会造成double-free错误。

- 但是对一个空指针调用`delete`或`free`则不会发生任何事情。

  - > 如果 *表达式* 求值为空指针值，那么不会调用析构函数，且可能会也可能不会调用解分配函数（这是未指明的），但默认的解分配函数保证在传递了空指针时不做任何事。

  - 此处空指针指的是如 `int* p = nullptr`这样的显式置为0的指针

## malloc的 cookie

**有个问题是free怎么判断传给它的指针是指向能被析构的还是未定义内存**

这个问题的答案是，cookie不仅会保存分配内存的大小，而且会用最后一个bit保存是否已分配。如果已分配，就是能被析构的。就是1，未分配也就是不能析构的就是0.



## cookie是上下各4字节（一般情况）。



如果malloc8字节大小，则会有0x0-0x4的上cookie，0x4-0x12的数据, 0x12-0x15的下cookie。最后返回的是0x4也就是指向起始可用内存的指针。

free释放时候看起始地址-4。看cookie。如果是已分配的则只需要把cookie最后一位修改为未分配即可。

同时可以看这段内存的前一个分配内存的下cookie和下一个分配内存的上cookie。如果还有一些已经处于未分配的内存（已释放），则可以合并。

CSAPP 9.9.6~9.9.11



##  内存延迟分配

Linux内核在用户申请内存的时候，只是给它分配了一个线性区（也就是虚存），并没有分配实际物理内存；只有当用户使用这块内存的时候，内核才会分配具体的物理页面给用户，这时候才占用宝贵的物理内存。内核释放物理页面是通过释放线性区（也就是虚存），找到其所对应的物理页面，将其全部释放的过程。

```c++
char *p=malloc(2048)    //这里只是分配了虚拟内存2048，并不占用实际内存。 
strcpy(p,"123")			//分配了物理页面，虽只使用了3个字节，但内存还是为它分配了2048字节的物理内存。
free(p) 				//通过虚拟地址，找到其所对应的物理页面，释放物理页面，释放虚拟内存(线性区)。
```

我们知道用户的进程和内核是运行在不同的级别，进程与内核之间的通讯是通过系统调用来完成的。进程在申请和释放内存，主要通过brk,sbrk,mmap,unmmap这几个系统调用，传递的参数主要是对应的虚拟内存。

注意一点，在进程只能访问虚拟内存，它实际上是看不到内核物理内存的使用，这对于进程是完全透明的。

也就是说，**程序申请和操作的内存都是在虚拟内存上的，包括堆(heap)、栈(stack)等**。





### new 一个对象时加括号和不加括号的区别:

- 对于自定义类类型：

  -   如果该类没有定义构造函数（由编译器合成默认构造函数）也没有虚函数，那么`class c = new class;`将不调用合成的默认构造函数，而`class c = new class();`则会调用默认构造函数。


  -   如果该类没有定义构造函数（由编译器合成默认构造函数）但有虚函数，那么`class c = new class;`和`class c = new class();`一样，都会调用默认构造函数。
  - 如果该类定义了默认构造函数，那么`class c = new class;`和`class c = new class();`一样，都会调用默认构造函数。

- 对于内置类型：

  `int *a = new int;`不会将申请到的int空间初始化，而`int *a = new int();`则会将申请到的int空间初始化为0。

- 对于自定义类类型的**数组**：

  无论是否使用（），都会自动调用其默认构造函数来初始化： 

  ```c++
  string *psa = new string[10];  // 每个元素调用默认构造函数初始化 
  string *psa = new string[10]();  // 每个元素调用默认构造函数初始化
  ```

- 对于内置类型的**数组**：

  必须使用()来显示指定程序执行初始化操作，否则程序不执行初始化操作：

  ```c++
   int *pia = new int[10]; // 每个元素都没有初始化 
   int *pia2 = new int[10]();  // 每个元素初始化为0
  ```

- **基本上只看这句话：对于自定义类型来说没有区别，都是使用默认构造函数。对于原子（内置）类型来说加括号会初始化**

## 来一点`alloca`、`malloc`、`calloc`、`realloc`之间的区别

## `alloca`向栈申请内存，作用域结束自动释放

```c++
// 分配速度快，但是可移植性差。
void* alloca(size_t size);
```

## `malloc`向堆申请内存，不初始化内容，需要手动释放

老生常谈了，不赘述了

```c++
// 分配一块size字节大小的内存，并返回内存块起始位置的指针。
void* malloc (size_t size);
```

## `calloc`向堆申请内存，初始化内容为0，需要手动释放

```c++
// 分配一块内存，包含num个元素，每个元素size字节大小。
void* calloc (size_t num, size_t size);
```

**注意，参数和`malloc`不同。`malloc`提供的是size大小，而`calloc`提供的是n个size大小**

## `realloc`更改已经配置的内存空间，即更改由`malloc()/calloc()/realloc()`函数分配的内存空间的大小。

```c++
// 改变指针ptr指向的内存块大小为size字节。原来内存块的位置也可能发生变化。
void* realloc (void* ptr, size_t new_size);
//ptr ：指向要重新分配的内存块的指针。
```

- 如果`ptr`是`NULL`，则相当于调用`malloc(new_size)`, 成功返回首地址，失败返回NULL。
- 如果`new_size == 0` , 相当于调用`free(ptr)`;
- 如果`ptr`不是`NULL`、`malloc`、`calloc` 、`realloc()`的返回值，则报错`realloc invalid pointer`
- 若`new_size < old_size` ， 可能会丢失之前的部分数据
- 若`new_size > old_size` , 则会分配新的内存，**若分配到新的内存块**，则**`ptr`指向的内存被释放，`ptr`成为野指针**。
- `void *ptr = realloc(ptr, new_size);`：这样的写法，会造成**内存泄露**。（若**分配失败，返回NULL，而之前`ptr`所指向的内存没有释放，且无法被访问**）。
- 释放`realloc()`过的`ptr`时，要判断`new_size`是否为0，否则会造成`double free`错误。（`new_size`为0时，相当于`free(ptr)`,再次`free`时错误）。
- `realloc()`并**不保证调整后的内存空间和原来的内存空间保持同一内存地址**，相反，`realloc`返回的指针很可能指向一个新的地址
  - 如果当前内存段后面有需要的内存空间，则直接扩展这段内存空间，`realloc()`将返回原指针。
  - 如果当前内存段后面的空闲字节不够，那么就使用堆中的第一个能够满足这一要求的内存块，将目前的数据复制到新的位置，并将原来的数据块释放掉，返回新的内存块位置。
- 如果内存不足，`realloc()`失败，则**不释放旧内存块（此时，原来的指针仍然有效）**并返回空指针。

# c/c++风格指针类型转换

注意，在c++中，禁止指针类型的隐式转换。比如这样是不可以的

```c++
int* ptr = malloc(sizeof(int));
```

- 所以必须强制转换为`int*`类型
  - 注意是转换为`int*`而不是`int`

```c++
int* ptr = (int*)malloc(sizeof(int)); //C风格
int* ptr = static_cast<int*>(malloc(sizeof(int))); //C++风格
```



# delete 后必须直接设置指针为nullptr，否则造成的垃圾值会导致意外情况。

```c++
class myobj {
public:
    int* ptrs;
    myobj(int val) :ptrs(new int(val)) {}
    ~myobj() {
        if (ptrs != nullptr) {
            delete ptrs;
            ptrs = nullptr;
        }
    }
};

int main() {
    myobj* ptr = new myobj(20);
    delete ptr;
    delete ptr;//额外一次
    return 0;
}
```

这段代码中，我们重复`delete`居然会报错。按理来说不是应该第一次`delete`之后，`ptrs`被置为`nullptr`了吗？

问题在于，我们`delete`的时候，不仅会调用析构函数`delete`掉`ptrs`，还会`free`整个`myobj`对象空间。

所以我们给`ptrs`设置为`nullptr`后，整个外部的`ptr`指向的内存空间已经被释放了。全部都是垃圾值。虽然此时`ptr`指向的空间地址没变，但是整个空间本身被释放，已经是垃圾值了。在MSVC里，未初始化的堆内存会被设置为`0xd`而不是`0x0`，这就导致了if语句无效。所以再次`delete`会有问题。

如果我们在两次`delete`中间插入一个`nullptr`就不会有这个问题，因为此时ptr被置为了`0x0`。而`delete`一个`0x0`空指针是不会有任何事情发生的。

这就是说我们只要使用了`delete`，一定要随后直接设置指针为`nullptr`。



# kmalloc和vmalloc

- `kmalloc`和`vmalloc`是分配的是内核的内存,`malloc`分配的是用户的内存
- `kmalloc`申请的是较小的连续的物理内存，**内存物理地址上连续，虚拟地址上也是连续的**，使用的是内存分配器slab的一小片。申请的内存位于物理内存的直接映射区域（3G～3G+896M (high_memory)）。
  - 用`kzalloc`申请内存的时候， 效果等同于先是用` kmalloc()` 申请空间 , 然后用 `memset() `来初始化
  - 注意`kmalloc`最大只能开辟128k(32*PAGESIZE)-16，16个字节是被页描述符结构占用了。
  - **`kmalloc`是可能会睡眠的。---linux内核设计与实现 12.4**
- `vmalloc`用于申请较大的内存空间，虚拟内存是连续。申请的内存的则位于`vmalloc_start`～`vmalloc_end`之间（非连续内存区），与物理地址没有简单的转换关系，虽然在**虚拟地址上它们是连续的，但是在物理上它们不连续**。
  - `vmalloc_start` 是在(3G+896M)高端内存起始 + 8M空洞 的位置处起始
  - 一般情况下，只有硬件设备才需要物理地址连续的内存，因为硬件设备往往存在于MMU之外，根本不了解虚拟地址；但为了性能上的考虑，内核中一般使用 `kmalloc()`，而只有在需要获得大块内存时才使用`vmalloc()`，例如当模块被动态加载到内核当中时，就把模块装载到由`vmalloc()`分配 的内存上。
  
- `vmalloc`比`kmalloc`要慢。因为由于 `vmalloc `获得的物理内存页是不连续的，因此它只能将这些物理内存页一个一个地进行映射，在性能开销上会比直接映射大得多。

https://www.cnblogs.com/wuchanming/p/4465155.html

https://www.cnblogs.com/alantu2018/p/9000778.html

https://blog.csdn.net/macrossdzh/article/details/5958368
