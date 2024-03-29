# Repo相关
```python
[] 代表可选
XXname 代码参数

repo help init                  生成 Repo init 参数的说明和选项列表
repo init --help

repo init -u urlname [options]  当前目录中安装 Repo   （类似于初始化.git）
-u：指定从中检索清单代码库的网址。
-m：选择代码库中的清单文件。如果未选择清单名称，则默认为 default.xml。
-b：指定修订版本，即特定的 manifest-branch。
-g: 
eg:
  repo init -u urlname1 -b xxxx -g open --no-repo-verify --repo-branch=stable

repo sync [project-list-name] 更新本地工作文件 默认同步所有项目的文件 （类似git rebase origin）
-c：仅获取服务器中的当前清单分支
eg：
  repo sync -c  --no-tags   同步最新代码
```

# Svn
```python
svn up		update
svn status
svn log
svn add a.txt	(可有可无的)
svn ci -m 'msg1' 提交当前目录所有修改的
svn ci -m 'msg1' a1.o a2.o 指定文件提交
svn mv a.log dir1/  移动
svn del a.log -m 'msg1'
```

# 01-Git基本介绍
Git Bash：Unix与Linux风格的命令行，使用最多，推荐最多 <br>
Git CMD：Windows风格的命令行	<br>
Git GUI：图形界面的Git，不建议初学者使用，尽量先熟悉常用命令 <br>
### 配置相关
```python
git config -l 
config --system --list 
git config --global -l 查看当前用户（global）配置 

设置global级
git config --global user.name "kuangshen" #名称 
git config --global user.email 24736743@qq.com #邮箱 
```
### 常用知识和命令
```python
git status	修改的状态
git show      	最近一次commit的修改内容（配合git fetch之后使用）
git log         查看提交历史
git diff	查看冲突的点

文件两种状态：
untracked 未跟踪 未被纳入版本控制
tracked 已跟踪的(staged(暂存的) modified )

git status -s 更简洁的查看
 	M 已修改的状态(红色 为add之前  绿色位add之后
	??未跟踪的状态)
	D 被删除的文件
git rm 就是删除一个文件 和右键删除一个文件效果一样

git tag 列出标签
git tag v1 本地标签
git push origin v1 本地标签推送到远程标签用于发布软件 
git checkout -b b3 v1 基于本地v1标签创建b3分支
git tag -d v1 删除本地标签
git push origin :refs/tag/v1 删除远程标签v1
```

### 本地仓库搭建
```python
创建本地仓库的方法有两种：
1、创建全新的仓库
git init  在当前目录新建一个Git代码库 
2，克隆远程仓库
 $ git clone [url] # https://gitee.com/kuangstudy/openclass.git 
git status [filename]  #查看指定文件状态 
git status #查看所有文件状态 
	未git add 是红色
	git add. 后是绿色
	git commit 后无状态
```
### 忽略文件
在主目录下建立".gitignore"文件，此文件有如下规则：
0. 可以忽略本身 .gitignore
1. 忽略文件中的空行或以井号（#）开始的行将会被忽略。
2. 可以使用Linux通配符。例如：星号（*）代表任意多个字符，问号（？）代表一个字符，方括号（[abc]）代表可选字符范围，大括号（{string1,string2,...}）代表可选的字符串等。
3. 如果名称的最前面有一个感叹号（!），表示例外规则，将不被忽略。
4. 如果名称的最前面是一个路径分隔符（/），表示要忽略的文件在此目录下，而子目录中的文件不忽略。
5. 如果名称的最后面是一个路径分隔符（/），表示要忽略的是此目录下该名称的子目录，而非文件（默认文件或目录都忽略）。
```python
 #为注释 
 *.txt 		忽略所有 .txt结尾的文件,这样的话上传就不会被选中 
 !lib.txt	不忽略lib.txt
 /temp 		仅忽略项目根目录下的temp文件,不包括其它目录temp 
 build/ 	忽略build/目录下的所有文件 
 doc/*.txt 	会忽略 doc/notes.txt 但不包括 doc/server/arch.txt
```


