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
深拷贝：（return nums2时失效了）
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
力扣179
class Solution:
    def largestNumber(self, nums: List[int]) -> str:
        strs = map(str, nums)
        def cmp(a, b):
            if a + b == b + a:
                return 0
            if a + b < b + a: # 降序
                return 1
            return -1
        strs = sorted(strs, key = functools.cmp_to_key(cmp))
        ans = ''.join(strs)
        if strs[0]=='0': return '0'  # 开头时0的，ans就是0
        return ans 
	
strs = map(str,nums)	# 
def cmp(a,b):
    if a+b == b+a:
	return 0
    elif a+b>b+a:
	return 1
    else:
	return -1
strs = sorted(strs,key=functools.cmp_to_key(cmp),reverse=True)

反转：
nums.reverse()
切片反转：
nums[idx:] = list(reversed(nums[idx:]))

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

## 读写文件表格
```python
# openpyxl使用： 只要调用了save(filename) 就能实时保存
import openpyxl
from openpyxl import Workbook

# 添加内容

def t1():
# 创建一个文件 加入内容 保存并命名
    workbook = Workbook()
    workbook.create_sheet(index=0, title="s1")
    worksheet1 = workbook.active
    worksheet1['A1'] = 'test_id'
    worksheet1['B1'] = 'test_result'
    worksheet1['C1'] = 'chip_at_bootloader'

    row1 = [1, 'succ', 'no']
    worksheet1.append(row1)
    worksheet1.append(row1)
    worksheet1.append(row1)
    workbook.save("t1.xlsx")

def t2():
# 为文件新增内容 没有找到就新建
    file_path = "t1.xlsx"
    wb = openpyxl.load_workbook(file_path)
    worksheets = wb['s1']
    end_row = worksheets.max_row

    cell_data = worksheets.cell(row = 1, column = 1).value
    print(cell_data)
    worksheets.append(['pengpeng1', 'pengpeng2', 'pengpeng3'])
    wb.save(file_path)

if __name__ == '__main__':
    # t1()
    t2()

    # test2()
```

```python
# xlsxwriter（只能创建）
import re
import os
import xlsxwriter

# normal
dir_path = 'D:\\ws\\get_voltage\\IBC'

table_header = [
    "chip_type",
    "dieid",
    "test_time",
    "power_name",
    "vol_val"
]
chip_type_col = 0
dieid_col = 1
test_time_col = 2
power_name_col = 3
vol_val_col = 4

chip_type_end = 1
dieid_end = 1
test_time_end = 1
power_name_end = 1
vol_val_end = 1

workbook = xlsxwriter.Workbook("data.xlsx")
worksheet1 = workbook.add_worksheet("sheet1")

def init_xlsx():
    bold_format = workbook.add_format({'bold': True})
    worksheet1.write_row(0, 0, table_header, bold_format)
    worksheet1.set_column(0, 0, 50)
    worksheet1.set_column(0, 1, 100)
    worksheet1.set_column(0, 2, 100)
    worksheet1.set_column(0, 3, 50)
    worksheet1.set_column(0, 4, 50)

def find_file(rt_path):
    # cnt = 10
    for root, dirs, files in os.walk(rt_path, topdown=False): # False优先遍历子目录
        for file in files: # dirs = test_time
            if file == "internal voltage.log":
                fullname = os.path.join(root, file)
                chip_type = os.path.basename(os.path.abspath(os.path.join(fullname, "../../..")))
                dieid = os.path.basename(os.path.abspath(os.path.join(fullname, "../..")))
                test_time = os.path.basename(os.path.abspath(os.path.join(fullname, "..")))
                if dieid in ["123456", "0"*40, "f"*40]:
                    break
                rt_cnt = get_data(fullname)
                if rt_cnt == -1:
                    print("Erro file:" + fullname)
                if rt_cnt != -1:  # OK
                    global chip_type_end, dieid_end, test_time_end
                    worksheet1.write_column(chip_type_end, chip_type_col, [chip_type] * rt_cnt)
                    worksheet1.write_column(dieid_end, dieid_col, [dieid] * rt_cnt)
                    worksheet1.write_column(test_time_end, test_time_col, [test_time] * rt_cnt)
                    chip_type_end = chip_type_end + rt_cnt
                    dieid_end = dieid_end + rt_cnt
                    test_time_end = test_time_end + rt_cnt
    print("generate data.xlsx succ")

def get_data(file_path):
    '''
    :param file_path:
    :return:
        -1   ERROR 电源值数量!=分压值数量
        >=0  OK
    '''
    with open(file_path, 'r', encoding='utf-8') as file:
        text = file.read()
        power_name = re.findall(r"电源:(.*?)，", text, re.S)
        vol_val = re.findall(r"，测得分压：(.*?) V", text, re.S)
        power_name_cnt = len(power_name)
        vol_val_cnt = len(vol_val)
        if vol_val_cnt == 0:  # "万用表测得分压" 情况
            vol_val = re.findall(r"，万用表测得分压：(.*?) V", text, re.S)
            vol_val_cnt = len(vol_val)
        file.close()
        vol_val = [float(i) for i in vol_val]
        if power_name_cnt == vol_val_cnt:
            global power_name_end, vol_val_end
            worksheet1.write_column(power_name_end, power_name_col, power_name)
            worksheet1.write_column(vol_val_end, vol_val_col, vol_val)
            power_name_end = power_name_end + power_name_cnt
            vol_val_end = vol_val_end + vol_val_cnt
            return power_name_cnt
        return -1

if __name__ == '__main__':
    init_xlsx()
    find_file(dir_path)
    workbook.close()


```
