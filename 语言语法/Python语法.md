<a name="jlM9n"></a>
# 01-认识Python
<a name="xRHIP"></a>
## 01-特点

- Python 是**完全面向对象的语言**
   - **函数**、**模块**、**数字**、**字符串**都是对象，**在 Python 中一切皆对象**
   - 完全支持继承、重载、多重继承
   - 支持重载运算符，也支持泛型设计
- Python **拥有一个强大的标准库**，Python 语言的核心只包含 **数字**、**字符串**、**列表**、**字典**、**文件** 等常见类型和函数，而由 Python 标准库提供了 **系统管理**、**网络通信**、**文本处理**、**数据库接口**、**图形系统**、**XML 处理** 等额外的功能
- Python 社区提供了**大量的第三方模块**，使用方式与标准库类似。它们的功能覆盖 **科学计算**、**人工智能**、**机器学习**、**Web 开发**、**数据库接口**、**图形系统** 多个领域
<a name="Z2zZY"></a>
## 02-优缺点
<a name="FOBNU"></a>
### 优点

- 简单、易学
- 免费、开源
- **面向对象**
- 丰富的库
- 可扩展性
   - 如果需要一段关键代码运行得更快或者希望某些算法不公开，可以把这部分程序用 C 或 C++ 编写，然后在 Python 程序中使用它们
- ……
<a name="OGB6J"></a>
### 缺点

- 运行速度慢
- 国内市场较小
- 中文资料匮乏
<a name="emqkI"></a>
## 03-Python 2.x 与 3.x 版本简介
目前市场上有两个 Python 的版本并存着，分别是 Python 2.x 和 Python 3.x<br />新的 Python 程序建议使用 Python 3.0 版本的语法

- Python 2.x 是 **过去的版本**
   - 解释器名称是 **python**
- Python 3.x 是 **现在和未来 主流的版本**
   - 解释器名称是 **python3**
   - 相对于 Python 的早期版本，这是一个 **较大的升级**
   - 为了不带入过多的累赘，Python 3.0 在设计的时候 **没有考虑向下兼容**
      - 许多早期 Python 版本设计的程序都无法在 Python 3.0 上正常执行
   - Python 3.0 发布于 **2008 年**
   - 到目前为止，Python 3.0 的稳定版本已经有很多年了
      - Python 3.3 发布于 2012
      - Python 3.4 发布于 2014
      - Python 3.5 发布于 2015
      - Python 3.6 发布于 2016
- 为了照顾现有的程序，官方提供了一个过渡版本 —— **Python 2.6**
   - 基本使用了 Python 2.x 的语法和库
   - 同时考虑了向 Python 3.0 的迁移，**允许使用部分** Python 3.0 的语法与函数
   - 2010 年中推出的 Python 2.7 被确定为 **最后一个Python 2.x 版本**

提示：如果开发时，无法立即使用 Python 3.0（还有极少的第三方库不支持 3.0 的语法），建议

- 先使用 Python 3.0 版本进行开发
- 然后使用 Python 2.6、Python 2.7 来执行，并且做一些兼容性的处理
<a name="uy1Rv"></a>
## 04. 执行 Python 程序的三种方式
<a name="tkTdl"></a>
### 01-解释器 python / python3
<a name="UuevC"></a>
#### Python 的解释器
# 使用 python 2.x 解释器 $ python xxx.py <br /># 使用 python 3.x 解释器 $ python3 xxx.py 
<a name="Rh9Ic"></a>
##### 其他解释器（知道）
**Python 的解释器** 如今有多个语言的实现，包括：

- CPython —— 官方版本的 C 语言实现
- Jython —— 可以运行在 Java 平台
- IronPython —— 可以运行在 .NET 和 Mono 平台
- PyPy —— Python 实现的，支持 JIT 即时编译
<a name="qsZB2"></a>
### 02-交互式运行 Python 程序

- 直接在终端中运行解释器，而不输入要执行的文件名
- 在 Python 的 Shell 中直接输入 **Python 的代码**，会立即看到程序执行结果
<a name="gceE4"></a>
#### 1) 交互式运行 Python 的优缺点
<a name="niUvt"></a>
##### 优点

- 适合于学习/验证 Python 语法或者局部代码
<a name="dSvQE"></a>
##### 缺点

- 代码不能保存
- 不适合运行太大的程序
<a name="kpckN"></a>
#### 2) 退出 官方的解释器
<a name="myCV4"></a>
##### 1> 直接输入 exit()
>>> exit() 
<a name="aCf9E"></a>
##### 2> 使用热键退出
在 python 解释器中，按热键 ctrl + d 可以退出解释器
<a name="e3edg"></a>
#### 3) IPython

- IPython 中 的 “I” 代表 **交互 interactive**
<a name="MmONA"></a>
##### 特点

- IPython 是一个 python 的 **交互式 shell**，比默认的 python shell 好用得多
   - 支持自动补全
   - 自动缩进
   - 支持 bash shell 命令
   - 内置了许多很有用的功能和函数
- IPython 是基于 BSD 开源的
<a name="ItrSu"></a>
##### 版本

- Python 2.x 使用的解释器是 **ipython**
- Python 3.x 使用的解释器是 **ipython3**
- 要退出解释器可以有以下两种方式：
<a name="SN7sV"></a>
##### 1> 直接输入 exit
In [1]: exit 
<a name="ce1Ab"></a>
##### 2> 使用热键退出
在 IPython 解释器中，按热键 ctrl + d，IPython 会询问是否退出解释器
<a name="xzPi5"></a>
#### IPython 的安装
$ sudo apt install ipython 
<a name="V5GYd"></a>
### 03-Python 的 IDE —— PyCharm
<a name="GPucK"></a>
# 02-基本语法
<a name="keXQB"></a>
## 01-注释
单行注释(行注释)
```c
# 这是第一个单行注释 
print("hello python") 
print("hello python")  # 输出 `hello python` 

注意点：
	1.为了保证代码的可读性，# 后面建议先添加一个空格，然后再编写相应的说明文字
	2.为了保证代码的可读性，注释和代码之间 至少要有 两个空格
```
02-多行注释（块注释）
```c
"""
这是一个多行注释

在多行注释之间，可以写很多很多的内容……
""" 
print("hello python")
```
<a name="q9C0U"></a>
## 02-算数运算符
<a name="d6CbL"></a>
### 01. 算数运算符

- 算数运算符是 **运算符的一种**
- 是完成基本的算术运算使用的符号，用来处理四则运算
| **运算符** | **描述** | **实例** |
| --- | --- | --- |
| + | 加 | 10 + 20 = 30 |
| - | 减 | 10 - 20 = -10 |
| * | 乘 | 10 * 20 = 200 |
| / | 除 | 10 / 20 = 0.5 |
| // | 取整除 | 返回除法的整数部分（商） 9 // 2 输出结果 4 |
| % | 取余数 | 返回除法的余数 9 % 2 = 1 |
| ** | 幂 | 又称次方、乘方，2 ** 3 = 8 |

```c
在 Python 中 * 运算符还可以用于字符串，计算结果就是字符串重复指定次数的结果
In [1]: "-" * 50
Out[1]: '----------------------------------------' 
```
 
<a name="zw54j"></a>
### 02. 算数运算符的优先级

- 和数学中的运算符的优先级一致，在 Python 中进行数学计算时，同样也是：
   - **先乘除后加减**
   - 同级运算符是 **从左至右** 计算
   - 可以使用 () 调整计算的优先级
- 以下表格的算数优先级由高到最低顺序排列
| **运算符** | **描述** |
| --- | --- |
| ** | 幂 (最高优先级) |
| * / % // | 乘、除、取余数、取整除 |
| + - | 加法、减法 |

<a name="CExpB"></a>
## 03-变量
<a name="EQJS5"></a>
### 01. 变量定义

- 在 Python 中，每个变量 **在使用前都必须赋值**，变量 **赋值以后** 该变量 **才会被创建**
- 等号（=）用来给变量赋值
   - = 左边是一个变量名
   - = 右边是存储在变量中的值

变量名 = 值 <br />变量定义之后，后续就可以直接使用了
```python
# 1. 输入苹果单价
price_str = input("请输入苹果价格：")

# 2. 要求苹果重量
weight_str = input("请输入苹果重量：")

# 3. 计算金额
# 1> 将苹果单价转换成小数
price = float(price_str)

# 2> 将苹果重量转换成小数
weight = float(weight_str)

# 3> 计算付款金额
money = price * weight

print(money)
```
<a name="f5Q3Z"></a>
### 02. 变量的类型

- 数据类型可以分为 **数字型** 和 **非数字型**
   - 数字型
      - 整型 (int)
      - 浮点型（float）
      - 布尔型（bool）
         - 真 True 非 0 数 —— **非零即真**
         - 假 False 0
      - 复数型 (complex)
         - 主要用于科学计算，例如：平面场问题、波动问题、电感电容等问题
   - 非数字型
      - 字符串
      - 列表
      - 元组
      - 字典
- 在 Python 中定义变量是 **不需要指定类型**（在其他很多高级语言中都需要）
- 在 Python 中，所有 **非数字型变量** 都支持以下特点：
   1. 都是一个 **序列** sequence，也可以理解为 **容器**
   2. **取值** []
   3. **遍历** for in
   4. **计算长度**、**最大/最小值**、**比较**、**删除**
   5. **链接** + 和 **重复** *
   6. **切片**
<a name="FZFK2"></a>
#### 03-不同类型变量之间的计算
<a name="xHdEE"></a>
#### 1) **数字型变量** 之间可以直接计算

- 在 Python 中，两个数字型变量是可以直接进行 算数运算的
- 如果变量是 bool 型，在计算时
   - True 对应的数字是 1
   - False 对应的数字是 0
<a name="lnDda"></a>
#### 2) **字符串变量** 之间使用 + 拼接字符串

- 在 Python 中，字符串之间可以使用 + 拼接生成新的字符串
```python
In [1]: first_name = "三"

In [2]: last_name = "张"

In [3]: first_name + last_name
Out[3]: '三张'
```
<a name="hMli1"></a>
#### 3) **字符串变量** 可以和 **整数** 使用 * 重复拼接相同的字符串
```python
In [1]: "-" * 50
Out[1]: '--------------------------------------------------'
```
<a name="EsqyQ"></a>
#### 4) **数字型变量** 和 **字符串** 之间 **不能进行其他计算**
<a name="UNUfv"></a>
### 04-变量的输入
<a name="fRO0j"></a>
#### 1) input 函数实现键盘输入

- 在 Python 中可以使用 input 函数从键盘等待用户的输入
- 用户输入的 **任何内容** Python 都认为是一个 **字符串**
- 语法如下：

字符串变量 = input("提示信息：") 
<a name="S8zET"></a>
#### 2) 类型转换函数
| **函数** | **说明** |
| --- | --- |
| int(x) | 将 x 转换为一个整数 |
| float(x) | 将 x 转换到一个浮点数 |

```python
# 1. 输入苹果单价
price_str = input("请输入苹果价格：")

# 2. 要求苹果重量
weight_str = input("请输入苹果重量：")

# 3. 计算金额
# 1> 将苹果单价转换成小数
price = float(price_str)

# 2> 将苹果重量转换成小数
weight = float(weight_str)

# 3> 计算付款金额
money = price * weight

price = float(input("请输入价格:"))

print(money)
```
<a name="NRVA1"></a>
### 05-变量的格式化输出
| **格式化字符** | **含义** |
| --- | --- |
| %s | 字符串 |
| %d | 有符号十进制整数，%06d 表示输出的整数显示位数，不足的地方使用 0 补全 |
| %f | 浮点数，%.2f 表示小数点后只显示两位 |
| %% | 输出 % |

- 语法格式如下：
```python
print("格式化字符串" % 变量1)
print("格式化字符串" % (变量1, 变量2...))

# 例子
"""
在控制台依次提示用户输入：姓名、公司、职位、电话、电子邮箱
"""
name = input("请输入姓名：")
company = input("请输入公司：")
title = input("请输入职位：")
phone = input("请输入电话：")
email = input("请输入邮箱：")

print("*" * 50)
print(company)
print()
print("%s (%s) " % (name, title))
print()
print("电话：%s" % phone)
print("邮箱：%s" % email)
print("*" * 50)
```
<a name="PfYpO"></a>
### 06-标识符

- 标示符可以由 **字母**、**下划线** 和 **数字** 组成
- **不能以数字开头**
- **不能与关键字重名**
<a name="nSm0l"></a>
# 03-逻辑语句
<a name="dGLWH"></a>
## 01-判断
<a name="G1JHp"></a>
### 01-逻辑写法
if:
```python
if age >= 18:
    print("可以进网吧嗨皮……")

```
if : else :
```python
if age >= 18:
    print("可以进网吧嗨皮……")
else:
    print("你还没长大，应该回家写作业！")

```
if: elif: elif: else:
```python
holiday_name = "平安夜"

if holiday_name == "情人节":
    print("买玫瑰")
    print("看电影")
elif holiday_name == "平安夜":
    print("买苹果")
    print("吃大餐")
elif holiday_name == "生日":
    print("买蛋糕")
else:
    print("每天都是节日啊……")
```
<a name="KIRzV"></a>
### 02-逻辑运算

- Python 中的 **逻辑运算符** 包括：**与 and**        **或 or**        **非 not** 三种
```python

if age >= 0 and age <= 120:

if python_score > 60 or c_score > 60:

is_employee = True
if not is_employee:
```
<a name="lRNt5"></a>
# 04-运算符
<a name="h0MX8"></a>
## 01. 算数运算符

- 是完成基本的算术运算使用的符号，用来处理四则运算
| **运算符** | **描述** | **实例** |
| --- | --- | --- |
| + | 加 | 10 + 20 = 30 |
| - | 减 | 10 - 20 = -10 |
| * | 乘 | 10 * 20 = 200 |
| / | 除 | 10 / 20 = 0.5 |
| // | 取整除 | 返回除法的整数部分（商） 9 // 2 输出结果 4 |
| % | 取余数 | 返回除法的余数 9 % 2 = 1 |
| ** | 幂 | 又称次方、乘方，2 ** 3 = 8 |

 
<a name="IwQS5"></a>
## 02. 比较（关系）运算符
| **运算符** | **描述** |
| --- | --- |
| == | 检查两个操作数的值是否 **相等**，如果是，则条件成立，返回 True |
| != | 检查两个操作数的值是否 **不相等**，如果是，则条件成立，返回 True |
| > | 检查左操作数的值是否 **大于** 右操作数的值，如果是，则条件成立，返回 True |
| < | 检查左操作数的值是否 **小于** 右操作数的值，如果是，则条件成立，返回 True |
| >= | 检查左操作数的值是否 **大于或等于** 右操作数的值，如果是，则条件成立，返回 True |
| <= | 检查左操作数的值是否 **小于或等于** 右操作数的值，如果是，则条件成立，返回 True |

