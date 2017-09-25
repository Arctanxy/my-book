前面已经介绍了我们选择Python3的理由，这一节中我们将介绍一下Python3的语法知识，作为最容易学习的编程语言，相信经过这一节的讲解，大家对Python编程会有个大致的认识。

Python书写规则：

Python中一般不适用语句结束符号“；”，简单地依靠缩进来区分语句。

#参考地址：http://www.runoob.com/python/python-variable-types.html

#http://www.yiibai.com/python/python_variable_types.html

Python有五个标准的数据类型：

Numbers（数字）

String（字符串）

List（列表）

Tuple（元组）

Dictionary（字典）

1. Number数值

Python中无需声明变量类型，系统会自动识别，省去了很多烦恼，却也留下了一些陷阱。

变量第一次使用时必须赋值，不能像C语言中先声明而不赋值。

Python中的数值分为：

Python支持四种不同的数字类型（Python3中整数只有int类型，没有long类型）：

int（有符号整型）

long（长整型）

float（浮点型）

complex（复数）

在变量赋值时，Python会根据数值格式自动识别数据类型：

>>> a = 1
>>> b = 1.0
>>> c = 2j
>>> print(type(a),type(b),type(c))
<class 'int'> <class 'float'> <class 'complex'>

多个变量赋值

>>> a = b = c = 1
>>> a,b,c = 1,2,'string'

2. 字符串

Python中的字符串具备一些数组的功能：

>>> a = 'string'

读取字母

>>> a[1]
'r'

字符串切片

>>> a[2:4]
'in'

翻转字符串
>>> p = 'string'
>>> p[::-1]
'gnirts'

字符串拼接

>>> b = 'byte'
>>> a+b
'sringbyte'

使用格式化控制符将字符串格式化
Python中有两种格式化控制符%和{}
>>> print('%sa' % 1)
1a
>>> print('%sa%rb%fc' % (1,1,1))
1a1b1.000000c

上例中的%s为类型码，用于指定参数将以何种形式拼接入字符串，Python中的常用类型码如下：

%s    字符串 (采用str()的显示)

%r    字符串 (采用repr()的显示)

%c    单个字符

%b    二进制整数

%d    十进制整数

%i    十进制整数

%o    八进制整数

%x    十六进制整数

%e    指数 (基底写为e)

%E    指数 (基底写为E)

%f    浮点数

%F    浮点数，与上相同

%g    指数(e)或浮点数 (根据显示长度)

%G    指数(E)或浮点数 (根据显示长度)

format拼接字符串
使用参数位置调用
>>> '{0}{1}'.format('a',2)#0、1指定参数位置
'a2'
>>> '{0}{1}{0}'.format('a',2)
'a2a'
也能通过参数名调用
>>> '{a}{b}'.format(a='c',b='d')
'cd'
使用列表下标调用
>>> l = [1,2,3]
>>> k = [2,2,2]
>>> '{0[1]}{1[1]}{1[2]}'.format(l,k)
'222'

###Python字符串的其他功能

遍历字符串
>>> a = 'a,b,c,d,e,f,g'
>>> for char in a:
...     print(char)
...
a,b,c,d,e,f,g
分割字符串
>>> a = 'abcd-defg-hijk-lmn'
>>> a.split('-')
['abcd', 'defg', 'hijk', 'lmn']

字符串长度
>>> a = 'python'
>>> len(a)
6
字符串大小写转换
>>> a = 'python'
>>> a.upper()
'PYTHON'
>>> b = 'PYTHON'
>>> b.lower()
'python'


##列表
列表（list）是Python中最基本的数据结构之一，以一对方括号中的逗号分隔值的形式出现，如[1,2,3,4,5]。Python中列表最大的特点是其中可以混合存储任意类型的对象：Python中自带的数值、字符串、列表、字典、元组、自定义的类与对象等等。在访问到list中的任意元素时，Python会自动检测该元素的数据类型，所以list比其他编程语言中的数组运算速度更慢。
list的基本操作
以列表a = ['a','a','b','c','d','d','e']为例
访问
>>> print(a[1],a[2])
a b
切片
>>> a[2:6]
['b', 'c', 'd', 'd']
>>> a[:-1]
['a', 'a', 'b', 'c', 'd', 'd']
倒序
>>> a[::-1]
['e', 'd', 'd', 'c', 'b', 'a', 'a']
删除
>>> del a[0]
>>> a
['a', 'b', 'c', 'd', 'd', 'e']
去重
>>> b = set(a)#set()函数会返回一个集合对象
>>> list(b)
['b', 'c', 'd', 'a', 'e']
将list转换为字符串
使用特定字符将a中的每个元素连接起来
>>> ''.join(a)#使用空字符
'abcdde'
>>> '?'.join(a)
'a?b?c?d?d?e'
拼接
Python的list可以像字符串一样直接使用+号连接
>>> a+a
['a', 'b', 'c', 'd', 'd', 'e', 'a', 'b', 'c', 'd', 'd', 'e']
append()是最常用的list方法，用于往list中添加元素
>>> a.append(1)
>>> a
['a', 'b', 'c', 'd', 'd', 'e', 1]
>>> a.append([1,2,3])
>>> a
['a', 'b', 'c', 'd', 'd', 'e', 1, [1, 2, 3]]
如果要将两个list连接起来，除了使用+号，还可以使用extend()
>>> a.extend(a)
>>> a
['a', 'b', 'c', 'd', 'd', 'e', 1, [1, 2, 3], 'a', 'b', 'c', 'd', 'd', 'e', 1, [1, 2, 3]]


其他list方法
> mean()只适用于纯数值列表

max()/min()

sum()

pop()

count()

remove()

reverse()

sort()

insert()

index()






> Python中还提供了一种array数组，array中只允许存储同一种类型的，所以运算速度快于list。

推导式：[i*2 for i in range(1,10)]
推导式是Python中独有的数据生成方式，参考http://www.cnblogs.com/tkqasn/p/5977653.html



##（2）字典


##（3）元组


2. 函数

3. 循环

（1）if

（2）while


4. 模块、类、对象

