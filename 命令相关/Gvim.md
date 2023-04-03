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
gvim 可以打开一个文件夹
## 1-编辑模式（输入模式）
```python
i        当前光标左侧插入
a        当前光标右侧插入
I        行首插入
A        行末插入
ctrl+p   代码补全
```

## 2-命令模式（Esc)

```python
剪切粘贴
   yy                  复制当前行
   p                   粘贴
   dd                  剪切当前行
   d5d 或者 5dd        删除5行 
   d + 鼠标左键 + d    删除对应的范围行
   v                  可视化模式，进行选择代码
   :5                 第5行

跳转：
   gg       移动到文件开头
   G        移动到文件结尾
   gg=G     代码格式化


文件内部查找
   鼠标选中单词    按*
   /name1         按n选择下一个 按N选择上一个
   /\<x2\>  只搜x2
   退出查找 :noh+enter (就是退出高亮)
文件内部查找替换
   全局替换
      :%s/from_f/to_t/g 一次性把from_f替换成to_t
      :%s/from_f/to_t/gc 每次做选择
   局部替换
      :10,20s/from_f/to_t/gc 10-20行做替换
      

分窗口
:vs 左右分
:sp 上下分
:q  退出窗口
   
ll -t   时间降序
ll -rt  时间升序

:E 退出到目录页
:w 保存不退出
:x 保存退出
:q!   不保存强制退出
```

查找目录下 有str的文件
grep -rn "apple_come" ./
```
教学：https://blog.51cto.com/u_15346322/3670341


