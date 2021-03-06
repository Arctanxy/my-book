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
设
>>> a = [1,2,3,4,5,6,7,8]
len()
>>> len(a)
8
max()/min()
>>> max(a)
8
>>> min(a)
1
sum()
>>> sum(a)
36
pop()
用于移除列表中的一个元素，并返回该元素的值
>>> a.pop(1)#参数1为元素的位置
2
>>> a
[1, 3, 4, 5, 6, 7, 8]
count()
统计列表中特定对象的个数
>>> a.count(1)
1
>>> a.count(2)
0
remove()
删除列表中的某个对象
>>> a.remove(1)
>>> a
[3, 4, 5, 6, 7, 8]

reverse()
将列表中的元素反向返回，作用类似于a[::-1]
>>> a
[3, 4, 5, 6, 7, 8]
>>> a.reverse()
>>> a
[8, 7, 6, 5, 4, 3]

sort()
>>> a
[8, 7, 6, 5, 4, 3]
>>> a.sort()
>>> a
[3, 4, 5, 6, 7, 8]

insert()
插入元素
>>> a.insert(2,10)#第一个参数为插入位置，第二个参数为插入对象
>>> a
[3, 4, 10, 5, 6, 7, 8]
index()
找到某个元素在列表中第一次出现的位置
>>> a
[3, 4, 10, 5, 6, 7, 8]
>>> a.index(5)
3





> Python中还提供了一种array数组，array中只允许存储同一种类型的，所以运算速度快于list。

推导式：
推导式是Python中独有的数据生成方式，参考http://www.cnblogs.com/tkqasn/p/5977653.html
列表推导式
列表推导式是最常用的推导式
其使用方法如下：
>>> a = [i*2 for i in range(1,10)]
>>> a
[2, 4, 6, 8, 10, 12, 14, 16, 18]
相当于
>>> a = []
>>> for i in range(1,10):
...     a.append(i*2)
...
>>> a
[2, 4, 6, 8, 10, 12, 14, 16, 18]

字典推导式
>>> dic = {'a':2,'b':3,'c':4}
>>> a = {k.upper():v+1 for k,v in dic.items()}
>>> a
{'B': 4, 'A': 3, 'C': 5}




##（2）字典
字典是一种由成对的键值（Key-Value）组成的数据集合，也被称为关联数组或者哈希表。Python中的字典也可以存储任意类型的对象，如数值、字符串、元素、列表等，但是不能使用字典或者列表作为键（Key），可以使用元组作为键。对于值并没有类型限制，但是要求值必须是不可变的。
一个字典的整体内容由{}包围，不同键值对之间用逗号分隔，键与值之间使用冒号分隔，形式如下：
>>> a = {'a':(1,2,3),('b','c'):[4,5,6],'f':'g'}
以上述字典a为例，讲解字典的基本操作
访问和修改字典中的元素
>>> a['a']#使用键来访问
(1, 2, 3)
如果键不存在会出现Key Error
>>> a['b']
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'b'
对字典元素赋值
>>> a['a']=[1,2,3,4]
>>> a
{'f': 'g', 'a': [1, 2, 3, 4], ('b', 'c'): [4, 5, 6]}
添加元素
>>> a['h']=1
>>> a
{'f': 'g', 'a': [1, 2, 3, 4], ('b', 'c'): [4, 5, 6], 'h': 1}
  
删除字典元素
>>> del a['a']
>>> a
{'f': 'g', ('b', 'c'): [4, 5, 6]}
遍历字典的方法
遍历字典的方式有三种：
（1）遍历键
>>> a={'f': 'g', ('b', 'c'): [4, 5, 6]}
>>> for k in a.keys():
...     print(k)
...
f
('b', 'c')
（2）遍历值
>>> for v in a.values():
...     print(v)
...
g
[4, 5, 6]
（3）同时遍历键值
>>> for k,v in a.items():
...     print(k,v)
...
f g
('b', 'c') [4, 5, 6]
注意：dict.has_key(key)方法只在Python2.x中有效
将两个列表合并为字典
>>> m = [1,2,3,4]
>>> n = ['a','b','c','d']
>>> k = dict(zip(n,m))
>>> k
{'c': 3, 'a': 1, 'd': 4, 'b': 2}