# 02-分支相关
较为复杂的分支相关命令： <br>
[https://blog.csdn.net/weixin_30699831/article/details/101982286](https://blog.csdn.net/weixin_30699831/article/details/101982286)
常用分支命令
```python
git branch 		        查看本地分支		
git branch -r	    		查看远程仓库的分支
git branch dev1                 创建分支dev1
git checkout dev2               切换到分支dev2 （可以在查看玩远程后直接切换）
git checkout -b dev2            创建并切换到分支dev2
git merge dev3 			吸收dev3（将dev3合并过来）
git branch -d dev2              删除dev2
git branch -D dev2              强制删除
git push origin -d dev2	   	删除远程的dev2 
git push origin dev2            从当前分支push到dev2分支
```


# 03-reset相关
```python
git reset 撤销操作 撤销add
git reset --soft HEAD^ 软撤销，保留代码修改,HEAD^代表最近的版本号 撤销 commit
git reset --hard HEAD^ 硬撤销，不保留代码修改

撤销add
git add .
git reset

撤销commit 软撤销
git add .
git commit
git reset --soft HEAD^
```


# 04-fetch和pull
详细教学：[https://blog.csdn.net/weixin_44821980/article/details/108536648](https://blog.csdn.net/weixin_44821980/article/details/108536648) <br>
git pull（拉取代码） 	会自动合并本地的代码	<br>
git pull rebase 	执行变基，无视本地的修改，都使用远程的 <br>
git fetch（获取代码） 	不会自动合并本地的代码，后用 git diff可看冲突的点 <br>
git fetch 远程常用
```python
1.获取远端master信息 	
	git fetch origin master	 
	//获取master的信息，不过不写origin master，默认是获取所有分支信息 
2.切换到远程master分支 	
	git checkout origin/master	 
	//切换分支的时候如果在 分支名的前面加 origin/ 则代表切换的远程分支， 
	//这个分支现在是项目最新版本，应为第一步的时候已经获取过远程master的信息了 
3.观察远程master分支，然后切回本地分支 	
	git checkout master 
4. 合并远程master分支 	
	git merge origin/master 
```

# 05-fork仓库
使用fork 仓库 
```python
1，clone fork 仓库
2，查看 repoA的 origin：
git remote -v
3，设置repoA fork的upstream 为repoA的 origin： 
git remote add upstream git@github.houston.softwaregrp.net:SMA-RnD/suite-registry.git
3.5 跳转origin 或 upstream分支
git checkout --track origin/patch/2020.08
4，指定pull的来源 （upstream和origin）git pull upstream --rebase
git fetch upstream 将远程所有的分支fetch下来
如果是分支（patch/2020.08是一个分支）：git pull upstream patch/2020.08 --rebase  
5，指定push的地方  git push origin 

打开 Git Bash。
列出当前为复刻配置的远程仓库。
$ git remote -v
> origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
> origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
指定将与复刻同步的新远程上游仓库。
$ git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git
验证为复刻指定的新上游仓库。
$ git remote -v
> origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
> origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
> upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (fetch)
> upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (push)
```
eg：在公司中：
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22347830/1676561621315-25f57907-f7f7-49a0-b722-369705f057bf.png#averageHue=%23292c39&clientId=uc653fb8e-644a-4&from=paste&height=248&id=u2dce24d4&name=image.png&originHeight=248&originWidth=675&originalType=binary&ratio=1&rotation=0&showTitle=false&size=20146&status=done&style=none&taskId=ucfca84d6-e019-4ab7-9ad6-d03211c86ae&title=&width=675)

# 05-常用流程和场景
## 01-基本使用流程
```python
```

```python
1. 创建git仓库
2. 将git仓库克隆下来，将仓库文件放到idea项目中
   1. git clone [url] # https://gitee.com/kuangstudy/openclass.git 
3. dea 中：最重要的
   1. 拉取最新的代码：
      1.  git pull --rebase 
4. 提交到暂存区
   1.  git add .		 使用add 节点变绿 
5. 提交到仓库
   1.  git commit -m "填写msg" 节点变黄 
6. push到远程仓库gitee中
   1.  git push 
```

## 02-撤销类常见
### 01-撤销git add:
```python
撤销了add但本地修改的代码还在
git reset			常用于当前目录所有文件
git reset HEAD filename		常用于单个文件
git restore --staged filename   
git reset HEAD  撤销最近的一次
```

### 02-撤销commit：
```python
git reset --soft HEAD^ 		仅仅是撤回commit操作，您写的代码仍然保留。
```

### 03-已commit，撤销一个文件的修改
```python
git log a.txt
git reset commitid a.txt  撤销到前一个commitid,会保留代码
git checkout commitid --a.txt	  对文件还原到commitid
git add .
git commit --amend
```

### 04-commit注释写错了，只是想改一下注释 或代码，只需要：
```python
 git add .
 git commit --amend 
```

### 05-fetch之后消除冲突
```python
git pull
git fetch
git diff
点击文件进去 resolve冲突
git commit
```

### 06-多个合并成一个commitid
```python
两个gerrit （要在同git环境下，同git conf下）提交合并成一个commit[id]：
相关命令：
    git stash				# let stash
    git stash list			# list
    git stash pop			# pop
步骤：
    git status  确保clear
    git fetch ssh://sssssm:394181111111111  会拉下来代码  (包含commit信息，后面的fetch想合到这个commit上的话，就不用git reset， 后面的git fetch的 git reset --soft HEAD^ 再 add+commit)
    git reset --soft HEAD^  软撤销
    （中途可修改代码）
    git stash
    git fetch ssh://sssssom:39422222222222  # 尽量在对应分支下面 fetch
    git reset --soft HEAD^
    （中途可修改代码）
    git stash pop
    git add .
    git commit
    repo upload
其他步骤:
    git fetch no1
    git fetch no2
    git fetch no3
    用 git reset --hard HEAD^    可以去除当前仓最近的一个git fetch 
```

## 03-分支类常用

### 01-main存发布版本，分支1做开发版本
```python
git clone ..git (main分支就行)(远程环境的已经做过了)
git checkout -b new_branch
git add ..
git commit -m 'xx'
git push origin new_branch
在git_lab提merger rq，merge到main中
git checkout main  (git checkout origin mian)
git pull origin
之后就是接收git check循环了
```

### 02-拉取远程分支到本地：
```python
git init			            初始化空文件	
git remote add origin http.....git          拉master(只是初始.git文件)
git fetch origin remote_dev                 拉远程的分支(初始化)
git checkout -b local_dev origin/remote_dev 建立本地分支（出现代码）	
git pull origin remote_dev                  拉取远程分支最新的代码
```

### 03-从master分支拉出的t2分支，然后合并回master
```python
1、切换到master分支：
	git checkout master
2、创建并切换到two分支：
	git checkout -b t2  或者 git branch t2 + checkout
3、将当前的分支push到远程仓库的t2分支（与本地仓库同步）：
	git push origin t2
4、修改t2分支上的内容并提交到本地仓库：
	git commit -a -m"修改子分支"
5、将t2分支上的修改提交到远程仓库：
	git push origin t2
6、t2分支上的修改ok后，切换到master分支：
	git checkout master（注意，只有checkout切换到当前分支后，pull代码，才能看见当前分支的代码，如果没有checkout到当前分支，pull了也在相应文件夹下也看不见当前分支的代码，而是上次checkout的代码）
7、将t2分支合并到master分支：
	git merge origin/t2   或者在 master分支中 git merge t2
8、将合并之后的代码push到远程仓库：
	git push origin master
此例是父分支和自分支之间的merge操作，爷孙分支亦如此，旁系分支合并亦然
```

### 04-将master分支内容合并到dev分支
```python
1、切换到你所在分支dev：
	git checkout dev
2、git merge master
3、将本地内容push到dev分支：
	git push
```




