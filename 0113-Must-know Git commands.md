参考[廖雪峰的教程](https://www.liaoxuefeng.com/wiki/896043488029600)，记录了一些Git常用指令。

### 【Help】

1. 初始化仓库：
   git init
2. 添加文件到Git仓库：
   step 1: git add <file>
   e.g. git add readme.txt
   step 2: git commit -m <message>
   e.g. git commit -m "added xxx"
3. 查看工作区状态（是否有修改、是否待commit、是否已commit）：
   git status
4. 查看修改内容：
   git diff <file>

### 【关于版本管理】

————已经commit到本地版本库————

5. 回到过去某个版本：
   git reset --hard <commit_id> (前几位数即可）
   回到最新版本：
   git reset HEAD <file.x>
6. 查看commit历史：
   git log
7. 查看命令历史：
   git reflog （用于找回“未来”）
   ————还未commit到本地版本库————
8. 丢弃工作区修改//让这个文件回到最近一次git commit或git add时的状态:
   git checkout -- <file>
9. 丢弃暂存区修改：
   git reset HEAD <file>

### 【关于删除文件】

1. 删除file（手动or rm test.txt）
2. 把变化添加到暂存区：
   git rm <file>
3. 把变化添加到版本库：
   git commit -m "remove xxx"

### 【本地->远程库】

1. 关联一个远程库: git remote add origin git@github.com:username/repo-name.git
2. 第一次推送master分支的所有内容：
   git push -u origin master
3. 推送最新修改：
   git push origin master

### 【远程->本地】

git clone git@github.com:username/repo-name.git

### 【分支-basics】*encouraged

1. 查看分支：git branch
2. 创建分支：git branch <name>
3. 切换分支：git checkout <name>或git switch <name>
4. 创建+切换分支：git checkout -b <name>或git switch -c <name>
5. 合并某分支到当前分支：
   git merge <name> 
   或 
   git merge --no-ff -m "merge with no-ff" dev （禁用Fast forward模式：保留分支信息）
6. 删除分支：git branch -d <name>

### 【分支-conflict】

1. 查看filename的内容：
   cat filename.x
   查看分支合并图：
   git log --graph --pretty=oneline --abbrev-commit
2. 解决conflict后addcommit

### [【分支-bug】](https://www.liaoxuefeng.com/wiki/896043488029600/900388704535136)

git stash
git stash pop
git cherry-pick <commit>

