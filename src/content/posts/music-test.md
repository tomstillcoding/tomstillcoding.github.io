---
title: "网易云外链插入Jekyll博客教程和注意事项"
slug: "music-test"
published: 2022-05-01T02:50:00-05:00
description: ""
tags: ["生活"]
category: "随笔"
draft: false
typora-root-url: ../../../public
---

# 网易云外链插入Jekyll博客教程和注意事项

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="330" height="86" src="//music.163.com/outchain/player?type=2&amp;id=28723836&amp;auto=1&amp;height=66"> </iframe>

这里是教程：

首先找到网易云的外链生成，这里不多说了。生成了的外链大概长这样

```html
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86
        src="//music.163.com/outchain/player?type=2&id=28723836&auto=1&height=66"></iframe>
```

这里有几个雷区：

1：需要修改`width=330 height=86`为 `width="330" height="86"`

2：链接前面不要加http也不要加https，会自动解析。

3：最后面一个`<\iframe>`要和前面的`>`中间隔一个空格。

4：海外用户由于版权原因无法播放外链音频，表现形式为点不动。只能看见播放器。

修改后的链接大概长这样

```html
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="330" height="86"
        src="//music.163.com/outchain/player?type=2&id=28723836&auto=1&height=66"> </iframe>
```

