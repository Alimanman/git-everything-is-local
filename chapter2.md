# 进阶篇
---

## HEAD：当前 commit 的引用

- HEAD 是引用中最特殊的一个：它是指向当前 commit 的引用。
- HEAD 也会转而指向最新的 commit。
- HEAD 是 Git 中一个独特的引用，它是唯一的。

总之，当前 commit 在哪里，HEAD 就在哪里，这是一个永远自动指向当前 commit 的引用。

#### 所以你永远可以用 HEAD 来操作当前 commit。

## branch

Git 还有一种引用，叫做 branch（分支）。
HEAD 除了可以指向 commit，还可以指向一个 branch。
HEAD -> master 中的 master 就是一个 branch 的名字，而它左边的箭头 -> 表示 HEAD 正指向它。

另外，当 HEAD 在提交时自动向前移动的时候，它会像一个拖钩一样带着它所指向的 branch 一起移动。

![](https://user-gold-cdn.xitu.io/2017/11/20/15fd779f983c81e7?imageslim)

## master:默认 branch


