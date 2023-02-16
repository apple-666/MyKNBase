<a name="gTveI"></a>
# 01-Linux 常用基础命令
<a name="O9wkJ"></a>
## 01-命令解析器

- shell就是命令解释器
- 命令解析器的作用：对用户输入到终端的命令进行解析，调用对应的执行程序。

                     ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671206101203-f3e4f37a-73dd-4394-883a-a37d0e9023ec.png#averageHue=%23fefdfc&clientId=u6d5f4c1d-808e-4&from=paste&height=313&id=u3b035cc6&name=image.png&originHeight=290&originWidth=188&originalType=binary&ratio=1&rotation=0&showTitle=false&size=13029&status=done&style=none&taskId=u2c573555-985f-40a2-b345-167e6f15c49&title=&width=202.88890075683594)<br />用户在终端输入命令, 由shell命令解释器对命令进行解析(按照$PATH环境变量搜索命令), 解析成内核能够识别的指令, 然后由内核执行命令, 最后由终端显示命令执行的结果给用户.<br />注意：shell在寻找命令的时候是按照$PATH环境变量去查找的，如果找到了就执行对应的命令，若找不到就报错, 执行echo $PATH可以查看PATH环境变量的值.<br /> 

- 常用的命令解析器：
   - shell -- Bourne Shell
      - /bin/sh	
   - bash -- Bourne Again Shell
      - /bin/bash
- 当前系统所使用的shell
   - echo $SHELL
- 当前系统下有哪些shell
   - cat /etc/shells

<a name="qRW57"></a>
## 02-Linux下常用快捷键
<a name="wnYf0"></a>
### 01 tab键

- 补齐命令

如:在终端输入his然后按tab键, 会补齐history命令;<br />如:输入l然后按tab键, 会显示所有以l开头的命令.

- 补齐文件(包括目录和文件)

例如: 如果在执行ls, 然后按tab键, 会显示当前目录下所有的文件<br />使用tab键的优点: 减少用户输入, 加快输入速度, 减少出错的机会。
<a name="JTjtu"></a>
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
<a name="pxLbL"></a>
## 03-linux下的目录结构
<a name="UnV3i"></a>
### 01-linux系统的目录结构

- Linux系统的目录结构是一个倒立的树状结构, 根目录用/表示，对比windows目录结构理解linux的目录结构。
- ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671206841712-9311699b-e1f8-4e8b-95e0-41169e18a0ef.png#averageHue=%23fcfcfc&clientId=u6d5f4c1d-808e-4&from=paste&height=359&id=u479c0d2e&name=image.png&originHeight=323&originWidth=751&originalType=binary&ratio=1&rotation=0&showTitle=false&size=69703&status=done&style=none&taskId=uf7253497-b55d-4d2a-a55f-20d5b6f9268&title=&width=834.4444665496737)
<a name="q9eqW"></a>
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
<a name="fVXyL"></a>
### 03-相对路径和绝对路径
               ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671207136389-950deb3e-6145-410b-804a-8518f874dc68.png#averageHue=%23320c26&clientId=u6d5f4c1d-808e-4&from=paste&height=424&id=u6e3e1a02&name=image.png&originHeight=569&originWidth=513&originalType=binary&ratio=1&rotation=0&showTitle=false&size=135719&status=done&style=none&taskId=u37fc9cc8-30a2-410b-b8e7-1f9f91330de&title=&width=381.98614501953125)

-  绝对路径
   - 从根目录开始表示的路径，也就是从/开始，例如：/home/itcast
- 对路径
   -   从当前所处的目录开始表示的路径。
   - . 表示当前目录
   - .. 表示当前目录的上一级目录
- Linux中的命令提示符

      ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671207215028-a2fd059b-e272-40df-b35c-8b8af647d149.png#averageHue=%23f5f2ef&clientId=u6d5f4c1d-808e-4&from=paste&height=29&id=ue1f9fcfa&name=image.png&originHeight=26&originWidth=589&originalType=binary&ratio=1&rotation=0&showTitle=false&size=12666&status=done&style=none&taskId=u597b316f-0f40-4cc9-935b-b27dede59cf&title=&width=654.444461781302)

   -   itcast: 当前登录的用户
   - @：英文at, 在的意思
   -   itcast-virtual-machine: 主机名
      - 主机名在/etc/hosts这个文件中
   - ~/test/course/day1：当前工作目录, ~表示宿主目录（家目录或者主目录）

可通过：echo ~或者echo $HOME查看当前用户的宿主目录

   - $:表示当前用户为普通用户, #表示当前用户为root用户
<a name="FHZ6U"></a>
## 04-文件和目录操作相关的命令
<a name="n8lMh"></a>
### 01-tree命令
以树状形式查看指定目录内容，使用该命令需要安装软件tree
> sudo apt-get update    sudo apt-get install tree

命令使用方法
> tree  --  树形结构显示当前目录下的文件信息

>        tree 目录  -- 树形结构显示指定目录下的文件信息

> **常用： tree -N**

说明: 使用tree命令查看目录内容层次清晰, 一目了然.<br />tree命令只能查看目录内容, 不能查看普通文件内容.
<a name="Lmnbp"></a>
### 02-ls命令
查看指定目录下的文件信息<br />使用方法：

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