Python 2.x 中判断 **不等于** 还可以使用 <> 运算符
<a name="WOunh"></a>
## 03. 逻辑运算符
| **运算符** | **逻辑表达式** | **描述** |
| --- | --- | --- |
| and | x and y | 只有 x 和 y 的值都为 True，才会返回 True<br />否则只要 x 或者 y 有一个值为 False，就返回 False |
| or | x or y | 只要 x 或者 y 有一个值为 True，就返回 True<br />只有 x 和 y 的值都为 False，才会返回 False |
| not | not x | 如果 x 为 True，返回 False<br />如果 x 为 False，返回 True |

<a name="AtcbS"></a>
## 04. 赋值运算符

- 在 Python 中，使用 = 可以给变量赋值
- 在算术运算时，为了简化代码的编写，Python 还提供了一系列的 与 **算术运算符** 对应的 **赋值运算符**
- 注意：**赋值运算符中间不能使用空格**
| **运算符** | **描述** | **实例** |
| --- | --- | --- |
| = | 简单的赋值运算符 | c = a + b 将 a + b 的运算结果赋值为 c |
| += | 加法赋值运算符 | c += a 等效于 c = c + a |
| -= | 减法赋值运算符 | c -= a 等效于 c = c - a |
| *= | 乘法赋值运算符 | c *= a 等效于 c = c * a |
| /= | 除法赋值运算符 | c /= a 等效于 c = c / a |
| //= | 取整除赋值运算符 | c //= a 等效于 c = c // a |
| %= | 取 **模** (余数)赋值运算符 | c %= a 等效于 c = c % a |
| **= | 幂赋值运算符 | c **= a 等效于 c = c ** a |

<a name="b2aYs"></a>
## 05. 运算符的优先级

- 以下表格的算数优先级由高到最低顺序排列
| **运算符** | **描述** |
| --- | --- |
| ** | 幂 (最高优先级) |
| * / % // | 乘、除、取余数、取整除 |
| + - | 加法、减法 |
| <= < > >= | 比较运算符 |
| == != | 等于运算符 |
| = %= /= //= -= += *= **= | 赋值运算符 |
| not or and | 逻辑运算符 |

<a name="tVTVF"></a>
# 05-循环
<a name="beLzV"></a>
## 01-while使用
```python
初始条件设置 —— 通常是重复执行的 计数器

while 条件(判断 计数器 是否达到 目标次数):
    条件满足时，做的事情1
    条件满足时，做的事情2
    条件满足时，做的事情3
    ...(省略)...
    
    处理条件(计数器 + 1)

# 例子
# 1. 定义重复次数计数器
i = 1

# 2. 使用 while 判断条件
while i <= 5:
    # 要重复执行的代码
    print("Hello Python")

    # 处理计数器 i
    i = i + 1

print("循环结束后的 i = %d" % i)
```
<a name="XI0hu"></a>
## 02-break
```python
在循环过程中，如果 某一个条件满足后，不 再希望 循环继续执行，可以使用 break 退出循环
i = 0

while i < 10:

    # break 某一条件满足时，退出循环，不再执行后续重复的代码
    # i == 3
    if i == 3:
        break

    print(i)

    i += 1

print("over")
```
<a name="Pru8o"></a>
## 03-continue
```python
在循环过程中，如果 某一个条件满足后，不 希望 执行循环代码，但是又不希望退出循环，可以使用 continue
也就是：在整个循环中，只有某些条件，不需要执行循环代码，而其他条件都需要执行
i = 0

while i < 10:

    # 当 i == 7 时，不希望执行需要重复执行的代码
    if i == 7:
        # 在使用 continue 之前，同样应该修改计数器
        # 否则会出现死循环
        i += 1

        continue

    # 重复执行的代码
    print(i)

    i += 1
```
<a name="emJ9D"></a>
# 06-01-函数
<a name="JXzn6"></a>
## 01-定义
```python
def 函数名():

    函数封装的代码
    ……
def 是英文 define 的缩写
函数名称 应该能够表达 函数封装代码 的功能，方便后续的调用
函数名称 的命名应该 符合 标识符的命名规则
可以由 字母、下划线 和 数字 组成
不能以数字开头
不能与关键字重名

#例子
# 解释器知道这里定义了一个函数

def say_hello():
    print("hello 1")
    print("hello 2")
    print("hello 3")
say_hello()

def sum_2_num(num1, num2):

def sum_2_num(num1, num2):
    """对两个数字的求和"""
    return num1 + num2
```
<a name="oerdz"></a>
# <br />06-02-函数进阶
<a name="w9o6w"></a>
## 01. 函数参数和返回值的作用
函数根据 **有没有参数** 以及 **有没有返回值**，可以 **相互组合**，一共有 **4 种** 组合形式

1. 无参数，无返回值
2. 无参数，有返回值
3. 有参数，无返回值
4. 有参数，有返回值

定义函数时，**是否接收参数，或者是否返回结果**，是根据 **实际的功能需求** 来决定的！

1. 如果函数 **内部处理的数据不确定**，就可以将外界的数据以参数传递到函数内部
2. 如果希望一个函数 **执行完成后，向外界汇报执行结果**，就可以增加函数的返回值
<a name="iVctI"></a>
### 1.1 无参数，无返回值
此类函数，不接收参数，也没有返回值，应用场景如下：

1. **只是单纯地做一件事情**，例如 **显示菜单**
2. 在函数内部 **针对全局变量进行操作**，例如：**新建名片**，最终结果 **记录在全局变量** 中

注意：

- 如果全局变量的数据类型是一个 **可变类型**，在函数内部可以使用 **方法** 修改全局变量的内容 —— **变量的引用不会改变**
- 在函数内部，**使用赋值语句** 才会 **修改变量的引用**
<a name="fPP6j"></a>
### 1.2 无参数，有返回值
此类函数，不接收参数，但是有返回值，应用场景如下：

- 采集数据，例如 **温度计**，返回结果就是当前的温度，而不需要传递任何的参数
<a name="bC4js"></a>
### 1.3 有参数，无返回值
此类函数，接收参数，没有返回值，应用场景如下：

- 函数内部的代码保持不变，针对 **不同的参数 处理 不同的数据**
- 例如 **名片管理系统** 针对 **找到的名片** 做 **修改**、**删除** 操作
<a name="WRRgK"></a>
### 1.4 有参数，有返回值
此类函数，接收参数，同时有返回值，应用场景如下：

- 函数内部的代码保持不变，针对 **不同的参数 处理 不同的数据**，并且 **返回期望的处理结果**
- 例如 **名片管理系统** 使用 **字典默认值** 和 **提示信息** 提示用户输入内容
   - 如果输入，返回输入内容
   - 如果没有输入，返回字典默认值
<a name="vybap"></a>
## 02. 函数的返回值 进阶

- 在程序开发中，有时候，会希望 **一个函数执行结束后，告诉调用者一个结果**，以便调用者针对具体的结果做后续的处理
- **返回值** 是函数 **完成工作**后，**最后** 给调用者的 **一个结果**
- 在函数中使用 return 关键字可以返回结果
- 调用函数一方，可以 **使用变量** 来 **接收** 函数的返回结果

问题：一个函数执行后能否返回多个结果？
<a name="aEzgO"></a>
### 示例 —— 温度和湿度测量

- 假设要开发一个函数能够同时返回当前的温度和湿度
- **先完成返回温度**的功能如下：

def measure():     """返回当前的温度"""          print("开始测量...")     temp = 39     print("测量结束...")          return temp result = measure() print(result) 

- 在利用 **元组** 在返回温度的同时，也能够返回 **湿度**
- 改造如下：

def measure():     """返回当前的温度"""     print("开始测量...")     temp = 39     wetness = 10     print("测量结束...")     return (temp, wetness) <br />提示：如果一个函数返回的是元组，括号可以省略<br />**技巧**

- 在 Python 中，可以 **将一个元组** 使用 **赋值语句** 同时赋值给 **多个变量**
- 注意：变量的数量需要和元组中的元素数量保持一致

result = temp, wetness = measure() 
<a name="E6SiX"></a>
### 面试题 —— 交换两个数字
**题目要求**

1. 有两个整数变量 a = 6, b = 100
2. 不使用其他变量，**交换两个变量的值**
<a name="AePQk"></a>
#### 解法 1 —— 使用其他变量
# 解法 1 - 使用临时变量 c = b b = a a = c 
<a name="WnOiR"></a>
#### 解法 2 —— 不使用临时变量
# 解法 2 - 不使用临时变量 a = a + b b = a - b a = a - b 
<a name="KCuNL"></a>
#### 解法 3 —— Python 专有，利用元组
a, b = b, a 
<a name="HESRA"></a>
## 03. 函数的参数 进阶
<a name="qVzXU"></a>
### 3.1. 不可变和可变的参数
问题 1：在函数内部，针对参数使用 **赋值语句**，会不会影响调用函数时传递的 **实参变量**？ —— 不会！

- 无论传递的参数是 **可变** 还是 **不可变**
   - 只要 **针对参数** 使用 **赋值语句**，会在 **函数内部** 修改 **局部变量的引用**，**不会影响到 外部变量的引用**

问题 2：如果传递的参数是 **可变类型**，在函数内部，使用 **方法** 修改了数据的内容，**同样会影响到外部的数据**
```python
def mutable(num_list):

    # num_list = [1, 2, 3]
    num_list.extend([1, 2, 3])

    print(num_list)

gl_list = [6, 7, 8]
mutable(gl_list)
print(gl_list)
```
<a name="lPTI2"></a>
#### 面试题 —— +=

- 在 python 中，列表变量调用 += 本质上是在执行列表变量的 extend 方法，不会修改变量的引用
<a name="oIQWQ"></a>
### 3.2 缺省参数

- 定义函数时，可以给 **某个参数** 指定一个**默认值**，具有默认值的参数就叫做 **缺省参数**
- 调用函数时，如果没有传入 **缺省参数** 的值，则在函数内部使用定义函数时指定的 **参数默认值**
- 函数的缺省参数，**将常见的值设置为参数的缺省值**，从而 **简化函数的调用**
- 例如：对列表排序的方法
```python
gl_num_list = [6, 3, 9]

# 默认就是升序排序，因为这种应用需求更多
gl_num_list.sort()
print(gl_num_list)

# 只有当需要降序排序时，才需要传递 `reverse` 参数
gl_num_list.sort(reverse=True)
print(gl_num_list)

```
<a name="YG0Gt"></a>
#### 指定函数的缺省参数

- 在参数后使用赋值语句，可以指定参数的缺省值

def print_info(name, gender=True):<br />**提示**

1. 缺省参数，需要使用 **最常见的值** 作为默认值！
2. 如果一个参数的值 **不能确定**，则不应该设置默认值，具体的数值在调用函数时，由外界传递！
<a name="qfLXf"></a>
#### 缺省参数的注意事项
<a name="xBNVU"></a>
##### 1) 缺省参数的定义位置

- **必须保证** **带有默认值的缺省参数** **在参数列表末尾**
- 所以，以下定义是错误的！

def print_info(name, gender=True, title): 
<a name="sA4sv"></a>
##### 2) 调用带有多个缺省参数的函数

- 在 **调用函数时**，如果有 **多个缺省参数**，**需要指定参数名**，这样解释器才能够知道参数的对应关系！
```python
def print_info(name, title="", gender=True):
    """

    :param title: 职位
    :param name: 班上同学的姓名
    :param gender: True 男生 False 女生
    """

    gender_text = "男生"

    if not gender:
        gender_text = "女生"

    print("%s%s 是 %s" % (title, name, gender_text))


# 提示：在指定缺省参数的默认值时，应该使用最常见的值作为默认值！
print_info("小明")
print_info("老王", title="班长")
print_info("小美", gender=False)
```

-  
<a name="LZhMo"></a>
### 3.3 多值参数（知道）
<a name="EO2Lo"></a>
#### 定义支持多值参数的函数

- 有时可能需要 **一个函数** 能够处理的参数 **个数** 是不确定的，这个时候，就可以使用 **多值参数**
- python 中有 **两种** 多值参数：
   - 参数名前增加 **一个** * 可以接收 **元组**
   - 参数名前增加 **两个** * 可以接收 **字典**
- 一般在给多值参数命名时，**习惯**使用以下两个名字
   - *args —— 存放 **元组** 参数，前面有一个 *
   - **kwargs —— 存放 **字典** 参数，前面有两个 *
- args 是 arguments 的缩写，有变量的含义
- kw 是 keyword 的缩写，kwargs 可以记忆 **键值对参数**
```python
    def demo(num, *args, **kwargs):  # 一个数据 *一个元组 **一个字典
        print(num)      # 1
        print(args)     # (2, 3, 4, 5)
        print(kwargs)   # {'name': '小明', 'age': 18, 'gender': True}


    demo(1, 2, 3, 4, 5, name="小明", age=18, gender=True)
```
提示：**多值参数** 的应用会经常出现在网络上一些大牛开发的框架中，知道多值参数，**有利于我们能够读懂大牛的代码**
<a name="EOyLc"></a>
#### 元组和字典的拆包（知道）

- 在调用带有多值参数的函数时，如果希望：
   - 将一个 **元组变量**，直接传递给 args
   - 将一个 **字典变量**，直接传递给 kwargs
- 就可以使用 **拆包**，简化参数的传递，**拆包** 的方式是：
   - 在 **元组变量前**，增加*
   - 在 **字典变量前**，增加**
```python
def demo(*args, **kwargs):

    print(args)
    print(kwargs)


# 需要将一个元组变量/字典变量传递给函数对应的参数
gl_nums = (1, 2, 3)
gl_xiaoming = {"name": "小明", "age": 18}

# 会把 num_tuple 和 xiaoming 作为元组传递个 args
# demo(gl_nums, gl_xiaoming)
demo(*gl_nums, **gl_xiaoming)
```
<a name="YFzFt"></a>
# 07-高级变量类型
<a name="QxfIV"></a>
## 01-列表
<a name="iCd8O"></a>
### 1.1 列表的定义

