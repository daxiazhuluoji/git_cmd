
#第一节 GIT是个什么

#第二节 GIT理论基础

	SVN原理：记录每一次版本变动的内容
	GIT原理：将每个版本独立保存

##三棵树
	工作区域(Working Directory)
	暂存区域(Stage (Index))
	GIT仓库(Repository(HEAD))
	
##基本操作

	创建仓库
	git init        //初始化工作区
	git init --bare //出事化裸仓库

	配置git：
	git config --global user.name "lidianjun"           //设置用户名
	git config --global user.email "lidianjun@yeah.net"  //设置用户邮箱
	git config --list                                   //查看配置信息

	工作流程	
	1、在工作目录中添加、修改文件           //创建readme.txt
	2、将需要进行版本管理的文件放入暂存区域  //add指令
	3、将暂存区域的文件递交到git仓库        //commit指令

#第三节 指令说明

##status	
	git status

##add
	git add readme.txt //添加一个文件
	git add .          //添加所有文件
	git add ant        //将ant目录下所有文件纳入追踪
	git add -u         //update 所有以追踪文件
	git add -h		   //查看add帮助

##commit
	git commit --amend				//修改递交说明
	git commit -m -s "something" 	//递交，说明里包含递交者信息
	git commit -m '
		1、line_1
		2、line_2
		'                			//递交信息换行

##log
	git log
	git log --decorate --oneline --graph --all

##diff
	git diff                 //比较暂存区域与工作目录
	git diff --cached 快照ID  //比较暂存区和GIT仓库快照
	git diff 快照ID1 快照ID2  //比较两个历史快照
	git diff 快照ID           //比较某个历史快照与当前工作目录

##branch
	git branch 分支名				//创建分支	
	git branch -d 分支名				//删除分支
	git branch -m 旧分支名 新分支名	//重命名分支	

##checkout
	git checkout --<file> //覆盖工作区的修改
	git checkout 分支名

##reset
	git reset HEAD <file> 注：<file>为可选
	git reset HEAD~1
	git reset HEAD~2 
	git reset HEAD~3
	git reset --mixed HEAD~ //--mixed默认添加,移动HEAD指向上一个快照,
							//并将指向的快照回滚到暂存区

	git reset --soft HEAD   //移动HEAD指向上一个快照

	git reset --hard HEAD~  //移动HEAD指向上一个快照
						    //将指向的快照回滚到暂存区
						    //将暂存区域的文件还原到工作目录

##merge
	git merge 分支名 //合并分支

##rm
	git rm 文件名               //删除本地和暂存区文件
	git rm --cached 文件名      //只删除暂存区文件
	git rm --cached -r 文件夹名 //只递归删除暂存区文件夹下文件
	git rm -f 文件名            //强制删除本地和暂存区文件，无论两文件是否相同

##mv
	git mv 旧文件名 新文件名    	//重命名文件

##reflog
	git reflog //查看历史递交


#错误记录：
##1、git checkout <分支号>出现如下提示(切换分支的操作应该是git checkout <分支名>)

You are in 'detached HEAD' state. You can look around, make experimental

您现在处于"游离头"状态下，你可以查看，

changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

修改和递交，同时，如果执行了分支切换，你在本分支下所做的修改都将被忽略，
不会影响其他分支。

If you want to create a new branch to retain commits you create, 

如果你想创建一个新的分支用来保留你的递交，

you may do so (now or later) by using -b with the checkout command again. 

你可以使用checkout指令配以操作符-b实现。

Example: git checkout -b <new-branch-name>

例如：git checkout -b <new-branch-name>







	

	

	




	




