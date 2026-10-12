---
title: "太脑瘫了！"
slug: "new"
published: 2022-04-30T05:34:00-05:00
description: ""
tags: ["生活"]
category: "随笔"
draft: false
typora-root-url: ../../../public
---

# 折腾了五个小时发现为什么不能部署了 

这里每次部署都会弹出来

```c++
remote: Permission to Sterben-01/Sterben-01.github.io.git denied to github-actions[bot]. 
fatal: unable to access https://github.com/Sterben-01/Sterben-01.github.io/: The requested URL returned error: 403 
Error: Process completed with exit code 128.
```

结果折腾了五个小时偶然间发现我的仓库的Workflow permission 是tm只读的。赶紧改过来了。

![微信图片_20220430053643](/assets/blog_res/2021-04-30-new.assets/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20220430053643.png)