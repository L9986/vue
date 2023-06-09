### 查看git版本：
		-git -v
### 配置：
	name  
		-git config --global user.name "l2312"
	email
		-git config --global user.email "l2312367816@163.com"
### 使用git:
	git status
		-查看当前仓库的状态
	git init
		-初始化仓库
	刚刚添加的文件处于未跟踪的状态：
		未跟踪--->暂存
			- git add <filename> 将文件切换到暂存的状态 
			- git add  *  将所有已修改(未跟踪)的文件切换到暂存状态
		暂存--->未修改	
			- git commit -m(message) "xxxx" 将暂存的文件存储到仓库中
			-  git commit -a -m "xxxx" 提交所有已经修改的文件(未跟踪的文件不会被提交)
		未修改--->修改
			- 修改代码后，文件会变为修改状态
		git log 
			-查看所有历史记录
### 常用的命令：
	git restore <filename>
		- 重置文件
	git restore --staged <filename>
		- 将文件从暂存位置取消掉
	git rm <filename>
		- 删除文件
	git rm <filename> -f
		- 强制删除
	git mv from to
		- 移动文件或者重命名文件
### 分支：
	git 在存储文件时，每一此代码的提交都会创建一个与之对应的节点，git 就是通过一个一个节点来记录代码的状态的。节点会构成一个树状结构，树状结构就意味着这个树辉存在分支，默认情况下仓库只有一个		分支，命名为master。在使用git 时，可以创建多个分支，分支与分支之间相互独立，在一个分支上修改代码不会影响其他分支。
	git branch 
		- 查看当前分支
	git branch <branch name>
		- 创建新的分支
	git branch -d <branch name>
		- 删除分支
	git switch <branch name> 
		- 切换分支
	git switch -c <branch name> 
		- 创建并切换分支
	
	- 在开发中，都是在自己的分支上编写代码，代码编写完成后，再将自己的分支合并到主分支中
	
	git merge <分支名>
		- 合并分支
	
	- 在开发中除了通过merge来合并分支外，还可以通过变基（rebase）来完成分支的合并,通过merge合并分支时，在提交记录中会将所有的分支创建和分支合并的过程全部显示出来，这样当项目比较复杂，开发过		程比较波折时，我们要反复进行创建、合并、删除分支。这样一来将会使我们的代码提交记录变得极为混乱。
	变基原理（变基时发生了什么）：
		-1.当我们发起变基时，git会首先找到两条分支的最近的共同祖先
		-2.对比当前分支相对于祖先的历史提交，并且将它们提取出来存储到一个临时文件中
		-3.将当前部分指向目标的基底
		-4.以当前基底开始，重新执行历史操作
	变基和merge对于合并分支来说最终的结果时一样的，但是变基会使得代码的提交记录更整洁更清晰。
		注意：大部分情况下合并和变基是可以进行互换的，但是如果分支已经提交给了远程仓库，那么这时尽量不要使用变基
	
	### 远程仓库
		目前对于git的操作都是在本地进行的。在开发中不能这样，这时我们就需要一个远程的git仓库，远程的git仓库和本地的仓库本质上没有什么区别，不同点在于远程的仓库可以被多人同时访问使用，方便			我们协同开发。在实际开发中，git的服务器通常由公司搭建由内部使用或购买一些公共的私有git服务器。学习阶段直接使用一些公共的git仓库。目前我们常用的库有两个：GitHub,Gitee(码云)
		- 将本地库上传git:(下面的命令在新建仓库后会自动生成)
			- git remote add origin https://github.com/L9986/git-demo.git	# origin 表示远程分支的名字
			- git branch -M main	# 修改分支的名字为 main
			- git push -u origin main	# git push 命令可以将代码上传到服务器上
		- 将本地库上传Gitee:
			- git remote add gitee https://gitee.com/huawei-technology_27/git-demo.git
			- git push -u gitee main

### github/gitee教程相关代码地址
	- git remote add gitee https://gitee.com/ymhold/vue-course.git
	- git push -u gitee main 

### 远程库的操作命令
	- git remote 	
		- 列出当前关联的远程库
	- git remote add <远程库名> <url>
		- 关联远程仓库 
    - git remote remove <远程库名>
		- 删除远程库
	- git push -u <远程库名> <分支名>
		- 向远程库推送代码并和当前分支关联
	- git clone <url>
		- 从远程库下载或克隆代码（新建一个文件夹，在终端打开，并输入克隆的命令）