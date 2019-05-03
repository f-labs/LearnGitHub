# 给git分支重命名

* 第一步：修改本地分支

  使用命令：`git branch -m 要改的本地分支名 修改后的分支名`

```bash
$ git branch -m old-name new-name
```
  
* 第二步：删除远程分支

   使用命令：`git push origin :远程分支名(你要删除的远程分支名)`
   
```bash
$ git push origin :old-name
```

* 第三部：将本地分支 push 到远程分支上，如果远程分支不存在，则创建此远程分支

  使用命令：`git push origin 本地分支名（修改后的分支名）:远程分支名（修改后的分支名）`
  
```bash
$ git push origin new-name:new-name
```

  完成第三步，若进行提交时报错，可能需要执行第四步。

* 第四部：绑定远程分支

  我们的分支是基于 'origin/old-name' 建立的, 但是上游（upstream）已经不在了，使用 `git branch --unset-upstream`修正：

```bash
$ git branch --unset-upstream
```

  push当前分支并设置远程（remote）作为上游（upstream）
  

```bash
$ git push --set-upstream origin new-name
```

-----

## 远程分支删除以后，本地显示仍然存在的解决办法

显示所有分支：

```git branch -a```

执行下面命令查看远程分支和本地分支的对应关系：

```git remote show origin```

会看到：

``refs/remotes/origin/my_branch    stale (use 'git remote prune' to remove)``

执行下面命令同步删除：

```git remote prune origin```

或者

```git fetch -p```

再查看，就已经没有了：

```git remote show origin```

