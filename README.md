## 常用

### 替换文件与当前版本保持一致
```git checkout -- <filename>```

### 创建并切换分支
```git checkout -b <branch_name>```

### 克隆远程仓库
```git clone https://github.com/ConciseA/learngit.git```

### 每一个分支的最后提交
```git branch -v```

### 查看远程分支
```git branch -a```

### 获取远程分支
```git checkout -b <local_branchname> <remote_branchname>```

### 删除远程分支
```git push origin :<branch_name>```
```git push origin --delete <branch_name>```

### 覆盖本地当前分支
```git reset --hard <branch_name>```

### 比较两个分支
```git diff <branch_name> <other_branch_name>```  
eg:  
```git fetch origin```  
```git diff master origin/master```  
```git diff master dev```

### 查看所有标签
```git tag```

### 基于最新提交并创建标签
```git tag <tagname>```

### 提交标签到远程
```git push origin <tagname>```

### 删除标签
```git tag -d <tagname>```

### 删除远程标签
```git push origin :<tagname>```

## 小技巧
### 定义别名
```git config --global alias.br branch```
```git config --global alias.st status```
```git config --global alias.ci commit```

### 忽略换行符影响
```git config --global core.whitespace cr-at-eol```

### 配置日志别名
```git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"```
