## 基础
### 添加到暂缓区
`git add .`

### 提交到本地仓库
`git commit -m 'message'`

### 暂存
`git stash`  
`git stash save <message>`  
`git stash pop`   
`git stash apply <id>` 

`git stash drop <id>` 



## 仓库
### 初始化仓库
`git init`

### 克隆远程仓库(所有分支)
`git clone https://github.com/menng/learngit.git`

### 克隆远程仓库(指定分支)
`git clone -b <branch_name> https://github.com/menng/learngit.git`

### 远程仓库信息
`git remote -v`  
`git remote show/add/remove/rename <远程仓库>`

### 替换文件与当前版本保持一致
`git checkout -- <filename>`

### 替换当前工作目录与上次提交保持一致(重置)
`git reset --hard HEAD`  未被加入暂存区的文件还是会存在

## 分支
### 查看分支
`git branch -a/r/v`
`git branch -vv` 查看本地分支与远程分支关联关系

### 创建并切换分支
`git checkout -b <branch_name>`

### 分支重命名

`git branch -m <old_branch_name> <new_branch_name>`

### 基于tag创建分支
`git branch <new_branch_name> <tag_name>`

### 基于tag创建并切换到新分支

`git checkout -b <new_branch_name> <tag_name> `

### 获取远程分支
`git fetch origin`

`git checkout -b <local_branchname> <remote_branchname>`

### 更新本地分支与远端同步
`git pull -p`

`git remote prune <remote_repo_alias> `

`git remote prune -n/--dry-run <remote_repo_alias>`

### 删除远程分支
`git push origin :<branch_name>`  
`git push origin --delete <branch_name>`

### 覆盖本地当前分支
`git reset --hard <branch_name>`  
eg:  
`git reset --hard HEAD^1` 恢复到上次提交  
`git reset --hard`  重置本地修改  
`git reset --hard 98d3dde`  

### 比较两个分支
`git diff <branch_name> <other_branch_name>`  
eg:  
`git fetch origin`  
`git diff master origin/master`  
`git diff master dev`

### 比较分支与暂存区
`git diff --cached`

### 查看是否有空格等提交
`git diff --check`

### 查看两个版本的变更文件列表
`git diff <branch_name> <other_branch_name> --stat`
`git diff <branch_name> <other_branch_name> --name-only`
`git diff <branch_name> <other_branch_name> --name-status`

## 标签
### 查看所有标签

`git tag -n`

### 基于最新提交并创建轻量标签

`git tag <tagname>`

### 基于最新提交并创建附注标签
`git tag -a <tagname> -m <message>`

### 提交标签到远程
`git push origin <tagname>`

### 提交所有标签到远程
`git push origin --tags`

### 删除标签
`git tag -d <tagname>`

### 删除远程标签
`git push origin :<tagname>`

## 历史
### 查看历史
`git log -p -2` 显示最近两次提交的差异  
`git log --stat` 显示每次提交的简略统计信息  
`git log --pretty=oneline` 不同的风格展示提交历史  
`git log --pretty=format:"%h %an %ar - %s"` 格式化输出  
`git log --pretty=format:"%h %an %ar - %s" --graph` 图标格式化输出  
`git log --pretty=format:"%h %an %ar - %s" --graph -5` 图标格式化输出最近5次提交  

### 查看文件列表
`git log --name-status` 显示新增、修改、删除的文件清单 

`git log --name-only` 文件修改列表  
`git whatchanged` 文件修改列表

### 操作历史

`git reflog` 记录本地仓库的操作历史。



## 配置
### 定义别名
`git config --global alias.br branch`  
`git config --global alias.st status`  
`git config --global alias.ci commit`

`git config --global alias.ck checkout`

### 忽略换行符影响
`git config --global core.whitespace cr-at-eol`

### 配置日志别名
`git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"`



## 常见问题

### 1、撤销commit并保留之前修改

操作：

````
git reset --soft HEAD^/HEAD~1/<前一次的commitid>  撤销最近一次commit
git reset --soft HEAD^^/HEAD~2/<前两次的commitid> 撤销最近二次commit 等等
````

参数说明：

```
--mixed 不删除工作区改动代码，撤销commit，撤销git add .  (默认参数)
--soft  不删除工作区改动代码，撤销commit，不撤销git add .
--hard  删除工作区改动代码，撤销commit，撤销git add .
```

### 2、修改commit注释

```
git commit --amend 默认进入vim，修改注释完毕后保存即可。
```

### 3、恢复已经清除的stash内容

```
git log --graph --oneline --decorate  $(git fsck --no-reflog | awk '/dangling commit/ {print $3}')          查看stash历史
git stash apply xxxx  恢复最后stash的内容
```

### 4、.gitignore不起作用解决办法
```
git rm -r --cached .
git add .
git commit -m '更新 .gitignore'
```
说明：.gitignore只忽略那些原来没有被track的文件，如果某些文件已经被纳入了版本管理中，则修改.gitignore是无效的。清理之前提交的缓存，再次提交即可。


### 5、git reflog回到未来
```
git reflog 查看所有操作历史
```

## 参考

[Pro Git book](https://git-scm.com/book/zh/v2)