##（3）元组
元组与列表类似，是包含在圆括号中的由逗号分隔的数据集，元组中也可以存放各种类型的元素，只是元组一旦创建之后便不能修改，所以在网络爬虫中，较少使用元组来储存数据。
下面介绍元组的使用方法
创建元组：
>>> t = ()#创建空元组
>>> t
()
>>> t = (1)#创建只有一个元素的元组时，需要在末尾加上逗号，否则相当于一个变量赋值语句
>>> t
1
>>> t = (1,)
>>> t
(1,)
访问元素
访问元组中的元素与数组、字符串等类似，都是通过下标来访问
>>> t = ('a','b','c','d')
>>> t
('a', 'b', 'c', 'd')
>>> t[1]
'b'
元组也能和列表一样进行切片操作
>>> t[1:3]
('b', 'c')
>>> t[:-1]
('a', 'b', 'c')
>>> t[::-1]
('d', 'c', 'b', 'a')
修改元组
前面已经提到，元组是无法修改的，如果对元组元素进行赋值，会发生报错
>>> t[1] = 2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
只能从元组中获取元素，然后再将新元素重新创建为一个新元组，如元组的拼接：
>>> t1 = (2,2,3)
>>> t2 = (3,4,5)
>>> t3 = t1 + t2
>>> t3
(2, 2, 3, 3, 4, 5)
删除元组
元组的删除操作在网络爬虫中应用较少，因为元组中的元素是不可修改的，故只能整体删除元组。
元组中还内置了以下函数：
>>> len(t1)#返回元组长度
3
>>> max(t1)#返回元组中最大值
3
>>> min(t1)#返回元组中最小值
2
>>> tuple([1,2,3])#将列表转换为元组
(1, 2, 3)
  
2. 函数
函数是指预先设定好能实现一定功能，并且能够重复利用的代码段。
Python中的函数为function()形式，上一节中讲到的这种类型的代码如max(),min(),print()等都是函数。
函数包括三大要素，函数名、参数列表、返回对象。
以上一节中求元组中最大值的函数max(t1)为例：
函数名为max
参数为元组t1
返回对象为元组t1中的最大元素3
然而，在Python中，对于函数来讲，这三要素都不是必须的。
函数相关基本概念：
形参
实参
全局变量
局部变量
这一节中将主要介绍如何函数和调用函数。
自定义函数
假设有函数如下：
>>> def func(a,b=1,c=False):
...     if c == False:
...             return a*b
...     else:
...             return a+1
...
此函数中函数名为func，参数中有三个变量a,b,c。其中a未给定默认值，b和c均给定了默认值。返回对象有两个算式，根据C的取值决定返回哪一个算式的运算结果。
调用函数
在这个函数中，a为必备参数，如果调用func()不提供a参数，函数会出现报错：
>>> func()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: func() missing 1 required positional argument: 'a'
在调用函数时，只需给出a即可正常运行，其他参数会自动选择其默认值带入运算。
>>> func(a=1)
1
>>> func(a=1,b=2)
2
>>> func(a=1,c=True)
2
如果传入参数时未给出变量名，函数会自动按照变量顺序将变量值与变量名进行匹配。
>>> func(1,2)
2
>>> func(1,2,True)
2
自定义匿名函数
Python中的匿名函数又称lambda函数，可以快速地实现单行的小函数。简单方便，但是缺点也很明显：只能有一个表达式，没有return语句，表达式即为返回值。
上述函数改为匿名函数的语法如下：
>>> f = lambda a,b=1,c=False:a*b if c==False else a+1
直接调用的方法与普通函数类似：
>>> f(1,2,True)
2
  
3. 条件与循环
（1）if

（2）for

（3）while


4. 模块、类、对象


5. Python代码书写规范
http://www.cnblogs.com/wangcp-2014/p/4608265.html