![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671207974072-891f3a23-5016-47fe-b957-6dce24056b62.png#averageHue=%23e2e1e0&clientId=u6d5f4c1d-808e-4&from=paste&height=322&id=u74f95166&name=image.png&originHeight=290&originWidth=254&originalType=binary&ratio=1&rotation=0&showTitle=false&size=21150&status=done&style=none&taskId=u5b88832f-23db-4917-a001-6e990f5227d&title=&width=282.2222296985581)

- 下图是ls -l命令截图

![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671207992865-9261bbaf-2e6c-4c84-b6d0-f7acdf8d6df3.png#averageHue=%239ec683&clientId=u6d5f4c1d-808e-4&from=paste&height=395&id=u356ed5ad&name=image.png&originHeight=493&originWidth=715&originalType=binary&ratio=1&rotation=0&showTitle=false&size=171303&status=done&style=none&taskId=u351452bb-63c5-45d4-93be-db4c2708d85&title=&width=573.53125)
<a name="H7Up1"></a>
### 03-cd 命令
切换目录(change directory), 命令使用方式：cd + 路径<br />路径可以使用相对路径或者绝对路径<br />cd  /home/itcast   绝对路径(从根目录开始)<br />cd  ./itcast/test    相对路径(从当前工作目录开始)

- 切换到家目录（例如: /home/itcast）
   - cd
   - cd ~
   - cd /home/itcast
   - cd $HOME
- 临近两个目录直接切换 

cd – 相互切换
> 如开始在: /home/itcast/test/course/day1/test目录下, 执行了cd命令切换到家目录下, 然后在执行cd -又回到了/home/itcast/test/course/day1/test下.

<a name="hP6rf"></a>
### 04-pwd命令
查看用户当前所处的工作目录, printf working directory
<a name="m32pO"></a>
### 05-which命令
显示命令(源码)所在的目录, 如which ls   which cp 
<a name="h02Qu"></a>
### 06-touch命令
如果文件不存在, 创建新文件, 如果文件存在, 更新文件的最后修改时间。<br />命令使用方式：touch 文件名
<a name="tHIbo"></a>
### 07-mkdir命令
创建新目录, make directory<br />创建方式：mkdir目录名<br />如果创建多级目录需要添加参数 -p
> 例   在当前目录下创建目录:  mkdir mydir
> 在宿主目录下创建多级目录:  mkdir -p ~/test/hello/world/aa

<a name="m9CnO"></a>
### 08-rmdir命令
删除空目录，只能删除空目录，使用方式：rmdir 目录名
<a name="JzpxM"></a>
### 09-rm命令
强制删除整个文件夹(包含内容)：rm -r -f 目录<br />删除文件： rm 文件名<br />删除目录： rm  -r 目录名<br />参数：

   - -r：递归删除目录，删除目录必须添加此参数
   - -i：提示用户是否删除文件或目录
   - -f：强制删除

**常用：rm -rf  文件/文件夹**<br />注意事项：<br />使用rm命令删除的文件或目录不会放入回收站中，数据不易恢复。
<a name="zy8hO"></a>
### 10-cp 命令
命令使用方式：cp 源目录或文件目标目录或文件<br />若有目录的拷贝需要使用-r参数<br />cp 要拷贝的文件（file1） file（不存在）<br />创建file，将file1中的内容拷贝到file eg： cp 1.txt 2.txt<br />cp file1 file（存在）<br />file1覆盖file<br />cp file dir（存在）<br />拷贝file到dir目录<br />cp -r dir（存在） dir1（存在）   <br />将dir目录拷贝到dir1目录中<br />包括dir目录<br />cp -r dir（存在） dir1（不存在）<br />创建dir1<br />将dir中的内容拷贝到dir1中, 不包括dir目录<br />cp 拷贝目录也可以用-a参数, 这样可以保留被拷贝的文件的一些属性信息
<a name="of0Ic"></a>
### 11-mv命令
改名或者移动文件 mv file1 file2<br />改名<br />mv file（存在） file1（不存在）<br />mv dir（存在） dir1（不存在）<br />mv file（存在） file2（存在）<br />file文件覆盖file2文件,file改名为file2<br />移动(第二个参数一定是目录文件)<br />mv file（文件） dir（存在目录）<br />将file文件移动到dir中<br />mv dir（目录存在） dir1（目录存在）<br />将dir移动到dir1中, dir就会作为dir1的子目录而存在
<a name="v0JK6"></a>
### 11-cat命令
将文件内容一次性输出到终端。<br />使用方式： cat 文件名<br />缺点：终端显示的内容有限，如果文件太长无法全部显示。<br />可用于文件重定向: cat file1>file2, 相当于cp file1 file2
<a name="l190Q"></a>
### 12-more命令
文件内容分页显示到终端，但是只能一直向下浏览，不能回退。<br />使用方式：more + 文件名<br />相关操作：<br />显示下一行：回车<br />显示下一页：空格<br />退出：q（ctrl + c）
<a name="LL6EK"></a>
### 13-less命令
文件内容分页显示到终端，可以自由上下浏览。<br />使用方式：less 文件名<br />相关操作：<br />显示下一行：回车、ctrl + p、键盘向下键<br />显示上一行：ctrl + n、键盘向上键<br />显示下一页：空格、PageDown<br />显示上一页：PageUp<br />退出：q
<a name="sGotO"></a>
### 14-head命令
从文件头部开始查看前n行的内容<br />使用方式：head -n[行数] 文件名<br />head -20 hello.txt<br />如果没有指定行数，默认显示前10行内容
<a name="JuT6c"></a>
### 15-tail命令
从文件尾部向上查看最后n行的内容<br />使用方式：tail -n[行数] 文件名<br />如果没有指定行数，默认显示最后10行内容<br />一个比较重要的应用：显示日志 : tail -f test.log<br />一个终端tail -f test.log , 另一个终端: echo “hello world” >>test.log
<a name="GxPla"></a>
### 16-软链接
软连接类似于windows下的快捷方式<br />如何创建软连接<br />ln -s 文件名快捷方式的名字<br />例如：ln -s aa.soft aa<br />目录也可以创建软连接<br />例如：ln -s tmp.link tmp<br />创建软链接应注意事项<br />ln创建软连接要用绝对路径，因为如果不使用绝对路径，一旦这个连接文件发生位置变动，就不能找到那个文件了。<br />软连接文件的大小是: 路径+文件名的总字节数
<a name="F7f59"></a>
### 17-硬链接
ln 文件名硬链接的名字<br />ln test.log test.log.hard<br />使用硬链接应注意事项

   - 硬链接不能建在目录上
   - 硬连接对绝对路径没有要求
   - 硬连接不能跨文件系统
   - 硬链接文件和源文件的inode是相同的，文件系统的inode要求唯一，跨文件系统可能会使inode不同, 所以硬链接不能跨文件系统

硬链接的本质<br />硬连接的本质是不同的文件名所在的inode节点是相同的，相同的inode节点指向了相同的数据块，所以他们的文件内容是一样的，文件内容会同步。

      - ls -i 文件名 ----可以查看文件的i节点
      - stat 文件名---可以查看i节点信息

如下图, file.hard是file的硬链接, 这个两个文件指向了同一个inode, 同一个inode指向了相同的数据块(文件内容).<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671246434652-3bd57e8c-1f5f-45b2-8da3-88cf6bc26574.png#averageHue=%23fefdfd&clientId=ua0f55837-4533-4&from=paste&height=322&id=ubb93daf7&name=image.png&originHeight=322&originWidth=240&originalType=binary&ratio=1&rotation=0&showTitle=false&size=16097&status=done&style=none&taskId=udef641dd-0e9f-4c18-839d-22cbfc60228&title=&width=240)

   - 当新创建了一个文件, 硬链接计数为1
   - 给文件创建了一个硬链接后, 硬链接计数加1
   - 删除一个硬链接后, 硬链接计数减1
   - 如果删除硬链接后, 硬链接计数为0, 则该文件会删除

硬链接应用场合

   - 可以起到同步文件的作用
      - 修改file的内容, 会在其余三个硬链接文件上同步.
   - 可以起到保护文件的作用
      - 删除文件的时候, 只要硬链接计数不为0, 不会真正删除, 起到保护文件的作用.
<a name="P29h3"></a>
### 18-wc 
显示文件行数, 字节数, 单词数<br />wc -l file显示文件的总行数<br />wc -c file显示文件的总字节数<br />wc -w file显示文件的总单词数<br />wc file 显示文件的总行数, 单词数和总字节数 第一个是显示行数很常用
<a name="XCXd2"></a>
### 19-whoami
who am I 显示当前用户名登录信息等<br />显示当前登陆的用户名
<a name="iHNRN"></a>
## 05-用户权限、用户、用户组
<a name="r2Kcd"></a>
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
<a name="kUTTf"></a>
### 02-修改文件所有者和所属组

- 修改文件所有者chown
   - 用法：chown 文件所有者文件名
      - sudo chown mytest file.txt
- 修改文件所有者和所属组chown
   - 用法：chown 文件所有者:文件所属组文件名
      - sudo chown mytest:mytest file.txt
      - sudo chown mytest.mytest file.txt

注意:普通用户需要使用管理员用户权限执行该命令<br />注意: 若系统没有其他用户, 可以使用sudo adduser 用户名创建一个新用户.
<a name="ZIjp2"></a>
### 03-修改文件所属组

- chgrp命令
- 使用方法：chgrp 用户组文件或目录名
   - 示例：修改文件所属组为mytest
   - sudo chgrp mytest file.txt

普通用户需要使用管理员权限执行该命令。
<a name="hhhum"></a>
## 06-find命令
<a name="FfjUe"></a>
### 01-按文件名查询：使用参数 -name

   - 命令：find  路径  -name   "文件名"
   - 示例：
      - find /home -name "*.c"
      - Find -name “a.xxx” 在当前目录下查找
<a name="BAws0"></a>
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
<a name="uK68t"></a>
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
<a name="yyHSs"></a>
### 04-按文件日期

   5. 创建日期：-ctime -n/+ n
      1. -n: n天以内
      2. +n: n天以外
   6. 修改日期：-mtime -n/+n
   7. 访问日期：-atime -n/+n
<a name="ZchYf"></a>
### 05-按深度

   8. -maxdepth n(层数）
      1. 搜索n层以下的目录, 搜索的层数不超过n层
   9. -mindepth n（层数）
      1. 搜搜n层以上的目录,搜索的层数不能小于n层
<a name="DkcTt"></a>
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
<a name="Z3kDH"></a>
## 07-grep命令(查找文字内有对应字符的)
<a name="qAKr7"></a>
### 01-grep -r（有目录） “查找的内容” 搜索的路径

   1. -r参数, 若是目录, 则可以递归搜索
   2. -n参数可以显示该查找内容所在的行号
   3. -i参数可以忽略大小写进行查找
   4. -v参数不显示含有某字符串
<a name="TpKh1"></a>
### 02-搜索当前目录下包含hello world字符串的文件

   1. grep -r -n "hello world" ./     ------显示行号
   2. grep -r -i -n "HELLO world" ./  -------忽略大小小查找

 
<a name="Sqmrt"></a>
## 08-find和grep命令结合使用
先使用find命令查找文件, 然后使用grep命令查找哪些文件包含某个字符串

   1. find . -name "*.c" | xargs grep -n "main"
   2. find -name "*.txt" | xargs grep -r  "aplle"  
      1. -r是递归查找

 
<a name="Z3gFQ"></a>
## 09-Linux中常用的压缩工具
<a name="rpSoW"></a>
### 01-gzip和bzip2
不能压缩目录，只能一个一个文件进行压缩，压缩之后会使原文件消失

   1. gzip *    压缩当前目录下所有的文件, 但是目录不能压缩
   2. gunzip *  解压当前目录下所有的.gz文件
   3. bzip2 *   压缩当前目录下所有的文件, 但是目录不能压缩
   4. bunzip2 * 解压当前目录下所有的.bz2文件
<a name="GREvm"></a>
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
<a name="WvE1O"></a>
### 03-rar工具
使用前需要安装 rar 工具<br />sudo apt-get install rar

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
<a name="gTNpg"></a>
### 04-zip工具

1. 压缩：zip -r 压缩包名要压缩的文件(含文件或目录)
   1. 压缩目录需要使用参数-r
   2. 使用该命令不需要指定压缩包后缀
      1. zip -r xxx file dir ---生成xxx.zip文件
2. 解压缩：unzip压缩包名
   1. 解压缩到指定目录：添加参数 –d 解压目录
      1. unzip xxx.zip -d /home/itcast/test/day1
      2. 注意：解压目录若不存在则会创建．
<a name="kKXTQ"></a>
## 10-软件的安装和卸载
<a name="zbxJs"></a>
### 01-在线安装 apt-get是Ubuntu的

1. 软件安装：sudo apt-get install 软件名
2. 软件卸载：sudo apt-get remove 软件名
3. 更新软件列表：sudo apt-get update
4. 清理安装包：sudo apt-get clean
   1. 清理的是缓存路径：/var/cache/apt/archives
<a name="ZJ69e"></a>
### 02-软件包安装

1. 在Ubuntu系统下必须有deb格式的安装包
2. 软件安装
   1. sudo dpkg -i xxx.deb
3. 软件卸载
   1. sudo dpkg -r 软件名

<a name="gxe6V"></a>
# 02- Vim和GCC
<a name="afoyK"></a>
## 01-vim
<a name="c53n0"></a>
### 01-vim简单介绍

1. vi是”visual interface”的简称, 它在Linux上的地位就仿佛Windows中的记事本一样. 它可以执行编辑、删除、查找、替换、块操作等众多文本操作, 而且用户可以根据自己的需要对其进行定制. vi是一个文本编辑程序, 没有菜单, 只有命令. 
2. vim更高级一些, 可以理解是vi的高级版本.
3. vim需要自行安装, 在shell中输入vimtutor命令可以查看相关的帮助文档.
<a name="UnBiH"></a>
### 02-vim的三种模式
Vi有三种基本工作模式: 命令模式、文本输入模式、末行模式。<br />三种工作模式的切换如图所示, 从下图中可以看出编辑模式和末行模式之间不能相互切换, 必须经过命令模式.<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671248974072-6a232361-43fa-494b-857b-e6723c47b7ea.png#averageHue=%23fafafa&clientId=udabe5b67-2304-4&from=paste&height=456&id=u205f1c04&name=image.png&originHeight=456&originWidth=556&originalType=binary&ratio=1&rotation=0&showTitle=false&size=67051&status=done&style=none&taskId=uc81b2792-3841-498a-8990-c55354e867c&title=&width=556)
<a name="gAo56"></a>
### 03-vim基本操作
<a name="GYb1w"></a>
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
| **剪切**<br />**操作** | 按dd或者ndd删除, 将删除的行保存到剪贴板中, 然后按p/P就可以粘贴了 |

- 可视模式
| **快捷键** | **操作** |
| --- | --- |
| **v/ctrl+v** | 使用h、j、k、l移动选择内容;<br />使用d删除（是剪切）<br />使用y复制 <br />使用p粘贴到光标的后面<br />使用P粘贴到光标的前面 |

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

<a name="DYeD5"></a>
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

<a name="V7oos"></a>
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

!shell命令<br />按下两次esc可以回到命令模式

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

分屏: vim -on file1 file2 …  <br />垂直分屏: vim -On file1 file2…   垂直分屏<br />注意: n可以省略, 有几个文件就分几屏

- 从末行模式切换回命令模式

按两次ESC, 退格(backspace)或者回车键
<a name="MajWt"></a>
#### 04-vim的配置文件

- 用户级别配置文件
   - ~/.vimrc, 修改用户级别的配置文件只会影响当前用户, 不会影响其他的用户.

例如: 在用户的家目录下的.vimrc文件中添加

      - set tabstop=4  ----设置缩进4个空格
      - set     ----设置行号
      - set shiftwidth=4  ---设置gg=G缩进4个空格, 默认是缩进8个空格
- 系统级别配置文件

/etc/vim/vimrc, 修改了系统级别的配置文件将影响系统下的所有用户.<br />说明: 由于linux是多用户操作系统, 建议只在用户级别的配置文件下进行修改, 不要影响其他用户.
<a name="uR9fA"></a>
## 02-gcc编译器
<a name="Yye2G"></a>
### 01-gcc的工作流程
gcc编译器将c源文件到生成一个可执行程序，中间一共经历了四个步骤：<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671249539301-762d4ddb-f861-4ca6-a545-d5186e52c135.png#averageHue=%23cdc75f&clientId=udabe5b67-2304-4&from=paste&height=124&id=u2993b0ca&name=image.png&originHeight=124&originWidth=865&originalType=binary&ratio=1&rotation=0&showTitle=false&size=18078&status=done&style=none&taskId=u986e6129-ad0e-4480-a116-ef8c5cf865e&title=&width=865)<br />四个步骤并不是gcc独立完成的，而是在内部调用了其他工具，从而完成了整个工作流程, 其中编译最耗时, 因为要逐行检查语法.

下面以test.c为例介绍gcc的四个步骤:

   - gcc -E test.c -o test.i
   - gcc -S test.i -o test.s
   - gcc -c test.s -o test.o
   - gcc test.o -o test

一步生成最终的可执行程序: <br />  gcc test.c -o test
<a name="VUIRu"></a>
### 02-gcc常用参数

- -v  查看gcc版本号, --version也可以
- -E  生成预处理文件
- -S  生成汇编文件
- **-c  只编译, 生成.o文件, 通常称为目标文件**
- **-I   指定头文件所在的路径**
- **- 指定库文件所在的路径**
- **-  指定库的名字**
- **-o   指定生成的目标文件的名字**
- **-g   包含调试信息, 使用gdb调试需要添加-g参数**
- -On n=0∼3 编译优化,n越大优化得越多
- 例如:下面代码片段
```cpp
int a = 10;
int b = a;
int c = b;
printf("%d", c);

上面的代码可能会被编译器优化成:
int c = 10;
printf("%d", 10);
```

-Wall 提示更多警告信息
```cpp
int a;
int b;
int c = 10;
printf(“[%d]\n”, c);
编译如下: 
gcc -o test -Wall test.c
warning: unused variable ‘b’ [-Wunused-variable]
warning: unused variable ‘a’ [-Wunused-variable]
```

-D  编译时定义宏
```cpp
test.c文件中的代码片段: 
printf("MAX==[%d]\n", MAX);

编译: 
gcc -o test test.c -D MAX=10
gcc -o test test.c -DMAX=10
```
静态库和共享（动态）库
<a name="YirmK"></a>
## 03-库的介绍   
<a name="HArrY"></a>
### 01-什么是库
 库是二进制文件, 是源代码文件的另一种表现形式, 是加了密的源代码; <br />是一些功能相近或者是相似的函数的集合体.
<a name="cjO8z"></a>
### 02-使用库有什么好处

- 提高代码的可重用性, 而且还可以提高程序的健壮性;
- 可以减少开发者的代码开发量, 缩短开发周期.
<a name="AmhS2"></a>
### 03-库制作完成后, 如何给用户使用
头文件---包含了库函数的声明<br />库文件---包含了库函数的代码实现<br />注意: 库不能单独使用, 只能作为其他执行程序的一部分完成某些功能, 也<br />就是说只能被其他程序调用才能使用.<br />库可分静态库(static library)和共享库(shared library)
<a name="QEUjb"></a>
### 04-静态库（static library）
<a name="UY5jq"></a>
#### 01-介绍
静态库可以认为是一些目标代码的集合, 是在可执行程序运行前就已经加入到执行码中, 成为执行程序的一部分. 按照习惯, 一般以.a做为文件后缀名.<br />静态库的命名一般分为三个部分：

- 前缀：lib
- 库名称：自定义即可, 如test
- 后缀：.a

所以最终的静态库的名字应该为：libtest.a
<a name="Z9C9N"></a>
#### 02-静态库的制作
下面以fun1.c , fun2.c和head.h三个文件为例讲述静态库的制作和使用, 其中head.h文件中有函数的声明,  fun1.c和fun2.c中有函数的实现.<br />步骤1：将c源文件生成对应的.o文件<br />gcc -c fun1.c fun2.c<br />或者分别生成.o文件:<br />            gcc -c fun1.c -o fun1.o<br />            gcc -c fun2.c -o fun2.o<br />步骤2：使用打包工具ar将准备好的.o文件打包为.a文件<br />在使用ar工具是时候需要添加参数rcs<br />r更新、c创建、s建立索引<br />命令：ar rcs 静态库名 .o文件<br />ar rcs libtest1.a fun1.o fun2.o<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671250047950-592eee4a-fc7c-481c-b88a-1b60c8b99b39.png#averageHue=%23f8f4f3&clientId=udabe5b67-2304-4&from=paste&height=377&id=u97052b58&name=image.png&originHeight=377&originWidth=521&originalType=binary&ratio=1&rotation=0&showTitle=false&size=59881&status=done&style=none&taskId=u909fb16d-a0b9-4cb7-b487-0264cb57dee&title=&width=521)
<a name="N4ukV"></a>
#### 03-静态库的使用
静态库制作完成之后, 需要将.a文件和头文件一定发布给用户.<br />假设测试文件为main.c, 静态库文件为libtest1.a, 头文件为head.h<br />用到的参数：<br />-L：指定要连接的库的所在目录<br />-l：指定链接时需要的静态库, 去掉前缀和后缀<br />-I: 指定main.c文件用到的头文件head.h所在的路径<br />gcc -o main1 main.c -L./ -ltest1 -I./   参数和value可以连在一起可以不连在一起
<a name="HgwBs"></a>
#### 04-静态库的优缺点

- 优点：

函数库最终被打包到应用程序中，实现是函数本地化，寻址方便、速度快。<br />（库函数调用效率==自定义函数使用效率）<br />程序在运行时与函数库再无瓜葛，移植方便。

- 缺点：

消耗系统资源较大, 每个进程使用静态库都要复制一份, 无端浪费内存。<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671250121689-858dd7e6-d13a-4e11-8e2c-24e002b809e9.png#averageHue=%23f0ebeb&clientId=udabe5b67-2304-4&from=paste&height=496&id=u726206cd&name=image.png&originHeight=496&originWidth=591&originalType=binary&ratio=1&rotation=0&showTitle=false&size=128381&status=done&style=none&taskId=ub2912bff-01bc-476b-acd2-473662f4eda&title=&width=591)静态库会给程序的更新、部署和发布带来麻烦。如果静态库libxxx.a更新了，所有使用它的应用程序都需要重新编译、发布给用户（对于玩家来说，可能是一个很小的改动，却导致整个程序重新下载）。
<a name="LxjqY"></a>
### 05-共享库（shared library）/动态库
<a name="mODXr"></a>
#### 01-介绍
共享库在程序编译时并不会被连接到目标代码中, 而是在程序运行是才被载入. 不同的应用程序如果调用相同的库, 那么在内存里只需要有一份该共享库的拷贝, 规避了空间浪费问题.动态库在程序运行时才被载入, 也解决了静态库对程序的更新、部署和发布会带来麻烦. 用户只需要更新动态库即可, 增量更新. 为什么需要动态库, 其实也是静态库的特点导致. <br />按照习惯, 一般以”.so”做为文件后缀名. 共享库的命名一般分为三个部分：

   - 前缀：lib
   - 库名称：自己定义即可, 如test
   - 后缀：.so

所以最终的静态库的名字应该为：libtest.so

<a name="avBKD"></a>
#### 02-共享库的制作
1.     生成目标文件.o, 此时要加编译选项：-fPIC（fpic）<br />gcc -fpic -c fun1.c fun2.c<br />参数：-fpic创建与地址无关的编译程序(pic, position independent code), 目的就是为了能够在多个应用程序间共享.<br />2.     生成共享库, 此时要加链接器选项: -shared（指定生成动态链接库**）**<br />gcc -shared fun1.o fun2.o -o libtest2.so
<a name="gqA1R"></a>
#### 03-共享库的使用
引用动态库编译成可执行文件（跟静态库方式一样）：<br />用到的参数：

   - -L：指定要连接的库的所在目录
   - -l：指定链接时需要的动态库, 去掉前缀和后缀
   - -I: 指定main.c文件用到的头文件head.h所在的路径

gcc main.c -I./ -L./ -ltest2 -o main2<br />然后运行：./main2，发现竟然报错了.<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671250160475-50361dea-b1e7-4101-8663-05cb0450f125.png#averageHue=%23320d29&clientId=udabe5b67-2304-4&from=paste&height=34&id=ucd8f375f&name=image.png&originHeight=34&originWidth=743&originalType=binary&ratio=1&rotation=0&showTitle=false&size=29950&status=done&style=none&taskId=u1cc1e231-770f-4e6a-b51d-765b3b8f973&title=&width=743)**- 分析为什么在执行的时候找不到libtest2.so库**<br />当系统加载可执行代码时候, 能够知道其所依赖的库的名字, 但是还需要知道所依赖的库的绝对路径。此时就需要系统动态载入器(dynamic linker/loader)。<br />**ldd命令可以查看可执行文件依赖的库文件, 执行ldd main2, 可以发现libtest2.so找不到.**<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671250171189-c5fb85dc-e2e0-4eb5-a117-22cceac12877.png#averageHue=%23320f2c&clientId=udabe5b67-2304-4&from=paste&height=76&id=u8f58fbbc&name=image.png&originHeight=76&originWidth=708&originalType=binary&ratio=1&rotation=0&showTitle=false&size=68592&status=done&style=none&taskId=u0bf00a6b-5b95-410f-8968-30f9cf71ef0&title=&width=708)**对于elf格式的可执行程序，是由ld-linux.so*来完成的**, 它先后搜索elf文件的 DT_RPATH段 — 环境变量LD_LIBRARY_PATH— /etc/ld.so.cache文件列表 — /lib/, /usr/lib目录找到库文件后将其载入内存。<br />**使用file命令可以查看文件的类型: file main2**<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671250181017-fd23c638-fcbf-4a80-a25b-b8d773b62055.png#averageHue=%233f284f&clientId=udabe5b67-2304-4&from=paste&height=64&id=uda9a4db1&name=image.png&originHeight=64&originWidth=865&originalType=binary&ratio=1&rotation=0&showTitle=false&size=77266&status=done&style=none&taskId=u93e2e4f8-89aa-4487-9246-6dc0a21011d&title=&width=865)

<a name="MnBDp"></a>
#### 04-如何让系统找到共享库（以下5种方法，第3种最常用）

1. 拷贝自己制作的共享库到/lib或者/usr/lib
2. 临时设置LD_LIBRARY_PATH:
   - export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:库路径 
3. 永久设置, 把export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:库路径, 设置到∼/.bashrc文件中, 然后在执行下列三种办法之一:
   - 执行. ~/.bashrc使配置文件生效(第一个.后面有一个空格)
   - 执行source ~/.bashrc配置文件生效
   - 退出当前终端, 然后再次登陆也可以使配置文件生效
4. 永久设置,把export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:库路径，设置到/etc/profile文件中
5. 将其添加到 /etc/ld.so.cache文件中
   - 编辑/etc/ld.so.conf文件, 加入库文件所在目录的路径
   - 运行sudo ldconfig -v, 该命令会重建/etc/ld.so.cache文件

**解决了库的路径问题之后, 再次ldd命令可以查看可执行文件依赖的库文件, ldd main2:**<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671250196171-fac541b3-3181-4541-91f5-2ccf67838045.png#averageHue=%23320f2c&clientId=udabe5b67-2304-4&from=paste&height=78&id=u382cc4ee&name=image.png&originHeight=78&originWidth=705&originalType=binary&ratio=1&rotation=0&showTitle=false&size=75821&status=done&style=none&taskId=ub5a3ee38-665a-41b0-8f9d-acc61181a57&title=&width=705)
<a name="K9OeP"></a>
#### 05-共享库的特点

1. 动态库把对一些库函数的链接载入推迟到程序运行的时期。
2. 可以实现进程之间的资源共享。（因此动态库也称为共享库）
3. 将一些程序升级变得简单。
4. 甚至可以真正做到链接载入完全由程序员在程序代码中控制（显示调用）

<a name="tunzW"></a>
### 06-比较静态库和动态库的优缺点
静态库的优点:<br />     1 执行速度快, 是因为静态库已经编译到可执行文件内部了<br />     2 移植方便, 不依赖域其他的库文件<br />缺点: <br />     1 耗费内存, 是由于每一个静态库的可执行程序都会加载一次<br />     2 部署更新麻烦, 因为静态库修改以后所有的调用到这个静态库的可执行文<br />件都需要重新编译

动态库的优点:<br />     1 节省内存<br />     2 部署升级更新方便, 只需替换动态库即可, 然后再重启服务.<br />缺点: <br />     1 加载速度比静态库慢<br />     2 移植性差, 需要把所有用到的动态库都移植.

由于由静态库生成的可执行文件是把静态库加载到了其内部, 所以静态库生成的可执行文件一般会比动态库大.
<a name="Rbx9C"></a>
# 03-makefile
<a name="aSYBA"></a>
## 01-makefile
makefile文件中定义了一系列的规则来指定, 哪些文件需要先编译, 哪些文件需要后编译, 哪些文件需要重新编译, 甚至于进行更复杂的功能操作, 因为makefile就像一个Shell脚本一样, 其中也可以执行操作系统的命令.  makefile带来的好处就是——“自动化编译”, 一旦写好, 只需要一个make命令, 整个工程完全自动编译, 极大的提高了软件开发的效率.<br />make是一个命令工具, 是一个解释makefile中指令的命令工具, 一般来说, 大多数的IDE都有这个命令, 比如：Visual C++的nmake, Linux下GNU的make. 可见, makefile都成为了一种在工程方面的编译方法.<br />makefile文件中会使用gcc编译器对源代码进行编译, 最终生成可执行文件或者是库文件.<br />makefile文件的命名：makefile或者Makefile
<a name="tEfm4"></a>
## 02-makefile的基本规则
<a name="pJvDv"></a>
### 01-makefile的规则
makefile由一组规则组成,规则如下:<br />目标: 依赖<br />（tab）命令

   1. 目标: 要生成的目标文件
   2. 依赖: 目标文件由哪些文件生成
   3. 命令: 通过执行该命令由依赖文件生成目标

下面以具体的例子来讲解:<br />当前目录下有main.c fun1.c fun2.c sum.c, 根据这个基本规则编写一个简单的makefile文件, 生成可执行文件main.

<a name="Y1LJ0"></a>
#### 第一个版本的makefile:
![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671255964701-49ec4b08-e7e6-460f-94c4-dbf953cb5667.png#averageHue=%23350f2b&clientId=udabe5b67-2304-4&from=paste&height=50&id=u7d810163&name=image.png&originHeight=50&originWidth=634&originalType=binary&ratio=1&rotation=0&showTitle=false&size=31599&status=done&style=none&taskId=ucb8e6a97-edfb-43a8-8b37-b5e07dca302&title=&width=634)<br />缺点: 效率低, 修改一个文件, 所有的文件会全部重新编译.
<a name="LM9Bz"></a>
### 02-makefile工作原理
**基本原则:**

- 若想生成目标, 检查规则中的所有的依赖文件是否都存在:
   - 如果有的依赖文件不存在,则向下搜索规则, 看是否有生成该依赖文件的规则:
      - 如果有规则用来生成该依赖文件, 则执行规则中的命令生成依赖文件;
      - 如果没有规则用来生成该依赖文件, 则报错.
      - ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671256053882-0a72b7e6-76a8-4cd3-9466-00810fd44b31.png#averageHue=%23fdf5ef&clientId=udabe5b67-2304-4&from=paste&height=235&id=u76f8abca&name=image.png&originHeight=235&originWidth=613&originalType=binary&ratio=1&rotation=0&showTitle=false&size=35742&status=done&style=none&taskId=ue576fef9-eef4-4386-9545-74e2018a92f&title=&width=613)
   - 如果所有依赖都存在,检查规则中的目标是否需要更新, 必须先检查它的所有依赖,依赖中有任何一个被更新, 则目标必须更新.(检查的规则是哪个时间大哪个最新)
      - 若目标的时间 > 依赖的时间, 不更新
      - 若目标的时间 < 依赖的时间, 则更新
      - ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671256062968-7d31d469-486b-438e-bd61-d052ea146c38.png#averageHue=%23fef6f3&clientId=udabe5b67-2304-4&from=paste&height=255&id=u72665591&name=image.png&originHeight=255&originWidth=476&originalType=binary&ratio=1&rotation=0&showTitle=false&size=24263&status=done&style=none&taskId=ufc28279f-fe0e-40e5-9732-78fc5ed0d58&title=&width=476)
- **总结：**
- 分析各个目标和依赖之间的关系
- 根据依赖关系自底向上执行命令
- 根据依赖文件的时间和目标文件的时间确定是否需要更新
- 如果目标不依赖任何条件, 则执行对应命令, 以示更新(如:伪目标)

<a name="dwhia"></a>
#### 第二个版本的makefile:
![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671256091945-a382c61c-89ab-4c2d-9a25-dc87156a3e9a.png#averageHue=%23320c26&clientId=udabe5b67-2304-4&from=paste&height=301&id=u6c034d28&name=image.png&originHeight=301&originWidth=497&originalType=binary&ratio=1&rotation=0&showTitle=false&size=78405&status=done&style=none&taskId=ufa854680-d3df-4258-8366-5ea4aea3382&title=&width=497)<br />缺点: 冗余, 若.c文件数量很多, 编写起来比较麻烦.
<a name="Qvp1T"></a>
### 03-makefile中的变量
在makefile中使用变量有点类似于C语言中的宏定义, 使用该变量相当于内容替换, 使用变量可以使makefile易于维护, 修改起来变得简单。<br />makefile有三种类型的变量:

   1. 普通变量
   2. 自带变量
   3. 自动变量
<a name="xNy8O"></a>
#### 01-普通变量
变量定义直接用 =<br />使用变量值用 $(变量名)<br />如:下面是变量的定义和使用
```cpp
foo = abc                    // 定义变量并赋值
bar = $(foo)                // 使用变量, $(变量名)
```
定义了两个变量: foo、bar, 其中bar的值是foo变量值的引用。<br />除了使用用户自定义变量, makefile中也提供了一些变量（变量名大写）供用户直接使用, 我们可以直接对其进行赋值：
```cpp
CC = gcc #arm-linux-gcc
CPPFLAGS : C预处理的选项 -I
CFLAGS:   C编译器的选项 -Wall -g -c
LDFLAGS :  链接器选项 -L  -l
```
<a name="uC0cm"></a>
#### 02-自动变量

- $@: 表示规则中的目标
- $<: 表示规则中的第一个条件
- $^: 表示规则中的所有条件, 组成一个列表, 以空格隔开, 如果这个列表中有重复的项则消除重复项。

特别注意：自动变量只能在规则的命令中使用.
<a name="x90GW"></a>
#### 03-模式规则
至少在规则的目标定义中要包含'%', ‘%'表示一个或多个, 在依赖条件中同样可以使用'%', 依赖条件中的'%'的取值取决于其目标:<br />比如: main.o:main.c  fun1.o: fun1.c  fun2.o:fun2.c, 说的简单点就是: xxx.o:xxx.c
<a name="xHbWH"></a>
#### 第三个版本的makefile:
![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671256338830-ff48e421-cac8-4c19-9875-6231098ecba1.png#averageHue=%23300a25&clientId=udabe5b67-2304-4&from=paste&height=291&id=ub6df2451&name=image.png&originHeight=291&originWidth=491&originalType=binary&ratio=1&rotation=0&showTitle=false&size=94426&status=done&style=none&taskId=uf70bf7e8-0ea3-4ee2-9568-11a65f4eea8&title=&width=491)
<a name="eeSQg"></a>
### 04-makefile函数
**makefile中的函数有很多, 在这里给大家介绍两个最常用的。**
```cpp
1. wildcard – 查找指定目录下的指定类型的文件
src=$(wildcard *.c)  //找到当前目录下所有后缀为.c的文件,赋值给src
2. patsubst – 匹配替换
obj=$(patsubst %.c,%.o, $(src)) //把src变量里所有后缀为.c的文件替换成.o
```
**在makefile中所有的函数都是有返回值的。**
```cpp
当前目录下有main.c fun1.c fun2.c sum.c
src=$(wildcard *.c) 等价于src=main.c fun1.c fun2.c sum.c
obj=$(patsubst %.c,%.o, $(src))等价于obj=main.o fun1.o fun2.o sum.o
```
<a name="KLvh4"></a>
#### 第四个版本的makefile:
![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671256472433-f9eb1ca1-f274-4e20-95ca-54a9b8fdde98.png#averageHue=%23300a24&clientId=udabe5b67-2304-4&from=paste&height=267&id=u7c416fa3&name=image.png&originHeight=267&originWidth=502&originalType=binary&ratio=1&rotation=0&showTitle=false&size=89249&status=done&style=none&taskId=u7795014f-c426-4a21-b046-eb814053dec&title=&width=502)<br />缺点: 每次重新编译都需要手工清理中间.o文件和最终目标文件<br />1.5 makefile的清理操作<br />用途: 清除编译生成的中间.o文件和最终目标文件<br />make clean 如果当前目录下有同名clean文件,则不执行clean对应的命令, 解决方案：

- 伪目标声明: 
- .PHONY:clean
   - 声明目标为伪目标之后, makefile将不会检查该目标是否存在或者该目标是否需要更新
- clean命令中的特殊符号：
   - “-”此条命令出错,make也会继续执行后续的命令。如:“-rm main.o”

	rm -f: 强制执行,比如若要删除的文件不存在使用-f不会报错

   - “@”不显示命令本身, 只显示结果。如:“@echo clean done”
- 其它

– make 默认执行第一个出现的目标, 可通过make dest指定要执行的目标<br />– make -f : -f执行一个makefile文件名称, 使用make执行指定的makefile: make -f mainmak
<a name="LapGq"></a>
#### 第5个版本的makefile:
```cpp
src=$(wildcard ./*.c)
object=$(patsubst %.c, %.o, $(src))
target=main
CC=gcc
CPPFLAGS=-I./

$(target):$(object)
	$(CC) -o $@ $^

%.o:%.c
	$(CC) -o $@ -c $< $(CPPFLAGS) 

.PHONY:clean
clean:
	-rm -f $(target) $(object)

```
在makefile的第5个版本中, 综合使用了变量, 函数, 模式规则和清理命令, <br />是一个比较完善的版本.<br />gdb调试
<a name="rD94D"></a>
# 04-gdb
<a name="ntpww"></a>
## 01-介绍
GDB（GNU Debugger）是GCC的调试工具。其功能强大, 现描述如下：<br />GDB主要帮忙你完成下面四个方面的功能：<br />启动程序, 可以按照你的自定义的要求随心所欲的运行程序。<br />可让被调试的程序在你所指定的断点处停住。（断点可以是条件表达式）<br />当程序被停住时, 可以检查此时你的程序中所发生的事。<br />动态的改变你程序的执行环境。
<a name="nJQkc"></a>
## 02-生成调试信息
一般来说GDB主要调试的是C/C++的程序。要调试C/C++的程序, 首先在编译时, 我们必须要把调试信息加到可执行文件中。使用编译器（cc/gcc/g++）的 -g 参数可以做到这一点。如：<br />gcc -g hello.c -o hello<br />如果没有-g, 你将看不见程序的函数名、变量名, 所代替的全是运行时的内存地址。当你用-g把调试信息加入之后, 并成功编译目标代码以后, 让我们来看看如何用gdb来调试他。
<a name="Z9Flj"></a>
## 03-启动gdb

1. 启动gdb：gdb program
   1. program 也就是你的执行文件, 一般在当前目录下。
2. 设置运行参数
   1. set args 可指定运行时参数。（如：set args 10 20 30 40 50 ）
   2. show args 命令可以查看设置好的运行参数。
3. 启动程序
   1. run：程序开始执行, 如果有断点, 停在第一个断点处
   2. start：程序向下执行一行。(在第一条语句处停止)
<a name="wI42y"></a>
## 04-显示源代码
GDB 可以打印出所调试程序的源代码, 当然, 在程序编译时一定要加上-g的参数, 把源程序信息编译到执行文件中。不然就看不到源程序了。当程序停下来以后, GDB会报告程序停在了那个文件的第几行上。你可以用list命令来打印程序的源代码, 默认打印10行, list命令的用法如下所示:

- list linenum：打印第linenum行的上下文内容.
- list function：显示函数名为function的函数的源程序。
- list：显示当前行后面的源程序。
- list -：显示当前文件开始处的源程序。
- list file:linenum: 显示file文件下第n行
- list file:function: 显示file文件的函数名为function的函数的源程序

一般是打印当前行的上5行和下5行, 如果显示函数是是上2行下8行, 默认是10行, 当然, 你也可以定制显示的范围, 使用下面命令可以设置一次显示源程序的行数。

- set listsize count：设置一次显示源代码的行数。         
- show listsize：   查看当前listsize的设置。
<a name="cbGwP"></a>
## 05-设置断点

- **简单断点—当前文件**
   - break 设置断点, 可以简写为b
      - b 10 设置断点, 在源程序第10行
      - b func 设置断点, 在func函数入口处
- **多文件设置断点---其他文件**
   - 在进入指定函数时停住:
      - b filename:linenum --在源文件filename的linenum行处停住
      - b filename:function --在源文件filename的function函数的入口处停住
- **查询所有断点**
   - info b == info break == i break == i b
- **条件断点**
   - 一般来说, 为断点设置一个条件, 我们使用if关键词, 后面跟其断点条件。设置一个条件断点：
      - b test.c:8 if intValue == 5
- **维护断点**
- delete [range...] 删除指定的断点, 其简写命令为d。
   - 如果不指定断点号, 则表示删除所有的断点。range表示断点号的范围（如：3-7）。
      - 删除某个断点: delete num
      - 删除多个断点: delete num1 num2  ...
      - 删除连续的多个断点: delete m-n
      - 删除所有断点: delete
   - 比删除更好的一种方法是disable停止点, disable了的停止点, GDB不会删除, 当你还需要时, enable即可, 就好像回收站一样。
- disable [range...] 使指定断点无效, 简写命令是dis。
   - 如果什么都不指定, 表示disable所有的停止点。
   - 使一个断点无效/有效: disable num
   - 使多个断点无效有效: disable num1 num2 ...
   - 使多个连续的断点无效有效: disable m-n
   - 使所有断点无效有效: disable
- enable [range...] 使无效断点生效, 简写命令是ena。
- 如果什么都不指定, 表示enable所有的停止点。
   - 使一个断点无效/有效: enable num
   - 使多个断点无效有效: enable num1 num2 ...
   - 使多个连续的断点无效有效: enable m-n
   - 使所有断点无效有效: disable/enable
<a name="xfS14"></a>
## 06-调试代码

- run 运行程序, 可简写为r
- next 单步跟踪, 函数调用当作一条简单语句执行, 可简写为n
- step 单步跟踪, 函数调进入被调用函数体内, 可简写为s
- finish 退出进入的函数, 如果出不去, 看一下函数体中的循环中是否有断点，如果有删掉，或者设置无效
- until 在一个循环体内单步跟踪时, 这个命令可以运行程序直到退出循环体,可简写为u,
   - 如果出不去, 看一下函数体中的循环中是否有断点，如果有删掉，或者设置无效
- continue 继续运行程序, 可简写为c(若有断点则跳到下一个断点处)
<a name="z1tJz"></a>
## 07-查看变量的值

- **查看运行时变量的值**
   - print 打印变量、字符串、表达式等的值, 可简写为p
   - p count -----打印count的值
- **自动显示变量的值**
   - 你可以设置一些自动显示的变量, 当程序停住时, 或是在你单步跟踪时, 这些变量会自动显示。相关的GDB命令是display。
   - display 变量名
   - info display -- 查看display设置的自动显示的信息。
   - undisplay num（info display时显示的编号）
   - delete display dnums… -- 删除自动显示, dnums意为所设置好了的自动显式的编号。如果要同时删除几个, 编号可以用空格分隔, 如果要删除一个范围内的编号, 可以用减号表示（如：2-5）
      - 删除某个自动显示: undisplay num 或者delete display num
      - 删除多个: delete display num1 num2
      - 删除一个范围: delete display m-n
   - disable display dnums…
      - 使一个自动显示无效: disable display num
      - 使多个自动显示无效: delete display num1 num2
      - 使一个范围的自动显示无效: delete display m-n
   - enable display dnums…
      - 使一个自动显示有效: enable display num
      - 使多个自动显示有效: enable display num1 num2
      - 使一个范围的自动显示有效: enable display m-n
   - disable和enalbe不删除自动显示的设置, 而只是让其失效和恢复。
- **查看修改变量的值**
   - ptype width --查看变量width的类型
      - type = double
   - p width --打印变量width 的值
      - $4 = 13
   - 你可以使用set var命令来告诉GDB, width不是你GDB的参数, 而是程序的变量名, 如：
   - set var width=47  // 将变量var值设置为47
   - 在你改变程序变量取值时, 最好都使用set var格式的GDB命令。
<a name="nDrvl"></a>
# 05-文件IO
<a name="GHmDF"></a>
## 01-基本原理

- 从本章开始学习各种Linux系统函数, 这些函数的用法必须结合Linux内核的工作原理来理解, 因为系统函数正是内核提供给应用程序的接口, 而要理解内核的工作原理, 必须熟练掌握C语言, 因为内核也是用C语言写的, 我们在描述内核工作原理时必然要用“指针”、“结构体”、“链表”这些名词来组织语言, 就像只有掌握了英语才能看懂英文书一样, 只有学好了C语言才能看懂我描述的内核工作原理。
<a name="TASTt"></a>
### 01-C库IO函数的工作流程
![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671257350738-104e4dc5-1eba-4971-9bd5-c874f5f62142.png#averageHue=%23ecd2bd&clientId=udabe5b67-2304-4&from=paste&height=542&id=u0bff41a1&name=image.png&originHeight=542&originWidth=780&originalType=binary&ratio=1&rotation=0&showTitle=false&size=113973&status=done&style=none&taskId=u65af3a87-c7a3-4706-b14e-dadcf022da9&title=&width=780)<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671257356315-d8cc883d-c6de-4594-b734-d2544e3d130e.png#averageHue=%23f1f1f1&clientId=udabe5b67-2304-4&from=paste&height=240&id=u1b4268f3&name=image.png&originHeight=240&originWidth=604&originalType=binary&ratio=1&rotation=0&showTitle=false&size=34161&status=done&style=none&taskId=ufdd37fcd-31b9-4092-9fad-c70adf323c7&title=&width=604)<br />c语言操作文件相关问题:<br />使用fopen函数打开一个文件, 返回一个FILE* fp, 这个指针指向的结构体有三个重要的成员.

- 文件描述符: 通过文件描述可以找到文件的inode, 通过inode可以找到对应的数据块
- 文件指针: 读和写共享一个文件指针, 读或者写都会引起文件指针的变化
- 文件缓冲区: 读或者写会先通过文件缓冲区, 主要目的是为了减少对磁盘的读写次数, 提高读写磁盘的效率.

备注: 

- 头文件stdio.h 的第48行处:  typedef struct _IO_FILE FILE;
- 头文件libio.h 的第241行处:  struct _IO_FILE, 这个接头体定义中有一个_fileno成员, 这个就是文件描述符
<a name="JQKfA"></a>
### 02-C库函数与系统函数的关系
![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671257399271-e9a5a325-0a8f-4d60-a123-62ce198700f9.png#averageHue=%23e8a43a&clientId=udabe5b67-2304-4&from=paste&height=562&id=u073909bd&name=image.png&originHeight=562&originWidth=813&originalType=binary&ratio=1&rotation=0&showTitle=false&size=64073&status=done&style=none&taskId=ue4469f5a-413e-4d14-aeef-87e776e6186&title=&width=813)<br />系统调用: 由操作系统实现并提供给外部应用程序的编程接口,<br />(Application Programming Interface, API), 是应用程序同系统之间数据交互的桥梁.
<a name="CxHwd"></a>
### 03-虚拟地址空间
![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671257415320-912c780a-0d15-4287-8df3-b9faca8243ba.png#averageHue=%232c1d0f&clientId=udabe5b67-2304-4&from=paste&height=639&id=u68b70887&name=image.png&originHeight=639&originWidth=906&originalType=binary&ratio=1&rotation=0&showTitle=false&size=166601&status=done&style=none&taskId=u43e066e9-e2c6-4232-aa1e-102f0c9b7c2&title=&width=906)

- 进程的虚拟地址空间分为用户区和内核区, 其中内核区是受保护的, 用户是不能够对其进行读写操作的;
- 内核区中很重要的一个就是进程管理, 进程管理中有一个区域就是PCB(本质是一个结构体);
- PCB中有文件描述符表, 文件描述符表中存放着打开的文件描述符, 涉及到文件的IO操作都会用到这个文件描述符.
<a name="wZQr3"></a>
### 04-pcb和文件描述符表
![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671257450468-6d3f4d9a-1d4f-4c64-ade4-ce0123f7d379.png#averageHue=%23633d0d&clientId=udabe5b67-2304-4&from=paste&height=530&id=u87d357b2&name=image.png&originHeight=530&originWidth=781&originalType=binary&ratio=1&rotation=0&showTitle=false&size=81867&status=done&style=none&taskId=ua90946e8-d02a-42f8-9ecb-b69c44a5458&title=&width=781)<br />备注:<br />pcb：结构体:task_stuct, 该结构体在:<br />/usr/src/linux-headers-4.4.0-97/include/linux/sched.h:1390<br />一个进程有一个文件描述符表：1024

- 前三个被占用, 分别是STDIN_FILENO, STDOUT_FILENO, STDERR_FILENO
-  文件描述符作用：通过文件描述符找到inode, 通过inode找到磁盘数据块.

虚拟地址空间->内核区->PCB->文件描述表->文件描述符->文件IO操作使用文件描述符

<a name="RdrCv"></a>
## 02-文件IO
<a name="Q5j6l"></a>
### 01-C标准函数与系统函数的区别
**什么是系统调用**<br />由操作系统实现并提供给外部应用程序的编程接口。(Application Programming Interface，API)。是应用程序同系统之间数据交互的桥梁。<br />一个helloworld如何打印到屏幕。<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671258302739-289ebaea-4458-4347-a14f-954f6208b107.png#averageHue=%23eeeeed&clientId=udabe5b67-2304-4&from=paste&height=551&id=u15273a0d&name=image.png&originHeight=551&originWidth=577&originalType=binary&ratio=1&rotation=0&showTitle=false&size=129831&status=done&style=none&taskId=u41308e3f-6a8a-4080-a279-1ebb138b25c&title=&width=577)<br />每一个FILE文件流（标准C库函数）都有一个缓冲区buffer，默认大小8192Byte。Linux系统的IO函数默认是没有缓冲区.<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671258315455-aa869d5c-f68e-4683-9c4e-cb8323309f90.png#averageHue=%23f2f1f1&clientId=udabe5b67-2304-4&from=paste&height=365&id=u2c2131e2&name=image.png&originHeight=365&originWidth=865&originalType=binary&ratio=1&rotation=0&showTitle=false&size=62978&status=done&style=none&taskId=u720325e5-83e7-48e3-a5b2-1d5d744a4ea&title=&width=865)
<a name="BvoSs"></a>
### 02-open/close
<a name="Bc7wT"></a>
#### 01-文件描述符
一个进程启动之后，默认打开三个文件描述符：<br />#define  STDIN_FILENO                  0<br />#define  STDOUT_FILENO              1    打印到终端的<br />#define  STDERR_FILENO               2<br />**新打开文件返回文件描述符表中未使用的最小文件描述符, 调用open函数可以打开或创建一个文件, 得到一个文件描述符.**
<a name="GTPai"></a>
#### 02-open()函数

- 函数描述: 打开或者新建一个文件
- 函数原型:
   - int open(const char *pathname, int flags);
   - int open(const char *pathname, int flags, mode_t mode);
- 函数参数：
- pathname参数是要打开或创建的文件名,和fopen一样, pathname既可以是相对路径也可以是绝对路径。
- flags参数有一系列常数值可供选择, 可以同时选择多个常数用按位或运算符连接起来, 所以这些常数的宏定义都以O_开头,表示or。
   - 必选项:以下三个常数中必须指定一个, 且仅允许指定一个。
      - O_RDONLY 只读打开
      - O_WRONLY 只写打开
      - O_RDWR 可读可写打开
   - 以下可选项可以同时指定0个或多个, 和必选项按位或起来作为flags参数。可选项有很多, 这里只介绍几个常用选项：
      - O_APPEND 表示追加。如果文件已有内容, 这次打开文件所写的数据附加到文件的末尾而不覆盖原来的内容。
      - O_CREAT 若此文件不存在则创建它。使用此选项时需要提供第三个参数mode, 表示该文件的访问权限。
         -  **文件最终权限：mode & ~umask**
      - O_EXCL 如果同时指定了O_CREAT,并且文件已存在,则出错返回。
      - O_TRUNC 如果文件已存在, 将其长度截断为为0字节。
      - O_NONBLOCK 对于设备文件, 以O_NONBLOCK方式打开可以做非阻塞I/O(NonblockI/O),非阻塞I/O。
- **函数返回值:**
   - 成功: 返回一个最小且未被占用的文件描述符
   - 失败: 返回-1, 并设置errno值.
<a name="DcR5A"></a>
#### 03-close函数

- 函数描述: 关闭文件
- 函数原型:  int close(int fd);
- 函数参数:  fd文件描述符
- 函数返回值:
   - 成功返回0
   - 失败返回-1, 并设置errno值.

需要说明的是,当一个进程终止时, 内核对该进程所有尚未关闭的文件描述符调用close关闭,所以即使用户程序不调用close, 在终止时内核也会自动关闭它打开的所有文件。但是对于一个长年累月运行的程序(比如网络服务器), 打开的文件描述符一定要记得关闭, 否则随着打开的文件越来越多, 会占用大量文件描述符和系统资源。
<a name="b8lGX"></a>
### 03-read/write/access
<a name="xoB6V"></a>
#### 01-read()

- 函数描述: 从打开的设备或文件中读取数据
- 函数原型: ssize_t read(int fd, void *buf, size_t count);
- 函数参数:
   - fd: 文件描述符
   - buf: 读上来的数据保存在缓冲区buf中
   - count: buf缓冲区存放的最大字节数
- 函数返回值:
   - >0：读取到的字节数
   - =0：文件读取完毕
   - -1：出错，并设置errno
<a name="h7Fct"></a>
#### 02-write()

- 函数描述: 向打开的设备或文件中写数据
- 函数原型: ssize_t write(int fd, const void *buf, size_t count);
- 函数参数：
   - fd：文件描述符
   - buf：缓冲区，要写入文件或设备的数据
   - count：buf中数据的长度
- 函数返回值:
   - 成功：返回写入的字节数
   - 错误：返回-1并设置errno
<a name="zchuB"></a>
#### 03-access()

- 函数描述:**access()会检查是否可以读/写某一已存在的文件。**
- 函数原型: **int access(const char * pathname, int mode);**
- 函数参数：
   - pathname:（绝对/相对）文件路径
   - mode：操作形式
      - F_OK      0     /* Check for file existence */
      - X_OK      1     /* Check for execute permission. */
      - W_OK     2     /* Check for write permission */
      - R_OK      4     /* Check for read permission *
- 函数返回值:
   - 成功：0
   - 错误：返回-1
<a name="WOvGt"></a>
### 04-lseek
所有打开的文件都有一个当前文件偏移量(current file offset),以下简称为cfo. cfo通常是一个非负整数, 用于表明文件开始处到文件当前位置的字节数. 读写操作通常开始于 cfo, 并且使 cfo 增大, 增量为读写的字节数. 文件被打开时, cfo 会被初始化为 0, 除非使用了 O_APPEND.<br />使用 lseek 函数可以改变文件的 cfo.
> #include <sys/types.h>
> #include <unistd.h>
> off_t lseek(int fd, off_t offset, int whence);

- 函数描述: 移动文件指针
- 函数原型: off_t lseek(int fd, off_t offset, int whence);
- 函数参数：
   - fd：文件描述符
   - 参数 offset 的含义取决于参数 whence：
      - 如果 whence 是 SEEK_SET，文件偏移量将设置为 offset。
      - 如果 whence 是 SEEK_CUR，文件偏移量将被设置为 cfo 加上 offset，offset 可以为正也可以为负。
      - 如果 whence 是 SEEK_END，文件偏移量将被设置为文件长度加上 offset，offset 可以为正也可以为负。
- 函数返回值: 若lseek成功执行, 则返回新的偏移量。
- lseek函数常用操作
   - 文件指针移动到头部
      - lseek(fd, 0, SEEK_SET);
   - 获取文件指针当前位置
      - int len = lseek(fd, 0, SEEK_CUR);
   - 获取文件长度
      - int len = lseek(fd, 0, SEEK_END);
   - lseek实现文件拓展
      - off_t currpos;
      - // 从文件尾部开始向后拓展1000个字节
      - currpos = lseek(fd, 1000, SEEK_END); 
      - // 额外执行一次写操作，否则文件无法完成拓展
      - write(fd, “a”, 1);       // 数据随便写

<a name="EXxNT"></a>
### 05-perror和errno
errno是一个全局变量, 当系统调用后若出错会将errno进行设置, perror可以将errno对应的描述信息打印出来.<br />如:perror("open"); 如果报错的话打印: open:(空格)错误信息

<a name="iemxR"></a>
### 06-阻塞和非阻塞:
思考: 阻塞和非阻塞是文件的属性还是read函数的属性?

- 普通文件：hello.c
   - 默认是非阻塞的
- 终端设备：如/dev/tty
   - 默认阻塞
- 管道和套接字
   - 默认阻塞

得出结论: 阻塞和非阻塞是文件本身的属性, 不是read函数的属性.
<a name="abA78"></a>
## 03-文件和目录
<a name="uAEVJ"></a>
### 01-文件操作相关函数
<a name="qMtHs"></a>
#### 01-stat/lstat函数

- 函数描述: 获取文件属性
- 函数原型: int stat(const char *pathname, struct stat *buf);
   - int lstat(const char *pathname, struct stat *buf);
- 函数返回值：
   - 成功返回 0
   - 失败返回 -1
```cpp
struct stat {
    dev_t          st_dev;        //文件的设备编号
    ino_t           st_ino;        //节点
    mode_t         st_mode;      //文件的类型和存取的权限
    nlink_t         st_nlink;     //连到该文件的硬连接数目，刚建立的文件值为1
    uid_t           st_uid;       //用户ID
    gid_t           st_gid;       //组ID
    dev_t          st_rdev;      //(设备类型)若此文件为设备文件，则为其设备编号
    off_t          st_size;      //文件字节数(文件大小)
    blksize_t       st_blksize;   //块大小(文件系统的I/O 缓冲区大小)
    blkcnt_t        st_blocks;    //块数
    time_t         st_atime;     //最后一次访问时间
    time_t         st_mtime;     //最后一次修改时间
    time_t         st_ctime;     //最后一次改变时间(指属性)
};
```
- st_mode -- 16位整数<br />○ 0-2 bit -- 其他人权限<br />S_IROTH      00004  读权限<br />S_IWOTH     00002  写权限<br />S_IXOTH      00001  执行权限<br />S_IRWXO     00007  掩码, 过滤 st_mode中除其他人权限以外的信息<br />○ 3-5 bit -- 所属组权限<br />S_IRGRP     00040  读权限<br />S_IWGRP    00020  写权限<br />      S_IXGRP     00010   执行权限<br />S_IRWXG    00070  掩码, 过滤 st_mode中除所属组权限以外的信息<br />○ 6-8 bit -- 文件所有者权限<br />S_IRUSR    00400    读权限<br />S_IWUSR   00200    写权限<br />S_IXUSR    00100     执行权限<br />S_IRWX 00700    掩码, 过滤 st_mode中除文件所有者权限以外的信息<br />If (st_mode & S_IRUSR)   -----为真表明可读<br />If (st_mode & S_IWUSR)  ------为真表明可写<br />If (st_mode & S_IXUSR)   ------为真表明可执行<br />○ 12-15 bit -- 文件类型<br />S_IFSOCK         0140000 套接字<br />S_IFLNK          0120000 符号链接（软链接）<br />      S_IFREG          0100000 普通文件<br />S_IFBLK           0060000 块设备<br />S_IFDIR           0040000 目录<br />     S_IFCHR           0020000 字符设备<br />S_IFIFO           0010000 管道<br />S_IFMT 0170000 掩码,过滤 st_mode中除文件类型以外的信息<br />If ((st_mode & S_IFMT)==S_IFREG) ----为真普通文件<br />if(S_ISREG(st_mode))   ------为真表示普通文件<br />if(S_ISDIR(st.st_mode))  ------为真表示目录文件<br />**stat函数和lstat函数的区别**

- 对于普通文件, 这两个函数没有区别, 是一样的.
- 对于连接文件,调用lstat函数获取的是链接文件本身的属性信息;

 	而stat函数获取的是链接文件指向的文件的属性信息.

<a name="ZLWVH"></a>
### 02-目录操作相关函数
<a name="GOkjI"></a>
#### 01-opendir函数
函数描述:打开一个目录<br />函数原型: DIR *opendir(const char *name);<br />函数返回值: 指向目录的指针<br />函数参数: 要遍历的目录(相对路径或者绝对路径)
<a name="GEqzX"></a>
#### 02-readdir函数
函数描述: 读取目录内容--目录项<br />函数原型: struct dirent *readdir(DIR *dirp);<br />函数返回值: 读取的目录项指针<br />函数参数: opendir函数的返回值
```cpp
struct dirent
{
ino_t d_ino;             // 此目录进入点的inode
off_t d_off;              // 目录文件开头至此目录进入点的位移
signed short int d_reclen;   // d_name 的长度, 不包含NULL 字符
unsigned char d_type;     // d_name 所指的文件类型
char d_name[256];             // 文件名
};
```
d_type的取值: <br />DT_BLK - 块设备<br />DT_CHR - 字符设备<br />DT_DIR - 目录<br />DT_LNK - 软连接<br />DT_FIFO - 管道<br />DT_REG - 普通文件<br />DT_SOCK - 套接字<br />DT_UNKNOWN - 未知<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671281970336-19634517-313c-44f0-8e54-b49372ee4dd5.png#averageHue=%23fefcfb&clientId=u96db4cd0-8067-4&from=paste&height=394&id=ub04dc4fb&name=image.png&originHeight=394&originWidth=363&originalType=binary&ratio=1&rotation=0&showTitle=false&size=39371&status=done&style=none&taskId=u36bfded4-83a6-4e87-b699-e042643ca63&title=&width=363)
<a name="loTBz"></a>
#### 03-closedir函数
函数描述: 关闭目录<br />函数原型: int closedir(DIR *dirp);<br />函数返回值: 成功返回0, 失败返回-1<br />函数参数: opendir函数的返回值
<a name="Z4VOl"></a>
#### 04-读取目录内容的一般步骤
1 DIR *pDir = opendir(“dir”);   //打开目录<br />2 while((p=readdir(pDir))!=NULL){}  //循环读取文件<br />3 closedir(pDir);  //关闭目录


<a name="zjlWH"></a>
### 03-复制文件描述符
<a name="hitWT"></a>
#### 01-dup函数
函数描述: 复制文件描述符<br />函数原型: int dup(int oldfd);<br />函数参数: oldfd -要复制的文件描述符<br />函数返回值:<br />成功: 返回最小且没被占用的文件描述符<br />失败: 返回-1, 设置errno值
<a name="VoSzT"></a>
#### 02-dup2函数
函数描述: 复制文件描述符<br />函数原型: int dup2(int oldfd, int newfd);<br />函数参数: <br /> oldfd-原来的文件描述符<br /> newfd-复制成的新的文件描述符<br />函数返回值:<br /> 成功: 将oldfd复制给newfd, 两个文件描述符指向同一个文件<br /> 失败: 返回-1, 设置errno值<br />假设newfd已经指向了一个文件，首先close原来打开的文件，然后newfd指向oldfd指向的文件.<br />若newfd没有被占用，newfd指向oldfd指向的文件.
<a name="ecwHk"></a>
#### 03-fcntl函数
函数描述: 改变已经打开的文件的属性<br />函数原型: int fcntl(int fd, int cmd, ... /* arg */ );<br />若cmd为F_DUPFD, 复制文件描述符, 与dup相同<br />若cmd为F_GETFL, 获取文件描述符的flag属性值<br />若cmd为 F_SETFL, 设置文件描述符的flag属性<br />函数返回值:返回值取决于cmd<br />成功<br />若cmd为F_DUPFD, 返回一个新的文件描述符<br />若cmd为F_GETFL, 返回文件描述符的flags值<br />若cmd为 F_SETFL, 返回0<br />失败返回-1, 并设置errno值.<br />**fcntl函数常用的操作:**
```cpp
1 复制一个新的文件描述符:
int newfd = fcntl(fd, F_DUPFD, 0);
2 获取文件的属性标志
int flag = fcntl(fd, F_GETFL, 0)
3 设置文件状态标志
flag = flag | O_APPEND;
fcntl(fd, F_SETFL, flag)
4 常用的属性标志
O_APPEND-----设置文件打开为末尾添加
O_NONBLOCK-----设置打开的文件描述符为非阻塞
```
 
<a name="LokXB"></a>
# 06-进程控制
<a name="aR2Vb"></a>
## 01-进程相关概念
<a name="DQfYC"></a>
### 01-程序和进程
程序，是指编译好的二进制文件，在磁盘上，占用磁盘空间, 是一个静态的概念.<br />进程，一个启动的程序，进程占用的是系统资源，如：物理内存，CPU，终端等，是一个动态的概念<br />程序→剧本(纸)           <br />进程→戏(舞台、演员、灯光、道具...)<br />同一个剧本可以在多个舞台同时上演。同样，同一个程序也可以加载为不同的进程(彼此之间互不影响)
<a name="fJlub"></a>
### 02-并行和并发
**并发，在一个时间段内, 是在同一个cpu上, 同时运行多个程序。**<br />如：若将CPU的1S的时间分成1000个时间片，每个进程执行完一个时间片必须无条件让出CPU的使用权，这样1S中就可以执行1000个进程。<br />**并行性指两个或两个以上的程序在同一时刻发生(需要有多颗)。**
<a name="qqXBv"></a>
## 02-PCB-进程控制块
每个进程在内核中都有一个进程控制块（PCB）来维护进程相关的信息，Linux内核的进程控制块是task_struct结构体。<br />/usr/src/linux-headers-4.4.0-96/include/linux/sched.h文件的1390行处可以查看struct task_struct 结构体定义。其内部成员有很多，我们重点掌握以下部分即可：

- 进程id。系统中每个进程有唯一的id，在C语言中用pid_t类型表示，其实就是一个非负整数。
- 进程的状态，有就绪、运行、挂起、停止等状态。
- 进程切换时需要保存和恢复的一些CPU寄存器。
- 描述虚拟地址空间的信息。
- 描述控制终端的信息。
- 当前工作目录（Current Working Directory）。
   - getcwd --pwd
- umask掩码。
- 文件描述符表，包含很多指向file结构体的指针。
- 和信号相关的信息。
- 用户id和组id。
- 会话（Session）和进程组。
- 进程可以使用的资源上限（Resource Limit）。
   - ulimit -a

2.4 进程状态(面试考)<br />进程基本的状态有5种。分别为**初始态，就绪态，**[运行态](http://baike.baidu.com/subview/1730379/1730379.htm)**，挂起态与终止态**。其中初始态为进程准备阶段，常与就绪态结合来看。<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671282413388-3afdde56-66a4-4826-85cd-1829ad41e0f1.png#averageHue=%23fdfcfc&clientId=uaae56d25-2eb9-4&from=paste&height=444&id=u8404f49a&name=image.png&originHeight=400&originWidth=467&originalType=binary&ratio=1&rotation=0&showTitle=false&size=46749&status=done&style=none&taskId=u904b9be3-a330-41d6-834e-9a3fca8481d&title=&width=518.8889026347506)

<a name="jhEo2"></a>
## 03-创建进程
<a name="je5tF"></a>
### 01-fork函数

- 函数作用：创建子进程
- 原型: pid_t fork(void);
   - 函数参数：无
   - 返回值：调用成功:父进程返回子进程的PID，子进程返回0；
   - 调用失败:返回-1，设置errno值。
- fork函数代码片段实例
- ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671282549393-0c70ccb6-c87e-49e0-91e6-e8d1a60557aa.png#averageHue=%23f5f5f5&clientId=uaae56d25-2eb9-4&from=paste&height=602&id=ua8088b7a&name=image.png&originHeight=542&originWidth=804&originalType=binary&ratio=1&rotation=0&showTitle=false&size=214253&status=done&style=none&taskId=u3d97e61d-f43b-459f-b707-29e4733120f&title=&width=893.3333569985855)
- 调用fork函数的内核实现原理:
- ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671282559321-70e20c07-4c1a-43fc-88ee-87ea512371c7.png#averageHue=%23fefdfc&clientId=uaae56d25-2eb9-4&from=paste&height=551&id=u02bb3c2b&name=image.png&originHeight=496&originWidth=984&originalType=binary&ratio=1&rotation=0&showTitle=false&size=99364&status=done&style=none&taskId=u8005e03a-adf1-4872-95d6-ad491d8d7fb&title=&width=1093.3333622967764)

**fork函数总结**

- ►fork函数的返回值？
   - 父进程返回子进程的PID，是一个大于0数;
   - 子进程返回0；
   - 特别需要注意的是：不是fork函数在一个进程中返回2个值，而是在父子进程各自返回一个值。
- ►子进程创建成功后，代码的执行位置？
   - 父进程执行到什么位置，子进程就从哪里执行
- ►如何区分父子进程
   - 通过fork函数的返回值
- ►父子进程的执行顺序
   - 不一定，哪个进程先抢到CPU，哪个进程就先执行
<a name="N5IdM"></a>
### 02-ps命令和kill命令

- ps aux | grep "xxx"
- ps ajx | grep "xxx" **显示所有用户进程不能交互的进程与作业控制有关的进程**
   - -a：（all）当前系统所有用户的进程
   - -u：查看进程所有者及其他一些信息
   - -x：显示没有控制终端的进程 -- 不能与用户进行交互的进程【输入、输出】
   - -j: 列出与作业控制相关的信息
- kill -l 查看系统有哪些信号
- kill -9 pid 杀死某个线程
<a name="YmKhI"></a>
### 03-getpid/getppid

- getpid - 得到当前进程的PID
   - pid_t getpid(void);
- getppid - 得到当前进程的父进程的PID
   - pid_t getppid(void);
<a name="taiLW"></a>
## 04-exec函数族
<a name="v44XP"></a>
### 01-函数作用和函数介绍   
   有的时候需要在一个进程里面执行其他的命令或者是用户自定义的应用程序，此时就用到了exec函数族当中的函数。<br />使用方法一般都是在父进程里面调用fork创建处子进程，然后在子进程里面调用exec函数。
<a name="kOvYL"></a>
#### 01-execl函数

- 函数原型: int execl(const char *path, const char *arg, ... /* (char  *) NULL */);
- 参数介绍：
   - path: 要执行的程序的绝对路径
   - 变参arg: 要执行的程序的需要的参数
   - arg:占位，通常写应用程序的名字
   - arg后面的: 命令的参数
   - 参数写完之后: NULL
- 返回值：若是成功，则不返回，不会再执行exec函数后面的代码；若是失败，会执行execl后面的代码，可以用perror打印错误原因。
- execl函数一般执行自己写的程序。

<a name="pzKSE"></a>
#### 02-execlp函数

- 函数原型: int execlp(const char *file, const char *arg, .../* (char  *) NULL */);
- 参数介绍：
   - file: 执行命令的名字, 根据PATH环境变量来搜索该命令
   - arg:占位
   - arg后面的: 命令的参数
   - 参数写完之后: NULL
- 返回值：若是成功，则不返回，不会再执行exec函数后面的代码；若是失败，会执行exec后面的代码，可以用perror打印错误原因。
- execlp函数一般是执行系统自带的程序或者是命令.
<a name="u2e7D"></a>
### 02-exec函数族原理介绍   
exec族函数的实现原理图：<br />如：execlp(“ls”, “ls”, “-l”, NULL);<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671283202998-18f43992-de76-47e7-83f7-a4a96bb62fbc.png#averageHue=%23fefdfc&clientId=u96db4cd0-8067-4&from=paste&height=458&id=u453c24b1&name=image.png&originHeight=458&originWidth=929&originalType=binary&ratio=1&rotation=0&showTitle=false&size=75640&status=done&style=none&taskId=ufb34be64-a488-404a-9e5e-10a5efa0f32&title=&width=929)<br />总结：<br />exec函数是用一个新程序替换了当前进程的代码段、数据段、堆和栈；原有的进程空间没有发生变化，并没有创建新的进程，进程PID没有发生变化。
<a name="jTFIU"></a>
### 
<a name="pPdci"></a>
## 05-进程回收
<a name="H4N39"></a>
### 01-为什么要进行进程资源的回收
  当一个进程退出之后，进程能够回收自己的用户区的资源，但是不能回收内核空间的PCB资源，必须由它的父进程调用wait或者waitpid函数完成对子进程的回收，避免造成系统资源的浪费。
<a name="xPBaT"></a>
### 02-孤儿进程

- 孤儿进程的概念：
   - 若子进程的父进程已经死掉，而子进程还存活着，这个进程就成了孤儿进程。
- 为了保证每个进程都有一个父进程，孤儿进程会被init进程领养，init进程成为了孤儿进程的养父进程，当孤儿进程退出之后，由init进程完成对孤儿进程的回收。
- 模拟孤儿进程的案例
   - 编写模拟孤儿进程的代码讲解孤儿进程，验证孤儿进程的父进程是否由原来的父进程变成了init进程。
<a name="BSCPm"></a>
### 03-僵尸进程

- 僵尸进程的概念: （进程已死了，但是没有被父回收）
   - 若子进程死了，父进程还活着，但是父进程没有调用wait或waitpid函数完成对子进程的回收，则该子进程就成了僵尸进程。
- 如何解决僵尸进程
   - 由于僵尸进程是一个已经死亡的进程，所以不能使用kill命令将其杀死
   - 通过杀死其父进程的方法可以消除僵尸进程。
   - 杀死其父进程后，这个僵尸进程会被init进程领养，由init进程完成对僵尸进程的回收。
- 模拟僵尸进程的案例
   - 编写模拟僵尸进程的代码讲解僵尸进程, 验证若子进程先于父进程退出, 而父进程没有调用wait或者waitpid函数进行回收, 从而使子进程成为了僵尸进程.
<a name="muC0l"></a>
### 04-进程回收函数
<a name="dJ7pN"></a>
#### 01-wait函数

- 函数原型：
   - pid_t wait(int *status);
- 函数作用：
   - 阻塞并等待子进程退出
   - 回收子进程残留资源
   - 获取子进程结束状态(退出原因)。
- 返回值：
   - 成功：清理掉的子进程ID；
   - 失败：-1 (没有子进程)
- status参数：子进程的退出状态 -- 传出参数
   - WIFEXITED(status)：为非0 → 进程正常结束
      - WEXITSTATUS(status)：获取进程退出状态
   - WIFSIGNALED(status)：为非0 → 进程异常终止
      - WTERMSIG(status)：取得进程终止的信号编号。
<a name="g8tPC"></a>
#### 02-waitpid函数

- 函数原型：
   - pid_t waitpid(pid_t pid, int *status, in options);
- 函数作用
   - 同wait函数
- 函数参数
   - pid：
      - pid = -1 等待任一子进程。与wait等效。
      - pid > 0 等待其进程ID与pid相等的子进程。
      - pid = 0 等待进程组ID与目前进程相同的任何子进程，也就是说任何和调用
         - waitpid()函数的进程在同一个进程组的进程。
      - pid < -1 等待其组ID等于pid的绝对值的任一子进程。(适用于子进程在其他组的情况)
   - status: 子进程的退出状态，用法同wait函数。
   - options：设置为WNOHANG，函数非阻塞，设置为0，函数阻塞。
- 函数返回值
   - >0：返回回收掉的子进程ID；
   - -1：无子进程
   - =0：参3为WNOHANG，且子进程正在运行。

<a name="c94bM"></a>
# 07-进程间通信
<a name="jrdxj"></a>
## 01-学习目标
熟练使用pipe进行父子进程间通信<br />熟练使用pipe进行兄弟进程间通信<br />熟练使用fifo进行无血缘关系的进程间通信<br />使用mmap进行有血缘关系的进程间通信<br />使用mmap进行无血缘关系的进程间通信
<a name="Xw3JV"></a>
## 02-进程间通信相关概念
<a name="xahA8"></a>
### 01-什么是进程间通信
Linux环境下，进程地址空间相互独立，每个进程各自有不同的用户地址空间。任何一个进程的全局变量在另一个进程中都看不到，所以进程和进程之间不能相互访问，要交换数据必须通过内核，在内核中开辟一块缓冲区，进程1把数据从用户空间拷到内核缓冲区，进程2再从内核缓冲区把数据读走，内核提供的这种机制称为进程间通信（IPC，InterProcess Communication）。<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671283718241-e3a3058b-9228-4450-b3b7-395ec8ac7566.png#averageHue=%23ececec&clientId=u96db4cd0-8067-4&from=paste&height=333&id=u87522fae&name=image.png&originHeight=333&originWidth=406&originalType=binary&ratio=1&rotation=0&showTitle=false&size=10344&status=done&style=none&taskId=ua5fee651-be06-4649-a2c5-90eaaafd518&title=&width=406)
<a name="wISoa"></a>
### 02-进程间通信的方式
在进程间完成数据传递需要借助操作系统提供特殊的方法，如：文件、管道、信号、共享内存、消息队列、套接字、命名管道等。随着计算机的蓬勃发展，一些方法由于自身设计缺陷被淘汰或者弃用。**现今常用的进程间通信方式有：**

- **管道 (使用最简单)**
- **信号 (开销最小)**
- **共享映射区 (无血缘关系)**
- **本地套接字 (最稳定)**
<a name="gI95J"></a>
## 03-管道-pipe
<a name="qaepd"></a>
### 01-管道的概念
管道是一种最基本的IPC机制，也称匿名管道，应用于有血缘关系的进程之间，完成数据传递。调用pipe函数即可创建一个管道。<br />有如下特质：

- 管道的本质是一块内核缓冲区
- 由两个文件描述符引用，一个表示读端，一个表示写端。
- 规定数据从管道的写端流入管道，从读端流出。
- 当两个进程都终结的时候，管道也自动消失。
- 管道的读端和写端默认都是阻塞的（读：无数据时阻塞。写：数据满了阻塞）。
<a name="NaJRO"></a>
### 02-管道的原理

- 管道的实质是内核缓冲区，内部使用环形队列实现。
- 默认缓冲区大小为4K，可以使用ulimit -a命令获取大小。
- 实际操作过程中缓冲区会根据数据压力做适当调整。
<a name="kfFU8"></a>
### 03-管道的局限性

- 数据一旦被读走，便不在管道中存在，不可反复读取。
- 数据只能在一个方向上流动，若要实现双向流动，必须使用两个管道
- 只能在有血缘关系的进程间使用管道。

3.4创建管道-pipe函数

- 函数作用:
   - 创建一个管道
- 函数原型:
   - int pipe(int fd[2]);
- 函数参数:
   - 若函数调用成功，fd[0]存放管道的读端，fd[1]存放管道的写端
- 返回值:
   - 成功返回0；
   - 失败返回-1，并设置errno值。
- 	函数调用成功返回读端和写端的文件描述符，其中**fd[0]是读端， fd[1]是写端**，**向管道读写数据是通过使用这两个文件描述符进行的，读写管道的实质是操作内核缓冲区。**
-   	管道创建成功以后，创建该管道的进程（父进程）同时掌握着管道的读端和写端。如何实现父子进程间通信呢？
<a name="tU58u"></a>
### 05-父子进程使用管道通信
一个进程在由pipe()创建管道后，一般再fork一个子进程，然后通过管道实现父子进程间的通信（因此也不难推出，只要两个进程中存在血缘关系，这里的血缘关系指的是具有共同的祖先，都可以采用管道方式来进行通信）。**父子进程间具有相同的文件描述符，且指向同一个管道pipe**，其他没有关系的进程不能获得pipe（）产生的两个文件描述符，也就不能利用同一个管道进行通信。<br />**第一步：父进程创建管道**<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671283913701-e1778188-037d-4991-83af-7aea1c4bcb24.png#averageHue=%23f4f4f4&clientId=u96db4cd0-8067-4&from=paste&height=250&id=ue5bea977&name=image.png&originHeight=250&originWidth=542&originalType=binary&ratio=1&rotation=0&showTitle=false&size=13074&status=done&style=none&taskId=u94f4fe22-b537-4384-bff5-319a6e4056a&title=&width=542)<br />**第二步：父进程fork出子进程**<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671283917461-656fc16c-9f64-4cc9-bc84-891112989d15.png#averageHue=%23f1f1f0&clientId=u96db4cd0-8067-4&from=paste&height=227&id=u8a693940&name=image.png&originHeight=227&originWidth=707&originalType=binary&ratio=1&rotation=0&showTitle=false&size=19870&status=done&style=none&taskId=u2cb92d8b-7e35-42d0-9ec4-74ef8c8ce93&title=&width=707)<br />**第三步：父进程关闭fd[0]，子进程关闭fd[1]**<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671283921185-51e9c774-d6cc-45df-915a-5d10a797570a.png#averageHue=%23f0f0f0&clientId=u96db4cd0-8067-4&from=paste&height=238&id=u1751b042&name=image.png&originHeight=238&originWidth=724&originalType=binary&ratio=1&rotation=0&showTitle=false&size=19072&status=done&style=none&taskId=u8f18801f-a6dd-499a-a3ca-48aea660cc5&title=&width=724)<br />**创建步骤总结：**

- 父进程调用pipe函数创建管道，得到两个文件描述符fd[0]和fd[1]，分别指向管道的读端和写端。
- 父进程调用fork创建子进程，那么子进程也有两个文件描述符指向同一管。
- 父进程关闭管道读端，子进程关闭管道写端。父进程可以向管道中写入数据，子进程将管道中的数据读出，这样就实现了父子进程间通信。
<a name="u1nQo"></a>
### 06-管道的读写行为

- 读操作
   - 有数据
      - read正常读，返回读出的字节数
   - 无数据
      - 写端全部关闭
         - read解除阻塞，返回0, 相当于读文件读到了尾部
      - 没有全部关闭
         - read阻塞
- 写操作
   - 读端全部关闭
      - 管道破裂，进程终止, 内核给当前进程发SIGPIPE信号
   - 读端没全部关闭
      - 缓冲区写满了
         - write阻塞
      - 缓冲区没有满
         - 继续write
<a name="PUnKS"></a>
### 07-如何设置管道为非阻塞
默认情况下，管道的读写两端都是阻塞的，若要设置读或者写端为非阻塞，则可参<br />考下列三个步骤进行：<br />第1步： int flags = fcntl(fd[0], F_GETFL, 0); <br />第2步： flag |= O_NONBLOCK;<br />第3步：fcntl(fd[0], F_SETFL, flags);<br />若是读端设置为非阻塞：

   - 写端没有关闭，管道中没有数据可读，则read返回-1；
   - 写端没有关闭，管道中有数据可读，则read返回实际读到的字节数
   - 写端已经关闭，管道中有数据可读，则read返回实际读到的字节数
   - 写端已经关闭，管道中没有数据可读，则read返回0
<a name="X388f"></a>
### 08-如何查看管道缓冲区大小
命令<br />ulimit -a<br />函数<br />long fpathconf(int fd, int name);<br />printf("pipe size==[%ld]\n", fpathconf(fd[0], _PC_PIPE_BUF));<br />printf("pipe size==[%ld]\n", fpathconf(fd[1], _PC_PIPE_BUF));
<a name="PmEos"></a>
## 04-FIFO
<a name="WyJpK"></a>
### 01-FIFO介绍
**FIFO常被称为命名管道**，以区分管道(pipe)。管道(pipe)只能用于“有血缘关系”的进程间通信。但通过FIFO，不相关的进程也能交换数据。<br />	FIFO是Linux基础文件类型中的一种（文件类型为p，可通过ls -l查看文件类型）。但FIFO文件在磁盘上没有数据块，文件大小为0，仅仅用来标识内核中一条通道。进程可以打开这个文件进行read/write，实际上是在读写内核缓冲区，这样就实现了进程间通信。
<a name="uZEEY"></a>
### 02-创建管道

- 方式1-使用命令 mkfifo
   - 命令格式： mkfifo 管道名
   - 例如：mkfifo myfifo
- 方式2-使用函数
   - int mkfifo(const char *pathname, mode_t mode);
   - 参数说明和返回值可以查看man 3 mkfifo
- 当创建了一个FIFO，就可以使用open函数打开它，常见的文件I/O函数都可用于FIFO。如：close、read、write、unlink等。
- FIFO严格遵循先进先出（first in first out），对FIFO的读总是从开始处返回数据，对它们的写则把数据添加到末尾。**它们不支持诸如**lseek**()等文件定位操作。**
<a name="hAdOI"></a>
### 03-使用FIFO完成两个进程通信
使用FIFO完成两个进程通信的示意图<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671284208990-df00a7c2-04c4-4aa6-8490-d03244fd64fb.png#averageHue=%23fefdfd&clientId=u96db4cd0-8067-4&from=paste&height=344&id=uaed29f7d&name=image.png&originHeight=344&originWidth=359&originalType=binary&ratio=1&rotation=0&showTitle=false&size=19500&status=done&style=none&taskId=uff2de7ef-e334-4cdf-93a7-dc4231c4c79&title=&width=359)<br />思路：

- 进程A：
   - 创建一个fifo文件：myfifo
   - 调用open函数打开myfifo文件
   - 调用write函数写入一个字符串如：“hello world”（其实是将数据写入到了内核缓冲区）
   - 调用close函数关闭myfifo文件
- 进程B：
   - 调用open函数打开myfifo文件
   - 调用read函数读取文件内容（其实就是从内核中读取数据）
   - 打印显示读取的内容
   - 调用close函数关闭myfifo文件

注意：myfifo文件是在进程A中创建的，如果先启动进程B会报错。思考一下如何解决这个问题呢？？？
<a name="zrBZy"></a>
## 05-内存映射区
<a name="nsMm6"></a>
### 01-存储映射区介绍
	存储映射I/O (Memory-mapped I/O) 使一个磁盘文件与存储空间中的一个缓冲区（内存）相映射。从缓冲区中取数据，就相当于读文件中的相应字节；将数据写入缓冲区，则会将数据写入文件。这样，就可在不使用read和write函数的情况下，使用地址（指针）完成I/O操作。<br />使用存储映射这种方法，首先应通知内核，将一个指定文件映射到存储区域(内存)中。这个映射工作可以通过mmap函数来实现<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671284355657-4096cd6e-72cf-4830-8ce7-9ed0af2731f7.png#averageHue=%23f9f8f8&clientId=u96db4cd0-8067-4&from=paste&height=361&id=u2c4c3eab&name=image.png&originHeight=361&originWidth=448&originalType=binary&ratio=1&rotation=0&showTitle=false&size=8414&status=done&style=none&taskId=u0c16a899-2f64-426c-9771-50cbc8de88a&title=&width=448)
<a name="li39T"></a>
### 02-mmap函数
```cpp
void * addr = mmap(NULL,len, PROT_READ|PROT_WRITE, MAP_SHARED,fd,0);
```

- 函数作用:
   - 建立存储映射区
- 函数原型
   - void *mmap(void *addr, size_t length, int prot, int flags, int fd, off_t offset);
- 函数返回值：
   - 成功：返回创建的映射区首地址；
   - 失败：MAP_FAILED宏
- 参数：    
   - addr:    指定映射的起始地址, 通常设为NULL, 由系统指定
   - length：映射到内存的文件长度
   - prot：  映射区的保护方式, 最常用的:
      - 读：PROT_READ
      - 写：PROT_WRITE
      - 读写：PROT_READ | PROT_WRITE
   - flags：映射区的特性, 可以是
      - MAP_SHARED: 写入映射区的数据会写回文件, 且允许其他映射该文件的进程共享。
      - MAP_PRIVATE: 对映射区的写入操作会产生一个映射区的复制(copy-on-write), 对此区域所做的修改不会写回原文件。
   - fd：由open返回的文件描述符, 代表要映射的文件。
   - offset：以文件开始处的偏移量, **必须是4k的整数倍**, 通常为0, 表示从文件头开始映射。
<a name="WaNgb"></a>
### 03-munmap函数

- 函数作用:
   - 释放由mmap函数建立的存储映射区
- 函数原型:
   - int munmap(void *addr, size_t length);
- 返回值：
   - 成功：返回0
   - 失败：返回-1，设置errno值
- 函数参数:
   - addr：调用mmap函数成功返回的映射区首地址
   - length：映射区大小（mmap函数的第二个参数）
<a name="kkjOZ"></a>
### 04-mmap注意事项

- 创建映射区的过程中，隐含着一次对映射文件的读操作，将文件内容读取到映射区
- 当MAP_SHARED时，要求：映射区的权限应 <=文件打开的权限(出于对映射区的保护)。而MAP_PRIVATE则无所谓，因为mmap中的权限是对内存的限制。
- 映射区的释放与文件关闭无关，只要映射建立成功，文件可以立即关闭。
- 特别注意，当映射文件大小为0时，不能创建映射区。所以，用于映射的文件必须要有实际大小；mmap使用时常常会出现总线错误，通常是由于共享文件存储空间大小引起的。
- munmap传入的地址一定是mmap的返回地址。坚决杜绝指针++操作。
- 文件偏移量必须为0或者4K的整数倍
- mmap创建映射区出错概率非常高，一定要检查返回值，确保映射区建立成功再进行后续操作。
<a name="dVMTw"></a>
### 05-有关mmap函数的使用总结

- 第一个参数写成NULL
- 第二个参数要映射的文件大小 > 0
- 第三个参数：PROT_READ 、PROT_WRITE
- 第四个参数：MAP_SHARED 或者 MAP_PRIVATE
- 第五个参数：打开的文件对应的文件描述符
- 第六个参数：4k的整数倍

<a name="IAv00"></a>
# 07-信号
<a name="UGuCo"></a>
## 1 学习目标
了解信号中的基本概念<br />熟练使用信号相关的函数<br />参考文档使用信号集操作相关函数<br />熟练使用信号捕捉函数signal<br />熟练使用信号捕捉函数sigaction<br />熟练掌握使用信号完成子进程的回收
<a name="hHofG"></a>
## 信号介绍

- 信号的概念
   - 信号是信息的载体，Linux/UNIX 环境下，古老、经典的通信方式， 现下依然是主要的通信手段。
- 信号在我们的生活中随处可见，例如：
   - 古代战争中摔杯为号；
   - 现代战争中的信号弹；
   - 体育比赛中使用的信号枪......
- 信号的特点
   - 简单
   - 不能携带大量信息

满足某个特点条件才会产生
<a name="vyOi2"></a>
## 2 信号的机制
进程A给进程B发送信号，进程B收到信号之前执行自己的代码，收到信号后，不管执行到程序的什么位置，都要暂停运行，去处理信号，处理完毕后再继续执行。与硬件中断类似——异步模式。但信号是软件层面上实现的中断，早期常被称为“软中断”。<br />每个进程收到的所有信号，都是由内核负责发送的。<br />进程A给进程B发送信号示意图：![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671284927247-249a9377-c932-482d-ac6e-71f53967ddfb.png#averageHue=%23fefefd&clientId=u987adce2-077d-4&from=paste&height=318&id=udab71e32&name=image.png&originHeight=318&originWidth=471&originalType=binary&ratio=1&rotation=0&showTitle=false&size=21974&status=done&style=none&taskId=u537b145e-cef5-4b9f-9bf5-fd6b65fb34a&title=&width=471)
<a name="GVel1"></a>
### 2.1 信号的状态
信号有三种状态**：产生、未决和递达**。

- 信号的产生
   - 按键产生，如：Ctrl+c、Ctrl+z、Ctrl+\
   - 系统调用产生，如：kill、raise、abort
   - 软件条件产生，如：定时器alarm
   - 硬件异常产生，如：非法访问内存(段错误)、除0(浮点数例外)、内存对齐出错(总线错误)
   - 命令产生，如：kill命令
- 未决：产生和递达之间的状态。主要由于阻塞(屏蔽)导致该状态。
- 递达：递送并且到达进程。
<a name="SEEUx"></a>
### 2.2信号的处理方式

- 执行默认动作
- 忽略信号(丢弃不处理)
- 捕捉信号(调用用户的自定义的处理函数)
<a name="eQU51"></a>
### 2.3 信号的特质
信号的实现手段导致信号有很强的延时性，但对于用户来说，时间非常短，不易察觉。<br />Linux内核的进程控制块PCB是一个结构体，task_struct, 除了包含进程id，状态，工作目录，用户id，组id，文件描述符表，还包含了信号相关的信息，主要指**阻塞信号集和未决信号集**。<br />注:表示PCB的task_struct结构体定义在：
> /usr/src/linux-headers-4.4.0-97/include/linux/sched.h:1390

<a name="wCWG8"></a>
### 2.4 阻塞信号集和未决信号集
   	Linux内核的进程控制块PCB是一个结构体，这个结构体里面包含了信号相关的信息，主要有阻塞信号集和未决信号集。<br />阻塞信号集中保存的都是被当前进程阻塞的信号。若当前进程收到的是阻塞信号集中的某些信号，这些信号需要暂时被阻塞，不予处理。<br />信号产生后由于某些原因(主要是阻塞)不能抵达，这类信号的集合称之为未决信号集。在屏蔽解除前，信号一直处于未决状态；若是信号从阻塞信号集中解除阻塞，则该信号会被处理，并从未决信号集中去除。
<a name="cSYsT"></a>
### 2.5 信号的四要素
通过man 7 signal可以查看信号相关信息

1. 信号的编号
   1. 使用kill -l命令可以查看当前系统有哪些信号，不存在编号为0的信号。其中1-31号信号称之为常规信号（也叫普通信号或标准信号），34-64称之为实时信号，驱动编程与硬件相关。
2. 信号的名称
3. 产生信号的事件
4. 信号的默认处理动作

**Term**：终止进程<br />**Ign**：忽略信号 (默认即时对该种信号忽略操作)<br />**Core**：终止进程，生成Core文件。(查验死亡原因，用于gdb调试)<br />**Stop**：停止（暂停）进程<br />**Cont**：继续运行进程<br />特别需要注意的是：
> The signals SIGKILL and SIGSTOP cannot be caught, blocked, or ignored.

**几个常用到的信号**<br />**SIGINT (ctrl+c 终止进程 )**<br />**SIGQUIT ctrl+\ 退出进程**<br />**SIGKILL 杀死进程无法被捕获，无法被忽略**<br />SIGSEGV、SIGUSR1、SIGUSR2、SIGPIPE、SIGALRM、<br />**SIGTERM 终止程序的通用信号，是kill命令的默认行为**<br />SIGCHLD、<br />**SIGSTOP(ctrl+z 停止进程无法被捕获，无法被忽略)**<br />**SIGCONT 继续进行**
<a name="rlORP"></a>
## 3 信号相关函数
3.1 signal函数

- 函数作用：注册信号捕捉函数。对一个信号做回调函数
- 函数原型
   - typedef void (*sighandler_t)(int);
   -   sighandler_t signal(int signum, sighandler_t handler);
- 函数参数
   - signum：信号编号
   - handler：信号处理函数
<a name="DsVv5"></a>
### 3.2 kill函数/命令

- 描述：给指定进程发送指定信号
- kill命令：kill -SIGKILL 进程PID
- kill函数原型：int kill(pid_t pid, int sig);     
- 函数返回值：
   - 成功：0；
   - 失败：-1，设置errno
- 函数参数：
   - sig信号参数：不推荐直接使用数字，应使用宏名，因为不同操作系统信号编号可能不同，但名称一致。
   - pid参数：
      - pid > 0: 发送信号给指定的进程。
      - pid = 0: 发送信号给与调用kill函数进程属于同一进程组的所有进程。
      - pid < -1:  取|pid|发给对应进程组。
      - pid = -1：发送给进程有权限发送的系统中所有进程。
- 进程组：每个进程都属于一个进程组，进程组是一个或多个进程集合，他们相互关联，共同完成一个实体任务，每个进程组都有一个进程组长，默认进程组ID与进程组长ID相同。

3.3 abort函数raise函数

- raise函数
   - 函说描述：给当前进程发送指定信号(自己给自己发)
   - 函数原型：int raise(int sig);
   - 函数返回值：成功：0，失败非0值
   - 函数拓展：**raise(signo) == kill(getpid(), signo);**
- abort函数
   - 函数描述：给自己发送异常终止信号**6) SIGABRT**，并产生core文件
   - 函数原型：void abort(void);  
   - 函数拓展：abort() == kill(getpid(), **SIGABRT);**
<a name="pD6uA"></a>
### 3.4 alarm函数   

- **函数原型：**unsigned int alarm(unsigned int seconds);
- **函数描述：**设置定时器(闹钟)。在指定seconds后，内核会给当前进程发送**14）SIGALRM**信号。进程收到该信号，**默认动作终止**。**每个进程都有且只有唯一的一个定时器。**
- **函数返回值：**返回0或剩余的秒数，无失败。例如：
   - **首个闹钟返回0，之后的新闹钟返回旧闹钟剩余的秒数(会覆盖旧闹钟)**
- **常用操作：**取消定时器alarm(0)，返回旧闹钟余下秒数。
   - alarm使用的是自然定时法，与进程状态无关，就绪、运行、挂起(阻塞、暂停)、终止、僵尸...无论进程处于何种状态，alarm都计时。
<a name="OK0M0"></a>
### 3.5 setitimer函数

- **函数原型       **

**int setitimer(int which, const struct itimerval *new_value,**<br />**struct itimerval *old_value);**

- **函数描述**
   - 设置定时器(闹钟)，可代替alarm函数，精度微秒us，可以实现周期定时。
- **函数返回值**
   - 成功：0；
   - 失败：-1，设置errno值
- **函数参数：**
- which：指定定时方式
   - 自然定时：ITIMER_REAL → **14）SIGALRM**计算自然时间
   - 虚拟空间计时(用户空间)：ITIMER_VIRTUAL → **26）SIGVTALRM**  只计算进程占用cpu的时间
   - 运行时计时(用户+内核)：ITIMER_PROF → **27）SIGPROF**计算占用cpu及执行系统调用的时间
- new_value：struct itimerval, 负责设定timeout时间。
- i**timerval.it_value: 设定第一次执行function所延迟的秒数 itimerval.it_interval: 设定以后每几秒执行function**
```cpp
struct itimerval { 
struct timerval it_interval; // 闹钟触发周期
struct timerval it_value; // 闹钟触发时间
}; 
struct timeval { 
long tv_sec;                     // 秒
long tv_usec;                            // 微秒
}             
```

- old_value：存放旧的timeout值，一般指定为NULL


<a name="wVyTh"></a>
## 4信号集相关
4.1 未决信号集和阻塞信号集的关系<br />阻塞信号集是当前进程要阻塞的信号的集合，未决信号集是当前进程中还处于未决状态的信号的集合，这两个集合存储在内核的PCB中。<br />下面以SIGINT为例说明信号未决信号集和阻塞信号集的关系：

- 当进程收到一个SIGINT信号（信号编号为2），首先这个信号会保存在未决信号集合中，此时对应的2号编号的这个位置上置为1，表示处于未决状态；在这个信号需要被处理之前首先要在阻塞信号集中的编号为2的位置上去检查该值是否为1：
   - 如果为1，表示SIGNIT信号被当前进程阻塞了，这个信号暂时不被处理，所以未决信号集上该位置上的值保持为1，表示该信号处于未决状态；
   - 如果为0，表示SIGINT信号没有被当前进程阻塞，这个信号需要被处理，内核会对SIGINT信号进行处理（执行默认动作，忽略或者执行用户自定义的信号处理函数），并将未决信号集中编号为2的位置上将1变为0，表示该信号已经处理了，这个时间非常短暂，用户感知不到。
   - 当SIGINT信号从阻塞信号集中解除阻塞之后，该信号就会被处理。
   - ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671285465044-082b618f-c5b7-42fa-996a-02c038f7c74b.png#averageHue=%23fefdfd&clientId=u987adce2-077d-4&from=paste&height=426&id=u25a05bba&name=image.png&originHeight=426&originWidth=492&originalType=binary&ratio=1&rotation=0&showTitle=false&size=25079&status=done&style=none&taskId=u49e0ad64-81b6-43f5-9c79-d74a5e7dc81&title=&width=492)

4.2 信号集相关函数<br />由于**信号集属于内核的一块区域，用户不能直接操作内核空间**，为此，内核提供了一些信号集相关的接口函数，使用这些函数用户就可以完成对信号集的相关操作。<br />**信号集是一个能表示多个信号的数据类型，sigset_t set**，set即一个信号集。既然是一个集合，就需要对集进行添加、删除等操作。
```cpp
sigset_t类型的定义在signal.h文件中的第49行处:
typedef __sigset_t sigset_t;

__sigset_t的定义在sigset.h文件中的26，27行处: 
# define _SIGSET_NWORDS (1024 / (8 * sizeof (unsigned long int)))
typedef struct
{
unsigned long int __val[_SIGSET_NWORDS];
} __sigset_t;
```

上述变量类型的定义的查找有个小窍门：可以执行gcc的预处理命令：<br />gcc -E test.c -o test.i 这样头文件就会展开，可以直接到test.i文件中看到相关变量类型的定义。<br />常用写法：
```cpp
        // 阻塞 sigchld信号                                                                
sigset_t mask;                                                                   
sigemptyset(&mask);                                                              
sigaddset(&mask,SIGCHLD);                                                        
sigprocmask(SIGBLOCK,&mask,NULL);  
```


**信号集相关函数:**

1. int sigemptyset(sigset_t *set);
   1. 函数说明：将某个信号清0                     
   2. 函数返回值：成功：0；失败：-1，设置errno
2. int sigfillset(sigset_t *set);
   1. 函数说明：将某个信号集置1                           
   2. 函数返回值：成功：0；失败：-1，设置errno
3. int sigaddset(sigset_t *set, int signum);
   1. 函数说明：将某个信号加入信号集合中
   2. 函数返回值：成功：0；失败：-1，设置errno
4. int sigdelset(sigset_t *set, int signum);          
   1. 函数说明：将某信号从信号清出信号集      
   2. 函数返回值：成功：0；失败：-1，设置errno
5. int sigismember(const sigset_t *set, int signum);
   1. 函数说明：判断某个信号是否在信号集中
   2. 函数返回值：在：1；不在：0；出错：-1，设置errno
6. sigprocmask函数
   1. 函数说明：用来屏蔽信号、解除屏蔽也使用该函数。其本质，读取或修改进程控制块中的信号屏蔽字（阻塞信号集）。
   2. 特别注意，屏蔽信号只是将信号处理延后执行(延至解除屏蔽)；而忽略表示将信号丢弃处理。
   3. 函数原型：int sigprocmask(int how, const sigset_t *set, sigset_t *oldset);
   4. 函数返回值：成功：0；失败：-1，设置errno
   5. 函数参数：
      1. how参数取值：假设当前的信号屏蔽字为mask
         1. SIG_BLOCK: 当how设置为此值，set表示需要屏蔽的信号。**相当于 **mask = mask|set
         2. SIG_UNBLOCK: 当how设置为此，set表示需要解除屏蔽的信号。相当于 mask = mask & ~set
         3. SIG_SETMASK: 当how设置为此，set表示用于替代原始屏蔽及的新屏蔽集。相当于mask = set若，调用sigprocmask解除了对当前若干个信号的阻塞，则在sigprocmask返回前，至少将其中一个信号递达。
      2. set：传入参数，是一个自定义信号集合。由参数how来指示如何修改当前信号屏蔽字。
      3. oldset：传出参数，保存旧的信号屏蔽字。
7. sigpending函数
   1. 函数原型：int sigpending(sigset_t *set);          
   2. 函数说明：读取当前进程的未决信号集
   3. 函数参数：set传出参数
   4. 函数返回值：成功：0；失败：-1，设置errno
<a name="RxLut"></a>
## 5信号捕捉函数

- signal函数
- sigaction函数
   - 函数说明：
      - 注册一个信号处理函数
   - 函数原型：
      - int sigaction(int signum, const struct sigaction *act, struct sigaction *oldact);
   - 函数参数：
      - signum：捕捉的信号
      - act：    传入参数，新的处理方式。
      - oldact：传出参数，旧的处理方式

```cpp
struct sigaction {
void  (*sa_handler)(int);       // 信号处理函数
void  (*sa_sigaction)(int, siginfo_t *, void *); //信号处理函数
sigset_t  sa_mask; //信号处理函数执行期间需要阻塞的信号
int      sa_flags; //通常为0，表示使用默认标识
void     (*sa_restorer)(void);
};
```

总结：

- sa_handler：指定信号捕捉后的处理函数名(即注册函数)。也可赋值为SIG_IGN表忽略或 SIG_DFL表执行默认动作
- sa_mask: 用来指定在信号处理函数执行期间需要被屏蔽的信号，特别是当某个信号被处理时，它自身会被自动放入进程的信号掩码，因此在信号处理函数执行期间这个信号不会再度发生。注意：仅在处理函数被调用期间屏蔽生效，是临时性设置。
- sa_flags：通常设置为0，使用默认属性。
- sa_restorer：已不再使用   

**知识点: 信号处理不支持排队:**<br />**在XXX信号处理函数执行期间, XXX信号是被阻塞的, 如果该信号产生了多次, 在XXX信号处理函数结束之后,  该XXX信号只被处理一次.**<br />**在XXX信号处理函数执行期间,如果阻塞了YYY信号, 若YYY信号产生了多次, 当XXX信号处理函数结束后, YYY信号只会被处理一次.**

**内核实现信号捕捉的过程**<br />如果信号的处理动作是用户自定义函数，在信号递达时就调用这个函数，这称为捕捉信号。由于信号处理函数的代码是在用户空间的，处理过程比较复杂，举例如下：<br />1.       用户程序注册了SIGQUIT信号的处理函数sighandler。<br />2.       当前正在执行main函数，这时发生中断或异常切换到内核态。<br />3.       在中断处理完毕后要返回用户态的main函数之前检查到有信号SIGQUIT递达。<br />4.       内核决定返回用户态后不是恢复main函数的上下文继续执行，而是执行sighandler函数，sighandler和main函数使用不同的堆栈空间，它们之间不存在调用和被调用的关系，是两个独立的控制流程。<br />5.       sighandler函数返回后自动执行特殊的系统调用sigreturn再次进入内核态。<br />6.       如果没有新的信号要递达，这次再返回用户态就是恢复main函数的上下文继续执行了。<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671285764832-a3bb2c10-5dbb-45e8-b712-817ec9b12c91.png#averageHue=%23ebebeb&clientId=u987adce2-077d-4&from=paste&height=494&id=uad8832c8&name=image.png&originHeight=494&originWidth=617&originalType=binary&ratio=1&rotation=0&showTitle=false&size=64164&status=done&style=none&taskId=ub068d7f2-26a0-4f8a-a5e4-aa337665f44&title=&width=617)
<a name="tFsgV"></a>
## 6 SIGCHLD信号
6.1 产生SIGCHLD信号的条件

- 子进程结束的时候
- 子进程收到SIGSTOP信号
- 当子进程停止时，收到SIGCONT信号

6.2 SIGCHLD信号的作用

- 子进程退出后，内核会给它的父进程发送SIGCHLD信号，父进程收到这个信号后可以对子进程进行回收。
- 使用SIGCHLD信号完成对子进程的回收可以避免父进程阻塞等待而不能执行其他操作，只有当父进程收到SIGCHLD信号之后才去调用信号捕捉函数完成对子进程的回收，未收到SIGCHLD信号之前可以处理其他操作。

6.3 使用SIGCHLD信号完成对子进程的回收<br />**注意点：**

- **有可能还未完成信号处理函数的注册三个子进程都退出了。**
   - **解决办法：可以在fork之前先将SIGCHLD信号阻塞，当完成信号处理函数的注册后在解除阻塞。**
- **当SIGCHLD信号函数处理期间, SIGCHLD信号若再次产生是被阻塞的,而且若产生了多次, 则该信号只会被处理一次, 这样可能会产生僵尸进程。**
   - **解决办法: 可以在信号处理函数里面使用while(1)循环回收, 这样就有可能出现捕获一次SIGCHLD信号但是回收了多个子进程的情况，从而可以避免产生僵尸进程。**
<a name="VdK8U"></a>
# 08-守护进程和线程
<a name="O3GBH"></a>
## 1 守护进程
<a name="e0zxS"></a>
### 1.1 守护进程介绍
Daemon(精灵)进程，是Linux中的后台服务进程，通常独立于控制终端并且周期性地执行某种任务或等待处理某些发生的事件。一般采用以d结尾的名字，如vsftpd<br />Linux后台的一些系统服务进程**，没有控制终端，不能直接和用户交互**。不受用户登录、注销的影响，一直在运行着，他们都是守护进程。<br />如：**预读入缓输出机制的实现；ftp服务器；nfs服务器等。**<br />总结守护进程的特点：

- Linux后台服务进程
- 独立于控制终端
- 周期性的执行某种任务
- 不受用户登陆和注销的影响
- 一般采用以d结尾的名字
<a name="VFtd6"></a>
### 1.2 进程组和会话
**进程组**

- 进程组是一个或者多个进程的集合，每个进程都属于一个进程组，引入进程组是为了简化对进程的管理。当父进程创建子进程的时候，默认子进程与父进程属于同一个进程组。
   - **进程组ID==第一个进程ID（组长进程）**。如父进程创建了多个子进程，父进程和多个子进程同属于一个组，而由于父进程是进程组里的第一个进程，所以父进程就是这个组的组长, 组长ID==父进程ID。
- 可以使用kill -SIGKILL -进程组ID(负的)来将整个进程组内的进程全部杀死。
- **只要进程组中有一个进程存在，进程组就存在，与组长进程是否终止无关。**
- 进程组生存期：从进程组创建到最后一个进程离开

**会话**

- 一个会话是一个或多个进程组的集合。
- 创建会话的进程不能是进程组组长
- **创建会话的进程成为一个进程组的组长进程，同时也成为会话的会长。**
- 需要有root权限（ubuntu不需要）
- 新创建的会话丢弃原有的控制终端**如守护进程，不依赖终端**
- 建立新会话时，先调用fork, 父进程终止，子进程调用setsid函数

**可以使用ps ajx来查看进程组ID和会话ID**<br />可以fork出几个子进程，然后查看进程组ID和会话ID<br />**进程组和会话的关系图**<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671286052433-fb87253b-062d-417c-b990-e35152f573c6.png#averageHue=%23e8e7e7&clientId=u987adce2-077d-4&from=paste&height=430&id=u1acc3024&name=image.png&originHeight=430&originWidth=722&originalType=binary&ratio=1&rotation=0&showTitle=false&size=95228&status=done&style=none&taskId=ufcbf7817-c07c-4d2a-a325-14463367d3e&title=&width=722)
<a name="s23aa"></a>
### 1.3 创建守护进程的模型
第1步：fork子进程，父进程退出

- 子进程继承了父进程的进程组ID, 但具有一个新的进程ID,这样就保证了子进程不是一个进程组的组长ID,这对于下面要做的setsid函数的调用是必要的前提条件

第2步：子进程调用setsid函数创建新会话

- 调用这个函数以后
   - 该进程成为新会话的首进程，是会话的会长
   - 成为一个新进程组的组长进程，是进程组组长
   - 不受控制终端的影响

第3步：改变当前工作目录chdir

- 如：a.out在U盘上，启动这个程序，这个程序的当前的工作目录就是这个u盘，如果u盘拔掉后进程的当前工作目录将消失，a.out将不能正常工作。

第4步：重设文件掩码   mode & ~umask

- 子进程会继承父进程的掩码
- 增加子进程程序操作的灵活性
- umask(0000);

第5步：关闭文件描述符

- 守护进程不受控制终端的影响所以可以关闭，以释放资源
- close(STDIN_FILENO);
- close(STDOUT_FILENO);
- close(STDERR_FILENO);

第6步：执行核心工作

- 守护进程的核心代码逻辑
<a name="pbBT6"></a>
## 2 线程
<a name="v3apf"></a>
### 2.1 什么是线程

- 轻量级的进程（LWP：light weight process），在Linux环境下线程的本质仍是进程。
- 进程：拥有独立的地址空间，拥有PCB，相当于独居。
- 线程：有PCB，但没有独立的地址空间，多个线程共享进程空间，相当于合租。

![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671286162835-352f6460-a4aa-4d2d-b19b-16b8cbfb5629.png#averageHue=%23fefbfb&clientId=u987adce2-077d-4&from=paste&height=461&id=u17927fcc&name=image.png&originHeight=461&originWidth=615&originalType=binary&ratio=1&rotation=0&showTitle=false&size=90220&status=done&style=none&taskId=u9836aa69-db34-46e6-8dbe-55a9b19451d&title=&width=615)<br />在Linux操作系统下：        

- **线程：最小的执行单位**
- **进程：最小分配资源单位****，可看成是只有一个线程的进程。**

**线程的特点**

- 类Unix系统中，早期是没有“线程”概念的，80年代才引入，借助进程机制实现出了线程的概念。因此在这类系统中，进程和线程关系密切。
- 线程是轻量级进程(light-weight process)，也有PCB，创建线程使用的底层函数和进程一样，都是clone
- 从内核里看进程和线程是一样的，都有各自不同的PCB.
- 进程可以蜕变成线程
- 在linux下，线程最是小的执行单位；进程是最小的分配资源单位

![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671286217688-daf8e407-34a5-418e-88f9-51a6a83966a8.png#averageHue=%23fcfdfa&clientId=u987adce2-077d-4&from=paste&height=533&id=udc8c1399&name=image.png&originHeight=533&originWidth=745&originalType=binary&ratio=1&rotation=0&showTitle=false&size=294433&status=done&style=none&taskId=u1908759a-df27-4fa1-b635-cfeac2c471e&title=&width=745)

   - 察看指定线程的LWP号：ps –Lf pid

实际上，**无论是创建进程的fork，还是创建线程的pthread_create，底层实现都是调用同一个内核函数 clone。**

- 如果复制对方的地址空间，那么就产出一个“进程”；
- 如果共享对方的地址空间，就产生一个“线程”。

so：**Linux内核是不区分进程和线程的, 只在用户层面上进行区分**。<br />所以，线程所有操作函数 pthread_* 是库函数，而非系统调用。
<a name="egYav"></a>
### 2.2 线程共享资源

- 文件描述符表
- 每种信号的处理方式
- 当前工作目录
- 用户ID和组ID
- 内存地址空间 (.text/.data/.bss/heap/共享库) 
<a name="pi7DR"></a>
### 2.3 线程非共享资源

- 线程id
- 处理器现场和栈指针(内核栈)
- 独立的栈空间(用户空间栈)
- errno变量
- 信号屏蔽字
- 调度优先级
<a name="N8sFe"></a>
### 2.4 线程优、缺点

- 优点：   
   - **提高程序并发性  **
   - 开销小   
   - 数据通信、共享数据方便
- 缺点：   
   - 库函数，不稳定  
   - gdb调试、编写困难   
   - 对信号支持不好
- 优点相对突出，缺点均不是硬伤。Linux下由于实现方法导致进程、线程差别不是很大。
<a name="JQbTJ"></a>
### 2.5 pthread_create函数

- 函数作用：
   - 创建一个新线程
   - **要引入pthread命令**
   - **gcc -pthread -o 1_pthread_create 1_pthread_create.c**
- 函数原型
```cpp
int pthread_create(pthread_t *thread, 
                    const pthread_attr_t *attr,
                    void *(*start_routine) (void *),
                    void *arg);
```

- 返回值
   - 成功，返回0
   - 失败，返回错误号
- 函数参数：
   - pthread_t：传出参数，保存系统为我们分配好的线程ID
      - 当前Linux中可理解为：typedef unsigned long int pthread_t。
   - attr：通常传NULL，表示使用线程默认属性。若想使用具体属性也可以修改该参数。
   - start_routine：函数指针，指向线程主函数(线程体)，该函数运行结束，则线程结束。
   - arg：线程主函数执行期间所使用的参数。

注意点

- **由于pthread_create的错误码不保存在errno中，因此不能直接用perror()打印错误信息，可以先用strerror()把错误码转换成错误信息再打印。**
- 如果任意一个线程调用了exit或_exit，则整个进程的所有线程都终止，由于从main函数return也相当于调用exit，为了防止新创建的线程还没有得到执行就终止，我们在main函数return之前延时1秒，这只是一种权宜之计，即使主线程等待1秒，内核也不一定会调度新创建的线程执行，下一节我们会看到更好的办法。
<a name="FQtmh"></a>
### 2.6 pthread_exit函数
在线程中禁止调用exit函数，否则会导致整个进程退出，取而代之的是调用pthread_exit函数，这个函数是使一个线程退出，如果主线程调用pthread_exit函数也不会使整个进程退出，不影响其他线程的执行。

- 函数描述
   - 将单个线程退出
- 函数原型
   - void pthread_exit(void *retval);   
- 函数参数
   - retval表示线程退出状态，通常传NULL
- 另注意，pthread_exit或者return返回的指针所指向的内存单元必须是全局的或者是用malloc分配的，不能在线程函数的栈上分配，因为当其它线程得到这个返回指针时线程函数已经退出了，栈空间就会被回收。
- 通过程序测试得知，pthread_exit函数只是使一个线程退出，假如子线程里面调用了exit函数，会使整个进程终止；如果主线程调用了pthread_exit函数，并不影响子线程，只是使主线程自己退出。
<a name="Qv8z9"></a>
### 2.7 pthread_join函数

- 函数描述：阻塞等待线程退出，获取线程退出状态。其作用，对应进程中的waitpid() 函数。
- 函数原型：int pthread_join(pthread_t thread, void **retval); 
- 函数返回值：
   - 成功：0；
   - 失败：错误号
- 函数参数：
   - thread：线程ID
   - **retval：存储线程结束状态，整个指针和pthread_exit的参数是同一块内存地址。**

一般先定义void *ptr; 然后pthread_join(threadid, &ptr);
<a name="nCgqs"></a>
### 2.8 pthread_detach函数
线程分离状态：指定该状态，线程主动与主控线程断开关系。线程结束后，其退出状态不由其他线程获取，而直接自己自动释放。网络、多线程服务器常用。<br />进程若有该机制，将不会产生僵尸进程。僵尸进程的产生主要由于进程死后，大部分资源被释放，一点残留资源仍存于系统中，导致内核认为该进程仍存在。<br />也可使用 pthread_create函数参2(线程属性)来设置线程分离。pthread_detach函数是在创建线程之后调用的。

- 函数描述
   - 实现线程分离
- 函数原型
   - int pthread_detach(pthread_t thread);       
- 函数返回值
   - 成功：0；
   - 失败：错误号
- 一般情况下，线程终止后，其终止状态一直保留到其它线程调用pthread_join获取它的状态为止。但是线程也可以被置为detach状态，**这**样的线程一旦终止就立刻回收它占用的所有资源，而不保留终止状态。不能对一个已经处于detach状态的线程调用pthread_join，这样的调用将返回EINVAL错误。也就是说，如果已经对一个线程调用了pthread_detach就不能再调用pthread_join了。
- 说明：如果线程已经设置了分离状态，则再调用pthread_join就会失败，可用这个方法验证是否已成功设置分离状态。
<a name="ZoG3r"></a>
### 2.9 pthread_cancel函数

- 函数描述
   - 杀死(取消)线程。其作用，对应进程中 kill() 函数。
- 函数原型
   - int pthread_cancel(pthread_t thread);        
- 函数返回值
   - 成功：0；
   - 失败：错误号

【注意】：线程的取消并不是实时的，而有一定的延时。需要等待线程到达某个取消点(检查点)。<br />类似于玩游戏存档，必须到达指定的场所(存档点，如：客栈、仓库、城里等)才能存储进度。杀死线程也不是立刻就能完成，必须要到达取消点。<br />取消点：是线程检查是否被取消，并按请求进行动作的一个位置。通常是一些系统调用creat，open，pause，close，read，write..... 执行命令man 7 pthreads可以查看具备这些取消点的系统调用列表。可粗略认为一个系统调用(进入内核)即为一个取消点。还以通过调用pthread_testcancel函数设置一个取消点。<br />函数原型：void pthread_testcancel(void);
<a name="NJ7tu"></a>
### 2.10 pthread_equal函数

- 函数描述：
   - 比较两个线程ID是否相等。
- 函数原型
   - int pthread_equal(pthread_t t1, pthread_t t2);
- 注意：这个函数是为了以能够扩展使用的，有可能Linux在未来线程ID pthread_t 类型被修改为结构体实现。
<a name="Ah6sI"></a>
### 2.11 进程函数和线程函数比较
| **进程** | **线程** |
| --- | --- |
| **fork** | pthread_create |
| **exit** | pthread_exit |
| **wait/waitpid** | pthread_join |
| **kill** | pthread_cancel |
| **getpid** | pthread_self |

![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671287248570-215d8511-9e1f-45a1-ba17-81eee77397c3.png#averageHue=%23ccd4e7&clientId=u987adce2-077d-4&from=paste&height=237&id=u594dcc91&name=image.png&originHeight=237&originWidth=697&originalType=binary&ratio=1&rotation=0&showTitle=false&size=53503&status=done&style=none&taskId=ucf2ff747-a126-4709-b0dc-594c0dae26c&title=&width=697)
<a name="CfjEo"></a>
## 3      线程属性
<a name="pYE2j"></a>
### 01-线程属性
linux下线程的属性是可以根据实际项目需要，进行设置，之前讨论的线程都是采用线程的默认属性，默认属性已经可以解决绝大多数开发时遇到的问题，如果对程序的性能提出更高的要求，则需要设置线程属性，本节以设置线程的分离属性为例讲解设置线程属性。<br />线程的分离状态决定一个线程以什么样的方式来终止自己，有两种状态：

   - 非分离状态：线程的默认属性是非分离状态，这种情况下，原有的线程等待创建的线程结束。只有当pthread_join()函数返回时，创建的线程才算终止，才能释放自己占用的系统资源。
   - 分离状态：分离线程没有被其他的线程所等待，自己运行结束了，线程也就终止了，马上释放系统资源。应该根据自己的需要，选择适当的分离状态。
<a name="lBZKY"></a>
### 02-设置线程属性分为以下步骤
第1步：定义线程属性类型类型的变量<br />pthread_attr_t  attr;   <br />第2步：对线程属性变量进行初始化<br />int pthread_attr_init (pthread_attr_t* attr);<br />第3步：设置线程为分离属性
```cpp
int pthread_attr_setdetachstate(
        pthread_attr_t *attr, int detachstate);
```
参数:

- attr: 线程属性
- detachstate:
   - PTHREAD_CREATE_DETACHED(分离)
   - PTHREAD_CREATE_JOINABLE（非分离)

 注意：这一步完成之后调用pthread_create函数创建线程，则创建出来的线程就是分离线程；其实上述三步就是pthread_create的第二个参数做准备工作。<br />第4步：释放线程属性资源<br />int pthread_attr_destroy(pthread_attr_t *attr);<br />参数：线程属性<br />验证：设置为分离属性的线程是不能够被pthread_join函数回收的，<br />可以通过调用pthread_join函数测试该线程是否已经是分离属性的线程。
<a name="dmuLD"></a>
## 4      线程同步
<a name="Y6Eef"></a>
### 4.1 线程同步的概念
线程同步，指一个线程发出某一功能调用时，在没有得到结果之前，该调用不返回。同时其它线程为保证数据一致性，不能调用该功能。
<a name="mLpjr"></a>
### 4.2 线程同步的例子

- 原子操作的概念
   - 原子操作指的是该操作要么不做，要么就完成。
- 使用互斥锁解决同步问题
   - 使用互斥锁其实是模拟原子操作，互斥锁示意图：
   - ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671287767345-91e8c07b-8683-4c09-9448-083b716f688b.png#averageHue=%23f1f0f0&clientId=u987adce2-077d-4&from=paste&height=298&id=u4f3e04ac&name=image.png&originHeight=298&originWidth=416&originalType=binary&ratio=1&rotation=0&showTitle=false&size=25056&status=done&style=none&taskId=u378f9887-915c-42e4-9f0c-dfaf623ea4b&title=&width=416)
- Linux中提供一把互斥锁mutex（也称之为互斥量）。每个线程在对资源操作前都尝试先加锁，成功加锁才能操作，操作结束解锁。
- 资源还是共享的，线程间也还是竞争的，但通过“锁”就将资源的访问变成互斥操作，而后与时间有关的错误也不会再产生了。
- 线程1访问共享资源的时候要先判断锁是否锁着，如果锁着就阻塞等待；若锁是解开的就将这把锁加锁，此时可以访问共享资源，访问完成后释放锁，这样其他线程就有机会获得锁。
- 应该注意：图中同一时刻，只能有一个线程持有该锁，只要该线程未完成操作就不释放锁。
- 使用互斥锁之后，两个线程由并行操作变成了串行操作，效率降低了，但是数据不一致的问题得到解决了。
<a name="HjmPF"></a>
### 4.3 互斥锁主要相关函数
<a name="F5StR"></a>
#### 01-pthread_mutex_t 类型

   - 其本质是一个结构体，为简化理解，应用时可忽略其实现细节，简单当成整数看待。
   - pthread_mutex_t mutex; 变量mutex只有两种取值1、
<a name="RLDuA"></a>
#### 02-pthread_mutex_init函数

   - 函数描述：
      - 初始化一个互斥锁(互斥量) ---> 初值可看作1
   - 函数原型：
```cpp
int pthread_mutex_init(
	pthread_mutex_t *restrict mutex, 
    const pthread_mutexattr_t *restrict attr
);
```

- 函数参数
   - mutex：传出参数，调用时应传 &mutex         
   - attr：互斥锁属性。是一个传入参数，通常传NULL，选用默认属性(线程间共享)。
   - **restrict关键字**：只用于限制指针，告诉编译器，所有修改该指针指向内存中内容的操作，只能通过本指针完成。不能通过除本指针以外的其他变量或指针修改互斥量mutex的两种初始化方式：
      - **静态初始化：**如果互斥锁 mutex 是静态分配的（定义在全局，或加了static关键字修饰），可以直接使用宏进行初始化。
         - pthead_mutex_t **muetx**= **PTHREAD_MUTEX_INITIALIZER**;
      - **动态初始化：**局部变量应采用动态初始化。
         - **pthread_mutex_init**(&mutex, NULL)
<a name="NdqTG"></a>
#### 03-pthread_mutex_destroy函数

- 函数描述
   - 销毁一个互斥锁
- 函数原型
   - int pthread_mutex_destroy(pthread_mutex_t *mutex);
- 函数参数
   - mutex—互斥锁变量
<a name="WfXH0"></a>
#### 04-pthread_mutex_lock函数

- 函数描述
   - 对互斥所加锁，可理解为将mutex--
- 函数原型
   - int pthread_mutex_lock(pthread_mutex_t *mutex);
- 函数参数
   - mutex—互斥锁变量
<a name="to0IH"></a>
#### 05-pthread_mutex_unlock函数

- 函数描述
   - 对互斥所解锁，可理解为将mutex ++
- 函数原型
   - int pthread_mutex_unlock(pthread_mutex_t *mutex);
<a name="T9tYl"></a>
#### 06-pthread_mutex_trylock函数

- 函数描述
   - 尝试加锁
- 函数原型
   - int pthread_mutex_trylock(pthread_mutex_t *mutex);
- 函数参数
   - mutex—互斥锁变量
<a name="C87qD"></a>
### 4.4 加锁和解锁
lock尝试加锁，如果加锁不成功，线程阻塞，阻塞到持有该互斥量的其他线程解锁为止。<br />unlock主动解锁函数，同时将阻塞在该锁上的所有线程全部唤醒，至于哪个线程先被唤醒，取决于优先级、调度。默认：先阻塞、先唤醒。<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671288237173-21812454-af40-475e-9ae1-79bf02eda1d3.png#averageHue=%231e1d1b&clientId=u987adce2-077d-4&from=paste&height=263&id=u7311c753&name=image.png&originHeight=404&originWidth=384&originalType=binary&ratio=1&rotation=0&showTitle=false&size=74577&status=done&style=none&taskId=uc5c59a3d-86a8-4e58-bee9-959a026f767&title=&width=250)![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671288239746-b526e9d8-13fe-46f1-9e81-34ab03ec8123.png#averageHue=%231e1d1b&clientId=u987adce2-077d-4&from=paste&height=273&id=u88e11209&name=image.png&originHeight=402&originWidth=369&originalType=binary&ratio=1&rotation=0&showTitle=false&size=71858&status=done&style=none&taskId=u57793bfe-6e24-449b-9ee9-d8920064fc6&title=&width=251)<br />总结：使用互斥锁之后，两个线程由并行变为了串行，效率降低了，但是可以使两个线程同步操作共享资源，从而解决了数据不一致的问题。
<a name="MVDYd"></a>
# 09-线程同步
<a name="PaeKw"></a>
## 学习目标：
熟练掌握互斥量的使用<br />说出什么叫死锁以及解决方案<br />熟练掌握读写锁的使用<br />熟练掌握条件变量的使用<br />理解条件变量实现的生产消费者模型<br />理解信号量实现的生产消费者模型
<a name="cEERQ"></a>
## 1 互斥锁
<a name="ShNBy"></a>
### 1.1互斥锁的使用步骤

- 第1步：创建一把互斥锁
   - pthread_mutex_t mutex;
- 初始化互斥锁
   - pthread_mutex_init(&mutex);---相当于mutex=1
- 在代码中寻找共享资源（也称为临界区）
   - pthread_mutex_lock(&mutex);  -- mutex = 0
- [临界区代码]
   - pthread_mutex_unlock(&mutex); -- mutex = 1
- 释放互斥锁资源
   - pthread_mutex_destroy(&mutex);

注意：必须在所有操作共享资源的线程上都加上锁否则不能起到同步的效果。
<a name="VkKW7"></a>
### 1.2 练习
编写思路：<br />1 定义一把互斥锁，应该为一全局变量<br />pthread_mutex_t mutex;<br />2 在main函数中对mutex进行初始化<br />pthread_mutex_init(&mutex, NULL);<br />3 创建两个线程，在两个线程中加锁和解锁<br />4 主线程释放互斥锁资源<br />pthread_mutex_destroy(&mutex);
<a name="fFPjS"></a>
### 1.3 死锁
死锁并不是linux提供给用户的一种使用方法，而是由于用户使用互斥锁不当引起的一种现象。<br />**常见的死锁有两种：**<br />第一种：自己锁自己，如下图代码片段<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671291169417-89134cef-d948-42d7-82a7-374a794694ae.png#averageHue=%231e1c1a&clientId=u987adce2-077d-4&from=paste&height=415&id=ub9ed49d9&name=image.png&originHeight=415&originWidth=505&originalType=binary&ratio=1&rotation=0&showTitle=false&size=102339&status=done&style=none&taskId=u58ce492b-45e2-4d7f-94e5-e48b3b92553&title=&width=505)<br />第二种 线程A拥有A锁，请求获得B锁；线程B拥有B锁，请求获得A锁，这样造成线程A和线程B都不释放自己的锁，而且还想得到对方的锁，从而产生死锁，如下图所示：<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671291154712-b49063b0-69e9-4515-b074-bf3cf01a7c47.png#averageHue=%23fefcfb&clientId=u987adce2-077d-4&from=paste&height=298&id=u1a5f63c2&name=image.png&originHeight=298&originWidth=459&originalType=binary&ratio=1&rotation=0&showTitle=false&size=37780&status=done&style=none&taskId=ufbf20990-4c6a-45bc-9245-96c6f85d876&title=&width=459)<br />如何解决死锁：

- 让线程按照一定的顺序去访问共享资源
- 在访问其他锁的时候，需要先将自己的锁解开
- 调用pthread_mutex_trylock，如果加锁不成功会立刻返回
<a name="vAED3"></a>
## 2 读写锁

- 什么是读写锁
   - 读写锁也叫共享-独占锁。当读写锁以读模式锁住时，它是以共享模式锁住的；当它以写模式锁住时，它是以独占模式锁住的。**写独占、读共享。**
- 读写锁使用场合
   - 读写锁非常适合于对数据结构读的次数远大于写的情况。
- 读写锁特性   
   - 读写锁是“写模式加锁”时，解锁前，所有对该锁加锁的线程都会被阻塞。
   - 读写锁是“读模式加锁”时，如果线程以读模式对其加锁会成功；如果线程以写模式加锁会阻塞。
   - 读写锁是“读模式加锁”时， 既有试图以写模式加锁的线程，也有试图以读模式加锁的线程。那么读写锁会阻塞随后的读模式锁请求。优先满足写模式锁。读锁、写锁并行阻塞，写锁优先级高

读写锁总结<br />读并行，写独占，当读写同时等待锁的时候写的优先级高

**读写锁主要操作函数**

- 定义一把读写锁
   - pthread_rwlock_t rwlock;
- 初始化读写锁
```cpp
int pthread_rwlock_init(                                
        pthread_rwlock_t *restrict rwlock, 
        const pthread_rwlockattr_t *restrict attr
);
```

- 函数参数
   - rwlock-读写锁
   - attr-读写锁属性，传NULL为默认属性
- 销毁读写锁
   - int pthread_rwlock_destroy(pthread_rwlock_t *rwlock);        
- 加读锁
   - int pthread_rwlock_rdlock(pthread_rwlock_t *rwlock);              
- 尝试加读锁
   - int pthread_rwlock_tryrdlock(pthread_rwlock_t *rwlock);
- 加写锁
   - int pthread_rwlock_wrlock(pthread_rwlock_t *rwlock);
- 尝试加写锁
   - int pthread_rwlock_trywrlock(pthread_rwlock_t *rwlock);
- 解锁
   - int pthread_rwlock_unlock(&pthread_rwlock_t *rwlock);
<a name="oTzNL"></a>
## 3 条件变量

- **条件本身不是锁！但它也可以造成线程阻塞**。通常与互斥锁配合使用。给多线程提供一个会合的场所。
   - 使用互斥量保护共享数据;
   - 使用条件变量可以使线程阻塞, 等待某个条件的发生, 当条件满足的时候解除阻塞.
- 条件变量的两个动作:
   - 条件不满足, 阻塞线程
   - 条件满足, 通知阻塞的线程解除阻塞, 开始工作.
- 条件变量相关函数
   - **pthread_cond_t  cond;**
>       - 定义一个条件变量

   - **int pthread_cond_init(pthread_cond_t *restrict cond,**

**const pthread_condattr_t *restrict attr);**
>       - 函数描述:初始化条件变量
>       - 函数参数: 
>          - cond: 条件变量
>          - attr: 条件变量属性, 通常传NULL
>       - 函数返回值:成功返回0, 失败返回错误号

   - **int pthread_cond_destroy(pthread_cond_t *cond);**
>       - 函数描述: 销毁条件变量
>       - 函数参数: 条件变量
>       - 返回值: 成功返回0, 失败返回错误号

   - **int pthread_cond_wait(pthread_cond_t *restrict cond,**

**pthread_mutex_t *restrict mutex);**
>       - 函数描述:	条件不满足, 引起线程阻塞并解锁;
> 
			     	    条件满足, 解除线程阻塞, 并加锁
>       - 函数参数:
>          - cond: 条件变量
>          - mutex: 互斥锁变量
>       - 函数返回值: 成功返回0, 失败返回错误号

-  **int pthread_cond_signal(pthread_cond_t *cond);**
>       - 函数描述: 唤醒至少一个阻塞在该条件变量上的线程
>       - 函数参数: 条件变量
>       - 函数返回值: 成功返回0, 失败返回错误号

- 4 使用条件变量的代码片段
- ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671291906719-495bd01d-a47e-4bbf-a2fa-5f37da371eb7.png#averageHue=%23f7f7f7&clientId=u987adce2-077d-4&from=paste&height=425&id=ucee1f1c8&name=image.png&originHeight=425&originWidth=410&originalType=binary&ratio=1&rotation=0&showTitle=false&size=46540&status=done&style=none&taskId=uccb49c11-57c7-4cad-97f3-07d48efe92e&title=&width=410)
- ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671291917706-1e9b6ab3-08c3-4449-a894-01a627bb4561.png#averageHue=%23f7f7f7&clientId=u987adce2-077d-4&from=paste&height=434&id=u35c9030c&name=image.png&originHeight=434&originWidth=415&originalType=binary&ratio=1&rotation=0&showTitle=false&size=46046&status=done&style=none&taskId=ue48efea5-f617-4682-bcf3-293054e9b7c&title=&width=415)
- 上述代码中，生产者线程调用pthread_cond_signal函数会使消费者线程在pthread_cond_wait处解除阻塞。
<a name="tsX6e"></a>
## 4 信号量
1 信号量介绍<br />	信号量相当于多把锁, 可以理解为是加强版的互斥锁<br />2 相关函数

   - 定义信号量 **sem_t sem;**
   - **int sem_init(sem_t *sem, int pshared, unsigned int value);  **      
>       - 函数描述: 初始化信号量
>       - 函数参数:
>          - sem: 信号量变量
>          - pshared: 0表示线程同步, 1表示进程同步
>          - value: 最多有几个线程操作共享数据
>       - 函数返回值:成功返回0, 失败返回-1, 并设置errno值

   - **int sem_wait(sem_t *sem);**
>       - 函数描述: 调用该函数一次, 相当于sem--, 当sem为0的时候, 引起阻塞
>       - 函数参数: 信号量变量
>       - 函数返回值: 成功返回0, 失败返回-1, 并设置errno值

   - **int sem_post(sem_t *sem);**
>       - 函数描述: 调用一次, 相当于sem++
>       - 函数参数: 信号量变量
>       - 函数返回值: 成功返回0, 失败返回-1, 并设置errno值

   - **int sem_trywait(sem_t *sem);**
>       - 函数描述: 尝试加锁, 若失败直接返回, 不阻塞
>       - 函数参数: 信号量变量
>       - 函数返回值: 成功返回0, 失败返回-1, 并设置errno值

   - **int sem_destroy(sem_t *sem);**
>       - 函数描述: 销毁信号量
>       - 函数参数: 信号量变量
>       - 函数返回值: 成功返回0, 失败返回-1, 并设置errno值


3 信号量代码片段:<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671292073133-e46a0fe8-32f0-4792-99a2-4847d5f7dd2d.png#averageHue=%23f9f8f8&clientId=u987adce2-077d-4&from=paste&height=423&id=ua568c94e&name=image.png&originHeight=423&originWidth=403&originalType=binary&ratio=1&rotation=0&showTitle=false&size=50454&status=done&style=none&taskId=ud2154903-6870-4c90-9052-e6bfbb1a102&title=&width=403)

![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671292075576-9c56989c-e75e-4f6b-a0b5-86ee047b29bd.png#averageHue=%23f8f7f7&clientId=u987adce2-077d-4&from=paste&height=358&id=u06402d89&name=image.png&originHeight=358&originWidth=403&originalType=binary&ratio=1&rotation=0&showTitle=false&size=45032&status=done&style=none&taskId=u791d3bd7-480d-4a45-a636-fe30c84c0ef&title=&width=403)
