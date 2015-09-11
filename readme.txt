$ mkdir learngit //创建learngit目录
$ cd learngit //进入learngit目录
$ pwd //显示当前目录
$ git init //把当前目录变成git可以管理的仓库
$ git add readme.rtf //把文件添加到仓库，可以一次添加多个文件，但是只需要提交一次，（commit一次）
$ git commit -m “describe”// 提交文件，-m 后面跟的是此次提交的描述
$ git status //查看git的当前状态
$ git diff //查看git哪些文件做了哪些修改

如果你没有看到.git目录，那是因为这个目录默认是隐藏的，用ls -ah命令就可以看见。


$ git log //查看历史记录
$ git log - -pretty=oneline //查看历史记录单行显示
$ git reset - -hard HEAD^ //回退到上一版本，HEAD^^回退上2个版本，HEAD~100回退上一百版本
$ cat readme.rtf //查看readme.rtf内容
$ git reset - -hard 3628164//回到某个版本 版本号不用写全
$ git reflog //查看所有历史命令
$ git checkout -- file 一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。命令中的--很重要，没有--，就变成了“切换到另一个分支”的命令
$ git rm readme.rtf
$ git commit -m “discribe”删除一个文件 一定要执行提交的动作
//显示影藏文件和影藏影藏文件
显示：defaults write com.apple.finder AppleShowAllFiles -bool true
隐藏：defaults write com.apple.finder AppleShowAllFiles -bool false 

要关联一个远程库，使用命令$ git remote add origin git@github.com:iamdalianmao/learngit.git
如 $ git remote add origin git@github.com:iamdalianmao/learngit.git
关联后，使用命令git push -u origin master第一次推送master分支的所有内容；
此后，每次本地提交后，只要有必要，就可以使用命令$ git push origin master推送最新修改；

$ git clone git@github.com:iamdalianmao/dalianmaoBlog.git //从远程库克隆一个项目到本地的git库

查看分支：git branch
创建分支：git branch <name>
切换分支：git checkout <name>
创建+切换分支：git checkout -b <name>
合并某分支到当前分支：git merge <name>
删除分支：git branch -d <name>

用git log --graph命令可以看到分支合并图。

$ git merge --no-ff -m "merge with no-ff" dev 准备合并dev分支，请注意--no-ff参数，表示禁用Fast forward 因为本次合并要创建一个新的commit，所以加上-m参数，把commit描述写进去。

$ git stash //可以把当前工作现场“储藏”起来，等以后恢复现场后继续工作，当你需要临时去修复一个bug时可以用stash把你当前改了一半的代码储藏起来，等bug修复好了在回来继续工作

$ git checkout master
$ git checkout -b issue-101 //创建修复bug的分支issue-101
首先确定要在哪个分支上修复bug，假定需要在master分支上修复，就从master创建临时分支

$ git checkout dev
$ git stash list
bug修复完了以后回到自己原来的分支上去，用 stash list查看之前保存的工作现场

$ git stash apply
$ git stash pop
一是用git stash apply恢复，但是恢复后，stash内容并不删除，你需要用git stash drop来删除；
另一种方式是用git stash pop，恢复的同时把stash内容也删了

$ git stash apply stash@{0}
你可以多次stash，恢复的时候，先用git stash list查看，然后恢复指定的stash

多人协作的工作模式通常是这样：
首先，可以试图用git push origin branch-name推送自己的修改；
如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；
如果合并有冲突，则解决冲突，并在本地提交；
没有冲突或者解决掉冲突后，再用git push origin branch-name推送就能成功！
如果git pull提示“no tracking information”，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream branch-name origin/branch-name。

查看远程库信息，使用git remote -v；
本地新建的分支如果不推送到远程，对其他人就是不可见的；
从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交；
在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致；
建立本地分支和远程分支的关联，使用git branch --set-upstream branch-name origin/branch-name；
从远程抓取分支，使用git pull，如果有冲突，要先处理冲突。

命令git tag <name>用于新建一个标签，默认为HEAD，也可以指定一个commit id；
git tag -a <tagname> -m "blablabla..."可以指定标签信息；
git tag -s <tagname> -m "blablabla..."可以用PGP签名标签；
命令git tag可以查看所有标签。
命令git push origin <tagname>可以推送一个本地标签；
命令git push origin --tags可以推送全部未推送过的本地标签；
命令git tag -d <tagname>可以删除一个本地标签；
命令git push origin :refs/tags/<tagname>可以删除一个远程标签。

$ git config --global color.ui true
让Git显示颜色，会让命令输出看起来更醒目

忽略特殊文件
忽略某些文件时，需要编写.gitignore；
.gitignore文件本身要放到版本库里，并且可以对.gitignore做版本管理！
配置别名
$ git config --global alias.st status
当然还有别的命令可以简写，很多人都用co表示checkout，ci表示commit，br表示branch
$ git config --global alias.co checkout
$ git config --global alias.ci commit
$ git config --global alias.br branch
$ git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit”(这个不错，格式化log打印信息)
配置Git的时候，加上--global是针对当前用户起作用的，如果不加，那只针对当前的仓库起作用。
配置文件放哪了？每个仓库的Git配置文件都放在.git/config文件中
别名就在.git/config中的[alias]后面，要删除别名，直接把对应的行删掉即可。
