# git push -u origin master

在现实开发中，可能存在这样的情况，我们的同一套代码（或文档）需要push（推送）到不同的远程仓库，这时我们就可以进行分支管理，利用命令 `git push -u <远程主机> <当前分支>` 将当前分支的内容推送到指定的远程主机上去。例如我现在想要把本地 `gh-pages` 分支的内容，推送到另外一个指定的远程库取，即下面的远程库 `fc`，则具体操作如下：

* 第一步：配置远程仓库

  `origin` 是远程仓库的别名，我们也可以用其他自取名字代替，例如`fc`，代替了远程仓库的地址`xxx.git`，如下
  
  ```bash
  git remote add fc https://github.com/f-labs/Cryptoeconomics.git
  ```
  
  这样就把远程仓库 `https://github.com/f-labs/Cryptoeconomics.git` 用 `fc` 代替了。
  
* 第二步：push 到指定仓库

  那么 `fc` 便是我们指定的远程库，那么这个指定的动作由 `-u` 指令来完成：
  
  ```bash
  git push -u fc gh-pages
  ```
  
  这样我们就把本地的分支 `gh-pages` 上的内容推送到了远程 `fc` 上，并同时在 `fc` 上创建了一个叫 `gh-pages` 的分支来保存内容。
  
**注意：为了简单起见，我们在此前的 `fc` 远程库上并没有一个叫 `gh-pages` 的分支，因为若是存在同名分支，可能需要解决其他合并问题。**

-----
### git push origin与git push -u origin master的区别

`git push origin`将当前分支推送到 `origin` 主机的对应分支，一般情况下，我们的当前分支都只有一个追踪分支，即一个默认远程主机 `origin`，所以我们`git push`的时候省略了主机名。

`$ git push -u origin master` 将本地的`master`分支推送到`origin`主机，同时指定`origin`为默认主机。如果当前分支与多个主机存在追踪关系，那么这个时候`-u`选项会指定一个默认主机，这样后面就可以不加任何参数使用`git push`。

这里的`origin`是远程仓库的别名，`master`是本地分支别名，均可以替换为其他自取的对应主机或分支的别名。

---
git远程仓库分支的各命令的具体解析(git remote add)
https://blog.csdn.net/wq6ylg08/article/details/89028412
