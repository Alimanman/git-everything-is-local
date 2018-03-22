# 高级篇
---

## rebase

有些人不喜欢 merge，因为在 merge 之后，commit 历史就会出现分叉，这种分叉再汇合的结构会让有些人觉得混乱而难以管理。如果你不希望 commit 历史出现分叉，可以用 rebase 来代替 merge。

```
git checkout branch1
git rebase master
```
![](https://user-gold-cdn.xitu.io/2017/11/30/1600abd620a8e28c?imageslim)

```
git checkout master
git merge branch1
```
![](https://user-gold-cdn.xitu.io/2017/12/2/160149e054fe485c?imageslim)

**rebase 指令，它可以改变 commit 序列的基础点。**

##




