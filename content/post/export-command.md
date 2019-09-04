---
title: "关于export命令""
date: 2019-09-04T19:53:46+08:00
tags: ["shell", "bash"]
categories: ["computer"]
---
# 关于export命令

`export`命令是在POSIX定义了的: [export is defined in POSIX](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#export)定义中说

> export - set the export attribute for variables

字面上理解是给变量(variable)设置*对外的属性*(export attribute). 在网上搜索export命令的作用, 都会有"设置环境变量"这个答案. *export attribute*和环境变量的目的我觉得其实是类似的.

假如在网上搜索"如何设置shell环境变量"时, 答案可能大概有这几种(假如要设置环境变量\$JAVA_HOME:

1. 直接在shell中执行`export JAVA_HOME=/opt/jdk/jdk1.8.0_161`
2. 在/etc/profile中添加`export JAVA_HOME=/opt/jdk/jdk1.8.0_161`
3. 在~/.bash_profile中添加`export JAVA_HOME=/opt/jdk/jdk1.8.0_161`

三种方式都可以设置\$JAVA_HOME环境变量.我的问题是, 既然写在文件里可以设置环境变量,那么执行(1)会把`export JAVA_HOME=/opt/jdk/jdk1.8.0_161`写到哪个文件去?

假如只执行(1)之后,如果再去查看`~/.bash_profile`和`/etc/profile`会发现里面并没有刚刚执行的内容.

**这是由于export 并不向任何文件写内容.它的目标是当前进程的内存.**

/etc/profile文件是针对**所有用户**的login shell[^1]的配置文件.仅能被login shell读取.当l读取这个文件时,export的变量对所有用户都生效.

~/.bash_profile[^2]是针对**具体用户**的login shell的配置文件

另外需要注意的是**所有在shell中执行的命令都是当前shell的子进程**. 所以自然地也就继承了主shell export的变量

[^1]: login shell 由很多种, 比如 [bash](https://bash.cyberciti.biz/guide/Bash), [ksh](https://bash.cyberciti.biz/guide/Ksh), [sh](https://bash.cyberciti.biz/guide/Sh)
[^2]: 当login shell是bash时
