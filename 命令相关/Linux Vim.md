```python
scp fff@10.1113:/srv/ssss D:\ws\优化111\ 
```
# 01-Linux 常用基础命令
## 01-命令解析器

- shell就是命令解释器
- 命令解析器的作用：对用户输入到终端的命令进行解析，调用对应的执行程序。

                     ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671206101203-f3e4f37a-73dd-4394-883a-a37d0e9023ec.png#averageHue=%23fefdfc&clientId=u6d5f4c1d-808e-4&from=paste&height=313&id=LEO0W&name=image.png&originHeight=290&originWidth=188&originalType=binary&ratio=1&rotation=0&showTitle=false&size=13029&status=done&style=none&taskId=u2c573555-985f-40a2-b345-167e6f15c49&title=&width=202.88890075683594)
用户在终端输入命令, 由shell命令解释器对命令进行解析(按照$PATH环境变量搜索命令), 解析成内核能够识别的指令, 然后由内核执行命令, 最后由终端显示命令执行的结果给用户.
注意：shell在寻找命令的时候是按照$PATH环境变量去查找的，如果找到了就执行对应的命令，若找不到就报错, 执行echo $PATH可以查看PATH环境变量的值.
 

- 常用的命令解析器：
   - shell -- Bourne Shell
      - /bin/sh	
   - bash -- Bourne Again Shell
      - /bin/bash
- 当前系统所使用的shell
   - echo $SHELL
- 当前系统下有哪些shell
   - cat /etc/shells

## 02-Linux下常用快捷键
### 01 tab键

- 补齐命令

如:在终端输入his然后按tab键, 会补齐history命令;
如:输入l然后按tab键, 会显示所有以l开头的命令.

- 补齐文件(包括目录和文件)

例如: 如果在执行ls, 然后按tab键, 会显示当前目录下所有的文件
使用tab键的优点: 减少用户输入, 加快输入速度, 减少出错的机会。
### 02-主键盘快捷键

- 遍历输入的历史命令
   - 从当前位置向上遍历：ctrl + p（**↑**）
   - 从当前位置向下遍历：ctrl + n（**↓**）

注意：使用history命令可以显示用户输入的所有命令。

- 光标位置移动	
   - 光标左移： ctrl + b （**←**）
   - 坐标右移： ctrl + f （**→**）
   - **移动到头部： ctrl + a（home）**
   - **移动到尾部： ctlr + e（end）**
- 字符删除
   - 删除光标前边的字符：ctrl + h（Backspace）
   - 删除光标后边的字符：ctrl + d
      - 光标后边的字符即光标覆盖的字符
      - 执行该命令，删除的是字符W
   - 删除光标前所有内容：ctrl + u
   - 删除光标后所有内容：ctrl + k
## 03-linux下的目录结构
### 01-linux系统的目录结构

- Linux系统的目录结构是一个倒立的树状结构, 根目录用/表示，对比windows目录结构理解linux的目录结构。
- ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671206841712-9311699b-e1f8-4e8b-95e0-41169e18a0ef.png#averageHue=%23fcfcfc&clientId=u6d5f4c1d-808e-4&from=paste&height=359&id=o7Wvg&name=image.png&originHeight=323&originWidth=751&originalType=binary&ratio=1&rotation=0&showTitle=false&size=69703&status=done&style=none&taskId=uf7253497-b55d-4d2a-a55f-20d5b6f9268&title=&width=834.4444665496737)
### 02-linux下主要目录介绍

- /bin: binary，二进制文件，可执行程序，shell命令
   -  如: ls , rm , mv, cp等常用命令
- /sbin: s是Super User的意思，这里存放的是系统管理员使用的系统管理程序。
   -  如ifconfig, halt, shutdown, reboot等系统命令
- /dev: device，在linux下一切皆文件
   - 硬盘, 显卡, 显示器
   - 字符设备文件、块设备文件
   -  如: 在input目录下执行: sudo cat mouse0, 移动鼠标会显示有输入.
- /lib: linux运行的时候需要加载的一些动态库
   -  如: libc.so、libpthread.so等
- /mnt: 手动的挂载目录, 如U盘等
- /media: 外设的自动挂载目录, 如光驱等。
- /root: linux的超级用户root的家目录
- /usr: unix system resource--类似于WINDOWS的programe files目录
   -  include目录里存放头文件, 如: stdio.h、stdlib.h、string.h、pthread.h
   - games目录下的小游戏-如: sl小火车游戏
