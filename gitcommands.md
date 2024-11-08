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
# 6 日志
`git log` 显示提交历史，查看每个提交的详细信息  
`git reflog` 显示所有引用操作历史，包括commit reset etc. 

>git log默认按时间顺序（最新的提交在上）列出提交记录。
git log 只展示你分支的可访问的历史，无法显示被丢弃或分离的提交。  
如果执行了一个 git reset 或 git checkout 操作，把分支或 HEAD 移动到了不同的提交，但你需要找回旧的提交。这时候 git log 可能无法帮助你，而 git reflog 会记录所有这些移动操作。  
reflog 是本地的，它只记录你在本地仓库的操作历史，不会在远程仓库中共享。
它能看到很多在 git log 中看不到的内容，例如“被抛弃”的分支或提交。

# 7 回滚commit
`git reset --hard HEAD^`
git reset到HEAD^之后，git log中看不到reset之前的那个最新的版本，git log中最新的变回HEAD^  
此时在reflog中可以看到每一个commit的commit id  
`git reset --hard 1094a`
写出commit id的前几位，即可回到这个commit版本
# 8
>我们把文件往Git版本库里添加的时候，是分两步执行的：  
第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区；  
第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。  
因为我们创建Git版本库时，Git自动为我们创建了唯一一个master分支，所以，现在，git commit就是往master分支上提交更改。  
你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。  
# 9
>第一次修改 -> git add -> 第二次修改 -> git commit  
Git管理的是修改，当你用git add命令后，在工作区的第一次修改被放入暂存区，准备提交，但是，在工作区的第二次修改并没有放入暂存区，所以，git commit只负责把暂存区的修改提交了，也就是第一次的修改被提交了，第二次的修改不会被提交。

>那怎么提交第二次修改呢？你可以继续git add再git commit，也可以别着急提交第一次修改，先git add第二次修改，再git commit，就相当于把两次修改合并后一块提交了：  
第一次修改 -> git add -> 第二次修改 -> git add -> git commit

# 10 丢弃工作区修改
>你可以发现，Git会告诉你，git checkout可以丢弃工作区的修改：
`git checkout -- <file>`
这里有两种情况：  
一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；  
一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。  
总之，就是让这个文件回到最近一次git commit或git add时的状态。

# 11 丢弃暂存区修改
`git reset HEAD <file>`可以把暂存区的修改撤销掉（unstage），重新放回工作区  
git reset命令既可以回退版本，也可以把暂存区的修改回退到工作区。当我们用HEAD时，表示最新的版本。
再用git status查看一下，现在暂存区是干净的，工作区有修改：  
$ git status  
On branch master  
Changes not staged for commit:  
  (use "git add <file>..." to update what will be committed)  
  (use "git checkout -- <file>..." to discard changes in working directory)   
  modified:   readme.txt  

# 12 删除文件
先在文件夹里删除文件，或者在命令行中rm test.md  
然后，如果真的想从版本库中删除这个文件，就先git rm再commit  
`git rm test.md`  
`git commit -m "remove test.md"`  

如果是误删，则需要从版本库中恢复这个文件  
`git checkout -- <file>`
将指定的文件恢复到最近一次 git add 或者 git commit 的状态，等于丢弃该文件在工作区的修改。

# 13
创建SSH Key  
`ssh-keygen -t rsa -C "wu555sara@gmail.com"`  
成功则可以在用户主目录（我的是/c/git/）里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。

登陆GitHub，打开“Account settings”，“SSH Keys”页面，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容。

# 14
在GitHub建好一个空仓库，然后把本地的仓库添加上去  
`git remote add origin https://github.com/sarahwu5/learngit.git`  
添加后，远程库的名字就是origin，这是Git默认的叫法，也可以改成别的，但是origin这个名字一看就知道是远程库。

# 15 本地库push到远程库
下一步，可以把本地库的所有内容push到远程库上  
`git push -u origin master`  
-u 是 --set-upstream 的缩写，意思是将当前分支与远程仓库中的指定分支（这里是 origin/master）关联起来。  
在执行这个命令后，Git 会将本地的 master 分支与远程的 origin/master 分支关联起来，成为该分支的 "upstream"（上游分支）。  
下一次你在 master 分支上时，可以直接运行`git push`或`git pull`，而不需要再指定远程仓库和分支名（即不需要再写 git push origin master），Git 会自动知道你要与 origin/master 进行交互。

# 16 远程库clone到本地库
可以从远程库将内容克隆到本地库  
`git clone https://github.com/sarahwu5/gitskills.git`  
clone下来的仓库，在本地修改后，正常git add/commit，然后`git push`即可push到仓库

# 17
如何建立一个新的仓库，并远程push  
1. 在本地建好仓库 `git init`  `git add` `git commit`  
2. 在远程建好仓库  
`git remote add origin https://github.com/sarahwu5/torch.git`
3. 将本地和远程关联`git push -u origin master`

# 18
其他相关17的指令  
1. **检查现有的远程仓库**：
   使用 `git remote -v` 命令来查看当前配置的远程仓库地址

2. **修改远程仓库地址**：
   更改现有的远程仓库地址，可以使用 `git remote set-url origin <new-url>` 命令，其中 `<new-url>` 是新的远程仓库地址。

3. **添加新的远程仓库**：
   添加另一个远程仓库，可以为其指定不同的名称，比如 `git remote add upstream <new-url>`，这样你就可以拥有多个远程仓库，每个仓库有不同的名称。

4. **删除并重新添加远程仓库**：
   如果你确定要替换现有的远程仓库地址，可以先删除现有的远程仓库，然后重新添加：
   ```bash
   git remote remove origin
   git remote add origin https://github.com/sarahwu5/torch.git
   ```