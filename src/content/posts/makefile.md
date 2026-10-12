---
title: "makefile文件相关知识"
slug: "makefile"
published: 2022-05-11T21:30:00-05:00
description: ""
tags: ["开发"]
category: "笔记"
draft: false
typora-root-url: ../../../public
---

# makefile文件相关知识

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="330" height="86" src="//music.163.com/outchain/player?type=2&amp;id=1342840047&amp;auto=1&amp;height=66"> </iframe>

### 文件命名

makefile或者Makefile

### Makefile规则

一个makefile文件中可以有一个或者多个规则

```
目标 ...: 依赖...
	命令(Shell命令)
	...
```

目标：最终要生成的文件。__（伪目标除外）__

依赖：生成目标所需要用到的文件或者是目标

命令：通过执行命令对依赖操作生成目标（命令前必须用Tab缩进）

__一般来说，makefile中的其它规则一般都是为第一条规则服务的__



## 语法

### 自定义变量

```makefile
变量名 = 变量值
var = hello
```

### 预定义变量

```makefile
AR: 归档维护程序的名称，默认值为ar
CC: C编译器的名称，默认值为cc
CXX: C++编译器的名称，默认为g++
$@: 目标的完整名称
$<: 第一个依赖文件的名称
$^: 所有的依赖文件
```

### 获取变量的值

```makefile
$(变量名)
例如：
var = hello
$(var)就会获取var的值
```

__自动变量只能在规则的命令中使用__

```makefile
app:main.c a.c b.c
	$(CC) -c $^ -o $@
这里$^是获取所有的依赖。就是main.c a.c b.c
$@ 目标的完整名称就是app
注意这里第一行的依赖名称不可以使用自动变量如 $@ $< $^
```

## makefile示例

__尽量不要在第一个规则的命令里直接用一串的.c 因为makefile可以检测哪个文件改动了，针对那一个文件进行生成__

__如果都写在一起，会每次都重新生成所有文件。因为命令在一行。__

__如果按照下图这种.o然后分开写则会分步执行。没有更改过的文件不会重新生成__

```makefile
app:sub.o add.o mult.o div.o main.o //注意这里直接执行.o文件 但是我们没有，需要在下面规则写从.c到.o的方法
	gcc sub.o add.o mult.o div.o main.o -o app
sub.o:sub.c
	gcc -c sub.c -o sub.o
add.o:add.c
	gcc -c add.c -o add.o
mult.o:mult.c
	gcc -c mult.c -o mult.o
div.o:div.c
	gcc -c div.c -o div.o
main.o:main.c
	gcc -c main.c -o main.o
```

我们发现这样非常繁琐。我们可以换一种方式

```makefile
src = sub.o add.o mult.o div.o main.o
target = app
//app:sub.o add.o mult.o div.o main.o
	//gcc sub.o add.o mult.o div.o main.o -o app
$(target):$(src)
	$(CC) $(src) -o $(target)
sub.o:sub.c
	gcc -c sub.c -o sub.o
add.o:add.c
	gcc -c add.c -o add.o
mult.o:mult.c
	gcc -c mult.c -o mult.o
div.o:div.c
	gcc -c div.c -o div.o
main.o:main.c
	gcc -c main.c -o main.o
```

我们发现这样分开处理下面的依赖依然非常繁琐。我们可以引入模式匹配

```makefile
%.o:%.c
这里的%通配符是匹配一个字符串。注意这里前后的两个%匹配的是同一个字符串。
所以我们可以开始这样写
%.o:%.c
	gcc -c $< -o $@ //这里$<指的是第一个依赖文件的名称。我们这儿只有一个所以就用这个

放入示例就是
%.o:%.c
	$(CC) -c $< -o $@
```

之后我们的makefile就会变成这样

```makefile
src = sub.o add.o mult.o div.o main.o
target = app
$(target):$(src)
	$(CC) $(src) -o $(target)
%.o:%.c
	$(CC) -c $< -o $@
```

但是到这儿了，我们还是有一个问题。第一行的`src`依旧有一大串需要自己写。我们就引入函数功能

```makefile
$(wildcard PATTERN...)
```

这个函数详细信息：

​	功能：获取指定目录下指定类型的文件列表

​	参数：`PATTERN`指的是某个或者多个目录下的对应的某种类型的文件。如果有多个目录，一般使用空格间隔

​	返回：得到的若干个文件的文件列表。文件名之间使用空格间隔

​	示例：

```makefile
$(wildcard *.c ./sub/*.c) 这行指的是获取当前目录下所有的.c文件和 ./sub目录下所有的.c文件
返回值格式是
a.c b.c c.c d.c e.c f.c ...
```

但是这里我们需要`.o`文件。但是`.o`文件还没有被生成，需要靠着下面的子规则生成。我们怎么办？我们可以引入匹配替换函数

```makefile
$(patsubst <pattern>, <replacement>, <text)
```

这个函数详细信息：

​	功能：查找`<text>`中的单词（单词以空格，tab，回车或换行分割）是否符合模式`<pattern>`。如果匹配，则以`<replacement>`替换

​	__`<pattern>`可以包括通配符%表示任意长度的子串。如果`<replacement>`中也包含% 那么`<replacement>`中的这个%和`<pattern>`中的%将是一个子串__

​	返回：函数返回被替换过后的子字符串

​	示例

```makefile
$(patsubst %.c, %.o, x.c bar.c)
意思是将x.c 和bar.c里面的.c替换成.o
```

在这之后，我们就可以这样写了

```makefile
src = $(wildcard ./*.c) //先获取路径下所有.c文件
objs = $(patsubst %.c, %.o, $(src)) //把.c都换成.o
target = app
$(target):$(objs)
	$(CC) $(objs) -o $(target)
%.o:%.c
	$(CC) -c $< -o $@
```

## 清理阶段

我们发现编译后生成了很多无用的中间文件 比如`.o`文件。我们可以在上面的文件里面加入一个clean规则

```makefile
clean:
	rm $(objs) -f
```

__注意，这里直接运行makefile是不会自动执行clean规则，因为makefile不会执行任何与第一条规则无关的指令__

所以我们需要显式使用即可

```bash
make clean
```

__注意。这里我们会生成一个`clean`文件。这样做不仅没有意义，而且会导致报错如`clean已是最新`__

我们可以使用生成伪目标来解决这个问题

```makefile
.PHONY:clean
clean:
	rm $(objs) -f
```

这样做就解决了所有问题



## 整体文件

```makefile
//获取变量阶段
src = $(wildcard ./*.c) //先获取路径下所有.c文件
objs = $(patsubst %.c, %.o, $(src)) //把.c都换成.o
target = app
//第一条规则（主规则）
$(target):$(objs)
	$(CC) $(objs) -o $(target)
//子规则（处理依赖文件）	
%.o:%.c
	$(CC) -c $< -o $@
//清理阶段
.PHONY:clean
clean:
	rm $(objs) -f
```
