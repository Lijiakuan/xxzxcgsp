# xxzxcgsp
有三种方式的情况下，如何做到没有Bug的合并代码。。。 \
远程仓库发生改变，本地仓库没有改变 \
首先，查看远程仓库 git remote -v  \


$ git remote -v  \
origin	git@github.com:{User}/Understanding_Unix-Linux_Programming.git (fetch)   \
origin	git@github.com:{User}/Understanding_Unix-Linux_Programming.git (push)   \

把远程库更新到本地  \
git fetch origin master  \


$ git fetch origin master   \
Warning: Permanently added the RSA host key for IP address '{IP address such as: 192.168.1.1 }' to the list of known hosts.   \
From github.com:{User}/Understanding_Unix-Linux_Programming    \
 * branch            master     -> FETCH_HEAD     \
比较远程更新和本地版本库的差异 git log master.. origin/master    \

 
$ git log master.. origin/master     \
commit ce39f8b3eeee898a2a038444f897f2aef3673493     \
Author: {User} <794870409@qq.com>        \
Date:   Fri Feb 26 14:14:39 2016 +0800     \

    {The context origin added ... }    \
合并远程库 git merge origin/master    \

有差异      \


$ git merge origin/master     \
Updating eb32b20..ce39f8b     \
Fast-forward    \
 README.md | 2 +-    \
 1 file changed, 1 insertion(+), 1 deletion(-)    \
无差异      \
 git merge origin/master    \
Already up-to-date    \
远程仓库没有改变，本地仓库发生改变    \


命令推荐   \

git status // 查看版本库的状态    \
git add .|[file you want add like README.md] // 添加修改的文件进入版本库     \
git commit -m "the content of your modify" // 提交版本库     \
git push -u origin master // 上传到远程版本库     \
首先你的文件出现了修改 git status     \

$ git status     \
On branch master    \
Your branch is up-to-date with 'origin/master'.    \
Changes not staged for commit:    \
  (use "git add <file>..." to update what will be committed)    \
  (use "git checkout -- <file>..." to discard changes in working directory)    \

	modified:   README.md     \

no changes added to commit (use "git add" and/or "git commit -a")    \
你的文件被修改后就会出现这样的显示    \

添加文件 git add .|[或者某个文件]|like: README.md    \

$ git add README.md     \
$ git status    \
On branch master    \
Your branch is up-to-date with 'origin/master'.    \
Changes to be committed:     \
  (use "git reset HEAD <file>..." to unstage)     \

	modified:   README.md    \
文件添加后，就会出现这种     \

提交文件 git commit -m "content"    \

$ git commit -m "update content"     \
[master 7456161] update content     \
 Committer: {User} <wuyingqiang@wuyingqiangs-MacBook-Pro.local>     \
Your name and email address were configured automatically based      \
on your username and hostname. Please check that they are accurate.    \
You can suppress this message by setting them explicitly. Run the     \
following command and follow the instructions in your editor to edit    \
your configuration file:    \

    git config --global --edit    \

After doing this, you may fix the identity used for this commit with:    \

    git commit --amend --reset-author    \
 
 1 file changed, 8 insertions(+), 3 deletions(-)     \
文件提交到你的版本库，这样本地版本就更新了     \

和远程库进行同步 git push -u origin master    \

$ git push -u origin master     \
Counting objects: 3, done.      \
Delta compression using up to 8 threads.     \
Compressing objects: 100% (2/2), done.        \
Writing objects: 100% (3/3), 417 bytes | 0 bytes/s, done.     \
Total 3 (delta 1), reused 0 (delta 0)     \
To git@github.com:scofieldWyq/Understanding_Unix-Linux_Programming.git     \
   ce39f8b..7456161  master -> master     \
Branch master set up to track remote branch master from origin.     \
这样我们的版本库同步也就好了。     \
