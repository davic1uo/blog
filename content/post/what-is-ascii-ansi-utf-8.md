---
title: "不同编码的区别"
date: 2019-08-31T21:21:41+08:00
tags: ["conputer-base"]
categories: ["computer"]
---
# 编码标准

编码标准好比网络协议。会制定一些规则。常见的编码标准有`ANSI` `ASCII` `Unicode`等。在每个编码标准下，都有自己的字符集`code set` 字符集就好比莫斯代码表，规定字符编码的样式。

# ASCII
最早的编码标准，计算机刚问世时，只支持英语。因此ASCII是为英语量身打造的，它使用1字节来表示一个字符。(实际只用了7位,因此ASCII一共只表示128个字符)
比如0x0d=<CR>回车 0x0a=<LR>换行
**由于ASCII的编码标准和字符集名称相同，所以ASCII即代表字符集也代表编码协议**

# ANSI
> ANSI标准只用在Windwos中

由于Windwos的流行，对其他语言版本的Windows的需求也越来月急迫。为了解决这个问题，延伸出了**针对不同国家的字符集**

不同的国家或地区开始为自己用的字符编码，比如欧洲把ASCII剩余的编码用来表示带声调的字符。比如(é、ä、Ö ö、Ü ü、ß)的`扩展字符集` 中文简体的双字节编码`GB2312` 中文繁体的`Big-5`等等。

微软将这些编码封装了一层，也就是`ANSI`编码。它根据Windows上的CodePage值来使用具体的字符集。比如CodePage936=GBK(Win95之前表示GB2312), CodePage950=Big-5

可以通过在`cmd`命令行中输入`chcp 936`将默认的ASCII编码切换为GBK(chcp=change code page)

[更多](https://blog.csdn.net/imxiangzi/article/details/77370160)

# Unicode
由于ANSI是每一个国家或地区一个编码标准。不如全世界都用一个编码标准通用性强。所以Unicode就是全世界的编码标准。但是它并未规定字符与编码之间的映射关系(code set 未定义)
而`utf-8` `utf-16` 则是在Unicode标准下的code set

