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
1. 数值
Python中无需声明变量类型，系统会自动识别，省去了很多烦恼，却也留下了一些陷阱。
变量第一次使用时必须赋值，不能像C语言中先声明而不赋值。
Python中的数值分为：
Python支持四种不同的数字类型：
int（有符号整型）
long（长整型）
float（浮点型）
complex（复数）
在变量赋值时，Python会根据数值格式自动识别数据类型：
a = 1
b = 1.0
c = 0122L
d = 2j
print(type(a),type(b),type(c),type(d))

多个变量赋值
a = b = c = 1
a,b,c = 1,2,'sring'
2. 字符串
Python中的字符串具备一些数组的功能：
a = 'string'
读取字母
print(a[1])
字符串切片
a[2:4]
字符串拼接
b = 'byte'
a + b

打印时拼接
格式化字符串
2. 函数
3. 循环
（1）if
（2）while
4. 数据类型

（1）列表
推导式：[i*2 for i in range(1,10)]
（2）字典
（3）元组
5. 模块、类、对象
6. 读取写入文件
