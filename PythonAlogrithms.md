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
a = [int(i) for i in a1.split()

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
### 01-切片
```python
# 初始化
dp = [0]*N
dp = [[0]*N for _ in range(M)]  # M行N列 每行不会跟着变化
dp = [[0]*n]*m 每行都会跟着变化

# 常用切片
num2.append(num[:])	[:]复制出一个完整数组
list[-n]   		第倒n个数据
list[m:n]  		从[m,n) 左闭右开
list[m:n:k] 	按k的间隔
list[::-1]		倒序
	eg:	t = t[::-1]
# 复制数组
浅拷贝：地址相同
nums2 = nums  会同时改变
深拷贝：
nums2 = copy.deepcopy(nums)
nums2 = nums[::]

# int数组num转str的num2
nums2 = [str(i) for i in nums]
或者
strs = list(map(str,nums))

# 常用方法:
s.insert(idx,1) 在idx位置加数字1
```

## 02-02 排序
```python
strs = map(str,nums)	# 
def cmp(a,b):
    if a+b == b+a:
	return 0
    elif a+b>b+a:
	return 1
    else:
	return -1
strs = sorted(strs,key=functools.cmp_to_key(cmp),reverse=True)
```

## 03-常用函数
```python
str1.find(str2) 	返回字串str2的下标
isalnum() 			方法检测字符串是否由字母和数字组成。
str.upper() str.lower()
ord('A') 64 返回ASCLL码

# 列表相关
list.sort(cmp=None, key=None, reverse=False)
nums.sort() 		列表排序
nums.sort(reverse=True) 降序
nums.sorted()		
sorted() 和 sort()区别：
- sort() 	改变原数组，返回None
- sorted() 	不改变原数组,返回排序后的数组


map() 会根据提供的函数对指定序列做映射，返回映射值。
strs = map(str,nums)  	nums的列表，都加上str(),返回map类型
list(strs) 	

join() 字符串插入新元素组成新的字符串。
	symbol = "-";
	seq = ("a", "b", "c"); # 字符串序列
	print symbol.join( seq ); a-b-c
''.join(arr) arr列表转换成字符串

num = list.pop() 默认出最后一个,
eg:	list.pop(n)  出下标为n的   	list.pop(-1) 出最后一个
choice(nums) O(1)随机出nums中的数据

isnumeric() 函数，判断数字和字符串混合的字符串，返回False。 使用isnumeric() 函数，判断纯数字字符串，返回True。


	
```


## 04-常用运算
```python
a = 9//3  # 3 整除 向下取整  注意： -6/11 = -1
b = 9/3   # 3.0
c = 9**0.5 # 3  9的次方

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
## 类相关 
```python
class NestedIterator:

    def __init__(self, nestedList: [NestedInteger]):
        self.idx = -1   # 添加私有变量
        self.lens = 0
        self.myList = []
        list1 = nestedList[:]
        self.dfs(list1)

    def dfs(self,list): # 可以额外添加函数
            for i in list:
                if i.isInteger():
                    self.myList.append(i.getInteger())
                    self.lens += 1
                else:
                    t = i.getList()
                    self.dfs(t)

    def next(self) -> int:
        if not self.hasNext():
            return -1
        self.idx += 1
        return self.myList[self.idx] 
    
    def hasNext(self) -> bool:
        if self.idx<self.lens-1:
            return True
        return False
```



## 字符串string
### 去除空格
```python
去除左右空格：
strip()方法
lstrip()
rstrip()

正则表达式去除全部空格：
str = " Hello world "  str.replace(" ","")  输出： "Helloworld"
```
### 常用方法
```python
s.count(i)  字符i的数量
```



## 常见方法时间复杂度
```python
num in numList: in 是O(n) 推荐使用dict

```


## 常用的常量
```python
# 2^32
MASK = 0x100000000
# 整型最大值
MAX_INT = 0x7FFFFFFF
MIN_INT = MAX_INT + 1
```

##  
```python

```



##  
```python

```
