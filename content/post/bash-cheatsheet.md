---
title: "Bash Cheatsheet"
date: 2019-09-02T21:19:38+08:00
tags: ["cheatsheet", "linux", "bash"]
categories: ["computer"]
---
| 快捷键 | 用途                      |
| ------ | ------------------------ |
| ctrl-c | 终止程序                  |
| ctrl-d | 退出login-shell[^1]       |
| alt-f  | 光标向右跳转，每次1个单词 |
| alt-b  | 光标向左跳转，每次1个单词 |
| ctrl-a | 光标跳转到开头            |
| ctrl-e | 光标跳转到最后            |
| ctrl-l | 🆑清除(重绘)屏幕           |
| ctrl-r | 🔍搜索命令行历史           |
| ctrl-g | 退出ctrl-r                |
|  sudo!!|  重新以sudo身份执行上一条命令|
|  ctrl-k| ✂️剪切从光标到命令行行末尾的所有内容 |
|  ctrl-u | ✂️剪切从光标到命令行最开始的所有内容 |
|  ctrl-y | 粘贴剪切内容(ctrl-k ctrl-u)|
|  ctrl-w|  ✂️剪切1个单词(word)|
|  ctrl-x-e(按住ctrl-x-e) |  在$EDITOR中打开命令行输入的内容[^2]|
|  alt-.(英文句号)|  粘贴上一条命令的参数[^3]|




[^1]: 在没有安装GUI界面(X-window)的\*nix系统上，第一次登陆时的shell就是login-shell
[^2]: 前提是在shell中设置了\$EDITOR. 如果是MacOS， 不要把$EDITOR设置为mvim
[^3]: 如果是在MacOS上使用iTterm2，按command+o -> EditProfiles -> Keys 把Option键改为ESC+后，Option健就可以当Alt使用

