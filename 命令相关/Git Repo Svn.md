```python
[] 代表可选
XXname 代码参数

repo help init                  生成 Repo init 参数的说明和选项列表
repo init --help

repo init -u urlname [options]  当前目录中安装 Repo                （类似于初始化.git）
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
# 01-基本介绍
:::info
**Git Bash：**Unix与Linux风格的命令行，使用最多，推荐最多
**Git CMD：**Windows风格的命令行
**Git GUI**：图形界面的Git，不建议初学者使用，尽量先熟悉常用命令
:::
查看配置 
```python
git config -l 
```
查看不同级别的配置文件：
```python
 #查看系统config 
config --system --list 

 #查看当前用户（global）配置 
git config --global -l 
```
设置global级
```python
 git config --global user.name "kuangshen" #名称 
git config --global user.email 24736743@qq.com #邮箱 
```
上传本地repo到github
:::info
1，在github中创建一个repo2
2，在本地repo中，gitclone下repo2，repo中有repo2的.git就行了
3，git push一遍文件就行了
:::
**本地仓库搭建**
:::info
创建本地仓库的方法有两种：
1、创建全新的仓库
 # 在当前目录新建一个Git代码库 $ git init 
2，克隆远程仓库
 $ git clone [url] # https://gitee.com/kuangstudy/openclass.git 
:::
**查看文件状态**
:::info
 #查看指定文件状态 
git status [filename] 
#查看所有文件状态 
git status
:::
**忽略文件**
:::info
有些时候我们不想把某些文件纳入版本控制中，比如数据库文件，临时文件，设计文件等
在主目录下建立".gitignore"文件，此文件有如下规则：

1. 忽略文件中的空行或以井号（#）开始的行将会被忽略。
2. 可以使用Linux通配符。例如：星号（*）代表任意多个字符，问号（？）代表一个字符，方括号（[abc]）代表可选字符范围，大括号（{string1,string2,...}）代表可选的字符串等。
3. 如果名称的最前面有一个感叹号（!），表示例外规则，将不被忽略。
4. 如果名称的最前面是一个路径分隔符（/），表示要忽略的文件在此目录下，而子目录中的文件不忽略。
5. 如果名称的最后面是一个路径分隔符（/），表示要忽略的是此目录下该名称的子目录，而非文件（默认文件或目录都忽略）。

 #为注释 *.txt #忽略所有 .txt结尾的文件,这样的话上传就不会被选中 ！!lib.txt #但lib.txt除外 /temp #仅忽略项目根目录下的TODO文件,不包括其它目录temp build/ #忽略build/目录下的所有文件 doc/*.txt #会忽略 doc/notes.txt 但不包括 doc/server/arch.txt 
:::
**Git和idea项目绑定**
:::info

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
:::
# 02-常用场景 命令
## 00-常用命令
```python
git log                             查看提交历史
git branch				本地仓库上的分支	
当前所在的分支在查看时会变绿
git branch -r                       远程仓库的分支
git branch dev1                     创建分支dev1
git checkout -b dev2                创建并切换到分支dev2
git checkout dev2                   切换到分支dev2 （可以在查看玩远程后直接切换）
git merge dev3                      吸收dev3（将dev3合并过来）
git branch -d dev2                  删除dev2
git branch -D dev2                 强制删除
git push origin --delete dev2	   删除远程的dev2 
git push origin dev2               从我的分支上push
git push -f                        强制push
git branch -dr remote/dev2          删除远程的dev2
```
## 01-常用场景
### 撤销git add .:
```python
 git reset 
```
### 撤销到git add之前:
```python
 git reset HEAD
```
### 撤销刚才的commit
```python
 git reset --soft HEAD^ 		仅仅是撤回commit操作，您写的代码仍然保留。
```

### 撤销push：回到对应的版本号
```python
gitk 查询对应点的版本号（SHA1 ID） 
或者git log
按 q 退出查看 
git reset –-soft 版本号：回退到某个版本，只回退了commit的信息，不会恢复到index file一级。
	- 如果还要提交，直接commit + push即可； 
