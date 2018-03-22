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

## commit --amend

**可以修复最新 commit 的内容。**

更新刚提交了的commit，加上 --amend 参数，Git 不会在当前 commit 上增加 commit，而是会把当前 commit 里的内容和暂存区（stageing area）里的内容合并起来后创建一个新的 commit，用这个新的 commit 把当前 commit 替换掉。

```
git commit --amend
```

> 适用于已经commit但是没有push的内容。