- List（列表） 是 Python 中使用 **最频繁** 的数据类型，在其他语言中通常叫做 **数组**
- 专门用于存储 **一串 信息**
- 列表用 [] 定义，**数据** 之间使用 , 分隔
- 列表的 **索引** 从 0 开始
   - **索引** 就是数据在 **列表** 中的位置编号，**索引** 又可以被称为 **下标**
   - name_list = ["zhangsan", "lisi", "wangwu"]
<a name="pZpgh"></a>
### 1.2 列表常用操作

- 在 ipython3 中定义一个 **列表**，例如：name_list = []
- 输入 name_list. 按下 TAB 键，ipython 会提示 **列表** 能够使用的 **方法** 如下：

In [1]: name_list. name_list.append   name_list.count    name_list.insert   name_list.reverse name_list.clear    name_list.extend   name_list.pop      name_list.sort name_list.copy     name_list.index    name_list.remove  

| **序号** | **分类** | **关键字 / 函数 / 方法** | **说明** |
| --- | --- | --- | --- |
| 1 | 增加 | 列表.insert(索引, 数据) | 在指定位置插入数据 |
|  |  | 列表.append(数据) | 在末尾追加数据 |
|  |  | 列表.extend(列表2) | 将列表2 的数据追加到列表 |
| 2 | 修改 | 列表[索引] = 数据 | 修改指定索引的数据 |
| 3 | 删除 | del 列表[索引] | 删除指定索引的数据 |
|  |  | 列表.remove[数据] | 删除第一个出现的指定数据 |
|  |  | 列表.pop | 删除末尾数据 |
|  |  | 列表.pop(索引) | 删除指定索引数据 |
|  |  | 列表.clear | 清空列表 |
| 4 | 统计 | len(列表) | 列表长度 |
|  |  | 列表.count(数据) | 数据在列表中出现的次数 |
| 5 | 排序 | 列表.sort() | 升序排序 |
|  |  | 列表.sort(reverse=True) | 降序排序 |
|  |  | 列表.reverse() | 逆序、反转 |

![image.png](https://cdn.nlark.com/yuque/0/2023/png/22347830/1674619067323-fab90f82-4ae0-420a-837a-d5251135a326.png#averageHue=%23fbfbfb&clientId=uce65f72d-06b6-4&from=paste&height=448&id=u8dd84a8f&name=image.png&originHeight=493&originWidth=821&originalType=binary&ratio=1&rotation=0&showTitle=false&size=110863&status=done&style=none&taskId=ud4c0319e-417e-43ab-97ac-80c37fc7d42&title=&width=746.3636201866406)
<a name="oq5Vx"></a>
### 1.3循环遍历

- **遍历** 就是 **从头到尾** **依次** 从 **列表** 中获取数据
   - 在 **循环体内部** 针对 **每一个元素**，执行相同的操作
- 在 Python 中为了提高列表的遍历效率，专门提供的 **迭代 iteration 遍历**
- 使用 for 就能够实现迭代遍历
```python
name_list = ["zhangsan", "lisi", "wangwu"]

# for 循环内部使用的变量 in 列表
for name in name_list:

    循环内部针对列表元素进行操作
    print(name)
```
<a name="BijYV"></a>
## 02-元组
<a name="PVBix"></a>
### 2.1 元组的定义

- Tuple（元组）与列表类似，不同之处在于元组的 **元素不能修改**
   - **元组** 表示多个元素组成的序列
   - **元组** 在 Python 开发中，有特定的应用场景
- 用于存储 **一串 信息**，**数据** 之间使用 , 分隔
- 元组用 ( ) 定义
- 元组的 **索引** 从 0 开始
   - **索引** 就是数据在 **元组** 中的位置编号

info_tuple = ("zhangsan", 18, 1.75) 
<a name="SvTl1"></a>
#### 创建空元组
info_tuple = () 
<a name="Vu4ha"></a>
#### 元组中 **只包含一个元素** 时，需要 **在元素后面添加逗号**
info_tuple = (50, ) 
<a name="pCnvD"></a>
### 2.2 元组常用操作

- 在 ipython3 中定义一个 **元组**，例如：info = ()
- 输入 info. 按下 TAB 键，ipython 会提示 **元组** 能够使用的函数如下：

info.count  info.index <br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/22347830/1673858487009-1d3d8aae-c800-407e-9519-855fe01a76d4.png#averageHue=%23fafafa&clientId=u97285461-26c6-4&from=paste&height=373&id=ub4173067&name=image.png&originHeight=410&originWidth=627&originalType=binary&ratio=1&rotation=0&showTitle=false&size=39126&status=done&style=none&taskId=ucda6ff8d-f67a-4d1f-844f-4cb1a0fd39c&title=&width=569.999987645583)
<a name="MwuPf"></a>
### 2.3 循环遍历

- **取值** 就是从 **元组** 中获取存储在指定位置的数据
- **遍历** 就是 **从头到尾** **依次** 从 **元组** 中获取数据

# for 循环内部使用的变量 in 元组 for item in info:     循环内部针对元组元素进行操作     print(item) 

- 在 Python 中，可以使用 for 循环遍历所有非数字型类型的变量：**列表**、**元组**、**字典** 以及 **字符串**
- 提示：在实际开发中，除非 **能够确认元组中的数据类型**，否则针对元组的循环遍历需求并不是很多
```python
info_tuple = ("zhangsan", 18, 1.75)
info_tuple = ()
info_tuple = (50, )

# for 循环内部使用的变量 in 元组
for item in info:

    循环内部针对元组元素进行操作
    print(item)

info = ("zhangsan", 18)
print("%s 的年龄是 %d" % info)


```
<a name="ilBDP"></a>
### 2.4 应用场景

- 尽管可以使用 for in 遍历 **元组**
- 但是在开发中，更多的应用场景是：
   - **函数的 参数 和 返回值**，一个函数可以接收 **任意多个参数**，或者 **一次返回多个数据**
      - 有关 **函数的参数 和 返回值**，在后续 **函数高级** 给大家介绍
   - **格式字符串**，格式化字符串后面的 () 本质上就是一个元组
   - **让列表不可以被修改**，以保护数据安全
```python
info = ("zhangsan", 18)
print("%s 的年龄是 %d" % info)
```
<a name="BHlSJ"></a>
#### 元组和列表之间的转换

- 使用 list 函数可以把元组转换成列表

list(元组)  

- 使用 tuple 函数可以把列表转换成元组

tuple(列表)
<a name="Jy6qH"></a>
## 03. 字典
<a name="uIFKI"></a>
### 3.1 字典的定义

- dictionary（字典） 是 **除列表以外** Python 之中 **最灵活** 的数据类型
- 字典同样可以用来 **存储多个数据**
   - 通常用于存储 **描述一个 物体 的相关信息**
- 和列表的区别
   - **列表** 是 **有序** 的对象集合
   - **字典** 是 **无序** 的对象集合
- 字典用 {} 定义
- 字典使用 **键值对** 存储数据，键值对之间使用 , 分隔
   - **键** key 是索引
   - **值** value 是数据
   - **键** 和 **值** 之间使用 : 分隔
   - **键必须是唯一的**
   - **值** 可以取任何数据类型，但 **键** 只能使用 **字符串**、**数字**或 **元组**

xiaoming = {"name": "小明",             "age": 18,             "gender": True,             "height": 1.75} 
<a name="XNRLp"></a>
### 3.2 字典常用操作

- 在 ipython3 中定义一个 **字典**，例如：xiaoming = {}
- 输入 xiaoming. 按下 TAB 键，ipython 会提示 **字典** 能够使用的函数如下：

In [1]: xiaoming. xiaoming.clear       xiaoming.items       xiaoming.setdefault xiaoming.copy        xiaoming.keys        xiaoming.update xiaoming.fromkeys    xiaoming.pop         xiaoming.values xiaoming.get         xiaoming.popitem     <br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/22347830/1673858605477-8c2b1bbd-81d1-487b-a8da-7395544d36bf.png#averageHue=%23fafafa&clientId=u97285461-26c6-4&from=paste&height=595&id=u985b1216&name=image.png&originHeight=654&originWidth=827&originalType=binary&ratio=1&rotation=0&showTitle=false&size=135564&status=done&style=none&taskId=u9acc04e1-92f6-4e7b-8ca5-458fc351e00&title=&width=751.818165522962)
<a name="bxJww"></a>
### 3.3 循环遍历

- **遍历** 就是 **依次** 从 **字典** 中获取所有键值对
```python
xiaoming = {"name": "小明",
            "age": 18,
            "gender": True,
            "height": 1.75}

# for 循环内部使用的 `key 的变量` in 字典
for k in xiaoming:
    print("%s: %s" % (k, xiaoming[k]))
```
提示：在实际开发中，由于字典中每一个键值对保存数据的类型是不同的，所以针对字典的循环遍历需求并不是很多
<a name="a613T"></a>
### 3.4 **应用场景**

- 尽管可以使用 for in 遍历 **字典**
- 但是在开发中，更多的应用场景是：
   - **使用 多个键值对，存储 描述一个 物体 的相关信息 —— 描述更复杂的数据信息**
   - **将 多个字典 放在 一个列表 中，再进行遍历，在循环体内部针对每一个字典进行 相同的处理**
```python
card_list = [{"name": "张三",
              "qq": "12345",
              "phone": "110"},
             {"name": "李四",
              "qq": "54321",
              "phone": "10086"}
             ]
```
<a name="HnJfA"></a>
## 04. 字符串
<a name="C40Dd"></a>
### 4.1 字符串的定义

- **字符串** 就是 **一串字符**，是编程语言中表示文本的数据类型
- 在 Python 中可以使用 **一对双引号** " 或者 **一对单引号** ' 定义一个字符串
   - 虽然可以使用 \" 或者 \' 做字符串的转义，但是在实际开发中：
      - 如果字符串内部需要使用 "，可以使用 ' 定义字符串
      - 如果字符串内部需要使用 '，可以使用 " 定义字符串
- 可以使用 **索引** 获取一个字符串中 **指定位置的字符**，索引计数从 **0** 开始
- 也可以使用 for **循环遍历** 字符串中每一个字符

大多数编程语言都是用 " 来定义字符串<br />string = "Hello Python" 
<a name="ZRRqf"></a>
### 4.2 字符串的常用操作
```python
在 ipython3 中定义一个 字符串，例如：hello_str = ""
输入 hello_str. 按下 TAB 键，ipython 会提示 字符串 能够使用的 方法 如下：
In [1]: hello_str.
hello_str.capitalize    hello_str.isidentifier  hello_str.rindex
hello_str.casefold      hello_str.islower       hello_str.rjust
hello_str.center        hello_str.isnumeric     hello_str.rpartition
hello_str.count         hello_str.isprintable   hello_str.rsplit
hello_str.encode        hello_str.isspace       hello_str.rstrip
hello_str.endswith      hello_str.istitle       hello_str.split
hello_str.expandtabs    hello_str.isupper       hello_str.splitlines
hello_str.find          hello_str.join          hello_str.startswith
hello_str.format        hello_str.ljust         hello_str.strip
hello_str.format_map    hello_str.lower         hello_str.swapcase
hello_str.index         hello_str.lstrip        hello_str.title
hello_str.isalnum       hello_str.maketrans     hello_str.translate
hello_str.isalpha       hello_str.partition     hello_str.upper
hello_str.isdecimal     hello_str.replace       hello_str.zfill
hello_str.isdigit       hello_str.rfind
```
<a name="dLOpE"></a>
#### 1) 判断类型 - 9
| **方法** | **说明** |
| --- | --- |
| string.isspace() | 如果 string 中只包含空格，则返回 True |
| string.isalnum() | 如果 string 至少有一个字符并且所有字符都是字母或数字则返回 True |
| string.isalpha() | 如果 string 至少有一个字符并且所有字符都是字母则返回 True |
| string.isdecimal() | 如果 string 只包含数字则返回 True，全角数字 |
| string.isdigit() | 如果 string 只包含数字则返回 True，全角数字、⑴、\\u00b2 |
| string.isnumeric() | 如果 string 只包含数字则返回 True，全角数字，汉字数字 |
| string.istitle() | 如果 string 是标题化的(每个单词的首字母大写)则返回 True |
| string.islower() | 如果 string 中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是小写，则返回 True |
| string.isupper() | 如果 string 中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是大写，则返回 True |

<a name="U2CkN"></a>
#### 2) 查找和替换 - 7
| **方法** | **说明** |
| --- | --- |
| string.startswith(str) | 检查字符串是否是以 str 开头，是则返回 True |
| string.endswith(str) | 检查字符串是否是以 str 结束，是则返回 True |
| string.find(str, start=0, end=len(string)) | 检测 str 是否包含在 string 中，如果 start 和 end 指定范围，则检查是否包含在指定范围内，如果是返回开始的索引值，否则返回 -1 |
| string.rfind(str, start=0, end=len(string)) | 类似于 find()，不过是从右边开始查找 |
| string.index(str, start=0, end=len(string)) | 跟 find() 方法类似，不过如果 str 不在 string 会报错 |
| string.rindex(str, start=0, end=len(string)) | 类似于 index()，不过是从右边开始 |
| string.replace(old_str, new_str, num=string.count(old)) | 把 string 中的 old_str 替换成 new_str，如果 num 指定，则替换不超过 num 次 |

<a name="yz2ke"></a>
#### 3) 大小写转换 - 5
| **方法** | **说明** |
| --- | --- |
| string.capitalize() | 把字符串的第一个字符大写 |
| string.title() | 把字符串的每个单词首字母大写 |
| string.lower() | 转换 string 中所有大写字符为小写 |
| string.upper() | 转换 string 中的小写字母为大写 |
| string.swapcase() | 翻转 string 中的大小写 |

<a name="SuS6c"></a>
#### 4) 文本对齐 - 3
| **方法** | **说明** |
| --- | --- |
| string.ljust(width) | 返回一个原字符串左对齐，并使用空格填充至长度 width 的新字符串 |
| string.rjust(width) | 返回一个原字符串右对齐，并使用空格填充至长度 width 的新字符串 |
| string.center(width) | 返回一个原字符串居中，并使用空格填充至长度 width 的新字符串 |

<a name="Fr0Cz"></a>
#### 5) 去除空白字符 - 3
| **方法** | **说明** |
| --- | --- |
| string.lstrip() | 截掉 string 左边（开始）的空白字符 |
| string.rstrip() | 截掉 string 右边（末尾）的空白字符 |
| string.strip() | 截掉 string 左右两边的空白字符 |

<a name="alg1f"></a>
#### 6) 拆分和连接 - 5
| **方法** | **说明** |
| --- | --- |
| string.partition(str) | 把字符串 string 分成一个 3 元素的元组 (str前面, str, str后面) |
| string.rpartition(str) | 类似于 partition() 方法，不过是从右边开始查找 |
| string.split(str="", num) | 以 str 为分隔符拆分 string，如果 num 有指定值，则仅分隔 num + 1 个子字符串，str 默认包含 '\\r', '\\t', '\\n' 和空格 |
| string.splitlines() | 按照行('\\r', '\\n', '\\r\\n')分隔，返回一个包含各行作为元素的列表 |
| string.join(seq) | 以 string 作为分隔符，将 seq 中所有的元素（的字符串表示）合并为一个新的字符串 |

<a name="DDIJk"></a>
### 4.3 字符串的切片

- **切片** 方法适用于 **字符串**、**列表**、**元组**
   - **切片** 使用 **索引值** 来限定范围，从一个大的 **字符串** 中 **切出** 小的 **字符串**
   - **列表** 和 **元组** 都是 **有序** 的集合，都能够 **通过索引值** 获取到对应的数据
   - **字典** 是一个 **无序** 的集合，是使用 **键值对** 保存数据

字符串[开始索引:结束索引:步长] <br />**注意**：

1. 指定的区间属于 **左闭右开** 型 [开始索引, 结束索引) => 开始索引 >= 范围 < 结束索引
   - 从 起始 位开始，到 **结束位的前一位** 结束（**不包含结束位本身**)
