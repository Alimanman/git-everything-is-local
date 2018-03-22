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

1. 在新branch下commit，HEAD 就会带（跟）着新的 branch 移动了
2. 如果你再切换到 master 去 commit，就会真正地出现分叉了

![](https://user-gold-cdn.xitu.io/2017/11/22/15fe3354ab0861a7?imageslim)

## 删除 branch

```
git branch -d 名称
```

1. HEAD 指向的 branch 不能删除。
2. branch 只是一个引用，所以删除 branch 的操作也只会删掉这个引用，并不会删除任何的 commit。
如果一个 commit 不在任何一个 branch上，就是野生commit，当然不用担心，在一定时间后，它会被 Git 的回收机制删除掉。
3. 没有被合并到 master 过的 branch 在删除时会失败。
如果非要删除，可以把 -d 改成 -D，小写换成大写，就能删除了。

![](https://user-gold-cdn.xitu.io/2017/11/29/16006b7e3d35fe54?imageslim)

## HEAD、master、branch小结

1. HEAD 是指向当前 commit 的引用，它具有唯一性，每个仓库中只有一个 HEAD。在每次提交时它都会自动向前移动到最新的 commit 。
2. branch 是一类引用。HEAD 除了直接指向 commit，也可以通过指向某个 branch 来间接指向 commit。当 HEAD 指向一个 branch 时，commit 发生时，HEAD 会带着它所指向的 branch 一起移动。
3. master 是 Git 中的默认 branch，它和其它 branch 的区别在于：
 1. 新建的仓库中的第一个 commit 会被 master 自动指向；
 2. 在 git clone 时，会自动 checkout 出 master。
4. branch 的创建、切换和删除：
 1. 创建 branch 的方式是 git branch 名称 或 git checkout -b 名称（创建后自动切换）；
 2. 切换的方式是 git checkout 名称；
 3. 删除的方式是 git branch -d 名称。

---

## push 的本质

1. push 是把当前的分支上传到远程仓库，并把这个 branch 的路径上的所有 commits 也一并上传。
![](https://user-gold-cdn.xitu.io/2017/11/29/1600725e9973f71d?imageslim)

2. push 的时候，如果当前分支是一个本地创建的分支，需要指定远程仓库名和分支名，用 git push origin branch_name 的格式，而不能只用 git push。

   ```
   git push origin 名称
   ```

3. push 的时候之后上传当前分支，并不会上传 HEAD；远程仓库的 HEAD 是永远指向默认分支（即 master）的。
![](https://user-gold-cdn.xitu.io/2017/11/29/160073ccda56ef07?imageslim)

---

## merge 合并

merge 的含义：从两个 commit「分叉」的位置起，把目标 commit 的内容应用到当前 commit（HEAD 所指向的 commit），并生成一个新的 commit。

 ![](https://user-gold-cdn.xitu.io/2017/11/21/15fddc2aad5a0279?imageslim)

 ```
 git checkout HEAD 所指向的 commit
 git merge 目标 commit
 ```
 
1. 如果一个分支改了 A 文件，另一个分支改了 B 文件，那么合并后就是既改 A 也改 B，这个动作会自动完成；如果两个分支都改了同一个文件，但一个改的是第 1 行，另一个改的是第 2 行，那么合并后就是第 1 行和第 2 行都改，也是自动完成。
 
2. 如果两个分支修改了同一部分内容，会产生冲突（Conflict）。

   手动改冲突并commit一下，在这种状态下 commit，Git 就会自动地帮你添加「这是一个 merge commit」的提交信息。
   
   放弃合并：`git merge --abort`
   
3. HEAD 领先于目标 commit， Git 什么也不会做，merge 是一个空操作。
   （也不知道怎么遇到这种情况。。。
   ![](https://user-gold-cdn.xitu.io/2017/11/21/15fddc2b2357b9d9?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

4. HEAD 落后于 目标 commit
   地的 master 没有新提交，而远端仓库中有同事提交了新内容到 master。
   ![](https://user-gold-cdn.xitu.io/2017/11/21/15fddc2b46c69d46?imageslim)
   
---

## Feature Branching

这种工作流的核心内容可以总结为两点：

1. 任何新的功能（feature）或 bug 修复全都新建一个 branch 来写；
2. branch 写完后，合并到 master，然后删掉这个 branch。

![](https://user-gold-cdn.xitu.io/2017/11/21/15fde6edbfe362c4?imageslim)

## Pull Request

Pull Request 并不是 Git 的内容，而是一些 Git 仓库服务提供方（github和bitbucket都是这个功能）所提供的一种便捷功能，它可以让团队的成员方便地讨论一个 branch ，并在讨论结束后一键合并这个 branch 到 master。

流程
1. 点击提交分支Pull Request
2. 同意合并分支
3. 合并后删除分支（建议）

---

## git log

1. 查看历史中的多个 commit：log
   1. 查看详细改动： git log -p
   2. 查看大致改动：git log --stat
   
2. 查看具体某个 commit：show
   1. 要看最新 commit ，直接输入 git show ；要看指定 commit ，输入 git show commit的引用或SHA-1
   2. 如果还要指定文件，在 git show 的最后加上文件名

3. 查看未提交的内容：diff
   1. 查看暂存区和上一条 commit 的区别：git diff --staged（或 --cached）
   2. 查看工作目录和暂存区的区别：git diff 不加选项参数
   3. 查看工作目录和上一条 commit 的区别：git diff HEAD














