---
title: "Shell 常见配置文件"
date: 2019-09-04T19:49:34+08:00
tags: ["shell"]
categories: ["computer"]
---
在进行个性化shell配置的时候, 经常会遇到许多配置文件, 很容易混乱.这里梳理一下关于shell的配置文件.

-  ~/.bashrc

  针对不同用户的bash配置

- ~/.bash_profile

  用于login shell的系统初始化文件(主要是环境变量)

- /etc/profile

  针对所有用户的login shell的配置文件

- /etc/bashrc

  所有用户的bash配置(主要是环境变量).会被~/.bashrc读取

  ```bash
  # ~/.bashrc
  if [ -f /etc/bashrc ]; then
          . /etc/bashrc
  fi
  ```

---

配置文件的主要区别在

1. login shell 还是 interactive-shell
2. 是属于系统的还是属于个人用户的

**login shell**

类似\*profile的文件都是属于被login shell所使用. 比如 `~/.profile` `~/.bash_profile`

> 这些文件只在系统登陆时(login shell)被读取

**interactive shell**

基本上所有的\*rc文件都是用于交互式shell的配置文件. 比如`~/.bashrc` `~/.zshrc` 

> 这些文件会每次在程序启动时被读取

[stackoverflow 上的回答](https://stackoverflow.com/questions/415403/whats-the-difference-between-bashrc-bash-profile-and-environment )

**/etc属于系统**

/etc/下的配置文件几乎都是属于系统的配置文件, 而在/home下(~)的配置文件则是属于个人用户的
