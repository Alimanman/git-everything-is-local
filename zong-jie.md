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

* **本地直接创建仓库**  
  0. GitHub或Bitbucket新建仓库；  
  1. 本地文件夹目录下`git init`生成`.git`本地仓库。  
  2. 放入需要提交的文件；  
  3. `git add .`添加追踪文件；  
  4. `git commit -m "first commit"`提交暂存和填写提交信息；  
  5. `git remote add origin <git http>`添加远程仓库别名为origin；  
  6. `git push -u origin master`提交中央仓库并新建master作为默认，之后可以直接`git push`提交。

* **中央服务器获取（推荐）**  
  0. GitHub或Bitbucket新建仓库；  
  1. `git clone <git http>`  
  2. 放入需要提交的文件；  
  3. `git add .`添加追踪文件；  
  4. `git push`直接提交。

## 查看状态

文件有新建、更新、删除都可以监测到。

`git status`

## 查看提交历史

历史内容很多的情况下，按q退出。

```
git log
```

查看详细历史

```
git log -p
```

查看最新一条commit具体的commit

```
git show
```

查看指定commit ID具体的commit

```
git show <commit ID>
```

只显示一行注释信息

```
git config format.pretty oneline
```

## clone

自定义clone下来的仓库文件名

`git clone <git http> <file name>`

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

HEAD是最新commit的引用，^表示返回上一个版本，^^表示返回之前第二个版本，以此类推。  
也可以使用HEAD~n来返回，例HEAD~2。  
或者直接使用commit ID，返回到指定的版本。

> 如果要再返回（ctrl+y），可以使用commit ID来实现。

**1. mixed，保留工作目录，清空add，清空commit。**
文件始终保持最新版，不会随着版本变化而变化。一般使用在撤回add和commit后，重新提交add和commit用。

```
git reset HEAD^
```

**2. soft，保留工作目录，保留add，清空commit。**
文件始终保持最新版，不会随着版本变化而变化。一般使用在撤回commit后，重新commit用。

```
git reset --soft HEAD^
```

**3. hard，清空工作目录，清空add，清空commit。**
随着版本变化，文件也会变化，适用于恢复历史版本或者找回误删的文件。

```
git reset --hard HEAD^
```

> 以上HEAD同样可以使用branch名实现

例：
```
git reset master^^
git reset master~5
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

> `git push` 等于 `git push origin master`，因为通过`-u`设定了一个默认主机。

恢复历史版本

如果是reset --hard恢复历史版本，需要加-f强制push。

```
git push -f origin <branch>
git push -f
```

## 过滤不想上传的内容

```
touch .gitignore
```

**.gitignore设置**

```
# 过滤整个sass文件夹及其内容
sass/

# 过滤.gitignore自身
.gitignore

# 过滤所有zip
*.zip

# 过滤所有xls
*.xls
```

---

## 协作开发

## 只用一个branch

1. 写完所有的 commit 后，不用考虑中央仓库是否有新的提交，直接 push 就好
2. 如果 push 失败，就用 pull 把本地仓库的提交和中央仓库的提交进行合并，然后再 push 一次

## 多branch同步开发

大多数的开发团队会规定开发以 master 为核心，所有的分支都在一定程度上围绕着 master 来开发。

**现今主流的工作流**

1. Feature Branching
2. Git Flow

## Feature Branching

**这种工作流的核心内容**

1. 任何新的功能或 bug 修复全都新建一个 branch 来写；
2. branch 写完后，合并到 master，然后删掉这个 branch（本地和远程）。

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
git branch -d <new branch>
git push origin -d <new branch>
```

在你创建仓库的时候，master被“默认”创建。  
我就是叛逆不喜欢master这个名字，如何改名...

```
git branch -m <old name> <new name>
```

## 合并

* **merge**  
  1. 上传分支branch到中央仓库`git push origin <new branch>`；  
  2. 本地切换到`git checkout master`；  
  3. 合并`git merge <new branch>`；  
  4. `git push`；  
  5. 删除本地和远程的分支branch。

* **Pull Request\(推荐\)**  
  1. 上传分支branch到中央仓库`git push origin <new branch>`；  
  2. GitHub或Bitbucket页面点击Pull Request按钮；  
  3. 本地切换到`git checkout master`；  
  4. `git remote prune origin`清理远程分支，`git branch -d <new branch>`删除本地分支。

## 临时存放工作目录的改动

1. 必须先添加文件追踪`git add .`；
2. 在分支branch下，`git stash`；
3. 回到master，要干啥干啥。master的活儿干好了；
4. 切换回分支branch下，`git stash pop`。

## 给重要的版本添加tag

显示所有标签

```
git tag
```

commit时添加标签

```
git tag <tag name>
```

补打标签

```
git tag <tag name> <commit ID>
```

删除标签

```
git tag -d <tag name>
```

提交到中央仓库

```
git push --tags
```

通过标签切换版本

```
git reset --hard <tag name>
git checkout <tag name>
```

checkout和reset的最大区别之一就是，checkout后HEAD指向了一个没有分支名字的修订版本,已经处于游离状态了\(detached HEAD\)。  
checkout可以快速切换各个版本，因为没有分支名所以无法commit（安全）。  
可以通过`git checkout master`快速切换回最新版。

---

## vscode终端默认Git Bash

```	
"terminal.integrated.shell.windows": "C:\\Program Files (x86)\\Git\\bin\\bash.exe"
```


## 阅读

* [http://www.bootcss.com/p/git-guide/](http://www.bootcss.com/p/git-guide/)
* [https://www.gitbook.com/book/bingohuang/progit2](https://www.gitbook.com/book/bingohuang/progit2)



