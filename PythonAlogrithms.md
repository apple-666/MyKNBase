# 01-算法中常用的方法
力扣中：
执行代码的Ctrl+'
提交代码的Ctrl+Enter两个快捷键， ..
## 01-输入输出相关
```python
输入多个数据
a, b, c = map(int, input().split())

输入一行
str = input()

输入一个整数
n = int(input()) 或 (int)(input())

输入一个一维数组
a1 = input() 是一整行的字符  再转换成int
a = [int(i) for i in a1.split()]

输入一个二维数组----------------------------------------------------------------------------
int型二维:
a = [[0]*3]*2
for i in range(2):
    t = input()
    a[i] = [int(i) for i in t.split()]  
print(a)

char型二维:
n = int(input())        //输入二维数组的行数和列数
line = [[0]*n]*n        //初始化二维数组
for i in range(n):
    line[i] = input().split(" ")       //输入二维数组 1 2 4，同行数字用空格分隔，不同行则用回车换行
print(line)            //打印二维数组
----------------------------------------------------------------------------

保留位数：
print("%.2f",2.222)
print(format(2.2222,'.2f'))
```
## 02-数组
```python
# 初始化
dp = [0]*N
dp = [[0]*N for i in range(M)]  # M行N列 每行不会跟着变化
dp = [[0]*n]*m 每行都会跟着变化

# 常用切片
list[-n]   		第倒n个数据
list[m:n]  		从[m,n) 左闭右开
list[m:n:k] 	按k的间隔
list[::-1]		倒序
	eg:	t = t[::-1]
# 复制数组
深拷贝：
b = copy.deepcopy(a)

```

## 03-常用函数
```python
str1.find(str2) 	返回字串str2的下标
isalnum() 			方法检测字符串是否由字母和数字组成。
str.upper() str.lower()
ord('A') 64 返回ASCLL码

# 列表相关
nums.sort() 列表排序
num = list.pop() 默认出最后一个,
	eg:	list.pop(n)  出下标为n的   	list.pop(-1) 出最后一个
```


## 04-常用运算
```python
a = 9//3  # 3 整除
b = 9/3   # 3.0

#三目运算符
# ?的不允许
a = 1>0 ? True:False
# if else的运行
a= True if 1>0 else False

flag = not flag  取反操作

[0,n][nums[0]<nums[n]]  True是1下标 False是0下标
等价于:
n if nums[0] < nums[n] else 0

i>=0 and i<n 
可以优化成:
0<=i<n
```


## 05-常用容器
```python
默认字典,key可以为int,string等,value可以为list
mp = defaultdict(list) 
mp[0].append(1)
print(mp[0][0])
```



##  
```python

```



##  
```python

```


##  
```python

```


##  
```python

```

##  
```python

```



##  
```python

```
