$ mkdir learngit //创建learngit目录
$ cd learngit //进入learngit目录
$ pwd //显示当前目录
$ git init //把当前目录变成git可以管理的仓库
$ git add readme.rtf //把文件添加到仓库，可以一次添加多个文件，但是只需要提交一次，（commit一次）
$ git commit -m “describe”// 提交文件，-m 后面跟的是此次提交的描述
$ git status //查看git的当前状态
$ git diff //查看git哪些文件做了哪些修改

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