# 1
`pwd` print working directory
# 2
`git init`  初始化仓库
# 3 git add & commit
`git add file2.txt file3.txt`  
`git commit -m "wrote a readme file"`  
git add是把文件放进工作区
# 4
`git status`  查看当前工作区状态
>未跟踪的文件（Untracked files）：工作区中新建的文件，但还从未被添加到 Git 中（即没有被 git add 添加到暂存区）。  
已修改但未暂存的文件（Changes not staged for commit）：这些文件已经被修改，但还没有用 git add 命令将它们放入暂存区。  
已暂存的文件（Changes to be committed）：这些文件已经被 git add 命令放入了暂存区，准备通过 git commit 提交。 

已经被track的文件（即第一次git add）被修改后，如果本次修改被add，则为Changes not staged for commit；如果本次尚未被add，则为Changes to be committed。  
从未被git add的文件，为Untracked files。
# 5
`git diff`  
>git diff 比较的是工作区（Working Directory）和暂存区（Staging Area）之间的差异。
换句话说，当你修改了一个已经被 Git 跟踪的文件（tracked file），但还没有使用 git add 暂存这些修改时，git diff 会显示这些未暂存的变化。
# 6
`git log` 显示提交历史，查看每个提交的详细信息  
`git reflog` 显示所有引用操作历史，包括commit reset etc. 

>git log默认按时间顺序（最新的提交在上）列出提交记录。
git log 只展示你分支的可访问的历史，无法显示被丢弃或分离的提交。  
如果执行了一个 git reset 或 git checkout 操作，把分支或 HEAD 移动到了不同的提交，但你需要找回旧的提交。这时候 git log 可能无法帮助你，而 git reflog 会记录所有这些移动操作。  
reflog 是本地的，它只记录你在本地仓库的操作历史，不会在远程仓库中共享。
它能看到很多在 git log 中看不到的内容，例如“被抛弃”的分支或提交。

# 7
`git reset --hard HEAD^`
git reset到HEAD^之后，git log中看不到reset之前的那个最新的版本，git log中最新的变回HEAD^  



