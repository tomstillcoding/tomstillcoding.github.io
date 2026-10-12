---
title: "Linux多进程开发-2.12-父子进程通过匿名管道通信"
slug: "nowcoder_2.13"
published: 2022-05-20T01:50:00-05:00
description: ""
tags: ["牛客", "开发"]
category: "笔记"
draft: false
typora-root-url: ../../../public
---

# Linux多进程开发-2.12-父子进程通过匿名管道通信

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="330" height="86" src="//music.163.com/outchain/player?type=2&amp;id=410446173&amp;auto=1&amp;height=66"> </iframe>





## 一次性写入

```c
#include <unistd.h>
#include <sys/types.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(){
    
    int pipefd[2]; // 创建管道数组
    int ret = pipe(pipefd); //创建管道

    if(ret == -1){ //如果管道创建失败
        perror("pipe error");
        exit(0);
    }

       //必须要在fork之前创建管道。因为fork才能将文件描述符复制给子进程，这样才可以通信
    pid_t pid = fork(); //创建子进程
    if(pid > 0){ //fork返回的pid是子进程id。也就是在父进程中，这个数字一定是大于0的
        //父进程

        //从管道的读取端读取
        char buf[1024] = {0};
        int len = read(pipefd[0], buf, sizeof(buf)); //! read函数默认是阻塞的。如果子进程没有写入到管道的话，父进程会一直等待子进程把数据写入管道。


        printf("receive :%d , pid: %d\n", len, pid);



    }
    else if(pid == 0){ //如果pid是0，代表现在切换进了子进程。
        //子进程
        //管道写入端写入

        char* msg = "hello world";

        int len = write(pipefd[1], msg, strlen(msg));
        printf("send :%d , pid: %d\n", len, getpid());
    }

    return 0;
}
```

## 循环写入 - 这里去掉sleep会产生自己读取自己的问题

```c
#include <unistd.h>
#include <sys/types.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(){
    
    int pipefd[2]; // 创建管道数组
    int ret = pipe(pipefd); //创建管道

    if(ret == -1){ //如果管道创建失败
        perror("pipe error");
        exit(0);
    }

       //必须要在fork之前创建管道。因为fork才能将文件描述符复制给子进程，这样才可以通信
    pid_t pid = fork(); //创建子进程
    if(pid > 0){ //fork返回的pid是子进程id。也就是在父进程中，这个数字一定是大于0的
        //父进程

        //从管道的读取端读取
        char buf[1024] = {0};
        while(1){
            //父进程循环读取数据。不用sleep因为默认是阻塞
            int len = read(pipefd[0], buf, sizeof(buf)); //! read函数默认是阻塞的。如果子进程没有写入到管道的话，父进程会一直等待子进程把数据写入管道。
            printf("receive :%d , pid: %d, father pid: %d\n", len, pid, getpid());
            //printf(buf); 不要这样写。要按照下面去写。不要直接读变量，要按照字符串读写
            printf("%s\n", buf);
        }
    



    }
    else if(pid == 0){ //如果pid是0，代表现在切换进了子进程。
        //子进程
        //管道写入端写入
        //子进程循环写入
        while(1){
            char* msg = "hello world";
            int len = write(pipefd[1], msg, strlen(msg));
            printf("send :%d , pid: %d\n", len, getpid());
            sleep(1);//sleep不然太快了
            

        }
    }

    return 0;
}
```



## 通过使用单向管道解决问题（关闭读取程序的写入端和写入程序的读取端）

```c
#include <unistd.h>
#include <sys/types.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

/*
*如果我们去掉了sleep(1)会有什么问题呢？
如果去掉了，那么可能子进程或者父进程执行了管道写入操作后，cpu没有切换至子进程。因为时间片太短了。
在写入操作后，因为没有切换至另一个进程，就会导致同一个进程在写入后又读取了对应管道的内容。这样就会产生自己写自己读的问题。
?问题在于，开发中不可以写sleep 怎么办呢？
其实一般情况下我们不会父子互相切换读写。所以这种情况不用特别考虑。
一般来说，如果是进程只进行单独的读操作或者写操作，我们可以把不需要的操作进行关闭
TODO  close(pipefd[0/1]);
*/

int main(){
    
    int pipefd[2]; // 创建管道数组
    int ret = pipe(pipefd); //创建管道

    if(ret == -1){ //如果管道创建失败
        perror("pipe error");
        exit(0);
    }

       //必须要在fork之前创建管道。因为fork才能将文件描述符复制给子进程，这样才可以通信
    pid_t pid = fork(); //创建子进程

    char buf[1024] = {0}; //! 缓冲区不能写在这。写在这的话进程共用一个而且不清除的话第二轮父进程读的时候因为里面有数据所以不会被阻塞

    if(pid > 0){ //fork返回的pid是子进程id。也就是在父进程中，这个数字一定是大于0的
        //父进程
        //char buf[1024] = {0};
        //从管道的读取端读取
        close(pipefd[1]); // 关闭父进程的写入操作
        while(1){

            //父进程循环读取数据。不用sleep因为默认是阻塞
            int len = read(pipefd[0], buf, sizeof(buf)); //! read函数默认是阻塞的。如果子进程没有写入到管道的话，父进程会一直等待子进程把数据写入管道。
            printf("father receive :%d , pid: %d, father pid: %d\n", len, pid, getpid());
            //printf(buf); 不要这样写。要按照下面去写。不要直接读变量，要按照字符串读写
            printf("%s\n", buf);
            bzero(buf, 1024); //如果缓冲区写在外面就必须要清零缓冲区
        }
    }
    else if(pid == 0){ //如果pid是0，代表现在切换进了子进程。
        //子进程
        //管道写入端写入
        //子进程循环写入
        //char buf[1024] = {0};
        close(pipefd[0]); // 关闭子进程的读取操作
        while(1){
            //写入
            char* msg = "hello world i'm child";
            int len = write(pipefd[1], msg, strlen(msg));
            printf("child send :%d , pid: %d\n", len, getpid());
            bzero(buf, 1024); //如果缓冲区写在外面就必须要清零缓冲区
        
        }
    }

    return 0;
}
```