2. 从头开始，**开始索引** **数字可以省略，冒号不能省略**
3. 到末尾结束，**结束索引** **数字可以省略，冒号不能省略**
4. 步长默认为 1，如果连续切片，**数字和冒号都可以省略**
<a name="H3fdN"></a>
#### 索引的顺序和倒序

- 在 Python 中不仅支持 **顺序索引**，同时还支持 **倒序索引**
- 所谓倒序索引就是 **从右向左** 计算索引
   - 最右边的索引值是 **-1**，依次递减
```python
num_str = "abcdefg"  # 索引：0123456 

# 1. 截取从 2 ~ 5 位置 的字符串
print(num_str[2:6])     # cdef
# 2. 截取从 2 ~ `末尾` 的字符串
print(num_str[2:])      # cdefg
# 3. 截取从 `开始` ~ 5 位置 的字符串
print(num_str[:6])      # abcdef
# 4. 截取完整的字符串
print(num_str[:])       # abcdefg
# 5. 从开始位置，每隔一个字符截取字符串
print(num_str[::2])     # aceg
# 6. 从索引 1 开始，每隔一个取一个
print(num_str[1::2])    # bdf
# 倒序切片
# -1 表示倒数第一个字符
print(num_str[-1])      # g
# 7. 截取从 2 ~ `末尾 - 1` 的字符串
print(num_str[2:-1])    # cdef
# 8. 截取字符串末尾两个字符
print(num_str[-2:])     # fg
# 9. 字符串的逆序（面试题）
print(num_str[::-1])    # gfedcba
```
<a name="hMAsg"></a>
## 05. 公共方法
<a name="SNQMq"></a>
### 5.1 Python 内置函数
Python 包含了以下内置函数：

| **函数** | **描述** | **备注** |
| --- | --- | --- |
| len(item) | 计算容器中元素个数 |  |
| del(item) | 删除变量 | del 有两种方式 |
| max(item) | 返回容器中元素最大值 | 如果是字典，只针对 key 比较 |
| min(item) | 返回容器中元素最小值 | 如果是字典，只针对 key 比较 |
| cmp(item1, item2) | 比较两个值，-1 小于/0 相等/1 大于 | Python 3.x 取消了 cmp 函数 |

**注意**

- **字符串** 比较符合以下规则： "0" < "A" < "a"
<a name="mZrQ3"></a>
### 5.2 切片
| 描述 | Python 表达式 | 结果 | 支持的数据类型 | | :---: | --- | --- | --- | --- | | 切片 | "0123456789"[::-2] | "97531" | 字符串、列表、元组 |

- **切片** 使用 **索引值** 来限定范围，从一个大的 **字符串** 中 **切出** 小的 **字符串**
- **列表** 和 **元组** 都是 **有序** 的集合，都能够 **通过索引值** 获取到对应的数据
- **字典** 是一个 **无序** 的集合，是使用 **键值对** 保存数据
<a name="E7csx"></a>
### 5.3 运算符
| **运算符** | **Python 表达式** | **结果** | **描述** | **支持的数据类型** |
| --- | --- | --- | --- | --- |
| + | [1, 2] + [3, 4] | [1, 2, 3, 4] | 合并 | 字符串、列表、元组 |
| * | ["Hi!"] * 4 | ['Hi!', 'Hi!', 'Hi!', 'Hi!'] | 重复 | 字符串、列表、元组 |
| in | 3 in (1, 2, 3) | True | 元素是否存在 | 字符串、列表、元组、字典 |
| not in | 4 not in (1, 2, 3) | True | 元素是否不存在 | 字符串、列表、元组、字典 |
| > >= == < <= | (1, 2, 3) < (2, 2, 3) | True | 元素比较 | 字符串、列表、元组 |

**注意**

- in 在对 **字典** 操作时，判断的是 **字典的键**
- in 和 not in 被称为 **成员运算符**
<a name="PRZGp"></a>
#### 成员运算符
成员运算符用于 **测试** 序列中是否包含指定的 **成员**

| **运算符** | **描述** | **实例** |
| --- | --- | --- |
| in | 如果在指定的序列中找到值返回 True，否则返回 False | 3 in (1, 2, 3) 返回 True |
| not in | 如果在指定的序列中没有找到值返回 True，否则返回 False | 3 not in (1, 2, 3) 返回 False |

注意：在对 **字典** 操作时，判断的是 **字典的键**
<a name="TjVHy"></a>
### 5.4 完整的 for 循环语法

- 在 Python 中完整的 for 循环 的语法如下：
```python
for 变量 in 集合:
    
    循环体代码
else:
    没有通过 break 退出循环，循环结束后，会执行的代码
```
<a name="dE2nw"></a>
#### 应用场景

- 在 **迭代遍历** 嵌套的数据类型时，例如 **一个列表包含了多个字典**
- 需求：要判断 某一个字典中 是否存在 指定的 值
   - 如果 **存在**，提示并且退出循环
   - 如果 **不存在**，在 **循环整体结束** 后，希望 **得到一个统一的提示**
```python
students = [
    {"name": "阿土",
     "age": 20,
     "gender": True,
     "height": 1.7,
     "weight": 75.0},
    {"name": "小美",
     "age": 19,
     "gender": False,
     "height": 1.6,
     "weight": 45.0},
]

find_name = "阿土"

for stu_dict in students:

    print(stu_dict)

    # 判断当前遍历的字典中姓名是否为find_name
    if stu_dict["name"] == find_name:
        print("找到了")

        # 如果已经找到，直接退出循环，就不需要再对后续的数据进行比较
        break

else:
    print("没有找到")

print("循环结束")
```
<a name="AYknc"></a>
# 08-变量进阶
<a name="m7tBb"></a>
## 01. 变量的引用

- 变量 和 数据 都是保存在 **内存** 中的
- 在 Python 中 **函数 的 参数传递** 以及 **返回值** 都是靠 **引用** 传递的
<a name="JXPxr"></a>
### 1.1 引用的概念
在 Python 中

- **变量** 和 **数据** 是分开存储的
- **数据** 保存在内存中的一个位置
- **变量** 中保存着数据在内存中的地址
- **变量** 中 **记录数据的地址**，就叫做 **引用**
- 使用 id() 函数可以查看变量中保存数据所在的 **内存地址**

注意：如果变量已经被定义，当给一个变量赋值的时候，本质上是 **修改了数据的引用**

- 变量 **不再** 对之前的数据引用
- 变量 **改为** 对新赋值的数据引用
<a name="XDZSP"></a>
### 1.2 变量引用 的示例
在 Python 中，变量的名字类似于 **便签纸** 贴在 **数据** 上

- 定义一个整数变量 a，并且赋值为 1
| **代码** | **图示** |
| --- | --- |
| a = 1 |  |

- 将变量 a 赋值为 2
| **代码** | **图示** |
| --- | --- |
| a = 2 |  |

- 定义一个整数变量 b，并且将变量 a 的值赋值给 b
| **代码** | **图示** |
| --- | --- |
| b = a |  |

