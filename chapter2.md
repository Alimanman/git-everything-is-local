# 进阶篇
---

## HEAD：当前 commit 的引用

- HEAD 是引用中最特殊的一个。
- HEAD 也会转而指向最新的 commit。
- HEAD 是 Git 中一个独特的引用，它是唯一的。

总之，当前 commit 在哪里，HEAD 就在哪里，这是一个永远自动指向当前 commit 的引用。

#### 所以你永远可以用 HEAD 来操作当前 commit。

## branch

Git 还有一种引用，叫做 branch。
HEAD 除了可以指向 commit，还可以指向一个 branch。
HEAD -> master 中的 master 就是一个 branch 的名字，而它左边的箭头 -> 表示 HEAD 正指向它。

另外，当 HEAD 在提交时自动向前移动的时候，它会像一个拖钩一样带着它所指向的 branch 一起移动。

![](https://user-gold-cdn.xitu.io/2017/11/20/15fd779f983c81e7?imageslim)

## master:默认 branch

1. 所有的 branch 之间都是平等的。（branch 的本意是树枝，可以延伸为事物的分支）

![](https://user-gold-cdn.xitu.io/2017/11/20/15fd779ff346fbd7?imageslim)

2. branch 包含了从初始 commit 到它的所有路径，而不是一条路径。并且，这些路径之间也是彼此平等的。

![](https://user-gold-cdn.xitu.io/2017/11/22/15fe3354a1d3cd26?imageslim)

上图这样，master 在合并了 branch1 之后，从初始 commit 到 master 有了两条路径。这时，master 的串就包含了 `1 2 3 4 7` 和 `1 2 5 6 7` 这两条路径。而且，这两条路径是平等的，`1 2 3 4 7` 这条路径并不会因为它是「原生路径」而拥有任何的特别之处。

## 创建 branch

```
git branch 名称
```

## 切换 branch

```
git checkout 名称
```

**创建 + 切换**

```
git checkout -b 名称
```











