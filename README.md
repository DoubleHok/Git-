# Git-
Git使用总结
一、配置信息
1、因为Git是分布式版本控制系统，需要填写用户名和邮箱作为一个标识
命令：git config --global user.name "DoubleHok"
      git config --global user.email "DoubleHok@163.com"
注意：git config --global参数，有了这个参数，表示这台机器上所有的Git仓库都会
使用这个配置，当然你也可以对某个仓库制定不同的用户名和邮箱。
二、创建版本库
命令：
cd D: (进入某个磁盘）
cd xx （进入某个文件夹）
mkdir xxx （创建新文件夹）
touch xxx  （创建文件）
pwd （Print Working Directory：显示当前的目录）
git init （把目录变成git可以管理的仓库，这时新建文件夹下会多出一个.git的目录
若没有，调整“显示隐藏文件”即可）
vi/vim xxx （进入xxx文件进行编辑）
三、提交到本地库
命令：
git add xxx （添加文件到暂存区）
可能出现状况：
warning: LF will be replaced by CRLF in README.md.
The file will have its original line endings in your working directory
解决方法：git config --global core.autocrlf false
原因：
路径中存在 / 的符号转义问题，false就是不转换符号默认是true，
相当于把路径的 / 符号进行转义，这样添加的时候就有问题

git commit -m "描述改动" （提交文件到本地仓库）
git status （查看状态）
git diff （查看文件改动情况）
git restore xxx （放弃文件所做的修改）

四、版本退回
git log （显示从最近到最远的显示日志）
git log –-pretty=oneline （简洁显示最近到最远的显示日志）
git reflog （获取到版本号）
回退到上一版本：
方法一：git reset --hard HEAD^ （把当前的版本回退到上一个版本）
如果要回退到上上个版本只需把 HEAD^ 改成 HEAD^^ 以此类推。
方法二：git reset --hard 版本号 (把当前的版本回退到任一版本）

五、理解工作区与暂存区的区别
工作区：就是你在电脑上看到的目录，比如目录下 Git 里的文件 (.git 隐藏目录版本库除外)。
或者以后需要再新建的目录文件等等都属于工作区范畴。
版本库 (Repository)：工作区有一个隐藏目录.git, 这个不属于工作区，这是版本库。
其中版本库里面存了很多东西，其中最重要的就是 stage (暂存区)，还有 Git 为我们自动创建了第一个分支 master, 以及指向 master 的一个指针 HEAD。

我们前面说过使用 Git 提交文件到版本库有两步：

第一步：是使用 git add 把文件添加进去，实际上就是把文件添加到暂存区。

第二步：使用 git commit 提交更改，实际上就是把暂存区的所有内容提交到当前分支上。

六、Git撤销修改和删除文件操作
恢复以前的版本，现在可以有如下几种方法可以做修改：

第一：如果我知道要删掉那些内容的话，直接手动更改去掉那些需要的文件，然后 add 添加到暂存区，最后 commit 掉。

第二：我可以按以前的方法直接恢复到上一个版本。使用 git reset --hard HEAD^

第三：git checkout -- file （该命令可以丢弃工作区的修改）

第三种方法把文件在工作区做的修改全部撤销，这里有 2 种情况，如下：
1.readme.txt 自动修改后，还没有放到暂存区，使用 撤销修改就回到和版本库
一模一样的状态。
2. 另外一种是 readme.txt 已经放入暂存区了，接着又作了修改，撤销修改就回到
添加暂存区后的状态。

删除文件：
命令：rm xxx  (rm:remove)
恢复删除文件：
命令：git checkout -- xxx (文件与"--"前有空格）

七、远程仓库

Git commit 错误: Changes not staged for commit:
解决方法：使用git commit -am'..'
原因：git commit -m用于提交暂存区的文件，git commit -am用于提交跟踪过的文件。