变量 b 是第 2 个贴在数字 2 上的标签
<a name="hmtMS"></a>
### 1.3 函数的参数和返回值的传递
在 Python 中，函数的 **实参**/**返回值** 都是是靠 **引用** 来传递来的
```python
def test(num):

    print("-" * 50)
    print("%d 在函数内的内存地址是 %x" % (num, id(num)))

    result = 100

    print("返回值 %d 在内存中的地址是 %x" % (result, id(result)))
    print("-" * 50)

    return  result

a = 10
print("调用函数前 内存地址是 %x" % id(a))

r = test(a)

print("调用函数后 实参内存地址是 %x" % id(a))
print("调用函数后 返回值内存地址是 %x" % id(r))
# a的地址始终没变
# r的地址=result的地址
```
<a name="Uisvm"></a>
## 02. 可变和不可变类型

- **不可变类型**，变量值变化后，内存地址会改变
   - 数字类型 int, bool, float, complex, long(2.x)
   - 字符串 str
   - 元组 tuple
- **可变类型**，变量值变化后，内存地址不会改变
   - 列表 list
   - 字典 dict

注意：字典的 key **只能使用不可变类型的数据**<br />**注意**

1. **可变类型**的数据变化，是通过 **方法** 来实现的
2. 如果给一个可变类型的变量，赋值了一个新的数据，**引用会修改**
   - 变量 **不再** 对之前的数据引用
   - 变量 **改为** 对新赋值的数据引用
<a name="KqRTI"></a>
### 哈希 (hash)

- Python 中内置有一个名字叫做 hash(o) 的函数
   - 接收一个 **不可变类型** 的数据作为 **参数**
   - **返回** 结果是一个 **整数**
- 哈希 是一种 **算法**，其作用就是提取数据的 **特征码（指纹）**
   - **相同的内容** 得到 **相同的结果**
   - **不同的内容** 得到 **不同的结果**
- 在 Python 中，设置字典的 **键值对** 时，会首先对 key 进行 hash 已决定如何在内存中保存字典的数据，以方便 **后续** 对字典的操作：**增、删、改、查**
   - 键值对的 key 必须是不可变类型数据
   - 键值对的 value 可以是任意类型的数据
<a name="g43SF"></a>
## 03. 局部变量和全局变量

- **局部变量** 是在 **函数内部** 定义的变量，**只能在函数内部使用**
- **全局变量** 是在 **函数外部定义** 的变量（没有定义在某一个函数内），**所有函数** 内部 **都可以使用这个变量**

提示：在其他的开发语言中，大多 **不推荐使用全局变量** —— 可变范围太大，导致程序不好维护！
<a name="TVp38"></a>
### 3.1 局部变量

- **局部变量** 是在 **函数内部** 定义的变量，**只能在函数内部使用**
- 函数执行结束后，**函数内部的局部变量，会被系统回收**
- 不同的函数，可以定义相同的名字的局部变量，但是 **彼此之间** 不会产生影响
<a name="srKaa"></a>
#### 局部变量的作用

- 在函数内部使用，**临时** 保存 **函数内部需要使用的数据**

def demo1():     num = 10     print(num)     num = 20     print("修改后 %d" % num) def demo2():     num = 100     print(num) demo1() demo2() print("over") 
<a name="XAnND"></a>
#### 局部变量的生命周期

- 所谓 **生命周期** 就是变量从 **被创建** 到 **被系统回收** 的过程
- **局部变量** 在 **函数执行时** 才会被创建
- **函数执行结束后** 局部变量 **被系统回收**
- **局部变量在生命周期** 内，可以用来存储 **函数内部临时使用到的数据**
<a name="E2VEi"></a>
### 3.2 全局变量

- **全局变量** 是在 **函数外部定义** 的变量，所有函数内部都可以使用这个变量

# 定义一个全局变量 num = 10 def demo1():     print(num) def demo2():     print(num) demo1() demo2() print("over") <br />**注意**：函数执行时，**需要处理变量时** 会：

1. **首先** 查找 **函数内部** 是否存在 **指定名称 的局部变量**，**如果有，直接使用**
2. 如果没有，查找 **函数外部** 是否存在 **指定名称 的全局变量**，**如果有，直接使用**
3. 如果还没有，程序报错！
<a name="aOupF"></a>
#### 1) 函数不能直接修改 全局变量的引用

- **全局变量** 是在 **函数外部定义** 的变量（没有定义在某一个函数内），**所有函数** 内部 **都可以使用这个变量**

提示：在其他的开发语言中，大多 **不推荐使用全局变量** —— 可变范围太大，导致程序不好维护！

- 在函数内部，可以 **通过全局变量的引用获取对应的数据**
- 但是，**不允许直接修改全局变量的引用** —— 使用赋值语句修改全局变量的值

num = 10 def demo1():     print("demo1" + "-" * 50)     # 只是定义了一个局部变量，不会修改到全局变量，只是变量名相同而已     num = 100     print(num) def demo2():     print("demo2" + "-" * 50)     print(num) demo1() demo2() print("over") <br />注意：只是在函数内部定义了一个局部变量而已，只是变量名相同 —— 在函数内部不能直接修改全局变量的值
<a name="Ilkzw"></a>
#### 2) 在函数内部修改全局变量的值

- 如果在函数中需要修改全局变量，需要使用 global 进行声明

num = 10 def demo1():     print("demo1" + "-" * 50)     # global 关键字，告诉 Python 解释器 num 是一个全局变量     global num     # 只是定义了一个局部变量，不会修改到全局变量，只是变量名相同而已     num = 100     print(num) def demo2():     print("demo2" + "-" * 50)     print(num) demo1() demo2() print("over") 
<a name="zkDYA"></a>
#### 3) 全局变量定义的位置

- 为了保证所有的函数都能够正确使用到全局变量，应该 **将全局变量定义在其他函数的上方**

a = 10 def demo():     print("%d" % a)     print("%d" % b)     print("%d" % c) b = 20 demo() c = 30 <br />**注意**

- 由于全局变量 c，是在调用函数之后，才定义的，在执行函数时，变量还没有定义，所以程序会报错！

**代码结构示意图如下**
<a name="BccNe"></a>
#### 4) 全局变量命名的建议

- 为了避免局部变量和全局变量出现混淆，在定义全局变量时，有些公司会有一些开发要求，例如：
- 全局变量名前应该增加 g_ 或者 gl_ 的前缀

提示：具体的要求格式，各公司要求可能会有些差异
<a name="du5KO"></a>
# 09-面向对象
<a name="owzcq"></a>
## 01-面向对象基础语法
<a name="TRHhB"></a>
### 01. dir 内置函数

- 在 Python 中 **对象几乎是无所不在的**，我们之前学习的 **变量**、**数据**、**函数** 都是对象

在 Python 中可以使用以下两个方法验证：

1. 在 **标识符** / **数据** 后输入一个 .，然后按下 TAB 键，iPython 会提示该对象能够调用的 **方法列表**
2. 使用内置函数 dir 传入 **标识符** / **数据**，可以查看对象内的 **所有属性及方法**

**提示** __方法名__ 格式的方法是 Python 提供的 **内置方法 / 属性**，稍后会给大家介绍一些常用的 内置方法 / 属性

| **序号** | **方法名** | **类型** | **作用** |
| --- | --- | --- | --- |
| 01 | __new__ | 方法 | **创建对象**时，会被 **自动** 调用 |
| 02 | __init__ | 方法 | **对象被初始化**时，会被 **自动** 调用 |
| 03 | __del__ | 方法 | **对象被从内存中销毁**前，会被 **自动** 调用 |
| 04 | __str__ | 方法 | 返回**对象的描述信息**，print 函数输出使用 |

**提示** 利用好 dir() 函数，在学习时很多内容就不需要死记硬背了
<a name="KVped"></a>
### 02. 定义简单的类（只包含方法）
**面向对象** 是 **更大** 的 **封装**，在 **一个类中 封装 多个方法**，这样 **通过这个类创建出来的对象，就可以直接调用这些方法了**！
<a name="SvcXs"></a>
#### 2.1 定义只包含方法的类

- 在 Python 中要定义一个只包含方法的类，语法格式如下：
```python
class 类名:

    def 方法1(self, 参数列表):
        pass
    
    def 方法2(self, 参数列表):
        pass
```

- **方法** 的定义格式和之前学习过的**函数** 几乎一样
- 区别在于第一个参数必须是 self，大家暂时先记住，稍后介绍 self

注意：**类名** 的 命名规则 要符合 **大驼峰命名法**
<a name="IHmuA"></a>
#### 2.2 创建对象

- 当一个类定义完成之后，要使用这个类来创建对象，语法格式如下：

对象变量 = 类名() 
<a name="xJY6D"></a>
#### 2.3 第一个面向对象程序
```python
class Cat:
    """这是一个猫类"""

    def eat(self):
        print("小猫爱吃鱼")

    def drink(self):
        print("小猫在喝水")

tom = Cat()
tom.drink()
tom.eat()
```
<a name="viBbv"></a>
#### 引用概念的强调
在面向对象开发中，**引用**的概念是同样适用的！

- 在 Python 中使用类 **创建对象之后**，tom 变量中 仍然记录的是 **对象在内存中的地址**
- 也就是 tom 变量 **引用** 了 **新建的猫对象**
- 使用 print 输出 **对象变量**，默认情况下，是能够输出这个变量 **引用的对象** 是 **由哪一个类创建的对象**，以及 **在内存中的地址**（**十六进制表示**）

提示：在计算机中，通常使用 **十六进制** 表示 **内存地址**

- **十进制** 和 **十六进制** 都是用来表达数字的，只是表示的方式不一样
- **十进制** 和 **十六进制** 的数字之间可以来回转换
- %d 可以以 **10 进制** 输出数字
- %x 可以以 **16 进制** 输出数字
<a name="RS1ZI"></a>
### 03. 方法中的 self 参数
<a name="X1RWX"></a>
#### 3.1 案例改造 —— 给对象增加属性

- 在 Python 中，要 **给对象设置属性**，非常的容易，**但是不推荐使用**
   - 因为：对象属性的封装应该封装在类的内部
- 只需要在 **类的外部的代码** 中直接通过 . 设置一个属性即可

注意：这种方式虽然简单，但是不推荐使用！<br />tom.name = "Tom" ... lazy_cat.name = "大懒猫" 
<a name="gvqlF"></a>
#### 3.2 使用 self 在方法内部输出每一只猫的名字
由 **哪一个对象** 调用的方法，方法内的 self 就是 **哪一个对象的引用**

- 在类封装的方法内部，self 就表示 **当前调用方法的对象自己**
- **调用方法时**，程序员不需要传递 self 参数
- **在方法内部**
   - 可以通过 self. **访问对象的属性**
   - 也可以通过 self. **调用其他的对象方法**
- 在 **类的外部**，通过 变量名. 访问对象的 **属性和方法**
- 在 **类封装的方法中**，通过 self. 访问对象的 **属性和方法**
```python
    class Cat:

        def eat(self):
            print("%s 爱吃鱼" % self.name)


    tom = Cat()
    tom.name = "apple"
    tom.eat()

    lazy_cat = Cat()
    lazy_cat.name = "大懒猫"
    lazy_cat.eat()
```
<a name="Mf6ji"></a>
### 04. 初始化方法
<a name="ACuqL"></a>
#### 4.1 之前代码存在的问题 —— 在类的外部给对象增加属性

- 在日常开发中，不推荐在 **类的外部** 给对象增加属性
   - 如果**在运行时，没有找到属性，程序会报错**
- 对象应该包含有哪些属性，应该 **封装在类的内部**
<a name="juMHR"></a>
#### 4.2 初始化方法

- 当使用 类名() 创建对象时，会 **自动** 执行以下操作：
   1. 为对象在内存中 **分配空间** —— 创建对象
   2. 为对象的属性 **设置初始值** —— 初始化方法(init)
- 这个 **初始化方法** 就是 __init__ 方法，__init__ 是对象的**内置方法**

__init__ 方法是 **专门** 用来定义一个类 **具有哪些属性的方法**！<br />在 Cat 中增加 __init__ 方法，验证该方法在创建对象时会被自动调用
```python
    class Cat:
        """这是一个猫类"""

        def __init__(self):
            print("apple d 初始化方法")
    Tom = Cat()
```
 
<a name="Kyk8p"></a>
#### 4.3 在初始化方法内部定义属性

- 在 __init__ 方法内部使用 self.属性名 = 属性的初始值 就可以 **定义属性**
- 定义属性之后，再使用 Cat 类创建的对象，都会拥有该属性
```python
class Cat:

    def __init__(self):
        # 定义用 Cat 类创建的猫对象都有一个 name 的属性
        self.name = "Tom"
```
<a name="zWWVX"></a>
#### 4.4 改造初始化方法 —— 初始化的同时设置初始值

- 在开发中，如果希望在 **创建对象的同时，就设置对象的属性**，可以对 __init__ 方法进行 **改造**
   1. 把希望设置的属性值，定义成 __init__ 方法的参数
   2. 在方法内部使用 self.属性 = 形参 接收外部传递的参数
   3. 在创建对象时，使用 类名(属性1, 属性2...) 调用
```python
    class Cat:
        def __init__(self, name, age):
            print("初始化方法 %s" % name)
            self.name = name
            self.age = age

        def info(self):
            print("info: %s %d" % (self.name, self.age))

    tom = Cat("Tom", 21)
    tom.info()
```
<a name="AhCvA"></a>
### 05. 内置方法和属性
| **序号** | **方法名** | **类型** | **作用** |
| --- | --- | --- | --- |
| 01 | __del__ | 方法 | **对象被从内存中销毁**前，会被 **自动** 调用 |
| 02 | __str__ | 方法 | 返回**对象的描述信息**，print 函数输出使用 |

<a name="zpB45"></a>
#### 5.1 __del__ 方法（知道）

- 在 Python 中
   - 当使用 类名() 创建对象时，为对象 **分配完空间**后，**自动** 调用 __init__ 方法
   - 当一个 **对象被从内存中销毁** 前，会 **自动** 调用 __del__ 方法
- **应用场景**
   - __init__ 改造初始化方法，可以让创建对象更加灵活
   - __del__ 如果希望在对象被销毁前，再做一些事情，可以考虑一下 __del__ 方法
- **生命周期**
   - 一个对象从调用 类名() 创建，生命周期开始
   - 一个对象的 __del__ 方法一旦被调用，生命周期结束
   - 在对象的生命周期内，可以访问对象属性，或者让对象调用方法
```python

    class Cat:

        def __init__(self, new_name):
            self.name = new_name
            print("%s 来了" % self.name)

        def __del__(self):
            print("%s 走了" % self.name)

    # tom 是一个全局变量
    tom = Cat("Tom")
    print(tom.name)

    # del 关键字可以删除一个对象
    del tom
    print("-" * 50)
```
<a name="y4Qia"></a>
#### 5.2 __str__ 方法

- 在 Python 中，使用 print 输出 **对象变量**，默认情况下，会输出这个变量 **引用的对象** 是 **由哪一个类创建的对象**，以及 **在内存中的地址**（**十六进制表示**）
- 如果在开发中，希望使用 print 输出 **对象变量** 时，能够打印 **自定义的内容**，就可以利用 __str__ 这个内置方法了

注意：__str__ 方法必须返回一个字符串
```python
class Cat:
    def __init__(self, new_name):
        self.name = new_name
        print("%s 来了" % self.name)

    def __del__(self):
        print("%s 去了" % self.name)

    def __str__(self):
        return "我是小猫: %s" % self.name


tom = Cat("Tom")
print(tom)
```
<a name="ZZWST"></a>
## 02-私有属性和私有方法
<a name="S5PLJ"></a>
### 01. 应用场景及定义方式
**应用场景**

- 在实际开发中，**对象** 的 **某些属性或方法** 可能只希望 **在对象的内部被使用**，而 **不希望在外部被访问到**
- **私有属性** 就是 **对象** 不希望公开的 **属性**
- **私有方法** 就是 **对象** 不希望公开的 **方法**

**定义方式**

- 在 **定义属性或方法时**，在 **属性名或者方法名前** 增加 **两个下划线**，定义的就是 **私有** 属性或方法
```python
class Women:
    def __init__(self, name):
        self.name = name
        self.__age = 18

    def __sage(self):
        print("%d years old" % self.__age)

    def info(self):
        print("%s " %self.name)


apple = Women("aaa")
apple.info()
print(apple.name)
print(apple.__age)  # 无法访问
apple.__sage()      # 无法访问
```
<a name="i5Z7u"></a>
### 02. 访问私有的方法：伪私有属性和私有方法（科普）
提示：在日常开发中，**不要使用这种方式**，**访问对象的 私有属性 或 私有方法**<br />访问方式：<br />在 （变量函数）**名称** 前面加上 _类名 => _类名__名称
```python
class Women:
    def __init__(self, name):
        self.name = name
        self.__age = 18

    def __sage(self):
        print("%d years old" % self.__age)

    def info(self):
        print("%s " %self.name)


apple = Women("aaa")
apple.info()
print(apple.name)
print(apple._Women__age)  # 加了 _Women 可以访问私有属性了
apple._Women__sage()      # 加了 _Women 可以访问私有方法了
```
<a name="KceRH"></a>
## 03-单例
<a name="oQRke"></a>
### 01. 单例设计模式
 让 **类** 创建的对象，在系统中 **只有** **唯一的一个实例**

   - 每一次执行 类名() 返回的对象，**内存地址是相同的**
<a name="ov2sw"></a>
### 02. __new__ 方法

- 使用 **类名()** 创建对象时，Python 的解释器 **首先** 会 调用 __new__ 方法为对象 **分配空间**
- __new__ 是一个 由 object 基类提供的 **内置的静态方法**，主要作用有两个：
      1. 在内存中为对象 **分配空间**
      2. **返回** 对象的引用
- Python 的解释器获得对象的 **引用** 后，将引用作为 **第一个参数**，传递给 __init__ 方法

重写 __new__ 方法 的代码非常固定！

- 重写 __new__ 方法 **一定要** return super().__new__(cls)
- 否则 Python 的解释器 **得不到** 分配了空间的 **对象引用**，**就不会调用对象的初始化方法**
- 注意：__new__ 是一个静态方法，在调用时需要 **主动传递** cls 参数
- ![image.png](https://cdn.nlark.com/yuque/0/2023/png/22347830/1674791792585-44860dc2-66d8-4a14-804f-bce0c703c45c.png#averageHue=%23f7f7f7&clientId=uce65f72d-06b6-4&from=paste&height=216&id=u284113fd&name=image.png&originHeight=238&originWidth=817&originalType=binary&ratio=1&rotation=0&showTitle=false&size=38648&status=done&style=none&taskId=ubf63079b-2c84-4d95-989a-e3836b57a07&title=&width=742.727256629093)

**示例代码**
```python
from pywin.mfc.object import Object

class Women(Object):

    def __new__(cls, *args, **kwargs):
        print("分配空间返回对象引用new")
        return super().__new__(cls)

    def __init__(self, name, age):
        self.name = name
        self.age = age
        print("初始化Women")

apple = Women("aaa",22)
print(apple)
```
<a name="SsMSq"></a>
### 03. Python 中的单例

- **单例** —— 让 **类** 创建的对象，在系统中 **只有** **唯一的一个实例**
   1. 定义一个 **类属性**，初始值是 None，用于记录 **单例对象的引用**
   2. 重写 __new__ 方法
   3. 如果 **类属性** is None，调用父类方法分配空间，并在类属性中记录结果
   4. 返回 **类属性** 中记录的 **对象引用**
```python
class MusicPlayer(object):
    # 定义类属性记录单例对象引用
    instance = None
    def __new__(cls, *args, **kwargs):
        # 1. 判断类属性是否已经被赋值
        if cls.instance is None:
            cls.instance = super().__new__(cls)
        # 2. 返回类属性的单例引用
        return cls.instance
```
<a name="Mzd9d"></a>
### 只执行一次初始化工作

- 在每次使用 类名() 创建对象时，Python 的解释器都会自动调用两个方法：
   - __new__ 分配空间
   - __init__ 对象初始化
- 在上一小节对 __new__ 方法改造之后，每次都会得到 **第一次被创建对象的引用**
- 但是：**初始化方法还会被再次调用**

**需求**

- 让 **初始化动作** 只被 **执行一次**

**解决办法**

1. 定义一个类属性 init_flag 标记是否 **执行过初始化动作**，初始值为 False
2. 在 __init__ 方法中，判断 init_flag，如果为 False 就执行初始化动作
3. 然后将 init_flag 设置为 True
4. 这样，再次 **自动** 调用 __init__ 方法时，**初始化动作就不会被再次执行** 了
```python
class MusicPlayer(object):
    # 定义类属性记录单例对象引用
    instance = None
    init_flag = False
    def __new__(cls, *args, **kwargs):
        # 1. 判断类属性是否已经被赋值
        if cls.instance is None:
            cls.instance = super().__new__(cls)
        # 2. 返回类属性的单例引用
        return cls.instance

    def __init__(self):
        if not MusicPlayer.init_flag:
            print("第一次初始化")
            MusicPlayer.init_flag = True

music1 = MusicPlayer()
print(music1)
music2 = MusicPlayer()
print(music2)  # 两个地址相同说明单例成功
```
<a name="XEGnZ"></a>
# 10-多态
**面向对象三大特性**

1. **封装** 根据 **职责** 将 **属性** 和 **方法** **封装** 到一个抽象的 **类** 中
   - 定义类的准则
2. **继承** **实现代码的重用**，相同的代码不需要重复的编写
   - 设计类的技巧
   - 子类针对自己特有的需求，编写特定的代码
3. **多态** 不同的 **子类对象** 调用相同的 **父类方法**，产生不同的执行结果
   - **多态** 可以 **增加代码的灵活度**
   - 以 **继承** 和 **重写父类方法** 为前提
   - 是调用方法的技巧，**不会影响到类的内部设计**

**需求**

1. 在 Dog 类中封装方法 game
   - 普通狗只是简单的玩耍
2. 定义 XiaoTianDog 继承自 Dog，并且重写 game 方法
   - 哮天犬需要在天上玩耍
3. 定义 Person 类，并且封装一个 **和狗玩** 的方法
   - 在方法内部，直接让 **狗对象** 调用 game 方法

**案例小结**

- Person 类中只需要让 **狗对象** 调用 game 方法，而不关心具体是 **什么狗**
   - game 方法是在 Dog 父类中定义的
- 在程序执行时，传入不同的 **狗对象** 实参，就会产生不同的执行效果

**多态** 更容易编写出出通用的代码，做出通用的编程，以适应需求的不断变化！
```python
class Dog(object):

    def __init__(self, name):
        self.name = name

    def game(self):
        print("%s 蹦蹦跳跳的玩耍..." % self.name)


class XiaoTianDog(Dog):

    def game(self):  # 重写了父类方法 是多态的基本条件
        print("%s 飞到天上去玩耍..." % self.name)


class Person(object):

    def __init__(self, name):
        self.name = name

    def game_with_dog(self, dog):

        print("%s 和 %s 快乐的玩耍..." % (self.name, dog.name))

        # 让狗玩耍
        dog.game()


# 1. 创建一个狗对象
# wangcai = Dog("旺财")
wangcai = XiaoTianDog("飞天旺财")

# 2. 创建一个小明对象
xiaoming = Person("小明")

# 3. 让小明调用和狗玩的方法
xiaoming.game_with_dog(wangcai)  # 传入不同狗对象，产生不同效果，体现了多态
```
<a name="zsuSY"></a>
# 11-继承
<a name="Wr8ma"></a>
## 01. 单继承
<a name="M7ZqN"></a>
### 1.1 继承的概念、语法和特点
**继承的概念**：**子类** 拥有 **父类** 的所有 **方法** 和 **属性**
<a name="gJREY"></a>
#### 1) 继承的语法
class 类名(父类名):    

- **子类** 继承自 **父类**，可以直接 **享受** 父类中已经封装好的方法，不需要再次开发
- **子类** 中应该根据 **职责**，封装 **子类特有的** **属性和方法**
<a name="ytcKD"></a>
#### 2) 专业术语

- Dog 类是 Animal 类的**子类**，Animal 类是 Dog 类的**父类**，Dog 类从 Animal 类**继承**
- Dog 类是 Animal 类的**派生类**，Animal 类是 Dog 类的**基类**，Dog 类从 Animal 类**派生**
<a name="agRVc"></a>
#### 3) 继承的传递性

- C 类从 B 类继承，B 类又从 A 类继承
- 那么 C 类就具有 B 类和 A 类的所有属性和方法

**子类** 拥有 **父类** 以及 **父类的父类** 中封装的所有 **属性** 和 **方法**
<a name="uSxuI"></a>
### 1.2 方法的重写

- **子类** 拥有 **父类** 的所有 **方法** 和 **属性**
- **子类** 继承自 **父类**，可以直接 **享受** 父类中已经封装好的方法，不需要再次开发

**应用场景**

- 当 **父类** 的方法实现不能满足子类需求时，可以对方法进行 **重写(override)**

**重写** 父类方法有两种情况：

1. **覆盖** 父类的方法
2. 对父类方法进行 **扩展**
<a name="keMPO"></a>
#### 1) 覆盖父类的方法

- 如果在开发中，**父类的方法实现** 和 **子类的方法实现**，**完全不同**
- 就可以使用 **覆盖** 的方式，**在子类中** **重新编写** 父类的方法实现

具体的实现方式，就相当于在 **子类中** 定义了一个 **和父类同名的方法并且实现**<br />重写之后，在运行时，**只会调用** 子类中重写的方法，而不再会调用 **父类封装的方法**
<a name="g7OEa"></a>
#### 2) 对父类方法进行 **扩展**

- 如果在开发中，**子类的方法实现** 中 **包含** **父类的方法实现**
   - **父类原本封装的方法实现** 是 **子类方法的一部分**
- 就可以使用 **扩展** 的方式
   1. **在子类中** **重写** 父类的方法
   2. 在需要的位置使用 super().父类方法 来调用父类方法的执行
   3. 代码其他的位置针对子类的需求，编写 **子类特有的代码实现**
<a name="fqFJz"></a>
##### 关于 super

- 在 Python 中 super 是一个 **特殊的类**
- super() 就是使用 super 类创建出来的对象
- **最常** 使用的场景就是在 **重写父类方法时**，调用**在父类中封装的方法实现**
<a name="Lfovq"></a>
##### 调用父类方法的另外一种方式（知道）
在 Python 2.x 时，如果需要调用父类的方法，还可以使用以下方式：<br />父类名.方法(self) 

- 这种方式，目前在 Python 3.x 还支持这种方式
- 这种方法 **不推荐使用**，因为一旦 **父类发生变化**，方法调用位置的 **类名** 同样需要修改

**提示**

- 在开发时，父类名 和 super() 两种方式不要混用
- 如果使用 **当前子类名** 调用方法，会形成递归调用，**出现死循环**
<a name="QUQyx"></a>
### 1.3 父类的 私有属性 和 私有方法

1. **子类对象** **不能** 在自己的方法内部，**直接** 访问 父类的 **私有属性** 或 **私有方法**
2. **子类对象** 可以通过 **父类** 的 **公有方法** **间接** 访问到 **私有属性** 或 **私有方法**
- **私有属性、方法** 是对象的隐私，不对外公开，**外界** 以及 **子类** 都不能直接访问
- **私有属性、方法** 通常用于做一些内部的事情

**示例**

- B 的对象不能直接访问 __num2 属性
- B 的对象不能在 demo 方法内访问 __num2 属性
- B 的对象可以在 demo 方法内，调用父类的 test 方法
- 父类的 test 方法内部，能够访问 __num2 属性和 __test 方法
<a name="fgIW3"></a>
## 02. 多继承
**概念**

- **子类** 可以拥有 **多个父类**，并且具有 **所有父类** 的 **属性** 和 **方法**
- 例如：**孩子** 会继承自己 **父亲** 和 **母亲** 的 **特性**

**语法**<br />class 子类名(父类名1, 父类名2...):
<a name="FIP8S"></a>
### 2.1 多继承的使用注意事项
**问题的提出**

- 如果 **不同的父类** 中存在 **同名的方法**，**子类对象** 在调用方法时，会调用 **哪一个父类中**的方法呢？

提示：**开发时，应该尽量避免这种容易产生混淆的情况！** —— 如果 **父类之间** 存在 **同名的属性或者方法**，应该 **尽量避免** 使用多继承
<a name="naul7"></a>
#### Python 中的 MRO —— 方法搜索顺序（知道）

- Python 中针对 **类** 提供了一个 **内置属性** __mro__ 可以查看 **方法** 搜索顺序
- MRO 是 method resolution order，主要用于 **在多继承时判断 方法、属性 的调用 路径**

print(C.__mro__) <br />**输出结果**<br />(<class '__main__.C'>, <class '__main__.A'>, <class '__main__.B'>, <class 'object'>) 

- 在搜索方法时，是按照 __mro__ 的输出结果 **从左至右** 的顺序查找的
- 如果在当前类中 **找到方法，就直接执行，不再搜索**
- 如果 **没有找到，就查找下一个类** 中是否有对应的方法，**如果找到，就直接执行，不再搜索**
- 如果找到最后一个类，还没有找到方法，程序报错
<a name="PkHS3"></a>
### 2.2 新式类与旧式（经典）类
object 是 Python 为所有对象提供的 **基类**，提供有一些内置的属性和方法，可以使用 dir 函数查看

- **新式类**：以 object 为基类的类，**推荐使用**
- **经典类**：不以 object 为基类的类，**不推荐使用**
- 在 Python 3.x 中定义类时，如果没有指定父类，会 **默认使用** object 作为该类的 **基类** —— Python 3.x 中定义的类都是 **新式类**
- 在 Python 2.x 中定义类时，如果没有指定父类，则不会以 object 作为 **基类**

**新式类** 和 **经典类** 在多继承时 —— **会影响到方法的搜索顺序**<br />为了保证编写的代码能够同时在 Python 2.x 和 Python 3.x 运行！ 今后在定义类时，**如果没有父类，建议统一继承自 object**<br />class 类名(object):     
<a name="QIwBf"></a>
# 12-类属性和类方法
<a name="PzFs2"></a>
## 01. 类的结构
<a name="mMbXW"></a>
### 1.1 术语 —— 实例

1. 使用面相对象开发，**第 1 步** 是设计 **类**
2. 使用 **类名()** 创建对象，**创建对象** 的动作有两步：
      1. 在内存中为对象 **分配空间**
      2. 调用初始化方法 __init__ 为 **对象初始化**
3. 对象创建后，**内存** 中就有了一个对象的 **实实在在** 的存在 —— **实例**

因此，通常也会把：

1. 创建出来的 **对象** 叫做 **类** 的 **实例**
2. 创建对象的 **动作** 叫做 **实例化**
3. **对象的属性** 叫做 **实例属性**
4. **对象调用的方法** 叫做 **实例方法**

在程序执行时：

1. 对象各自拥有自己的 **实例属性**
2. 调用对象方法，可以通过 self.
   - 访问自己的属性
   - 调用自己的方法

**结论**

- **每一个对象** 都有自己 **独立的内存空间**，**保存各自不同的属性**
- **多个对象的方法**，**在内存中只有一份**，在调用方法时，**需要把对象的引用** 传递到方法内部
<a name="fIrxh"></a>
### 1.2 类是一个特殊的对象
Python 中 **一切皆对象**：

- class AAA: 定义的类属于 **类对象**
- obj1 = AAA() 属于 **实例对象**
- 在程序运行时，**类** 同样 **会被加载到内存**
- 在 Python 中，**类** 是一个特殊的对象 —— **类对象**
- 在程序运行时，**类对象** 在内存中 **只有一份**，使用 **一个类** 可以创建出 **很多个对象实例**
- 除了封装 **实例** 的 **属性** 和 **方法**外，**类对象** 还可以拥有自己的 **属性** 和 **方法**
   1. **类属性**
   2. **类方法**
- 通过 **类名.** 的方式可以 **访问类属性** 或者 **调用类方法**
<a name="FGpPa"></a>
## 02. 类属性和实例属性
<a name="IK6Jh"></a>
### 2.1 概念和使用

- **类属性** 就是给 **类对象** 中定义的 **属性**
- 通常用来记录 **与这个类相关** 的特征
- **类属性** **不会用于**记录 **具体对象的特征**

**示例需求**

- 定义一个 **工具类**
- 每件工具都有自己的 name
- **需求** —— 知道使用这个类，创建了多少个工具对象？
```python
class Tool(object):

    # 使用赋值语句，定义类属性，记录创建工具对象的总数
    count = 0

    def __init__(self, name):
        self.name = name

        # 针对类属性做一个计数+1
        Tool.count += 1


# 创建工具对象
tool1 = Tool("斧头")
tool2 = Tool("榔头")
tool3 = Tool("铁锹")

# 知道使用 Tool 类到底创建了多少个对象?
print("现在创建了 %d 个工具" % Tool.count)
```
<a name="xeoVs"></a>
### 2.2 属性的获取机制（科普）

- 在 Python 中 **属性的获取** 存在一个 **向上查找机制**
- 因此，要访问类属性有两种方式：
   1. **类名.类属性**
   2. **对象.类属性** （不推荐）

**注意**

- 如果使用 对象.类属性 = 值 赋值语句，只会 **给对象添加一个属性**，而不会影响到 **类属性的值**
<a name="YuKKL"></a>
## 03. 类方法和静态方法
<a name="V8WaL"></a>
### 3.1 类方法

- **类属性** 就是针对 **类对象** 定义的属性
   - 使用 **赋值语句** 在 class 关键字下方可以定义 **类属性**
   - **类属性** 用于记录 **与这个类相关** 的特征
- **类方法** 就是针对 **类对象** 定义的方法
   - 在 **类方法** 内部可以直接访问 **类属性** 或者调用其他的 **类方法**

**语法如下**
```python
@classmethod
def 类方法名(cls):
      ...
```

- 类方法需要用 **修饰器** @classmethod 来标识，**告诉解释器这是一个类方法**
- 类方法的 **第一个参数** 应该是 cls
   - 由 **哪一个类** 调用的方法，方法内的 cls 就是 **哪一个类的引用**
   - 这个参数和 **实例方法** 的第一个参数是 self 类似
   - **提示** 使用其他名称也可以，不过习惯使用 cls
1. 通过 **类名.** 调用 **类方法**，**调用方法时**，不需要传递 cls 参数
2. **在方法内部**
   - 可以通过 cls. **访问类的属性**
   - 也可以通过 cls. **调用其他的类方法**

**示例需求**

- 定义一个 **工具类**
- 每件工具都有自己的 name
- **需求** —— 在 **类** 封装一个 show_tool_count 的类方法，输出使用当前这个类，创建的对象个数
```python
@classmethod
def show_tool_count(cls):
    """显示工具对象的总数"""
    print("工具对象的总数 %d" % cls.count)
```
在类方法内部，可以直接使用 cls 访问 **类属性** 或者 **调用类方法**
<a name="TAQFv"></a>
### 3.2 静态方法

- 在开发时，如果需要在 **类** 中封装一个方法，这个方法：
   - 既 **不需要** 访问 **实例属性** 或者调用 **实例方法**
   - 也 **不需要** 访问 **类属性** 或者调用 **类方法**
- 这个时候，可以把这个方法封装成一个 **静态方法**

**语法如下**
```python
@staticmethod
def 静态方法名():
    pass
```
 

- **静态方法** 需要用 **修饰器** @staticmethod 来标识，**告诉解释器这是一个静态方法**
- 通过 **类名.** 调用 **静态方法**
```python
class Dog(object):
    
    # 狗对象计数
    dog_count = 0
    
    @staticmethod
    def run():
        
        # 不需要访问实例属性也不需要访问类属性的方法
        print("狗在跑...")

    def __init__(self, name):
        self.name = name
```
<a name="Q2mek"></a>
### 3.3 方法综合案例
**需求**

1. 设计一个 Game 类
2. 属性：
   - 定义一个 **类属性** top_score 记录游戏的 **历史最高分**
   - 定义一个 **实例属性** player_name 记录 **当前游戏的玩家姓名**
3. 方法：
   - **静态方法** show_help 显示游戏帮助信息
   - **类方法** show_top_score 显示历史最高分
   - **实例方法** start_game 开始当前玩家的游戏
4. 主程序步骤
      1. 查看帮助信息
      2. 查看历史最高分
      3. 创建游戏对象，开始游戏
<a name="SUPHT"></a>
#### 案例小结

1. **实例方法** —— 方法内部需要访问 **实例属性**
   - **实例方法** 内部可以使用 **类名.** 访问类属性
2. **类方法** —— 方法内部 **只** 需要访问 **类属性**
3. **静态方法** —— 方法内部，不需要访问 **实例属性** 和 **类属性**

**提问**<br />如果方法内部 即需要访问 **实例属性**，又需要访问 **类属性**，应该定义成什么方法？<br />**答案**

- 应该定义 **实例方法**
- 因为，**类只有一个**，在 **实例方法** 内部可以使用 **类名.** 访问类属性
```python
class Game(object):
    top_score = 0   # 游戏最高分，类属性

    @staticmethod  # 静态方法
    def show_help():
        print("帮助信息：让僵尸走进房间")

    @classmethod    # 类方法
    def show_top_score(cls):
        print("游戏最高分是 %d" % cls.top_score)

    def __init__(self, player_name):
        self.player_name = player_name

    def start_game(self):
        print("[%s] 开始游戏..." % self.player_name)

        # 使用类名.修改历史最高分
        Game.top_score = 999


# 1. 查看游戏帮助
Game.show_help()
# 2. 查看游戏最高分
Game.show_top_score()
# 3. 创建游戏对象，开始游戏
game = Game("小明")
game.start_game()
# 4. 游戏结束，查看游戏最高分
Game.show_top_score()
```
<a name="ixXLA"></a>
# 13-eval 函数
eval() 函数十分强大 —— **将字符串** 当成 **有效的表达式** 来求值 并 **返回计算结果**
```python
# 基本的数学计算
In [1]: eval("1 + 1")
Out[1]: 2

# 字符串重复
In [2]: eval("'*' * 10")
Out[2]: '**********'

# 将字符串转换成列表
In [3]: type(eval("[1, 2, 3, 4, 5]"))
Out[3]: list

# 将字符串转换成字典
In [4]: type(eval("{'name': 'xiaoming', 'age': 18}"))
Out[4]: dict
```
<a name="PwZ3P"></a>
## 案例 - 计算器
**需求**

1. 提示用户输入一个 **加减乘除混合运算**
2. 返回计算结果
```python
input_str = input("请输入一个算术题：")
print(eval(input_str))
```
<a name="jbDsu"></a>
## 不要滥用 eval
在开发时千万不要使用 eval 直接转换 input 的结果
```python
__import__('os').system('ls')
```

- 等价代码
```python
import os

os.system("终端命令")
```

- 执行成功，返回 0
- 执行失败，返回错误信息
<a name="DdsDt"></a>
# <br />14-模块和包
<a name="qzrbc"></a>
## 01. 模块
<a name="R9uIQ"></a>
### 1.1 模块的概念
**模块是 Python 程序架构的一个核心概念**

- 每一个以扩展名 py 结尾的 Python 源代码文件都是一个 **模块**
- **模块名** 同样也是一个 **标识符**，需要符合标识符的命名规则
- 在模块中定义的 **全局变量** 、**函数**、**类** 都是提供给外界直接使用的 **工具**
- **模块** 就好比是 **工具包**，要想使用这个工具包中的工具，就需要先 **导入** 这个模块
<a name="s0lIP"></a>
### 1.2 模块的两种导入方式
<a name="rK4nY"></a>
#### 1）import 导入
import 模块名1, 模块名2  <br />提示：在导入模块时，每个导入应该独占一行<br />import 模块名1 <br />import 模块名2  

- **导入之后**
   - 通过 模块名. 使用 **模块提供的工具** —— **全局变量**、**函数**、**类**
<a name="oe1Hi"></a>
##### 使用 as 指定模块的别名
**如果模块的名字太长**，可以使用 as 指定模块的名称，以方便在代码中的使用<br />import 模块名1 as 模块别名 <br />注意：**模块别名** 应该符合 **大驼峰命名法**
<a name="UkgRD"></a>
#### 2）from...import 导入

- 如果希望 **从某一个模块** 中，导入 **部分** 工具，就可以使用 from ... import 的方式
- import 模块名 是 **一次性** 把模块中 **所有工具全部导入**，并且通过 **模块名/别名** 访问

# 从 模块 导入 某一个工具 from 模块名1 import 工具名 

- 导入之后
   - **不需要** 通过 模块名.
   - 可以直接使用 **模块提供的工具** —— **全局变量**、**函数**、**类**

**注意**<br />如果 **两个模块**，存在 **同名的函数**，那么 **后导入模块的函数**，会 **覆盖掉先导入的函数**

- 开发时 import 代码应该统一写在 **代码的顶部**，更容易及时发现冲突
- 一旦发现冲突，可以使用 as 关键字 **给其中一个工具起一个别名**
<a name="JmLTq"></a>
##### from...import *（知道）
# 从 模块 导入 所有工具 from 模块名1 import * <br />**注意**<br />这种方式不推荐使用，因为函数重名并没有任何的提示，出现问题不好排查
<a name="AhK3e"></a>
### 1.3 模块的搜索顺序[扩展]
Python 的解释器在 **导入模块** 时，会：

1. 搜索 **当前目录** 指定模块名的文件，**如果有就直接导入**
2. 如果没有，再搜索 **系统目录**

在开发时，给文件起名，不要和 **系统的模块文件** **重名**<br />Python 中每一个模块都有一个内置属性 __file__ 可以 **查看模块** 的 **完整路径**<br />**示例**
```python
import random

# 生成一个 0～10 的数字
rand = random.randint(0, 10)

print(rand)
```
注意：如果当前目录下，存在一个 random.py 的文件，程序就无法正常执行了！

- 这个时候，Python 的解释器会 **加载当前目录** 下的 random.py 而不会加载 **系统的** random 模块
<a name="Wr7Jw"></a>
### 1.4 原则 —— 每一个文件都应该是可以被导入的

- 一个 **独立的 Python 文件** 就是一个 **模块**
- 在导入文件时，文件中 **所有没有任何缩进的代码** 都会被执行一遍！

**实际开发场景**

- 在实际开发中，每一个模块都是独立开发的，大多都有专人负责
- **开发人员** 通常会在 **模块下方** **增加一些测试代码**
   - 仅在模块内使用，而被导入到其他文件中不需要执行
<a name="P3G0J"></a>
#### __name__ 属性

- __name__ 属性可以做到，测试模块的代码 **只在测试情况下被运行**，而在 **被导入时不会被执行**！
- __name__ 是 Python 的一个内置属性，记录着一个 **字符串**
- 如果 **是被其他文件导入的**，__name__ 就是 **模块名**
- 如果 **是当前执行的程序** __name__ 是 **__main__**

**在很多 Python 文件中都会看到以下格式的代码**：
```python
# 导入模块
# 定义全局变量
# 定义类
# 定义函数

# 在代码的最下方
def main():
    # ...
    pass

# 根据 __name__ 判断是否执行下方代码
if __name__ == "__main__":
    main()

```
<a name="SebLL"></a>
## 02. 包（Package）
<a name="fo9i5"></a>
### 概念

- **包** 是一个 **包含多个模块** 的 **特殊目录**
- 目录下有一个 **特殊的文件** __init__.py
- 包名的 **命名方式** 和变量名一致，**小写字母** + _

**好处**

- 使用 import 包名 可以一次性导入 **包** 中 **所有的模块**
<a name="b0qVn"></a>
### 案例演练

1. 新建一个 hm_message 的 **包**
2. 在目录下，新建两个文件 send_message 和 receive_message
3. 在 send_message 文件中定义一个 send 函数
4. 在 receive_message 文件中定义一个 receive 函数
5. 在外部直接导入 hm_message 的包
<a name="q1pDO"></a>
### __init__.py

- 要在外界使用 **包** 中的模块，需要在 __init__.py 中指定 **对外界提供的模块列表**
```python
# 从 当前目录 导入 模块列表
from . import send_message
from . import receive_message
```
<a name="nKNpb"></a>
## 03. 发布模块（知道）

- 如果希望自己开发的模块，**分享** 给其他人，可以按照以下步骤操作
<a name="RPikJ"></a>
### 3.1 制作发布压缩包步骤
<a name="BD5La"></a>
#### 1) 创建 setup.py

- setup.py 的文件
```python
from distutils.core import setup

setup(name="hm_message",  # 包名
      version="1.0",  # 版本
      description="itheima's 发送和接收消息模块",  # 描述信息
      long_description="完整的发送和接收消息模块",  # 完整描述信息
      author="itheima",  # 作者
      author_email="itheima@itheima.com",  # 作者邮箱
      url="www.itheima.com",  # 主页
      py_modules=["hm_message.send_message",
                  "hm_message.receive_message"])
```
有关字典参数的详细信息，可以参阅官方网站：<br />[https://docs.python.org/2/distutils/apiref.html](https://docs.python.org/2/distutils/apiref.html)
<a name="cbyvn"></a>
#### 2) 构建模块
$ python3 setup.py build 
<a name="eOJaj"></a>
#### 3) 生成发布压缩包
$ python3 setup.py sdist <br />注意：要制作哪个版本的模块，就使用哪个版本的解释器执行！
<a name="mIHsy"></a>
### 3.2 安装模块
$ tar -zxvf hm_message-1.0.tar.gz  <br />$ sudo python3 setup.py install <br />**卸载模块**<br />直接从安装目录下，把安装模块的 **目录** 删除就可以<br />$ cd /usr/local/lib/python3.5/dist-packages/ <br />$ sudo rm -r hm_message* 
<a name="T4l5P"></a>
### 3.3 pip 安装第三方模块

- **第三方模块** 通常是指由 **知名的第三方团队** **开发的** 并且被 **程序员广泛使用** 的 Python 包 / 模块
   - 例如 pygame 就是一套非常成熟的 **游戏开发模块**
- pip 是一个现代的，通用的 Python 包管理工具
- 提供了对 Python 包的查找、下载、安装、卸载等功能

安装和卸载命令如下：
```python
# 将模块安装到 Python 2.x 环境
$ sudo pip install pygame
$ sudo pip uninstall pygame

# 将模块安装到 Python 3.x 环境
$ sudo pip3 install pygame
$ sudo pip3 uninstall pygame
在 Mac 下安装 iPython
$ sudo pip install ipython
在 Linux 下安装 iPython
$ sudo apt install ipython
$ sudo apt install ipython3
```
<a name="xWKaJ"></a>
# 15-文件
<a name="GR84N"></a>
## 01. 文件的概念
<a name="YYX7z"></a>
### 1.1 文件的概念和作用

- 计算机的 **文件**，就是存储在某种 **长期储存设备** 上的一段 **数据**
- 长期存储设备包括：硬盘、U 盘、移动硬盘、光盘...

**文件的作用**<br />将数据长期保存下来，在需要的时候使用

| **CPU** | **内存** | **硬盘** |
| --- | --- | --- |
|  |  |  |

<a name="tey9n"></a>
### 1.2 文件的存储方式

- 在计算机中，文件是以 **二进制** 的方式保存在磁盘上的
<a name="f9hHK"></a>
#### 文本文件和二进制文件

- 文本文件
   - 可以使用 **文本编辑软件** 查看
   - 本质上还是二进制文件
   - 例如：python 的源程序
- 二进制文件
   - 保存的内容 不是给人直接阅读的，而是 **提供给其他软件使用的**
   - 例如：图片文件、音频文件、视频文件等等
   - 二进制文件不能使用 **文本编辑软件** 查看
<a name="k0k9w"></a>
## 02. 文件的基本操作
<a name="BADgL"></a>
### 2.1 操作文件的套路
在 **计算机** 中要操作文件的套路非常固定，一共包含**三个步骤**：

1. 打开文件
2. 读、写文件
   - **读** 将文件内容读入内存
   - **写** 将内存内容写入文件
3. 关闭文件
<a name="gZKh2"></a>
### 2.2 操作文件的函数/方法

- 在 Python 中要操作文件需要记住 1 个函数和 3 个方法
| **序号** | **函数/方法** | **说明** |
| --- | --- | --- |
| 01 | open | 打开文件，并且返回文件操作对象 |
| 02 | read | 将文件内容读取到内存 |
| 03 | write | 将指定内容写入文件 |
| 04 | close | 关闭文件 |

- open 函数负责打开文件，并且返回文件对象
- read/write/close 三个方法都需要通过 **文件对象** 来调用
<a name="nsANA"></a>
### 2.3 read 方法 —— 读取文件

- open 函数的第一个参数是要打开的文件名（文件名区分大小写）
   - 如果文件 **存在**，返回 **文件操作对象**
   - 如果文件 **不存在**，会 **抛出异常**
- read 方法可以一次性 **读入** 并 **返回** 文件的 **所有内容**
- close 方法负责 **关闭文件**
   - 如果 **忘记关闭文件**，**会造成系统资源消耗，而且会影响到后续对文件的访问**
- **注意**：read 方法执行后，会把 **文件指针** 移动到 **文件的末尾**
```python
# 1. 打开 - 文件名需要注意大小写
file = open("README")

# 2. 读取
text = file.read()
print(text)

# 3. 关闭
file.close()
```
**提示**

- 在开发中，通常会先编写 **打开** 和 **关闭** 的代码，再编写中间针对文件的 **读/写** 操作！
<a name="QumeE"></a>
#### 文件指针（知道）

- **文件指针** 标记 **从哪个位置开始读取数据**
- **第一次打开** 文件时，通常 **文件指针会指向文件的开始位置**
- 当执行了 read 方法后，**文件指针** 会移动到 **读取内容的末尾**
   - 默认情况下会移动到 **文件末尾**

**思考**

- 如果执行了一次 read 方法，读取了所有内容，那么再次调用 read 方法，还能够获得到内容吗？

**答案**

- 不能
- 第一次读取之后，文件指针移动到了文件末尾，再次调用不会读取到任何的内容
<a name="efYnZ"></a>
### 2.4 打开文件的方式

- open 函数默认以 **只读方式** 打开文件，并且返回文件对象

语法如下：<br />f = open("文件名", "访问方式") 

| **访问方式** | **说明** |
| --- | --- |
| r | 以**只读**方式打开文件。文件的指针将会放在文件的开头，这是**默认模式**。如果文件不存在，抛出异常 |
| w | 以**只写**方式打开文件。如果文件存在会被覆盖。如果文件不存在，创建新文件 |
| a | 以**追加**方式打开文件。如果该文件已存在，文件指针将会放在文件的结尾。如果文件不存在，创建新文件进行写入 |
| r+ | 以**读写**方式打开文件。文件的指针将会放在文件的开头。如果文件不存在，抛出异常 |
| w+ | 以**读写**方式打开文件。如果文件存在会被覆盖。如果文件不存在，创建新文件 |
| a+ | 以**读写**方式打开文件。如果该文件已存在，文件指针将会放在文件的结尾。如果文件不存在，创建新文件进行写入 |

**提示**

- 频繁的移动文件指针，**会影响文件的读写效率**，开发中更多的时候会以 **只读**、**只写** 的方式来操作文件

**写入文件示例**
```python
# 打开文件
f = open("README", "w")

f.write("hello python！\n")
f.write("今天天气真好")

# 关闭文件
f.close()
```
<a name="Wbq50"></a>
### 2.5 按行读取文件内容

- read 方法默认会把文件的 **所有内容** **一次性读取到内存**
- 如果文件太大，对内存的占用会非常严重
<a name="vfDtf"></a>
#### readline 方法

- readline 方法可以一次读取一行内容
- 方法执行后，会把 **文件指针** 移动到下一行，准备再次读取

**读取大文件的正确姿势**
```python
# 打开文件
file = open("README")

while True:
    # 读取一行内容
    text = file.readline()

    # 判断是否读到内容
    if not text:
        break

    # 每读取一行的末尾已经有了一个 `\n`
    print(text, end="")

# 关闭文件
file.close()
```
<a name="Oxg2J"></a>
### 2.6 文件读写案例 —— 复制文件
**目标**<br />用代码的方式，来实现文件复制过程
<a name="JrCCI"></a>
#### 小文件复制

- 打开一个已有文件，读取完整内容，并写入到另外一个文件
```python
# 1. 打开文件
file_read = open("README")
file_write = open("README[复件]", "w")

# 2. 读取并写入文件
text = file_read.read()
file_write.write(text)

# 3. 关闭文件
file_read.close()
file_write.close()
```
<a name="stzzW"></a>
#### 大文件复制

- 打开一个已有文件，逐行读取内容，并顺序写入到另外一个文件
```python
# 1. 打开文件
file_read = open("README")
file_write = open("README[复件]", "w")

# 2. 读取并写入文件
while True:
    # 每次读取一行
    text = file_read.readline()

    # 判断是否读取到内容
    if not text:
        break

    file_write.write(text)

# 3. 关闭文件
file_read.close()
file_write.close()
```
<a name="YUzZM"></a>
## 03. 文件/目录的常用管理操作

- 在 **终端** / **文件浏览器**、 中可以执行常规的 **文件** / **目录** 管理操作，例如：
   - 创建、重命名、删除、改变路径、查看目录内容、……
- 在 Python 中，如果希望通过程序实现上述功能，需要导入 os 模块
<a name="oUQkw"></a>
### 文件操作
| **序号** | **方法名** | **说明** | **示例** |
| --- | --- | --- | --- |
| 01 | rename | 重命名文件 | os.rename(源文件名, 目标文件名) |
| 02 | remove | 删除文件 | os.remove(文件名) |

<a name="eyuXk"></a>
### 目录操作
| **序号** | **方法名** | **说明** | **示例** |
| --- | --- | --- | --- |
| 01 | listdir | 目录列表 | os.listdir(目录名) |
| 02 | mkdir | 创建目录 | os.mkdir(目录名) |
| 03 | rmdir | 删除目录 | os.rmdir(目录名) |
| 04 | getcwd | 获取当前目录 | os.getcwd() |
| 05 | chdir | 修改工作目录 | os.chdir(目标目录) |
| 06 | path.isdir | 判断是否是文件 | os.path.isdir(文件路径) |

提示：文件或者目录操作都支持 **相对路径** 和 **绝对路径**
<a name="YmmcK"></a>
## 04. 文本文件的编码格式（科普）

- 文本文件存储的内容是基于 **字符编码** 的文件，常见的编码有 ASCII 编码，UNICODE 编码等

Python 2.x 默认使用 ASCII 编码格式 Python 3.x 默认使用 UTF-8 编码格式
<a name="zij5n"></a>
### 4.1 ASCII 编码和 UNICODE 编码
<a name="gBTKF"></a>
#### ASCII 编码

- 计算机中只有 256 个 ASCII 字符
- 一个 ASCII 在内存中占用 **1 个字节** 的空间
   - 8 个 0/1 的排列组合方式一共有 256 种，也就是 2 ** 8
<a name="IUgVB"></a>
#### UTF-8 编码格式

- 计算机中使用 **1~6 个字节** 来表示一个 UTF-8 字符，涵盖了 **地球上几乎所有地区的文字**
- 大多数汉字会使用 **3 个字节** 表示
- UTF-8 是 UNICODE 编码的一种编码格式
<a name="czHUy"></a>
### 4.2 Ptyhon 2.x 中如何使用中文
Python 2.x 默认使用 ASCII 编码格式 Python 3.x 默认使用 UTF-8 编码格式

- 在 Python 2.x 文件的 **第一行** 增加以下代码，解释器会以 utf-8 编码来处理 python 文件

# *-* coding:utf8 *-* <br />这方式是官方推荐使用的！

- 也可以使用

# coding=utf8 
<a name="vYs4w"></a>
#### unicode 字符串

- 在 Python 2.x 中，即使指定了文件使用 UTF-8 的编码格式，但是在遍历字符串时，仍然会 **以字节为单位遍历** 字符串
- 要能够 **正确的遍历字符串**，在定义字符串时，需要 **在字符串的引号前**，增加一个小写字母 u，告诉解释器这是一个 unicode 字符串（使用 UTF-8 编码格式的字符串）
```python
# *-* coding:utf8 *-*

# 在字符串前，增加一个 `u` 表示这个字符串是一个 utf8 字符串
hello_str = u"你好世界"

print(hello_str)

for c in hello_str:
    print(c)
```
<a name="jI7S9"></a>
# 16-异常
<a name="gnZRS"></a>
## 01. 异常的概念

- 程序在运行时，如果 Python 解释器 **遇到** 到一个错误，**会停止程序的执行，并且提示一些错误信息**，这就是 **异常**
- **程序停止执行并且提示错误信息** 这个动作，我们通常称之为：**抛出(raise)异常**

程序开发时，很难将 **所有的特殊情况** 都处理的面面俱到，通过 **异常捕获** 可以针对突发事件做集中的处理，从而保证程序的 **稳定性和健壮性**
<a name="yU54S"></a>
## 02. 捕获异常
<a name="qrc15"></a>
### 2.1 简单的捕获异常语法

- 在程序开发中，如果 **对某些代码的执行不能确定是否正确**，可以增加 try(尝试) 来 **捕获异常**
- 捕获异常最简单的语法格式：
```python
try:
    尝试执行的代码
except:
    出现错误的处理
```

- try **尝试**，下方编写要尝试代码，不确定是否能够正常执行的代码
- except **如果不是**，下方编写尝试失败的代码
<a name="jSJTF"></a>
#### 简单异常捕获演练 —— 要求用户输入整数
```python
try:
    # 提示用户输入一个数字
    num = int(input("请输入数字："))
except:
    print("请输入正确的数字")
```
<a name="cyK9l"></a>
### 2.2 错误类型捕获

- 在程序执行时，可能会遇到 **不同类型的异常**，并且需要 **针对不同类型的异常，做出不同的响应**，这个时候，就需要捕获错误类型了
- 语法如下：
```python
try:
    # 尝试执行的代码
    pass
except 错误类型1:
    # 针对错误类型1，对应的代码处理
    pass
except (错误类型2, 错误类型3):
    # 针对错误类型2 和 3，对应的代码处理
    pass
except Exception as result:
    print("未知错误 %s" % result)
```

- 当 Python 解释器 **抛出异常** 时，**最后一行错误信息的第一个单词，就是错误类型**
<a name="mmfaX"></a>
#### 异常类型捕获演练 —— 要求用户输入整数
**需求**

1. 提示用户输入一个整数
2. 使用 8 除以用户输入的整数并且输出
```python
try:
    num = int(input("请输入整数："))
    result = 8 / num
    print(result)
except ValueError:
    print("请输入正确的整数")
except ZeroDivisionError:
    print("除 0 错误")
```
<a name="sqzbs"></a>
#### 捕获未知错误

- 在开发时，**要预判到所有可能出现的错误**，还是有一定难度的
- 如果希望程序 **无论出现任何错误**，都不会因为 Python 解释器 **抛出异常而被终止**，可以再增加一个 except

语法如下：
```python
except Exception as result:
    print("未知错误 %s" % result)
```
<a name="x4TlC"></a>
### 2.3 异常捕获完整语法

- 在实际开发中，为了能够处理复杂的异常情况，完整的异常语法如下：

提示：

- 有关完整语法的应用场景，在后续学习中，**结合实际的案例**会更好理解
- 现在先对这个语法结构有个印象即可
```python
try:
    # 尝试执行的代码
    pass
except 错误类型1:
    # 针对错误类型1，对应的代码处理
    pass
except 错误类型2:
    # 针对错误类型2，对应的代码处理
    pass
except (错误类型3, 错误类型4):
    # 针对错误类型3 和 4，对应的代码处理
    pass
except Exception as result:
    # 打印错误信息
    print(result)
else:
    # 没有异常才会执行的代码
    pass
finally:
    # 无论是否有异常，都会执行的代码
    print("无论是否有异常，都会执行的代码")
```

- else 只有在没有异常时才会执行的代码
- finally 无论是否有异常，都会执行的代码
- 之前一个演练的 **完整捕获异常** 的代码如下：
```python
try:
    num = int(input("请输入整数："))
    result = 8 / num
    print(result)
except ValueError:
    print("请输入正确的整数")
except ZeroDivisionError:
    print("除 0 错误")
except Exception as result:
    print("未知错误 %s" % result)
else:
    print("正常执行")
finally:
    print("执行完成，但是不保证正确")
```
<a name="vbB5C"></a>
## 03. 异常的传递

- **异常的传递** —— 当 **函数/方法** 执行 **出现异常**，会 **将异常传递** 给 函数/方法 的 **调用一方**
- 如果 **传递到主程序**，仍然 **没有异常处理**，程序才会被终止

提示

- 在开发中，可以在主函数中增加 **异常捕获**
- 而在主函数中调用的其他函数，只要出现异常，都会传递到主函数的 **异常捕获** 中
- 这样就不需要在代码中，增加大量的 **异常捕获**，能够保证代码的整洁

**需求**

1. 定义函数 demo1() **提示用户输入一个整数并且返回**
2. 定义函数 demo2() 调用 demo1()
3. 在主程序中调用 demo2()
```python
def demo1():
    return int(input("请输入一个整数："))

def demo2():
    return demo1()

try:
    print(demo2())
except ValueError:
    print("请输入正确的整数")
except Exception as result:
    print("未知错误 %s" % result)
```
<a name="im5R3"></a>
## 04. 抛出 raise 异常
<a name="tZy2u"></a>
### 4.1 应用场景

- 在开发中，除了 **代码执行出错** Python 解释器会 **抛出** 异常之外
- 还可以根据 **应用程序** **特有的业务需求** **主动抛出异常**

**示例**

- 提示用户 **输入密码**，如果 **长度少于 8**，抛出 **异常**

**注意**

- 当前函数 **只负责** 提示用户输入密码，如果 **密码长度不正确，需要其他的函数进行额外处理**
- 因此可以 **抛出异常**，由其他需要处理的函数 **捕获异常**
<a name="lfuWF"></a>
### 4.2 抛出异常

- Python 中提供了一个 Exception **异常类**
- 在开发时，如果满足 **特定业务需求时**，希望 **抛出异常**，可以：
   1. **创建** 一个 Exception 的 **对象**
   2. 使用 raise **关键字** 抛出 **异常对象**

**需求**

- 定义 input_password 函数，提示用户输入密码
- 如果用户输入长度 < 8，抛出异常
- 如果用户输入长度 >=8，返回输入的密码
```python
def input_password():

    # 1. 提示用户输入密码
    pwd = input("请输入密码：")

    # 2. 判断密码长度，如果长度 >= 8，返回用户输入的密码
    if len(pwd) >= 8:
        return pwd

    # 3. 密码长度不够，需要抛出异常
    # 1> 创建异常对象 - 使用异常的错误信息字符串作为参数
    ex = Exception("密码长度不够")

    # 2> 抛出异常对象
    raise ex


try:
    user_pwd = input_password()
    print(user_pwd)
except Exception as result:
    print("发现错误：%s" % result)
```
