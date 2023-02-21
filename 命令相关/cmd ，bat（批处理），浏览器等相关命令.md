# 01-window命令
:::info
•返回桌面：Win+D
•打开运行框 win+r
•打开我的电脑 win+e
•搜索功能：Win+S
•最大/最小化窗口 win+上/下
•使用放大镜：Win+；
•切换桌面Win+Ctrl+←/→
•恢复网页Ctrl+Shift+T
•创建虚拟桌面：Win+Ctrl+D
•剪贴板功能：Win+V
•快速锁定屏幕：Win+L
•应用切换：Alt+Tab或者Win+Tab
•应用程序分屏：Win+←/→
•截图功能Win+Shift+S
•新建：Ctrl+N
•鼠标复制文件：Ctrl+鼠标拖动
•快速关闭网页：Ctrl+W
•自动关机：shutdown -s -t XX
•取消自动关机：shutdown -a
•投屏：Win+P
•蓝牙连接：Win+K
•快速关机：Win+X+U+U
•任务管理器：Ctrl+Alt+./Delete或者Ctrl+Shift+ESC
:::
# DOS命令
操作系统命令
# 02-cmd命令
```python
切换磁盘：D：
cd ../          进入上一层目录
cd              查看当前目录
dir             显示目录下的文件
md              创建目录 文件夹
cd              change directory(改变目录）的缩写 
mv              移动文件，也可以重新命名
copy            复制的意思
cd . > a.txt    创建空文件
del             删除文件
rd              remove directory--删除目录，
help　　　      查看所有命令帮助
tree            文件结构
tree：          不输入任何参数，输出一棵目录树，不显示文件，只显示目录；
tree/F：        递归显示目录结构；显示目录，也显示文件；
tree /F         在给出项目文件说明时，会十分有用；
find -r         查找文件
        ：for /r 目录名 %i in (匹配模式1,匹配模式2) do @echo %i
        eg：for /r DJ %i in (*) do @echo %i     查找Dj下面所有文件
            for /r . %i in (*DJ*) do @echo %i   查找当前文件夹下的
ren             ---批量修改文件名---  
                ren *.mp4 *.txt
xxx /?          获取命令帮助 
```
# 03-bat（批处理语法命令）
## 01-介绍
:::info
1.批处理文件是一个“.bat”结尾的文本文件，这个文件的每一行都是一条DOS命令。可以使用任何文本文件编辑工具创建和修改。
2.批处理是一种简单的程序，可以用 if 和 goto 来控制流程，也可以使用 for 循环。
3.批处理的编程能力远不如C语言等编程语言，也十分不规范。
4.每个编写好的批处理文件都相当于一个DOS的外部命令，把它所在的目录放到DOS搜索路径(path)中，即可在任意位置运行。
5.C:\AUTOEXEC.BAT 是每次系统启动时都会自动运行的，可以将每次启动时都要运行的命令放入该文件中。
6.大小写不敏感(命令符忽略大小写)
7.批处理的文件扩展名为 .bat 或 .cmd。
8.在命令提示下键入批处理文件的名称，或者双击该批处理文件，系统就会调用Cmd.exe来运行该文件。
:::
## 02-命令
```python
:: 注释
rem 注释  更常用
%~dp0       [获取当前路径]
%cd%        [执行的路径]
set         eg:set var=我是值 echo %var%
    - set /p var=请输入变量的值:
    - set /a var=%input% 会计算表达式
@           表示运行时不显示这一行的命令行
echo        打印内容
@echo on/off    打印命令/关闭命令  （终端显示运行的命令）
:lable      设置一个锚点，用 goto label跳跃过来
goto label  (label是参数，指定所要转向的批处理程序中的行。)
Pause       会暂停批处理的执行并在屏幕上显示xxx
& 之后的命令无论如何都会被执行。
&& 之后的命令只有在前&&之前的命令执行成功才会被执行
Call，start         调用其他程序
IF
    -if [not] "参数" == "字符串"            eg： if "%1" == "a" 
    -if exist config.sys edit config.sys    如果存就...
    -if errorlevel number                   如果是number，则条件成立，运行命令，否则运行下一句
    比较运算符:#
        EQU - 等于 (一般使用“==”)
        NEQ - 不等于 (没有 “!=”,改用“ if not 1==1 ”的写法)
        LSS - 小于
        LEQ - 小于或等于
        GTR - 大于
        GEQ - 大于或等于
for
    /d  只对于目录操作
    /r  递归遍历文件夹
    /l  数值范围
        eg: for /l %%i in (1,1,5) do @echo %%i
    /f  对于文件
```
## 03-for 批处理 
eg：
**将目录下的 *.mp4移动 到指定目录**
```python
pushd E:\tokyo 7th sister\LK 合集\testt
::set dir=E:\tokyo 7th sister\LK 合集\testt
for /r %%a in (*.mp4) do (
::复制
::XCOPY  /Y "%%a"  "E:\1_acg\MP4\0820\lk\test_get\"  

:: 移动
MOVE "%%a"  "E:\1_acg\MP4\0820\lk\test_get\"  
echo %%a
)
popd
pause
```
优化1：
```python
set from_dir="E:\1_acg\MP4\0813\sayika\test"
set to_dir="E:\2_acg\1020\to\"

pushd %from_dir%
::set dir=E:\tokyo 7th sister\LK 合集\testt
for /r %%a in (*.txt) do (
::复制
::XCOPY  /Y "%%a"  "E:\1_acg\MP4\0820\lk\test_get\"  

:: 移动
MOVE "%%a"  "%to_dir%"  
echo %%a
)
popd
pause
```
优化2： 重复，new新名 文件
```python
@echo off	
rem 不打印命令

set from_dir="E:\1_acg\MP4\AKT"
set to_dir="D:\apple\vedio\apple\"

pushd %from_dir%

for /r %%a in (*.mp4 *.ass *.mkv *.webm) do set n=0&call:checkfile "%%~a"  rem 跳到checkfile 带参数1（代表文件）
pause&exit		rem 没有文件后会停止
rem 到文件末，停止访问
goto :eof		
:checkfile
if not exist "%to_dir%%~n1%n%%~x1" (	
	rem %~n1% 文件名    %~x1% 文件后缀名
    
	move "%~1" "%to_dir%%~n1%n%%~x1"	
	
	echo "%~1"
	rem %~1 代表参数1
) else (
set/a n+=1
goto checkfile
)
```
**查看目录下所有文件名**
```python
pushd E:\tokyo 7th sister\LK 合集\testt
::set dir=E:\tokyo 7th sister\LK 合集\testt
for /r %%a in (*.*) do (
echo %%a
)
popd
pause
```
# 浏览器快捷命令
:::info
•ctrl --- 我的google配置
•t 当前开新tab --- ·+3
•r 刷新页面 --- ·+4
•n 新页面开新tab
•w 关闭当前页 --- ·+2
•d 添加收藏
•l 跳转到地址栏
•shift+t 恢复前一个页面 --- ·+1
•shift+i 进入开发模式（F12）
•shift+r 刷新缓存
•shift+N 新页面开无痕新tab
•shift+w 关闭浏览器
•tab 切换页面
:::
点击链接：
:::info
•ctrl 跳转到
•+shift 新页面跳转
•+alt 下载链接
:::
开发者模式中的：
:::info
•ctrl+shift+p ：进入执行命令窗口
•输入截屏 可以截取网页全屏
:::
