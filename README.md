## 常用
### 克隆远程仓库
```git clone https://github.com/ConciseA/learngit.git```

### 获取远程分支
```git checkout -b local_branchname origin/remote_branchname```

### 覆盖本地当前分支
```git reset --hard branch_name```

### 比较两个分支
```git diff branch_name other_branch_name```  
eg:  
```git fetch origin```  
```git diff master origin/master```  
```git diff master dev```

### 查看所有标签
```git tag```

### 基于最新提交并创建标签
```git tag <tagname>```

### 删除标签
```git tag -d <tagname>```

## 小技巧
### 忽略换行符影响
```git config --global core.whitespace cr-at-eol```