- /etc: 存放配置文件
   -  /etc/passwd
      -  man 5 passwd可以查看passwd文件的格式信息
   - /etc/group
      - man 5 group可以查看group文件的格式信息
   - /etc/profile
      -   系统的配置文件, 修改该文件会影响这个系统下面的所有的用户
- /opt: 安装第三方应用程序
   - 比如安装oracle数据库可以在这个目录下
- /home: linux操作系统所有用户的家目录
   - 用户家目录：(宿主目录或者主目录）
      - /home/itcast
- /tmp: 存放临时文件
   - 新建在这个目录下的文件会在系统重启后自动清除
### 03-相对路径和绝对路径
               ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671207136389-950deb3e-6145-410b-804a-8518f874dc68.png#averageHue=%23320c26&clientId=u6d5f4c1d-808e-4&from=paste&height=424&id=ddodr&name=image.png&originHeight=569&originWidth=513&originalType=binary&ratio=1&rotation=0&showTitle=false&size=135719&status=done&style=none&taskId=u37fc9cc8-30a2-410b-b8e7-1f9f91330de&title=&width=381.98614501953125)

-  绝对路径
   - 从根目录开始表示的路径，也就是从/开始，例如：/home/itcast
- 对路径
   -   从当前所处的目录开始表示的路径。
   - . 表示当前目录
   - .. 表示当前目录的上一级目录
- Linux中的命令提示符

      ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671207215028-a2fd059b-e272-40df-b35c-8b8af647d149.png#averageHue=%23f5f2ef&clientId=u6d5f4c1d-808e-4&from=paste&height=29&id=FFSJr&name=image.png&originHeight=26&originWidth=589&originalType=binary&ratio=1&rotation=0&showTitle=false&size=12666&status=done&style=none&taskId=u597b316f-0f40-4cc9-935b-b27dede59cf&title=&width=654.444461781302)

   -   itcast: 当前登录的用户
   - @：英文at, 在的意思
   -   itcast-virtual-machine: 主机名
      - 主机名在/etc/hosts这个文件中
   - ~/test/course/day1：当前工作目录, ~表示宿主目录（家目录或者主目录）

可通过：echo ~或者echo $HOME查看当前用户的宿主目录

   - $:表示当前用户为普通用户, #表示当前用户为root用户
## 04-文件和目录操作相关的命令
### 00-常用
```python
cat 			查看文件
vim 			创建文件
mkdir +文件夹名 	创建文件夹
mkdir -p +文件夹名 	创建多级文件夹
rm  +文件 		移除（删除）文件
rm  -d +文件夹  	删除文件夹      
rm -rf 文件夹  	包括删除里面文件（不需要访问）
（正则表达式删除：
1，rm -rf a*   a开头的所有文件夹
2，rm -rf !(a1)  只保留a1 ； 
      rm -rf !(a1|a2)  只保留a1 a2；
）
（少用！！）mv 文件 位置  		移动文件到某个位置
（少用！！）mv 文件 位置/文件 	移动同时进行改名（重命名） 少用！！！！
cp  文件a 位置/文件b  			复制文件到某个位置
cp -r 文件夹    文件夹   		复制文件夹
复制并且改名：cp a  c/c1/b    a复制到c/c1下，并且改名为b

文件修改保存：
1，vim + 文件 打开文件
2，输入 i 进入输入模式
3，esc退出输入模式
4，输入 :wq  或者 :x 保存退出     :q!不保存强制退出

```
### 01-tree命令
以树状形式查看指定目录内容，使用该命令需要安装软件tree
> sudo apt-get update    sudo apt-get install tree

命令使用方法
> tree  --  树形结构显示当前目录下的文件信息

>        tree 目录  -- 树形结构显示指定目录下的文件信息

> **常用： tree -N**

说明: 使用tree命令查看目录内容层次清晰, 一目了然.
tree命令只能查看目录内容, 不能查看普通文件内容.
### 02-ls命令
查看指定目录下的文件信息
使用方法：

- ls  --显示当前目录下文件信息
- ls 目录或文件名  --显示指定目录下文件信息

| 相关参数

-  -a：列出当前目录下的所有文件
   - . 当前目录
   - .. 当前目录的上一级目录
   - 隐藏文件, 以 . 开头的文件名, 如.bashrc
   - 普通文件
- -R：递归方式列出所有目录中的内容
-  -l：列出文件的详细信息, 7部分内容
   -  文件类型（第1个字符）
      - - ：普通文件
      - d ：目录
      - l ：  符号链接，相当于windows中的快捷方式
      - s ：套接字
      - p ：管道
      - b ：块设备
      - c ：字符设备
   - 用户的操作权限（2 – 10个字符）
      - 文件所有者对文件的操作权限（2,3,4个字符）
      - 文件所属组用户对文件的操作权限（5,6,7个字符）
      - 其他人对文件的操作权限（8,9,10个字符）
   - 硬链接计数:
      - 对于目录来说, 链接计数等于该目录下所有的目录总数(含. 和 ..), 但是不包含该目录的子目录下的目录文件数量, 执行ls -la命令可以进行查看.
      -  对于文件来说, 指的是该文件所有的硬链接文件数量
   - 文件所有者： itcast
   - 文件所属组： itcast
   - 文件大小： 36
      - 如果是目录: 只表示目录大小, 不包含目录中的内容, 目录大小为4k
      - 如果是文件：表示文件大小
   - 文件的创建日期或最后修改时间：10月 13 11:41
   - 文件名：test.log
- 参数之间可以结合使用：
   -  ls -la : 列出当前目录下所有文件的相信信息, 包括隐藏文件
   -  ls -ltr: 列出当前目录下的文件, 按照时间逆向排序
- 文件所有者, 所属组, 其他人的概念

![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671207974072-891f3a23-5016-47fe-b957-6dce24056b62.png#averageHue=%23e2e1e0&clientId=u6d5f4c1d-808e-4&from=paste&height=322&id=hzTwG&name=image.png&originHeight=290&originWidth=254&originalType=binary&ratio=1&rotation=0&showTitle=false&size=21150&status=done&style=none&taskId=u5b88832f-23db-4917-a001-6e990f5227d&title=&width=282.2222296985581)

- 下图是ls -l命令截图

![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671207992865-9261bbaf-2e6c-4c84-b6d0-f7acdf8d6df3.png#averageHue=%239ec683&clientId=u6d5f4c1d-808e-4&from=paste&height=395&id=oMrPW&name=image.png&originHeight=493&originWidth=715&originalType=binary&ratio=1&rotation=0&showTitle=false&size=171303&status=done&style=none&taskId=u351452bb-63c5-45d4-93be-db4c2708d85&title=&width=573.53125)
### 03-cd 命令
切换目录(change directory), 命令使用方式：cd + 路径
路径可以使用相对路径或者绝对路径
cd  /home/itcast   绝对路径(从根目录开始)
cd  ./itcast/test    相对路径(从当前工作目录开始)

- 切换到家目录（例如: /home/itcast）
   - cd
   - cd ~
   - cd /home/itcast
   - cd $HOME
- 临近两个目录直接切换 

cd – 相互切换
> 如开始在: /home/itcast/test/course/day1/test目录下, 执行了cd命令切换到家目录下, 然后在执行cd -又回到了/home/itcast/test/course/day1/test下.

### 04-pwd命令
查看用户当前所处的工作目录, printf working directory
### 05-which命令
显示命令(源码)所在的目录, 如which ls   which cp 
### 06-touch命令
如果文件不存在, 创建新文件, 如果文件存在, 更新文件的最后修改时间。
命令使用方式：touch 文件名
### 07-mkdir命令
创建新目录, make directory
创建方式：mkdir目录名
如果创建多级目录需要添加参数 -p
> 例   在当前目录下创建目录:  mkdir mydir
> 在宿主目录下创建多级目录:  mkdir -p ~/test/hello/world/aa

### 08-rmdir命令
删除空目录，只能删除空目录，使用方式：rmdir 目录名
### 09-rm命令
强制删除整个文件夹(包含内容)：rm -r -f 目录
删除文件： rm 文件名
删除目录： rm  -r 目录名
参数：

   - -r：递归删除目录，删除目录必须添加此参数
   - -i：提示用户是否删除文件或目录
   - -f：强制删除

**常用：rm -rf  文件/文件夹**
注意事项：
使用rm命令删除的文件或目录不会放入回收站中，数据不易恢复。
### 10-cp 命令
命令使用方式：cp 源目录或文件目标目录或文件
若有目录的拷贝需要使用-r参数
cp 要拷贝的文件（file1） file（不存在）
创建file，将file1中的内容拷贝到file eg： cp 1.txt 2.txt
cp file1 file（存在）
file1覆盖file
cp file dir（存在）
拷贝file到dir目录
cp -r dir（存在） dir1（存在）   
将dir目录拷贝到dir1目录中
包括dir目录
cp -r dir（存在） dir1（不存在）
创建dir1
将dir中的内容拷贝到dir1中, 不包括dir目录
cp 拷贝目录也可以用-a参数, 这样可以保留被拷贝的文件的一些属性信息
### 11-mv命令
改名或者移动文件 mv file1 file2
改名
mv file（存在） file1（不存在）
mv dir（存在） dir1（不存在）
mv file（存在） file2（存在）
file文件覆盖file2文件,file改名为file2
移动(第二个参数一定是目录文件)
mv file（文件） dir（存在目录）
将file文件移动到dir中
mv dir（目录存在） dir1（目录存在）
将dir移动到dir1中, dir就会作为dir1的子目录而存在
### 11-cat命令
将文件内容一次性输出到终端。
使用方式： cat 文件名
缺点：终端显示的内容有限，如果文件太长无法全部显示。
可用于文件重定向: cat file1>file2, 相当于cp file1 file2
### 12-more命令
文件内容分页显示到终端，但是只能一直向下浏览，不能回退。
使用方式：more + 文件名
相关操作：
显示下一行：回车
显示下一页：空格
退出：q（ctrl + c）
### 13-less命令
文件内容分页显示到终端，可以自由上下浏览。
使用方式：less 文件名
相关操作：
显示下一行：回车、ctrl + p、键盘向下键
显示上一行：ctrl + n、键盘向上键
显示下一页：空格、PageDown
显示上一页：PageUp
退出：q
### 14-head命令
从文件头部开始查看前n行的内容
使用方式：head -n[行数] 文件名
head -20 hello.txt
如果没有指定行数，默认显示前10行内容
### 15-tail命令
从文件尾部向上查看最后n行的内容
使用方式：tail -n[行数] 文件名
如果没有指定行数，默认显示最后10行内容
一个比较重要的应用：显示日志 : tail -f test.log
一个终端tail -f test.log , 另一个终端: echo “hello world” >>test.log
### 16-软链接
软连接类似于windows下的快捷方式
如何创建软连接
ln -s 文件名快捷方式的名字
例如：ln -s aa.soft aa
目录也可以创建软连接
例如：ln -s tmp.link tmp
创建软链接应注意事项
ln创建软连接要用绝对路径，因为如果不使用绝对路径，一旦这个连接文件发生位置变动，就不能找到那个文件了。
软连接文件的大小是: 路径+文件名的总字节数
### 17-硬链接
ln 文件名硬链接的名字
ln test.log test.log.hard
使用硬链接应注意事项

   - 硬链接不能建在目录上
   - 硬连接对绝对路径没有要求
   - 硬连接不能跨文件系统
   - 硬链接文件和源文件的inode是相同的，文件系统的inode要求唯一，跨文件系统可能会使inode不同, 所以硬链接不能跨文件系统

硬链接的本质
硬连接的本质是不同的文件名所在的inode节点是相同的，相同的inode节点指向了相同的数据块，所以他们的文件内容是一样的，文件内容会同步。

      - ls -i 文件名 ----可以查看文件的i节点
      - stat 文件名---可以查看i节点信息

如下图, file.hard是file的硬链接, 这个两个文件指向了同一个inode, 同一个inode指向了相同的数据块(文件内容).
![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671246434652-3bd57e8c-1f5f-45b2-8da3-88cf6bc26574.png#averageHue=%23fefdfd&clientId=ua0f55837-4533-4&from=paste&height=322&id=CM2Up&name=image.png&originHeight=322&originWidth=240&originalType=binary&ratio=1&rotation=0&showTitle=false&size=16097&status=done&style=none&taskId=udef641dd-0e9f-4c18-839d-22cbfc60228&title=&width=240)

   - 当新创建了一个文件, 硬链接计数为1
   - 给文件创建了一个硬链接后, 硬链接计数加1
   - 删除一个硬链接后, 硬链接计数减1
   - 如果删除硬链接后, 硬链接计数为0, 则该文件会删除

硬链接应用场合

   - 可以起到同步文件的作用
      - 修改file的内容, 会在其余三个硬链接文件上同步.
   - 可以起到保护文件的作用
      - 删除文件的时候, 只要硬链接计数不为0, 不会真正删除, 起到保护文件的作用.
### 18-wc 
显示文件行数, 字节数, 单词数
wc -l file显示文件的总行数
wc -c file显示文件的总字节数
wc -w file显示文件的总单词数
wc file 显示文件的总行数, 单词数和总字节数 第一个是显示行数很常用
### 19-whoami
who am I 显示当前用户名登录信息等
显示当前登陆的用户名
## 05-用户权限、用户、用户组
### 01-修改文件权限chmod
linux是通过权限对文件进行控制的, 通过使用chmod命令可以修改文件相关的权限.

- 文字设定法
   - 命令：chmod [who] [+|-|=] [mode] 文件名
      - 操作对象【who】
         - u-- 用户（user）
         - g -- 同组用户（group）
         - o -- 其他用户（other）
         - a -- 所用用户（all）【默认】
      - 操作符【+-=】
         - + -- 添加权限
         - - -- 取消权限
         - = -- 赋予给定权限并取消其他权限
      - 权限【mode】
         - r -- 读
         - w -- 写
         - x -- 执行
      - 示例：给文件file.txt的所有者和所属组添加读写权限
         - chmod ug+wr file.txt
- **数字设定法**
   - 命令：chmod [+|-|=][mode] 文件名
      - 操作符【+-=】
         - + -- 添加权限
         - - -- 取消权限
         - = -- 赋予给定权限并取消其他权限 (默认为=)
      - 数字表示的含义
         - 0 -- 没有权限(-)
         - 1 -- 执行权限（x）
         - 2 -- 写权限（w）
         - 4 -- 读权限（r)
   - 例：给file.txt文件设置rw-rw-r--
      - chmod 664 file.txt
      - chmod 777 a1.txt 设置所有权限

  注意点: 使用数字设定法, 一定要使用3位的8进制数: 如:066
### 02-修改文件所有者和所属组

- 修改文件所有者chown
   - 用法：chown 文件所有者文件名
      - sudo chown mytest file.txt
- 修改文件所有者和所属组chown
   - 用法：chown 文件所有者:文件所属组文件名
      - sudo chown mytest:mytest file.txt
      - sudo chown mytest.mytest file.txt

注意:普通用户需要使用管理员用户权限执行该命令
注意: 若系统没有其他用户, 可以使用sudo adduser 用户名创建一个新用户.
### 03-修改文件所属组

- chgrp命令
- 使用方法：chgrp 用户组文件或目录名
   - 示例：修改文件所属组为mytest
   - sudo chgrp mytest file.txt

普通用户需要使用管理员权限执行该命令。
## 06-find命令
### 01-按文件名查询：使用参数 -name

   - 命令：find  路径  -name   "文件名"
   - 示例：
      - find /home -name "*.c"
      - Find -name “a.xxx” 在当前目录下查找
### 02-按文件类型查询：使用参数 -type

   1. 命令：find 路径 -type 类型
   2. 类型         
      1. f-> 普通文件
      2. d -> 目录
      3. l -> 符号链接
      4. b -> 块设备文件
      5. c -> 字符设备文件
      6. s -> socket文件
      7. p -> 管道文件
   3. 查找指定目录下的普通文件： find 路径 -type f
### 03-按文件大小查询：使用参数 -size

   4. 命令：find  路径  -size  范围
      1. 范围
         1. 大于：+表示 --  +100k
         2. 小于：-表示  --  -100k
         3. 等于: 不需要添加符号 --  100k
      2. 大小
         1. M 必须大写（10M）
         2. k 必须小写（20k）
         3. c 表示字节数
      3. 例子: 查询目录为家目录
         1. 等于100k的文件:  find ~/ -size 100k
         2. 大于100k的文件:  find ~/ -size +100k
         3. 大于50k, 小于100k的文件:  find ~/ -size +50k -size -100k
### 04-按文件日期

   5. 创建日期：-ctime -n/+ n
      1. -n: n天以内
      2. +n: n天以外
   6. 修改日期：-mtime -n/+n
   7. 访问日期：-atime -n/+n
### 05-按深度

   8. -maxdepth n(层数）
      1. 搜索n层以下的目录, 搜索的层数不超过n层
   9. -mindepth n（层数）
      1. 搜搜n层以上的目录,搜索的层数不能小于n层
### 06-高级查找

   10. 例：查找指定目录下所有目录，并列出目录中文件详细信息
   - find ./ -type d -exec shell命令 {} \;
   - find ./ -type d -exec ls -l {} \;
   - find ./ -type d -ok shell命令 {} \;
   - find ./ -type d -ok ls -l {} \;
   - 注意: {}中间不能有空格
   - ok比较安全, 特别是在执行rm删除文件的时候.
   - find ./ -type d | xargs shell命令
   - find ./ -type d | xargs ls -l
## 07-grep命令(查找文字内有对应字符的)
### 01-grep -r（有目录） “查找的内容” 搜索的路径

   1. -r参数, 若是目录, 则可以递归搜索
   2. -n参数可以显示该查找内容所在的行号
   3. -i参数可以忽略大小写进行查找
   4. -v参数不显示含有某字符串
### 02-搜索当前目录下包含hello world字符串的文件

   1. grep -r -n "hello world" ./     ------显示行号
   2. grep -r -i -n "HELLO world" ./  -------忽略大小小查找

 
## 08-find和grep命令结合使用
先使用find命令查找文件, 然后使用grep命令查找哪些文件包含某个字符串

   1. find . -name "*.c" | xargs grep -n "main"
   2. find -name "*.txt" | xargs grep -r  "aplle"  
      1. -r是递归查找

 
## 09-Linux中常用的压缩工具
### 01-gzip和bzip2
不能压缩目录，只能一个一个文件进行压缩，压缩之后会使原文件消失

   1. gzip *    压缩当前目录下所有的文件, 但是目录不能压缩
   2. gunzip *  解压当前目录下所有的.gz文件
   3. bzip2 *   压缩当前目录下所有的文件, 但是目录不能压缩
   4. bunzip2 * 解压当前目录下所有的.bz2文件
### 02-tar工具
相关参数说明

   - z：用gzip来压缩/解压缩文件
   - j：用bzip2来压缩/解压缩文件
   - c：create, 创建新的压缩文件, 与x互斥使用
   - x：从压缩文件中释放文件, 与c互斥使用
   - v：详细报告tar处理的文件信息
   - f：指定压缩文件的名字
   - t:  查看压缩包中有哪些文件

压缩：

   - tar cvf 压缩包名字.tar 原材料[要打包压缩的文件或目录]
   - tar zcvf 压缩包名字.tar.gz 原材料[要打包压缩的文件或目录]
   - tar jcvf 压缩包名字.tar.bz2 原材料[要打包压缩的文件或目录]

解压缩：

   - tar  xvf   已有的压缩包（test.tar.gz）
   - tar  zxvf  已有的压缩包（test.tar.gz）
   - tar  jxvf  已有的压缩包（test.tar.bz2）
   - 解压到指定目录：添加参数 -C（大写）
      - tar zxvf test.tar.gz -C 解压目录（./mytest）

查看压缩包中有哪些文件

   - tar -tvf test.tar
### 03-rar工具
使用前需要安装 rar 工具
sudo apt-get install rar

1. 压缩：
   1. 命令： rar a -r 要压缩的文件(含文件或者目录)
      1. 压缩目录需要使用参数：-r
      2. rar a -r my aa bb dir  ----将aa bb dir压缩到my.rar文件中
   2. 打包的生成的新文件不需要指定后缀
2. 解压缩：
   1. 命令：rar x xxx.rar 压缩目录

rar x my.rar  ----将my.rar解压到当前目录

   2. 解压到指定目录, 直接指定解压目录即可
      1. rar x xxx.rar目录
      2. rar x my.rar TAR  -----将my.rar解压到TAR目录下
3. 注意：若解压目录不存在则会报错
### 04-zip工具

1. 压缩：zip -r 压缩包名要压缩的文件(含文件或目录)
   1. 压缩目录需要使用参数-r
   2. 使用该命令不需要指定压缩包后缀
      1. zip -r xxx file dir ---生成xxx.zip文件
2. 解压缩：unzip压缩包名
   1. 解压缩到指定目录：添加参数 –d 解压目录
      1. unzip xxx.zip -d /home/itcast/test/day1
      2. 注意：解压目录若不存在则会创建．
## 10-软件的安装和卸载
### 01-在线安装 apt-get是Ubuntu的

1. 软件安装：sudo apt-get install 软件名
2. 软件卸载：sudo apt-get remove 软件名
3. 更新软件列表：sudo apt-get update
4. 清理安装包：sudo apt-get clean
   1. 清理的是缓存路径：/var/cache/apt/archives
### 02-软件包安装

1. 在Ubuntu系统下必须有deb格式的安装包
2. 软件安装
   1. sudo dpkg -i xxx.deb
3. 软件卸载
   1. sudo dpkg -r 软件名

# 02- Vim和GCC
## 01-vim
### 01-vim简单介绍

1. vi是”visual interface”的简称, 它在Linux上的地位就仿佛Windows中的记事本一样. 它可以执行编辑、删除、查找、替换、块操作等众多文本操作, 而且用户可以根据自己的需要对其进行定制. vi是一个文本编辑程序, 没有菜单, 只有命令. 
2. vim更高级一些, 可以理解是vi的高级版本.
3. vim需要自行安装, 在shell中输入vimtutor命令可以查看相关的帮助文档.
### 02-vim的三种模式
Vi有三种基本工作模式: 命令模式、文本输入模式、末行模式。
三种工作模式的切换如图所示, 从下图中可以看出编辑模式和末行模式之间不能相互切换, 必须经过命令模式.
![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671248974072-6a232361-43fa-494b-857b-e6723c47b7ea.png#averageHue=%23fafafa&clientId=udabe5b67-2304-4&from=paste&height=456&id=lEI8K&name=image.png&originHeight=456&originWidth=556&originalType=binary&ratio=1&rotation=0&showTitle=false&size=67051&status=done&style=none&taskId=uc81b2792-3841-498a-8990-c55354e867c&title=&width=556)
### 03-vim基本操作
#### 01-命令模式下的操作
用户按下esc键, 就可以使vi进入命令模式下; 当使用vi打开一个新文件开始也是进入命令模式下.

- 保存退出 (不要 用ctrl+z 这是不正常的退出 用 两个大写的ZZ)
- 代码格式化 gg=G
- 光标移动
| **快捷键** | **操作** |
| --- | --- |
| **h** | 光标左移 |
| **j** | 光标下移 |
| **k** | 光标上移 |
| **l** | 光标右移 |
| **w** | 移动一个单词 |
| **gg** | 光标移动到文件开头 |
| **G** | 光标移动到文件末尾 |
| **0** | 光标移到到行首 |
| **$** | 光标移到到行尾 |
| **nG** | 行跳转, 例12G, 跳到12行处 |

- 删除命令
| **快捷键** | **操作** |
| --- | --- |
| **x** | 删除光标后一个字符,相当于 Del |
| **X** | 删除光标前一个字符,相当于 Backspace |
| **dw** | 删除光标开始位置的字,包含光标所在字符 |
| **d0** | 删除光标前本行所有内容,不包含光标所在字符 |
| **D[d$]** | 删除光标后本行所有内容,包含光标所在字符 |
| **dd** | 删除光标所在行(本质其实是剪切) |
| **ndd** | 从光标当前行向下删除指定的行数, 如15dd |
| **v/ctrl+v** | 使用h、j、k、l移动选择内容, 然后按d删除其中ctrl+v是列模式, v为非列模式 |

- 撤销和反撤销命令
| **快捷键** | **操作** |
| --- | --- |
| **u** | 一步一步撤销, 相当于word文档的ctrl+z |
| **ctrl-r** | 反撤销, 相当于word文档的ctrl+y |

- 复制粘贴
| **快捷键** | **操作** |
| --- | --- |
| **yy** | 复制当前行 |
| **nyy ** | 复制n行, 如10yy |
| **p** | 在光标所在位置向下新开辟一行, 粘贴 |
| **P** | 在光标所在位置向上新开辟一行, 粘贴 |
| **剪切**
**操作** | 按dd或者ndd删除, 将删除的行保存到剪贴板中, 然后按p/P就可以粘贴了 |

- 可视模式
| **快捷键** | **操作** |
| --- | --- |
| **v/ctrl+v** | 使用h、j、k、l移动选择内容;
使用d删除（是剪切）
使用y复制 
使用p粘贴到光标的后面
使用P粘贴到光标的前面 |

- 替换操作
| **快捷键** | **操作** |
| --- | --- |
| **r** | 替换当前字符 |
| **R ** | 替换当前行光标后的字符 |

- 查找命令 搜到后按n/N下上搜索。
| **快捷键** | **操作** |
| --- | --- |
| **/** | /xxxx, 从光标所在的位置开始搜索, 按n向下搜索, 按N向上搜索 |
| **?** | ?xxxx, 从光标所在的位置开始搜索, 按n向上搜索, 按N向下搜索 |
| **#** | 将光标移动到待搜索的字符串上, 然后按n向上搜索,但N向下搜索 |
| **shift+k** | 在待搜索的字符串上按shift+k或者K, 可以查看相关的帮助文档 |

#### 02-切换到文本输入模式
从命令模式切换到文本输入模式只需输入如下命令:

| **快捷键** | **操作** |
| --- | --- |
| **i** | 在光标前插入 |
| **a** | 在光标后插入 |
| **I** | 在光标所在行的行首插入 |
| **A** | 在光标所在行的行尾插入 |
| **o** | 在光标所在的行的下面新创建一行, 行首插入 |
| **O** | 在光标所在的行的上面新创建一行, 行首插入 |
| **s** | 删除光标后边的字符, 从光标当前位置插入 |
| **S** | 删除光标所在当前行, 从行首插入 |
| **按列模式插入** | 先按ctrl+v进入列模式, 按hjkl移动选定某列,按I或者shift+i向前插入, 然后插入字符, 最后按两次esc. |

#### 03-末行模式下的操作
从命令模式切换到末行模式, 输入冒号(:)

- 保存退出
| **快捷键** | **操作** |
| --- | --- |
| q | 退出 |
| q! | 强制退出，不保存修改内容 |
| w | 保存修改内容, 不退出 |
| wq | 保存并退出 |
| x | 相当于wq |

- 替换操作（全局替换）

下面表格中old表示原字符串, new表示新字符串

| **快捷键** | **操作** |
| --- | --- |
| :s/old/new/ | 光标所在行的第一个old替换为new |
| :s/old/new/**g** | 光标所在行的所有old替换为new |
| :m, ns/old/new/g | 将第m行至第n行之间的old全部替换成new |
| :%s/old/new/g | 当前文件的所有old替换为new |
| :1,$s/old/new/g | 当前文件的所有old替换为new |
| :%s/old/new/g**c** | 同上，但是每次替换需要用户确认 |

- 快速翻屏 （ 这不是在末行模式 是在命令模式下）
| **  快捷键** | **操作** |
| --- | --- |
| ctrl + u | 向下翻半屏(up)--光标向上移动 |
| ctrl + d | 向上翻半屏(down)--光标向下移动 |
| ctrl + f | 向上翻一屏(front) （下） |
| ctrl + b | 向后翻一屏(back) (上） |

- 在末行模式下执行shell命令

!shell命令
按下两次esc可以回到命令模式

- 分屏操作
   - 在打开文件之后分屏:
| **快捷键** | **操作** |
| --- | --- |
| sp | 当前文件水平分屏 |
| vsp | 当前文件垂直分屏 |
| sp 文件名 | 当前文件和另一个文件水平分屏 |
| vsp 文件名 | 当前文件和另一个文件垂直分屏 |
| ctrl-w-w | 在多个窗口切换光标 |
| wall/wqall/xall/qall/qall! | 保存/保存退出/保存退出/退出/强制退出分屏窗口 |

   - 在打开文件之前分屏:

分屏: vim -on file1 file2 …  
垂直分屏: vim -On file1 file2…   垂直分屏
注意: n可以省略, 有几个文件就分几屏

- 从末行模式切换回命令模式

按两次ESC, 退格(backspace)或者回车键
