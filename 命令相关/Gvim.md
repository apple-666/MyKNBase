# 1-gvim的默认设置
在home目录下有 .vimrc 文件
```python
set showmatch        高亮显示匹配的括号
set matchtime = 2    高亮括号的闪烁时间
set shfitwidth = 4   自动缩进符
set tabstop = 4      tab制表符
set softtabstop = 4  4个空格为一个tab符
set expandtab        tab符号视为空格符
set smarttab         退格键时辨别tab
set number           显示行号
set cursorline       突出显示当前行
set lbr              折行显示时不折断单词
set nobackup         不生成备份文件
set noswapfile       不生成交换文件
set lines=30 columns= 100   文件窗口显示
set guioptions += b  添加水平滚动条
```
```python
set showmatch        
set matchtime = 2    
set shfitwidth = 4   
set tabstop = 4      
set softtabstop = 4  
set expandtab        
set smarttab         
set number           
set cursorline       
set lbr              
set nobackup         
set noswapfile       
set lines=30 columns= 100
set guioptions += b 
```

# 2-常用命令
## 1-编辑模式
```python
i 当前光标左侧插入
a 当前光标右侧插入
I 行首插入
A 行末插入
```
```python
文件内部查找
   /name1  按n选择下一个
文件内部查找
   %s/from_f/to_t/g 把from_f替换成to_t
   
ll -t   时间降序
ll -rt  时间升序

gg 到代码头
G  到代码尾

:w 保存不退出
```

Gvim:
```python
:E 退出到目录页

:/\<x2\>  只搜x2
搜到后 n下一个  N上一个

查找目录下 有str的文件
grep -rn "apple_come" ./
```
教学：https://blog.51cto.com/u_15346322/3670341


