---
title: "Effective STL 笔记（二）：关联容器、迭代器与容器使用杂项"
slug: "EFFSTL-2"
published: 2022-07-22T01:56:00-05:00
description: ""
tags: ["STL"]
category: "笔记"
draft: false
typora-root-url: ../../../public
---
# map/unordered_map不允许更改key

- 原因是我们依靠的是key来进行排序。
  - 而且我们会把key和data合成成为一个value。形式是`pair<const key_type, data_type>`。然后把这个传入红黑树/哈希表。指定他从中抽取出来pair的第一个值也就是key来排序。
- 所以换句话说就是红黑树/哈希表存的是map的key和value合成的pair。然后通过key排序。这也是为什么map的迭代器返回的是pair。因为我们就是按照pair存进去的。也是为什么用`insert`存入的时候需要`make_pair`。
- map不允许更改key是因为保存至红黑树的`pair`里面的`key`是`const`的。
  - 也就是如果有`map<k,v>` 或 `multimap<k,v>` 类型的对象，其中的元素类型会是`pair<const k, v>`

![QQ截图20230111183843](/assets/blog_res/2022-07-20-EFFSTL.assets/QQ%E6%88%AA%E5%9B%BE20230111183843.png)




## map的特殊的重载的operator[]

如果这个括号里面的元素不存在，他会帮你创建一个以括号内元素为key，等号后面为value的键值对。

所以会有陷阱 比如：

```c++
if (my_map[4] == 7){
    //...
}
```

上面这行表面是判断`key` 4的值是否为7， 但是这行执行的时候，如果`key`4不存在，他会创建一个`4,0`的键值对。

因为它访问了`my_map[4]`，此时发现该元素不存在，就使用该类型的**默认构造函数**构造出一个value插入进去。这里我们用的是`int`，`int`的默认是0，所以会有一个`4,0`

