### Git Revert
取反，对某次 commit 反向操作。
比如 上次commit 中 添加了一个文件， revert 就是 把这个文件删掉

### Git Log
查看提交日志（关键点 哈希数字）

### Git Reflog
查看历史操作日志，找到关键节点的标示 能用于恢复操作。

### Git Reset
写完代码后，我们一般这样
1. `git add . `//添加所有文件
2. `git commit -m "本功能全部完成"`

执行完commit后，想撤回commit，怎么办？

1. `git reset 用于撤销 commit`
2. `git reset --soft HEAD^`

> --mixed 
意思是：不删除工作空间改动代码，撤销commit，并且撤销git add . 操作
这个为默认参数,git reset --mixed HEAD^ 和 git reset HEAD^ 效果是一样的。
相当于 删除了 commit的日志记录，把文件修改为 待 添加状态。常用

> --soft  
不删除工作空间改动代码，撤销commit，不撤销git add .
相当于 删除了 commit的日志记录，把文件修改为 已 添加状态
 
> --hard
删除工作空间改动代码，撤销commit，撤销git add . 
注意完成这个操作后，就恢复到了上一次的commit状态。
---

`git reset` 和 `git Reflog` 配合使用 能恢复误操作导致的文件丢失问题。
`git reflog` 查找到 误操作的 编号。
`git reset` 到指定编号

> 1111 commit ”bad commit“

>2222 commit ”mormal Commit“

1111 是 错误的提交，想要撤回，只需要 `git reset 2222` 即可。
回退到指定版本。


### Git Stash
暂存功能
有些文件正在修改，但是有一些紧急的事情要切换 分支。可以先把这些文件 git stash 暂存到暂存区。
待再次切换到该分支时，

1. `git stash list` 查看暂存的标签
2. `git stash apply` 恢复，但是恢复后，stash内容并不删除，你需要用`git stash drop`来删除；
3. `git stash pop`，恢复的同时把stash内容也删了
4. `git stash apply stash@{0}`指定恢复 

