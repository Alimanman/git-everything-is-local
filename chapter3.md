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

关于merge的建议：
如果你想要一个干净的，没有merge commit的线性历史树，那么你应该选择git rebase
如果你想保留完整的历史记录，并且想要避免重写commit history的风险，你应该选择使用git merge

---

## commit --amend

**可以修复最新 commit 的内容。**

更新刚提交了的commit，加上 --amend 参数，Git 不会在当前 commit 上增加 commit，而是会把当前 commit 里的内容和暂存区（stageing area）里的内容合并起来后创建一个新的 commit，用这个新的 commit 把当前 commit 替换掉。

```
git commit --amend
```

> 适用于已经commit但是没有push的内容。

---

## 修改更加之前的commit

### 1.回到需要的版本

```
git rebase -i HEAD^^
git rebase -i HEAD～5
```

- ^表示往回偏移数量，1个表示1位
- ～加数字，表示指定之前第几步

弹出窗口，这个排列是正序的，旧的 commit 会排在上面，新的排在下面。
把需要修改的 pick 修改成 edit 后退出。

### 2.修改内容
> 不能对同一个文件进行再修改。

```
git add .
git commit --amend
```

### 3.最后
```
git rebase --continue
```

---

## 直接丢弃commit

```
git reset HEAD^
git reset --hard HEAD^
git reset --soft HEAD^
```

- mixed 如果不加参数，那么默认使用 --mixed，保留工作目录，并且清空暂存区。
- hard 彻底回退到某个版本，本地的源码也会变为上一个版本的内容
- soft 保留工作目录的内容，只回退了commit的信息，可以重提commit

> 不过，撤销的那条提交并没有消失，只是你不再用到它了。如果你在撤销它之前记下了它的 SHA-1 码，那么你还可以通过 SHA-1 来找到他它。

#### reset 指令的本质：重置 HEAD 以及它所指向的 branch 的位置。

这样也可以噢
```
git reset --hard branch2
```
![](https://user-gold-cdn.xitu.io/2017/11/22/15fe333cb605b0de?imageslim)

## 删除指定位置的commit

```
git rebase -i HEAD^^
```

弹出窗口，这个排列是正序的，旧的 commit 会排在上面，新的排在下面。
直接删除记录（不用把 pick 修改成 edit）
搞定！

还可以使用`git rebase --onto`删除指定位置的commit。

```
git rebase -i HEAD
```

在非--hard下，回到上次提交时的状态

---

## 如果已经push

1.需要撤销的在私有barnch

```
git push origin branch1 -f
```
>只建议在私有branch上使用，master下慎用。

2.需要撤销的master

```
git revert HEAD^
```
>如果出错内容在 master：不要强制 push，而要用 revert 把写错的 commit 撤销。

---

## branch改了一半，需要master内容。

无需在branch上commit后再撤回

只需要在branch下保存
```
git stash
```

其他弄好后，再回到branch提取
```
git stash pop
```

---

## reflog 起死回生技

```
git reflog
git reflog master
```

## .gitignore

这个文本文件记录了所有你希望被 Git 忽略的目录和文件。

```
touch .gitignore
```

**.gitignore设置**

```
# 过滤整个sass文件夹及其内容
sass/

# 只过滤根目录sass文件夹及其内容
/sass

# 过滤.gitignore自身
.gitignore

# 过滤所有zip
*.zip

# 过滤所有xls
*.xls

# checksheet.xls除外
!checksheet.xls
```

.gitignore 规则只能作用于 Untracked Files，也就是那些从来没有被 Git 记录过的文件，从未 add 及 commit 过的文件。
如果被 add 及 commit 过的文件，就算之后再设置过滤，也会被侦测到的。