---
title: "Tmux Cheetsheet"
date: 2019-09-04T19:57:36+08:00
tags: ["cheatsheet"]
categories: ["computer"]
---
# tmux cheatsheet

[TOC]

### Overview

tmux 可以划分为三个部分.

1. session
2. window
3. pane

每当在终端中输入`tmux` 命令后, 会进入一个`session` 中的一个`window`的1个`pane`中.这三个名词有点像集合.

$$ pane \subset window \subset session $$

**session**

可以有1个或多个`window` 

**window**

可以有1个或多个`pane`

---

进入`session`中, ==所有的命令都是通过`bind-key` + `cmd` 的形式才可以生效==. 默认的`bind-key` 是**Ctrl-b** (Ctrl 和 b)也许经常按**Ctrl-b**很不习惯. 可以在`~/.tmux.conf`中修改为自己喜欢的`bind-key`

```bash
vim ~/.tmux.conf
unbind C-b    # 取消原来的bind-key 
set-option -g prefix M-y    # 设置新的bind-key为Alt-y
```

>  如果映射键盘上的`Windows`键或者其他的键, 却又不知道按键的编码, 可以在有GUI的Linux系统中运行`xev` 命令,然后按下相应的键, 就会显示对应的按键代码

### 从普通终端进入tmux

安装好tmux后, 可以直接在终端中输入:

```bash
tmux
```

就可以进入tmux.这会让tmux打开一个新的session并且session的名称是默认的. 如果想在新建时, 给它起一个名称, 可以用下面的命令:

```bash
tmux new -s tmux1 
```

将会建立一个名称为tmux1的session.

### Session

进入tmux的session后, 就可以使用快捷键了. 与session相关的常用快捷键有👇

|   快捷键 | 用途        |
| -------: | :---------- |
| C-b :new | 新建session |
|  C-b :new -s tmux2 | 新建名为tmux2的session|
|  C-b s|  列出已存在的session|
|  C-b $ |   重命名当前session|
|  C-b d|  断开(detach)与当前session的连接|
|  C-b ( |  进入前一个session|
|  C-b ) |  进入后一个session|

### Window(Tab)

tmux的window就像浏览器上的页签(Tab). 关于Window的常用快捷键有👇

| 快捷键 | 用途                  |
| -----: | :-------------------- |
|  C-b c | 在session中新建window |
|  C-b & |  关闭当前window|
|  C-b w|  列出当前session的所有window|
|  C-b n|  进入下一个(next)window|
|  C-b p |  进入上一个(previous)window|
| C-b ,  |  重命名当前window|
|  C-b f  |  在所有window中的查找内容|
| C-b '  | 按照索引查找window|
| C-b  num(0-9的数字) |  进入索引号为num的window|

### Pane(split)

tmux的面板(pane)像vim里的split窗口. 关于pane的快捷键有👇

| 快捷键 | 用途     |
| -----: | -------- |
|  C-b % | 垂直分割 |
|  C-b " |  水平分割|
|  C-b o |  切换光标到其他pane中|
|  C-b 方向键|  切换光标到其他pane中|
|  C-b q| 显示每个pane的序号, 此时按序号可进入对应的pane|
| C-b x| 关闭pane|
| C-b 空格 | 重置pane布局(内置预设布局)|
| C-b ! |  使pane变为window|
| C-b { |  左移pane|
| C-b } | 右移pane|
| C-b z| 最大化当前pane(再按一次恢复)|

#### 同步使用所有Pane

如果想让所有pane同时接收键盘上的输入, 可以在某一个pane中输入Ctrl-b 然后按下冒号(:)会进入tmux命令行,然后输入

```bash
:setw synchronize-panes
```

将开启同步pane模式, 再执行一次该命令则会关闭. [演示](https://sanctum.geek.nz/arabesque/sync-tmux-panes/)

#### 改变pane大小
|       按键 | 作用            |
| ---------: | --------------- |
| Ctrl-b M-↑ | 向上增加5个单位 |
| Ctrl-b M-↓ | 向下增加5个单位 |
| Ctrl-b M-← | 向左增加5个单位 |
| Ctrl-b M-→ | 向右增加5个单位 |

M键代表Alt

也可以自定义长度移动, 按Ctrl-b再按冒号(:)进入命令模式

```bash
:resize-pane -R 20  # 向右扩展20个单位
:resize-pane -L        # 向左扩展1个单位
:resize-pane -U        # 向上扩展1个单位
:resize-pane -D        # 向下扩展1个单位

:resize-pane -t 2 -R 20 # 将2号pane向右扩展20个单位
```





