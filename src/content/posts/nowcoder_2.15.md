---
title: "Linux多进程开发-2.15-有名管道"
slug: "nowcoder_2.15"
published: 2022-05-20T01:50:00-05:00
description: ""
tags: ["牛客", "开发"]
category: "笔记"
draft: false
typora-root-url: ../../../public
---

# Linux多进程开发-2.15-有名管道

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="330" height="86" src="//music.163.com/outchain/player?type=2&amp;id=410446173&amp;auto=1&amp;height=66"> </iframe>

## 有名管道

__有名管道以FIFO的文件形式存在于文件系统中。但是内容是在内存中。__



### 创建有名管道

```c
#include <stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdlib.h>
#include <unistd.h>
int main(){

    int exist_or_not = access("2.14fifo", F_OK); //使用access函数判断文件。此处是判断是否存在。

    if(exist_or_not == -1){
        printf("管道不存在，创建管道");
        int ret = mkfifo("2.14fifo", 0664); //创建fifo文件
        if(ret == -1){
            perror("mkfifo");
            exit(0);
        }
    }
    return 0;
}
```

### 写入端

``` c
#include <stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdlib.h>
#include <unistd.h>
#include <fcntl.h>
#include <string.h>
//向管道中写入数据
int main(){
    //1. 创建管道文件
    int exist = access("2.14fifo", F_OK); //使用access函数判断文件。此处是判断是否存在。

    if(exist == -1){
        printf("管道不存在，创建管道");
        //2. 创建管道
        int ret = mkfifo("2.14fifo", 0664); //创建fifo文件
        if(ret == -1){ 
            //此处判断是否创建失败管道
            perror("mkfifo");
            exit(0);
        }
    }
    //3.以只写的方式打开管道
    int fd = open("2.14fifo", O_WRONLY);
    if(fd == -1){ 
        //此处判断是否打开失败
        perror("open");
        exit(0);
    }
    char buf[1024] = {0}; //创建字符串数组
    
    for(int i = 0; i < 100; i++){
        char buf[1024] = {0}; //创建字符串数组
        sprintf(buf, "hello, %d\n", i);  //将字符串写入字符串数组
        write(fd, buf, strlen(buf)); //将字符串数组写入管道文件
        bzero(buf, 1024); //清空数组
        sleep(1);
        
    }
    close(fd); //关闭文件
    return 0;
}
```



### 读取端

```c
#include <stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdlib.h>
#include <unistd.h>
#include <fcntl.h>
#include <string.h>
//从管道中读取数据
int main(){
    //1. 打开管道文件

    int fd = open("2.14fifo", O_RDONLY); //只读方式打开管道文件
    if(fd == -1){ 
        //如果打开失败
        perror("open");
        exit(0);
    }
    char buf[1024] = {0};
    //2. 读取数据
    while(1)
    {
        int len = read(fd, buf, sizeof(buf));
        if(len == -1)
        {
            perror("read");
            exit(0);
        }
        if(len == 0)
        {
            printf("写入端已经断开连接\n");
            break; //这里不可以用exit。因为如果用了exit，下面的close会运行不到。
        }
        printf("RECEIVE BUF : %s\n", buf);
        bzero(buf,1024); //清空数组
    }

    close(fd);

    return 0;
}
```

### 总结

### 有名管道的注意事项:

1. 一个为只读而打开一个管道的进程会被阻塞，直到另外一个进程为只写打开管道

2. 一个为只写而打开一个管道的进程会被阻塞，直到另外一个进程为只读打开管道

#### 读管道:

1. 管道中有数据，read返回实际读取的字节数。

2. 管道中没有数据：
   1. 管道的写入端被全部关闭，read返回0。（相当于读到了文件末尾）
   2. 写入端没有被全部关闭，read会被阻塞等待。

#### 写管道：

1. 管道读端被全部关闭，进行异常终止 (收到SIGPIPE信号)。

2. 管道读端没有被全部关闭：

   1.管道已经满了，write会阻塞等待。

   2.管道没有满，write将数据写入，并且返回实际写入的字节数。

