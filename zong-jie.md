# 总结
---

## 初始化信息

登录
```
git config --global user.name <name>
git config --global user.email <email>
```

查看
```
git config --global user.name
git config --global user.email
```

## 创建新仓库

- **本地直接创建仓库**
  0. GitHub或Bitbucket新建仓库；
  1. 本地文件夹目录下`git init`生成`.git`本地仓库。
  2. 放入需要提交的文件；
  3. `git add .`添加追踪文件；
  4. `git commit -m "first commit"`提交暂存和填写提交信息；
  5. `git remote add origin <git-http>`添加远程仓库别名为origin；
  6. `git push -u origin master`提交中央仓库并新建master作为默认，之后可以直接`git push`提交。
  
- **中央服务器获取（推荐）**
  0. GitHub或Bitbucket新建仓库；
  1. `git clone <git-http>`
  2. 放入需要提交的文件；
  3. `git add .`添加追踪文件；
  5. `git push`直接提交。

## 查看状态

文件有新建、更新、删除都可以监测到。 

`git status`

## 查看提交历史

内容很长情况下，按q退出。

```
git log
```

查看详细历史

```
git log -p
```

查看具体的 commit

```
git show
```



## clone

自定义clone下来的仓库文件名

`git clone <git-http> <file-name>`

## add

除了方便的`git add .`，也可以自定义需要提交的文件。

```
git add <file name> <file name>

```

## commit

进入编辑器模式，i进入输入模式，完成后ese+ZZ退出编辑器。

```
git commit
```

快捷写法

```
git commit -m "<message>"
```

## 撤回

HEAD只想最新commit的引用，^表示返回上一个版本，^^表示返回之前第二个版本，以此类推。
也可以使用HEAD~n来返回，或者直接使用commit ID。

> 如果要再返回（ctrl+y），可以使用commit ID来实现。

**1. mixed，保留工作目录，清空add，清空commit。**

```
git reset HEAD^
```

**2. soft，保留工作目录，保留add，清空commit。**

```
git reset --soft HEAD^
```

**3. hard，清空工作目录，清空add，清空commit。**

```
git reset --hard HEAD^
```

## push

标准写法

```
git push origin <branch>
```

快捷写法

```
git push
```

如果是reset --hard恢复历史版本

```
git push -f origin <branch>
git push -f
```

`git push` 等于 `git push origin master`，因为通过`-u`设定了一个默认主机。

## branch

1. `git branch`查看本地所有分支
2. `git branch -r`查看远程所有分支
3. `git branch -a`查看本地和远程所有分支

**新建并切换到新的branch**

```
git checkout -b <branch>
```

**提交到中央仓库**

```
git push origin <branch>
```

**切换当前barnch**

```
git checkout <branch>
```

**删除branch**

```
git branch -d <本地 branch>
git push origin -d <远程 branch>
```

在你创建仓库的时候，master被“默认”创建。
我就是叛逆不喜欢master这个名字，如何改名...

```
git branch -m <old name> <new name>
```

---

## 协作开发

大多数的开发团队会规定开发以 master 为核心，所有的分支都在一定程度上围绕着 master 来开发。

## 合并

- merge
- Pull Request
















http://www.bootcss.com/p/git-guide/
https://www.gitbook.com/book/bingohuang/progit2






