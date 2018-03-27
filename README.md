# 《Git 原理详解及实用指南》学习笔记
---

好记性不如烂笔头，边学边打代码边记录。

https://juejin.im/book/5a124b29f265da431d3c472e

## Git的学习曲线

![](https://user-gold-cdn.xitu.io/2017/10/24/38882ef09a324d15d99b3610fe01809d?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

**易学难精！**
想上手很容易，只要学会 commit、push、pull 等几个指令，就能够初步地使用它；但如果想要更进一步，让自己能够在团队项目中和朋友或同事自由合作，却又很难。

#### 学习目标：真正做到不仅会用git，还要了解其概念和原理。

---

## Git介绍

> Git 是一个分布式版本控制系统（Distributed Version Control System - DVCS）

我们生活中最常见的版本控制 - ctrl+z

## VCS与分布式VCS的区别

- VCS：**保存版本历史**、**同步团队代码**，全部服务器仓库负责。

- 分布式VCS：每个团队成员的本地仓库负责**保存版本历史**，服务器仓库主要负责**同步团队代码**。

- VCS版本历史都在中央仓库，分布式VCS的版本历史在中央仓库和本地仓库（.git）都有。

## 分布式VCS的优缺点

### 优点

- 大多数的操作可以在本地进行，而且由于无需联网，你也可以提交代码、查看历史；

- 由于可以提交到本地，所以你可以分步提交代码，把代码提交做得更细。

### 缺点

- 由于每一个机器都有完整的本地仓库，所以初次获取项目的时候会比较耗时。所以包含大素材类不建议使用；

- 由于每个机器都有完整的本地仓库，所以本地占用的存储比中央式 VCS 要高。