> **若键不存在：**
>
> **则默认构造的对象的key_type（也就是key）必须满足可复制/移动构造。**
>
> **mapped_type（也就是value）必须满足可默认构造**
>
> 来自[这里](https://zh.cppreference.com/w/cpp/container/map/operator_at)

- 对于自定义的对象，例子：

```c++
class myobj{
    public:
        myobj(){
            val = 12; //注意这里
        }
        myobj(int x){
            val = x;
        }
    int val;
};

class comp1{ //自定义排序
    public:
    bool operator()(const int& lhs, const int& rhs) const{ //注意map的自定义排序是key而不是整个pair。所以自定义排序的函数签名是key
        return lhs > rhs;
    }
};
int main()
{
    map<int,myobj, comp1> we;  
    myobj a(20);
    myobj b(30);
    if(we[2].val == a.val){ //key为2的元素的val是否等于a的val
        cout << "true1" << endl;
    }
    for(auto t:we){
        cout << t.first << t.second.val << endl; //输出2 12
    }
    cout << we.size() << endl;
}
```

由于判断`key`为`2`的元素的`val`是否等于`a`的`val`的时候会先访问`key`为`2`的元素，这时候发现元素不存在。所以会使用默认（无参）构造函数或默认值构造对应的键值对。所以会出现一个 `2,12`的元素。



所以为了避免陷阱，我们应该：

- 向map容器插入元素时直接使用insert函数
- 遍历map容器时使用iterator迭代器
- 修改或者删除元素时使用find函数找到元素后再进行操作

```c++
int main(){
    unordered_map <string,int> map;
    unordered_map <string,int> map2;
    vector<string> str = {"a","a","abc","abcd"};
    for(string a : str){
        cout << map[a] << endl;
        map[a] = map[a] + 1;//map[a]是你key对应的value。 a才是你的key。所以这里的意思是 你map[a]的这个val+1。也就是key为a的地方把他的value在原来的基础上加1
        //如果map[a]有这个key 比如map里面有a 那么这个val+1。简单来说就是key为a对应的value = key为a对应的value + 1
        //如果map[a] 没有这个key。那就加这个key 比如里面没有abc 那就把abc加进去
        //map[num];对于这个下标操作，如果存在num关键字，则返回对应的值；如果不存在num关键字，则创建一个键值对，键为num，值为值类型的默认初始化值。
       那么这句话的意思是。如果有a这个key，那么把这个key对应的value+1
       如果没有，那就先新建a这个key，value设为0+1.
       所以map[4] = "ffff" 这一句，如果有4这个key，那就把这个key对应的value改为"ffff"
       如果没有，就新建4， "ffff"这个键值对放入map
        //等号右侧的map[a]先执行。先在map里面找有没有元素为a的。如果没有就创建一个key=a value=0的元素。然后返回value= 0。之后value+1赋值给key为a的元素的value上面
        //先重载=返回自己。然后重载[]返回second也就是value。因为东西是按照pair存的。
    }
    for(auto x = map.begin(); x!= map.end(); x++){
        cout << x->first << x->second << endl;
    }
    
    pair<string,int> ss = *map.begin();
    //map里面的每一个元素可以看为一个pair。注意这里迭代器需要解引用。
    因为map的底层是把key和value合成起来成为真正的value。是用一个pair包起来的。
    用pair包起来之后，把key和这个包起来的pair放到红黑树里面。
    其实这个value应该叫data。没所谓了。
    所以map的每一个元素存起来应该长这个样子
    key = string
    value = pair<string, int>。
    所以迭代器的first其实是下面value存的pair的first
    迭代器的second是下面的value存的pair的second


    所以说才会有select1st从value里面取key。所以你自己要insert元素的时候需要传一个pair进去。他会把key从pair里面提出来变成key

}
```

### 为什么要这么设计

- 这么设计的原因，我的个人思考是，我们使用`x[5]`的时候，其实就是`x.operator[](5)`，但是我们既有可能要给这个地方赋值，如`x[5] = 1`，又有可能是获取一个这个地方的值，如`int a = x[5]`。但是这个函数本身无法做出这样的判断。同时STL容器是值语义 。所以它必须当做所有`operator[]`的调用都是写入。所以在用下标运算符访问不存在的元素的时候，会默认构造出这个元素，然后返回这个元素的引用。 -- 同时参考more effective c++ 条款29 P.190

所以我们查看文档

> | `T& operator[]( const Key& key );` | (1)  |            |
> | ---------------------------------- | ---- | ---------- |
> | `T& operator[]( Key&& key );`      | (2)  | (C++11 起) |

我们发现没有一个`const`成员函数

所以下面这样是不可以的：

```c++
const map<int, int> op{{1,2}};
op[1];//不可以。
op.at(1);//可以
```

因为`operator[]`总会有潜在的对象修改语义。所以针对`const map`而言，访问元素的唯一方法便是使用`at()`





# set不允许更改值

- 因为set的`key`和`data`是同一个东西，也就是`value`。

  - 我们是依靠这个值进行红黑树排序

  ![QQ截图20230111183159](/assets/blog_res/2022-07-20-EFFSTL.assets/QQ%E6%88%AA%E5%9B%BE20230111183159.png)
- 但是set不允许更改值是因为迭代器返回的是常量迭代器也就是`const iterator`
- map不允许更改key是因为保存至红黑树的pair里面的key是const的。

# set不会重复插入且不允许重复元素的原因

set使用的红黑树的`insert_unique`

multi_set使用的红黑树的`insert_equal`

# map不会重复插入且不允许重复key的原因

`map`使用的红黑树的`insert_unique`

`multi_map`使用的红黑树的`insert_equal`

# set容器 和 map容器在插入时会自动排序。所以在使用自定义数据类型的时候就必须要直接指定排序规则仿函数来进行自定义排序。 

## set 不多赘述

自定义排序比较常见

## map的自定义排序排序的是`key`而不是`pair`。所以自定义排序的函数签名是key

```c++
class myobj{
    public:
        myobj(){
            val = 12; //注意这里
        }
        myobj(int x){
            val = x;
        }
    int val;
};

class comp1{ //自定义排序
    public:
    bool operator()(const int& lhs, const int& rhs) const{ //注意map的自定义排序是key而不是整个pair。所以自定义排序的函数签名是key
        return lhs > rhs;
    }
};
int main()
{
    map<int, myobj, comp1> we;  
    myobj a(20);
    myobj b(30);
    if(we[2].val == a.val){ //key为2的元素的val是否等于a的val
        cout << "true1" << endl;
    }
    for(auto t:we){
        cout << t.first << t.second.val << endl; //输出2 12
    }
    cout << we.size() << endl;
}
```



## unordered_map/unordered_set 哈希表没有自定义排序。只有自定义哈希和自定义等比。想使用自定义的键类型，必须实现hash函数和等比函数。

- 自定义哈希的意义不多说。
- 自定义等比的意义是在两个对象哈希值相同的时候，需要告诉容器一个办法让其判断这两个对象是真的一模一样，还是只是哈希出来的值是一样但本身是不同的，



# c++的map是基于红黑树实现的，它不需要对key进行哈希，所以可以用vector做为key。但是unordered map是基于哈希表实现的，它需要对key进行哈希，但是c++ 默认不对vector提供哈希，所以要么自己写一个哈希函数对vector进行哈希，或不要在unordered map中使用vector做为key。





# 注意！随机访问迭代器支持>和<比较！！









![5740965-0d91567d9f259cce](/assets/blog_res/2022-07-20-EFFSTL.assets/5740965-0d91567d9f259cce.png)



# 对容器使用下标访问运算符访问或者是对其迭代器解引用返回的是元素的引用。front，back成员函数也是。

正因为是引用，我们才可以有如下操作，比如：

```c++
my_vec[0] = 1;
*my_vec.begin() = 1;
```

# 正因为上面那条，针对容器的常量引用或如果容器本身是常量，提取出来的元素也是常量性质的。

- 因为常量引用不能绑定到非常量引用。

```c++
const vector<int> a {1,2,3};
int& val = a[0]; //错误
const int& vala = a[0]; //正确
```



```c++
void functest(const vector<int>& vec){
    int& val = vec[0]; //错误
    const int& vala = vec[0]; //正确
}
```





# 为什么没有引用容器，除非使用std::reference_wrapper

1：容器内的元素必须是可赋值的。引用是不可赋值的（引用只能在声明的同时初始化）

2：没有指向引用的指针。容器有迭代器，迭代器是指针。元素如果是引用，迭代器无法工作，

除非使用`std::reference_wrapper`





# for_each

```c++
//这里函数对象对应的函数的形参应该是迭代器指向的容器对象的对应类型。
//比如vector<int>的话这里就要int, vector<pair<int,int>>的话就要pair<int, int>
void printvector01(int a){ 
    cout << a << endl;
}

//注意这里pair<int a, int b>是错的！！！
//pair<>括号里头的是数据类型，外面的才是名字！你不能vector<int a>吧
void printvector02(pair<int, int> a){ 
    cout << a.first << " , " << a.second << endl;
}


class printvector03{
public:
    void operator()(int a){
        cout << a << endl;

    }
};

/*
template <class _InIt, class _Fn>
_CONSTEXPR20 _Fn for_each(_InIt _First, _InIt _Last, _Fn _Func) { // perform function for each element [_First, _Last)
    _Adl_verify_range(_First, _Last);
    auto _UFirst      = _Get_unwrapped(_First);
    const auto _ULast = _Get_unwrapped(_Last);
    for (; _UFirst != _ULast; ++_UFirst) {
        _Func(*_UFirst); //这里已经对迭代器对象解引用了，所以直接传入的是迭代器对应的值。
        // 注意这里调用函数的方式是直接把参数塞进去。所以传递函数对象就行 不用() 加了括号叫调用
    }

    return _Func; //看好了！！有返回值！！
}
*/




```

```c++
int main(){
    vector<int> test = {1,2,3,4,5};
    for_each(test.begin(), test.end(), printvector01); //注意这里传递的是函数对象，不是函数。因为printvector01是个函数不是类，所以printvector01()加了括号的叫调用！！
    for_each(test.begin(), test.end(), printvector03()); //注意这里传递的是函数对象，不是类型名。因为printvector03是个类(仿函数)不是函数。所以printvector01()加了括号的是类的匿名对象，这里因为是仿函数所以叫函数对象，而不是调用！！
    //注意区分类和普通函数的对象。普通函数不加括号叫对象，加了括号叫调用。仿函数（类）要加括号。加了括号叫类的匿名对象，不加括号叫类型名。
    vector<pair<int,int>> test2{ {1,1}, {2,2}, {3,3}, {4,4}, {5,5} };
    for_each(test2.begin(),test2.end(), printvector02);
}
```

- **`for_each`是可以有返回值的。也就是可以施加一个有状态的函数对象。**
  - 比如下面的代码目的是获取所有性别为1的人的id，并放入容器。

```c++
class Person{
    public:
        int id;
        int sex;
        Person() = default;
        Person(int x, int y):id(x), sex(y){};

};

struct myfind{
    vector<int> persons;
    void operator()(const Person& item){ //这里不需要bool了。void即可。
        if(item.sex == 1){
            persons.push_back(item.sex);
        }
    }
};

int main(){
    vector<Person> my_vec{Person(1,1),Person(2,1),Person(3,1),Person(4,2),Person(5,2)};
    myfind t = for_each(my_vec.begin(), my_vec.end(), myfind());
    
    for(auto&i:t.persons){
        cout << i << endl;
    }
    return 0;
}
```









# 迭代器种类

迭代器分为五种：

- 输入迭代器（Input Iterator）：通过对输入迭代器解除引用，它将引用对象，而对象可能位于集合中。最严格的输入迭代只能以只读方式访问对象。例如：istream。 
- 输出迭代器（Output Iterator）：该类迭代器和Input Iterator极其相似，也只能单步向前迭代元素，不同的是该类迭代器对元素只有写的权力。例如：ostream, inserter。 
- 前向迭代器（Forward Iterator）：该类迭代器可以在一个正确的区间中进行读写操作，它拥有Input Iterator的所有特性，和Output Iterator的部分特性，以及单步向前迭代元素的能力。
  - 假设 p 是一个前向迭代器，则 p 支持 ：
    - `++p`
    - `p++`
    - `*p`
    - 复制
    - 赋值
    - 可以用` ==` 和 `!= `运算符进行比较。
    - 此外，两个正向迭代器可以互相赋值。
- 双向迭代器（Bidirectional Iterator）：该类迭代器是在Forward Iterator的基础上提供了单步向后迭代元素的能力。例如：list, set, multiset, map, multimap。
  - 假设 p 是一个双向迭代器，则 p 支持 ：
    - 正向迭代器的全部功能 和
    - `--p`
    - `p--` （即一次向后移动一个位置）。
- 随机迭代器（Random Access Iterator）：该类迭代器能完成上面所有迭代器的工作，它自己独有的特性就是可以像指针那样进行算术计算，而不是仅仅只有单步向前或向后迭代。例如：vector, deque, string, array。 
  - 假设 p 是一个随机迭代器，则 p 支持 ：
    - 双向迭代器的全部功能 和
    - `p+=i`：使得 p 往后移动 `i `个元素。
    - `p-=i`：使得 p 往前移动` i `个元素。
    - `p+i`：返回 p 后面第` i `个元素的迭代器。
    - `p-i`：返回 p 前面第` i `个元素的迭代器。
    - `p[i]`：返回 p 后面第 `i` 个元素的引用。
    - 此外，两个随机访问迭代器` p1`、`p2 `还可以用 `<`、`>`、`<=`、`>= `运算符进行比较。
    - 另外，表达式 `p2-p1` 也是有定义的，其返回值表示` p2` 所指向元素和 `p1` 所指向元素的序号之差（也可以说是` p2 `和` p1 `之间的元素个数减一）。

|   容器类型                                 |      迭代器类型          |
| :--------------------------------- | -------------- |
| array                              | 随机访问迭代器 |
| vector                             | 随机访问迭代器 |
| deque                              | 随机访问迭代器 |
| list                               | 双向迭代器     |
| set / multiset                     | 双向迭代器     |
| map / multimap                     | 双向迭代器     |
| forward_list                       | 前向迭代器     |
| unordered_map / unordered_multimap | 前向迭代器     |
| unordered_set / unordered_multiset | 前向迭代器     |
| stack                              | 不支持迭代器   |
| queue                              | 不支持迭代器   |

| 迭代器定义方式 | 具体格式                                   |
| -------------- | ------------------------------------------ |
| 正向迭代器     | 容器类名::iterator 迭代器名;               |
| 常量正向迭代器 | 容器类名::const_iterator 迭代器名;         |
| 反向迭代器     | 容器类名::reverse_iterator 迭代器名;       |
| 常量反向迭代器 | 容器类名::const_reverse_iterator 迭代器名; |

- 所以我们说，除了vector，deque，string和array以外，其他的容器都不支持如`begin()+n`的操作。

# 为什么迭代器的类型不是简单的T*，而一般都带了很长的包装器

https://quuxplusone.github.io/blog/2022/03/03/why-isnt-vector-iterator-just-t-star/

# 不同容器不同操作的*平均*时间复杂度

| 容器                                     | []下标访问 | push_back | pop_back | insert  | erase   | find    | sort       |
| ---------------------------------------- | ---------- | --------- | -------- | ------- | ------- | ------- | ---------- |
| std::array                               | O(1)       | /         | /        | /       | /       | O(n)    | O(n logn)  |
| std::vector                              | O(1)       | O(1)      | O(1)     | O(n)    | O(n)    | O(n)    | O(n logn)  |
| std::deque                               | O(1)       | O(1)      | O(1)     | O(n)    | O(n)    | O(n)    | O(n logn)  |
| std::list                                | /          | O(1)      | O(1)     | O(1)    | O(1)    | O(n)    | O(n logn)* |
| std::forward_list                        | /          | /         | /        | O(1)    | O(1)    | O(n)    | /          |
| std::set/std::multiset                   | /          | /         | /        | O(logn) | O(logn) | O(logn) | /          |
| std::map/std::multimap                   | /          | /         | /        | O(logn) | O(logn) | O(logn) | /          |
| std::unorderd_set/std::unorderd_multiset | /          | /         | /        | O(1)    | O(1)    | O(1)    | /          |
| std::unorderd_map/std::unorderd_multimap | /          | /         | /        | O(1)    | O(1)    | O(1)    | /          |

*list的sort是成员函数。因为list不提供随机访问迭代器。

- 需要随机访问或只在尾部进行插入或删除使用`vector`。
- 需要随机访问和头尾插入使用`deque`
- 如果不需要随机访问但频繁插入和删除使用`list`
- 如果内存格外受限则使用`forward_list`
- 如果需要搜索且保持排序则使用`map/set`
- 如果需要搜索但不需要排序使用`unordered_map/unordered_set`



# 原始数组的初始化

- 静态数组 `int array[100];` 
  - 定义了数组array，但并未对数组初始化；
- 静态数组` int array[100] = {0};` 
  - 定义了数组array，并将数组元素全部初始化为0；
- 静态数组 `int array[100] = {1}; `
  - 定义了数组array，并将数组第一个元素初始化为1，后面99个元素初始化为0；
- 静态数组` int array[100] = {4,5}; `
  - 定义数组array，并初始化前两个元素为4,5，后面剩余元素初始化为0；

`int a[5] = { 1 }; ` 曾经我认为这是把数组全部初始化为１，事实却是，只有数组的第一个元素被初始化为１，其他全为０；

- **数组初始化列表中的元素个数小于指定的数组长度时，不足的元素补以默认值。**

  - 对应基本类型`int`来说，就是补0
  - 非基本类型的数组就是调用默认构造函数。如`string`
  - `string a[5] = { "foo" };` 等同于 `string a[5] = { "foo", "", "", "", "" };`
  - **如果不明确指出初始化列表，那么基本类型是不会被初始化的（除全局变量和静态变量外），所有的内存都是“脏的”；**
  - **而类类型则会为每个元素调用默认构造函数或使用默认值进行初始化。**

  ```c++
  class testnum{
      public:
          testnum(){
          }
          int val = 200;
  };
  class testnum1{
      public:
          testnum1(){
              val = 23333;
          }
          int val;
  };
  int main() 
  {
      testnum arr[10]; //全是200
      testnum1 arr1[10]; //全是23333
      int arr2[10]; //没有初始化，脏数据，乱糟糟
      int arr3[10]; //初始化为默认值 10个0
  }  
  ```

  

- 注意，在C++11中，中间的赋值号可以省略，即

  - ` int a[5]{1};`是合法的，但依旧是只初始化第一个元素为1，剩下的都是默认0

- 并且，如果初始化列表为空，如` int a[5]{}`，那将初始化所有元素为默认值，即等同于` int a[5]{0}; `

# 再次重申容器是值语义。拷贝进来拷贝出去。

```c++
int main(){
    vector<int>my_vec;
    int a = 100;
    my_vec.push_back(a); //拷贝进
    a = 40000;
    cout << my_vec[0] <<endl; //还是100
}
```

为什么呢？我们看看push_back的源代码就好了

```c++
void push_back(const T& x) {
    if (finish != end_of_storage) {
        construct(finish, x);
        ++finish;
    } else
        insert_aux(end(), x);
}
```

我们先不管其他的，我们只看`construct`这个部分

```c++
template <class T1, class T2>
inline void construct(T1* p, const T2& value) {
    new (p) T1(value);
}
```

**`new (p) T1(value);`是一个`placement new`的用法，`new`的这个用法是在一个已分配好内存的地方调用构造函数来初始化一下。**

- 我们这里看到了，我们拿了一个`value`的值来在一块特定的地方**调用拷贝构造来构造**了一个元素。这就是为什么我们说是拷贝进。

https://blog.csdn.net/jmh1996/article/details/77968364

- 针对是否拷贝出来，这个地方要综合分析

```c++
int main(){
    vector<int>my_vec;
    int a = 100;
    my_vec.push_back(a); //拷贝进
    int b = my_vec.front();
    b = 12345;
    cout << my_vec[0] <<endl; //肯定还是100
    
    int& c = my_vec.front();
    c = 12345;
    cout << my_vec[0] <<endl; //变成12345
}
```

因为`front`返回第一个元素的引用。**我们如果用一个引用来初始化一个值，那么会调用其拷贝构造。因为需要独立开来。**



# 容器不能储存常量对象

没有`vector<const int>`。因为常量对象不是*可拷贝赋值*的。而且使用`cosnt vector<int>`可以达到同一效果。

```c++
const int a = 200;
const int b = 300;
b = a; //不可修改常量对象。所以是不可拷贝赋值的。
```

# deque的使用提示

- 在空容器上对 `deque.front()/back()` 的调用是未定义的。
  - 因为它返回的是容器首元素的**引用**。

# map不同接口的使用推荐

依旧来自Raymond Chen的[这篇文章](https://devblogs.microsoft.com/oldnewthing/20241118-00/?p=110535)

| Operation                                                    | Method                                                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Read, throw if missing / 读取，如果缺失则抛出异常            | `m.at(key)`                                                  |
| Read, allow missing / 读取，允许缺失                         | `m.find(key)`                                                |
| Read, create if missing / 读取，如果缺失则创建               | `m[key]`                                                     |
| Write, nop if exists, discard value / 写入，如果存在则nop，丢弃值 | `m.insert({ key, value })` /`m.emplace(key, value)`          |
| Write, nop if exists / 写入，如果存在则nop                   | `m.emplace(std::piecewise_construct, ...)` `m.try_emplace(key, params)` |
| Write, overwrite if exists / 写入，如果存在则覆盖。          | `m.insert_or_assign(key, value)`                             |

这么多接口，想实现如果没有就插入，如果有不要浪费构造这种逻辑，怎么做？

依旧是Raymond的[这篇文章](https://devblogs.microsoft.com/oldnewthing/20241118-00/?p=110535)，来自[这里](https://github.com/wanghenshui/cppweeklynews/blob/dev/posts/173.md)。 代码就是一坨。

# 实现`vector<T>`

https://quantdev.blog/posts/implementing_vector/index.html