git reset -–hard 版本号：彻底回退到某个版本，本地的源码也会变为上一个版本的内容，撤销的commit中所包含的更改被冲掉 
	- 然后 git push origin dev1 --force  强制提交

```
### commit注释写错了，只是想改一下注释 或代码，只需要：
```python
 git add .
 git commit --amend 
```
### 如果push失败：
```python
git gc 
git pull --rebase 
git push origin HEAD:refs/for/master%ready 
```
### 两个gerrit （要在同git环境下，同git conf下）提交合并成一个commit[id]：
```
相关命令：
    git stash				# let stash
    git stash list			# list
    git stash pop			# pop
步骤：
    git status  确保clear
    git fetch ssh://fwx1233030@rnd-hisi-kirin-origin.huawei.com:394181111111111
    git reset --soft HEAD^
    （中途可修改代码）
    git stash
    git fetch ssh://fwx1233030@rnd-hisi-kirin-origin.huawei.com:39422222222222  # 尽量在对应分支下面 fetch
    git reset --soft HEAD^
    （中途可修改代码）
    git stash pop
    git add .
    git commit
    repo upload
```

## 02-fetch和pull：
[https://blog.csdn.net/weixin_44821980/article/details/108536648](https://blog.csdn.net/weixin_44821980/article/details/108536648)
**pull（拉取）**
```python
:::info
作用和我的理解：把数据从远端拉到本地目前的分支上并进行自动合并
对本地文件的影响：如果有有冲突会自动合并，有些合并不了的会提示用户手动合并。
:::
**fetch（获取）**
:::info
作用和我的理解：获取远端仓库信息 , 比如现在远端的版本比本地的版本先进，用git branch -a可以查看远端的分支，但是这时我们查询的分支也是旧的 ， 当使用git fetch获取到远端信息之后，此时用git branch -a查询出来的远端分支是最新的，我们将远端分支和本地分支进行合并，并且解决冲突在进行commit和push
对本地文件的影响：和本地文件无关
:::
```
 
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
**使用fork 仓库：**
 
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
## 03-常用merge场景
**一、本文是从master分支拉出的two，然后合并回master**
```python
1、切换到master分支：
	git checkout master
2、创建并切换到two分支：
	git checkout -b two
3、将two分支push到远程仓库（与本地仓库同步）：
	git push origin two
4、修改two分支上的内容并提交到本地仓库：
	git commit -a -m"修改子分支"
5、将two分支上的修改提交到远程仓库：
	git push origin two
6、two分支上的修改ok后，切换到master分支：
	git checkout master（注意，只有checkout切换到当前分支后，pull代码，才能看见当前分支的代码，如果没有checkout到当前分支，pull了也在相应文件夹下也看不见当前分支的代码，而是上次checkout的代码）
7、将two分支合并到master分支：
	git merge origin/two
8、将合并之后的代码push到远程仓库：
	git push origin master
此例是父分支和自分支之间的merge操作，爷孙分支亦如此，旁系分支合并亦然
```
**二、将master分支内容合并到dev分支**
```python
1、切换到你所在分支dev：
	git checkout dev
2、git merge master
3、将本地内容push到dev分支：
	git push
	
我的分支(dev1)内容合并到master中：
git pull
git checkout master
get merge dev1
git push
```
**较为复杂的分支相关命令：**
[https://blog.csdn.net/weixin_30699831/article/details/101982286](https://blog.csdn.net/weixin_30699831/article/details/101982286)
### 04-拉取远程代码Git pull --rebase vs. --merge
**rebasing**
:::info
If you pull remote changes with the flag --rebase, then your local changes are reapplied on top of the remote changes.
git pull --rebase
:::
**merging**
:::info
If you pull remote changes with the flag --merge, which is also the default, then your local changes are merged with the remote changes. This results in a merge commit that points to the latest local commit and the latest remote commit.
git pull --merge 
:::


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


