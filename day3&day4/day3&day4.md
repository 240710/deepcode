# Day3 Study

## python

### 基本语法

####python标识符

1. 在python中，标识符可以由数字，英文，和下划线组成，但是标识符不能以数字开头。

2. 以下划线开头的标识符是有特殊意义的。

   以单下划线开头 **_foo** 的代表不能直接访问的类属性，需通过类提供的接口进行访问，不能用 **from xxx import \*** 而导入。

   以双下划线开头的 **__foo** 代表类的私有成员，以双下划线开头和结尾的 **__foo__** 代表 Python 里特殊方法专用的标识，如 **__init__()** 代表类的构造函数。

3. python是可以同一行显示多行语句的，但是要用；隔开。

~~~python
>>> print ('hello');print ('runoob');
~~~

#### 行与缩进

python的代码块不用大括号来控制类，函数，和逻辑判断。python是使用缩进来控制的。（空格来控制）

其中缩进数量是可变的，但是所有的代码语句必须有相同的缩进量

如

~~~python
if True:
    print ("True")
else:
    print ("False")
~~~

两个打印语句前面都是四个空格。

当没有严格执行相同缩进量的标准时，执行时会报错

~~~python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
# 文件名：test.py

if True:
    print ("Answer")
    print ("True")
else:
    print ("Answer")
    # 没有严格缩进，在执行时会报错
  print ("False")
~~~

会出现一下的错误提醒

~~~python
  File "test.py", line 11
    print ("False")
                  ^
IndentationError: unindent does not match any outer indentation level
~~~

***在编写时尽量使用同一个缩进标准，如单个制表符或两个空格等，避免报错***

#### 多行语句

1. 当我们想要将一行的语句分为多行显示时，需要使用（ \）表示这几行的语句为一行语句。

   ~~~python
   total = item_one + \
           item_two + \
           item_three
   ~~~

   

2. 语句中包含[]，{}，和（）时不需要使用多行连接符

   ~~~python
   days = ['Monday', 'Tuesday', 'Wednesday',
           'Thursday', 'Friday']
   ~~~

   

#### python引号用法

Python 可以使用引号( **'** )、双引号( **"** )、三引号( **'''** 或 **"""** ) 来表示字符串，引号的开始与结束必须是相同类型的。

~~~python
word = 'word'
sentence = "这是一个句子。"
paragraph = """这是一个段落。
包含了多个语句"""
~~~

其中三引号还可以用来做多行注释

~~~python
'''
这是多行注释，使用单引号。
这是多行注释，使用单引号。
这是多行注释，使用单引号。
'''

"""
这是多行注释，使用双引号。
这是多行注释，使用双引号。
这是多行注释，使用双引号。
"""
~~~

#### python空行

函数之间或类的方法之间用空行分隔，表示一段新的代码的开始。类和函数入口之间也用一行空行分隔，以突出函数入口的开始。

####print 输出

print 默认输出是换行的，如果要实现不换行需要在变量末尾加上逗号 **,**。

~~~python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

x="a"
y="b"
# 换行输出
print x
print y

print '---------'
# 不换行输出
print x,
print y,

# 不换行输出
print x,y
~~~

打印效果为

~~~python
a
b
---------
a b a b
~~~

#### 等待用户输入

在以下的语句实现用户输入内容就会显示的程序

~~~python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

raw_input("按下 enter 键退出，其他任意键显示...\n")
~~~

---

### 数据类型

#### 变量赋值

1.在python中变量不需要进行类型声明，但是一定要进行赋值，才能够确定变量的数据类型。

~~~python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
counter = 100 # 赋值整型变量
miles = 1000.0 # 浮点型
name = "John" # 字符串
 
print counter
print miles
print name
~~~

2. python多变量同时赋值

   ~~~python
   a, b, c = 1, 2, "john"
   ~~~

   1，2分别赋给a和b，John则是赋给了c

#### 基本数据类型

在python中有五个基本数据类型

#####Numbers（数字）

数字类型有四种

int型（整形）

long（长整型）

float（浮点型）

complex（复数）

**复数由实数部分和虚数部分构成，可以用 a + bj,或者 complex(a,b) 表示， 复数的实部 a 和虚部 b 都是浮点型。**

#####String（字符串）

python的字串列表有2种取值顺序:

+ 从左到右索引默认0开始的，最大范围是字符串长度少1
+ 从右到左索引默认-1开始的，最大范围是字符串开头

![img](https://www.runoob.com/wp-content/uploads/2013/11/python-string-slice.png)

如果想要实现从字符串中获取一段子字符串的话，可以使用 **[头下标:尾下标]** 来截取相应的字符串，其中下标是从 0 开始算起，可以是正数或负数，下标可以为空表示取到头或尾。

**[头下标:尾下标]** 获取的子字符串包含头下标的字符，但不包含尾下标的字符。

例如

~~~python
>>> s = 'abcdef'
>>> s[1:5]
~~~

从第一个字符取到第四个字符

~~~python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
str = 'Hello World!'
 
print str           # 输出完整字符串
print str[0]        # 输出字符串中的第一个字符
print str[2:5]      # 输出字符串中第三个至第六个之间的字符串
print str[2:]       # 输出从第三个字符开始的字符串
print str * 2       # 输出字符串两次
print str + "TEST"  # 输出连接的字符串
~~~

**其中加号（+）是字符串连接运算符，星号（*）是重复操作。**

---



#####List（列表）

1. 列表用**[ ]**来标识，创建一个列表只需要用逗号将不同的数据分隔开再用[ ]包裹起来即可。

~~~python
list1 = ['physics', 'chemistry', 1997, 2000]
list2 = [1, 2, 3, 4, 5 ]
list3 = ["a", "b", "c", "d"]
~~~

2. 访问列表中的元素

   使用索引来访问，索引的顺序如上面字符串类型的说明，

   ~~~python
   #!/usr/bin/python
    
   list1 = ['physics', 'chemistry', 1997, 2000]
   list2 = [1, 2, 3, 4, 5, 6, 7 ]
    
   print "list1[0]: ", list1[0]
   print "list2[1:5]: ", list2[1:5]
   ~~~

   结果为

   ~~~python
   list1[0]:  physics
   list2[1:5]:  [2, 3, 4, 5]
   ~~~

   3. 列表对+和*的操作符相似

      | Python 表达式                | 结果                         | 描述                 |
      | :--------------------------- | :--------------------------- | :------------------- |
      | len([1, 2, 3])               | 3                            | 长度                 |
      | [1, 2, 3] + [4, 5, 6]        | [1, 2, 3, 4, 5, 6]           | 组合                 |
      | ['Hi!'] * 4                  | ['Hi!', 'Hi!', 'Hi!', 'Hi!'] | 重复                 |
      | 3 in [1, 2, 3]               | True                         | 元素是否存在于列表中 |
      | for x in [1, 2, 3]: print x, | 1 2 3                        | 迭代                 |

---



#####Tuple（元组）

Python的元组与列表类似，**不同之处在于元组的元素不能修改。**

元组使用小括号，列表使用方括号。元组的创建和列表的创建相同

**当元组只包含一个元素时，需要在元素后面添加逗号**

~~~python
tup1 = (50,)
~~~

**元组的访问，修改，运算符，截取操作和列表都一样**

---



#####Dictionary（字典）

字典用"{ }"标识。字典由键值(key)和它对应的值value组成。键值和对应的值用（**：**）隔开，不同的值间用逗号隔开。

~~~python
d = {key1 : value1, key2 : value2 }
~~~

**访问字典里的值**

将想要访问的键放在[ ]里

~~~python
#!/usr/bin/python
 
tinydict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}
 
print "tinydict['Name']: ", tinydict['Name']
print "tinydict['Age']: ", tinydict['Age']
~~~

如果想要在字典里增加新内容，要给字典新增加一个键

~~~python
tinydict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}
tinydict['School'] = "RUNOOB" # 添加

~~~

**字典键的特性**

1. 键一般是唯一的，如果重复最后的一个键值对会替换前面的，值不需要唯一。

2. 键必须不可变，所以可以用数字，字符串或元组充当，但是用列表就不行。

   ---

   

###循环语句

在python中提供了for循环和while循环

##### while循环

基本形式为

~~~python 
while 判断条件(condition)：
    执行语句(statements)……
~~~

注意：**判断条件为任何非零、或非空的值时均为ture**

还可以加上else语句，使得循环条件为false时执行else语句

~~~python
#!/usr/bin/python
 
count = 0
while count < 5:
   print count, " is  less than 5"
   count = count + 1
else:
   print count, " is not less than 5"
~~~

---



##### for循环

形式为

~~~python
for iterating_var in sequence:
   statements(s)
~~~

iterating_var（迭代元素，设置的一个变量来进行迭代操作）

 sequence（任何序列的项目，如列表，元组）

statements(s)（操作的语句）

**示例**

~~~python
fruits = ["apple", "banana", "cherry"]
for x in fruits:
  print(x)
~~~

**当我们需要循环一组代码指定的次数，可以使用 range() 函数**

range() 函数返回一个数字序列，默认情况下从 0 开始，并递增 1（默认地）

~~~python
for x in range(10):
  print(x)
~~~

结果是0，1，2，3，4，5，6，7，8，9

**for循环也可以加上else语句使用**

---



###函数

####定义一个函数

函数代码块以 **def** 关键词开头，后接函数标识符名称和圆括号**()**。

任何传入参数和自变量必须放在圆括号中间。圆括号之间可以用于定义参数。

函数的第一行语句可以选择性地使用文档字符串—用于存放函数说明。

函数内容以冒号起始，并且缩进。

**return [表达式]** 结束函数，选择性地返回一个值给调用方。不带表达式的return相当于返回 None

~~~python
def functionname( parameters ):
   "函数_文档字符串"
   function_suite
   return [expression]
~~~

**示例**

~~~python
def printme( str ):
   "打印传入的字符串到标准显示设备上"
   print str
   return
~~~

####函数的调用

函数可以通过另一个函数调用或直接通过**函数名（）**调用

~~~python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
# 定义函数
def printme( str ):
   "打印任何传入的字符串"
   print str
   return
 
# 调用函数
printme("我要调用用户自定义函数!")
printme("再次调用同一函数")
~~~

####参数传递

在python中string，number，tuple为不可修改的对象，list和dictionary时可修改的对象。

1. 不可变类型

   传递的只是a的值，没有影响a对象本身。比如在 fun（a）内部修改 a 的值，只是修改另一个复制的对象，不会影响 a 本身。

   ~~~python
   #!/usr/bin/python
   # -*- coding: UTF-8 -*-
    
   def ChangeInt( a ):
       a = 10
    
   b = 2
   ChangeInt(b)
   print b # 结果是 2
   ~~~

   

2. 可变类型

   如 fun（la），则是将 la 真正的传过去，修改后fun外部的la也会受影响

   ~~~python
   #!/usr/bin/python
   # -*- coding: UTF-8 -*-
    
   # 可写函数说明
   def changeme( mylist ):
      "修改传入的列表"
      mylist.append([1,2,3,4])
      print "函数内取值: ", mylist
      return
    
   # 调用changeme函数
   mylist = [10,20,30]
   changeme( mylist )
   print "函数外取值: ", mylist
   ~~~

   

#### 参数

+ 必备参数

  当函数中有参数，调用函数也要输入一个参数**且数量和声明时一样**，不然会报错

+ 关键字参数

  使用关键字参数允许函数调用时参数的顺序与声明时不一致，如

  ~~~python
  #!/usr/bin/python
  # -*- coding: UTF-8 -*-
   
  #可写函数说明
  def printme( str ):
     "打印任何传入的字符串"
     print str
     return
   
  #调用printme函数
  printme( str = "My string")
  ~~~

  

+ 默认参数

  当我们在定义函数时给定义了一个参数，并且给参数赋了值，那么当我们调用函数时，如果不给参数重新赋值，就会默认使用定义时的参数值

  ~~~python
  #!/usr/bin/python
  # -*- coding: UTF-8 -*-
   
  #可写函数说明
  def printinfo( name, age = 35 ):
     "打印任何传入的字符串"
     print "Name: ", name
     print "Age ", age
     return
   
  #调用printinfo函数
  printinfo( age=50, name="miki" )
  printinfo( name="miki" )
  ~~~

  结果为

  ~~~
  Name:  miki
  Age  50
  Name:  miki
  Age  35
  ~~~

  

+ **不定长参数**

+ 我们可能需要一个函数能处理比当初声明时更多的参数。这样的参数就叫做不定长参数，和上述2种参数不同，声明时不会命名。基本语法如下

~~~python
def functionname([formal_args,]
*var_args_tuple ):
   "函数_文档字符串"
   function_suite
   return [expression]
~~~

示例

~~~python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
def printinfo( arg1, *vartuple ):
   "打印任何传入的参数"
   print "输出: "
   print arg1
   for var in vartuple:
      print var
   return
 
# 调用printinfo 函数
printinfo( 10 )
printinfo( 70, 60, 50 )
~~~

**~*vartuple~**是一个可以存放所有未定义但是输入了的参数的不定参数 ，arg1就只是一个常规的参数变量。

结果为：

~~~
输出:
10
输出:
70
60
50
~~~

#### 匿名函数

**python 使用 lambda 来创建匿名函数。**

语法

~~~python
lambda [arg1 [,arg2,.....argn]]:expression
~~~

[arg1 [,arg2,.....argn]]是变量，expression是执行语句**中间用冒号：隔开**

示例

~~~python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
# 可写函数说明
sum = lambda arg1, arg2: arg1 + arg2
 
# 调用sum函数
print "相加后的值为 : ", sum( 10, 20 )
print "相加后的值为 : ", sum( 20, 20 )
~~~

**优点**

1. 减少重复代码；

2. 模块化代码。

#### 变量作用域

一个程序的所有的变量并不是在哪个位置都可以访问的。访问权限决定于这个变量是在哪里赋值的。

变量的作用域决定了在哪一部分程序你可以访问哪个特定的变量名称。两种最基本的变量作用域如下：

+ 局部变量

  定义在函数内部的变量拥有一个局部作用域

  局部变量只能在其被声明的函数内部访问

+ 全局变量

  定义在函数外的变量拥有全局作用域。

  全局变量可以在整个程序范围内访问

~~~python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
total = 0 # 这是一个全局变量
# 可写函数说明
def sum( arg1, arg2 ):
   #返回2个参数的和."
   total = arg1 + arg2 # total在这里是局部变量.
   print "函数内是局部变量 : ", total
   return total
 
#调用sum函数
sum( 10, 20 )
print "函数外是全局变量 : ", total
~~~

结果为

~~~
函数内是局部变量 :  30
函数外是全局变量 :  0
~~~

**在函数内无法直接使用全局变量。全局变量想作用于函数内，需加 global**

~~~python
 global globvar    # 使用 global 声明全局变量
~~~

### 模块

Python 模块(Module)，是一个 Python 文件，以 .py 结尾

模块让你能够有逻辑地组织你的 Python 代码段。

把相关的代码分配到一个模块里能让你的代码更好用，更易懂。

模块能定义函数，类和变量，模块里也能包含可执行的代码。

#### 模块的引入

引入模块要在脚本的顶端引入

+ import语句

模块定义好后，我们可以使用 import 语句来引入模块，语法如下：

~~~python
import module1[, module2[,... moduleN]]
~~~

+ from……import*语句

把一个模块的所有内容全都导入到当前的命名空间也是可行的，只需使用如下声明：

~~~python
from modname import *
~~~

#### 模块中函数的调用

**模块名.函数名**

#### dir()函数

dir（）函数可以用来查看一个模块里面定义的所有变量，函数，如

~~~python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
# 导入内置math模块
import math
 
content = dir(math)
 
print content;
~~~

结果

~~~python
['__doc__', '__file__', '__name__', 'acos', 'asin', 'atan', 
'atan2', 'ceil', 'cos', 'cosh', 'degrees', 'e', 'exp', 
'fabs', 'floor', 'fmod', 'frexp', 'hypot', 'ldexp', 'log',
'log10', 'modf', 'pi', 'pow', 'radians', 'sin', 'sinh', 
'sqrt', 'tan', 'tanh']
~~~



#### globals（）和locals（）函数

根据调用地方的不同，globals() 和 locals() 函数可被用来返回全局和局部命名空间里的名字。

如果在函数内部调用 locals()，返回的是所有能在该函数里访问的命名。

如果在函数内部调用 globals()，返回的是所有在该函数里能访问的全局名字。

两个函数的返回类型都是字典。所以名字们能用 keys() 函数摘取。

#### reload（）函数

当一个模块被导入到一个脚本，模块顶层部分的代码只会被执行一次。

因此，如果你想重新执行模块里顶层部分的代码，可以用 reload() 函数。该函数会重新导入之前导入过的模块。语法如下：

~~~python
reload(module_name)
~~~

---



##数学

### 矩阵

#### 定义

像

 ![[公式]](https://www.zhihu.com/equation?tex=%5Cleft%5C%7B+%5Cbegin%7Baligned%7Dx_1%2B3x_2%2Bx_3%26%3D2%26%E2%91%A0%5Cspace%5C%5C+3x_1%2B4x_2%2B2x_3%26%3D9%26%E2%91%A1%5Cspace%5C%5C+-x_1-5x_2%2B4x_3%26%3D10%26%E2%91%A2%5Cspace%5C%5C+2x_1%2B7x_2+%2Bx_3%26%3D1+%26%E2%91%A3%5Cspace%5Cend%7Baligned%7D+%5Cright.)

这样的n元线性方程组把其未知数的系数和常系数按原来的相对位置可以排成一个**矩形数表**：

![[公式]](https://www.zhihu.com/equation?tex=%5Cbegin%7Bpmatrix%7D+1%263%261%262%5C%5C+3%264%262%269%5C%5C+-1%26-5%264%2610%5C%5C+2%267%263%261+%5Cend%7Bpmatrix%7D)

这个数表就是一个矩阵

矩阵Om×n表示矩阵有m行n列

**当两个矩形的行数和列数都相等则称他们为同型矩阵，而相等则是元素都相等**

---

#### 阶数

矩阵的阶数指的是它的行数和列数

如m*n阶矩阵就是指这个矩阵有m行n列

若m与n相等，则这个矩阵就是方阵，m阶的方阵

阶数判断：

1、m行n列矩阵的阶数：“m*n阶”

2、n行m列矩阵的阶数：“n*m阶”

3、m行m列矩阵的阶数：“n*n阶”，简称“n阶”方阵

---

#### 单位矩阵

它是个方阵，从左上角到右下角的对角线（称为主对角线）上的元素均为1。除此以外全都为0。

![单位矩阵](https://bkimg.cdn.bcebos.com/pic/6d81800a19d8bc3eb135d5fa2cc4b11ea8d3fd1feff9?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_jpg)

---



#### 运算

矩阵的**加减，减法，数乘**合称为矩阵的线性运算

**加法：**

**只有同型矩阵之间才可以进行加法运算**，将两个矩阵相同位置的元相加即可，m行n列的两个矩阵相加后得到一个新的m行n列矩阵，例如：

![[公式]](https://www.zhihu.com/equation?tex=%5Cbegin%7Bbmatrix%7D+1+%26+3+%26+5+%26+7+%5C%5C+2+%26+4+%26+6+%26+8+%5Cend%7Bbmatrix%7D+%2B+%5Cbegin%7Bbmatrix%7D+4+%26+3+%26+1+%26+4+%5C%5C+5+%26+3+%26+1+%26+6+%5Cend%7Bbmatrix%7D+%3D+%5Cbegin%7Bbmatrix%7D+5+%26+6+%26+6+%26+11+%5C%5C+7+%26+7+%26+7+%26+14+%5Cend%7Bbmatrix%7D)

**减法与加法相同。**

---



**数乘**：

将矩阵乘以一个常量，矩阵中的每个元都与这个常量相乘，例如：

![[公式]](https://www.zhihu.com/equation?tex=k+%2A+%5Cbegin%7Bbmatrix%7D+a_%7B11%7D+%26+a_%7B12%7D+%26+...+%26a_%7B1n%7D+%5C%5C+a_%7B21%7D+%26+a_%7B22%7D+%26+...+%26a_%7B2n%7D+%5C%5C+...+%26+...+%26+...+%26...+%5C%5C+a_%7Bm1%7D+%26+a_%7Bm2%7D+%26+...+%26a_%7Bmn%7D+%5Cend%7Bbmatrix%7D+%3D+%5Cbegin%7Bbmatrix%7D+k+%2A+a_%7B11%7D+%26+k+%2A+a_%7B12%7D+%26+...+%26k+%2A+a_%7B1n%7D+%5C%5Ck+%2A+a_%7B21%7D+%26+k+%2A+a_%7B22%7D+%26+...+%26k+%2A+a_%7B2n%7D+%5C%5C+...+%26+...+%26+...+%26...+%5C%5C+k+%2A+a_%7Bm1%7D+%26+k+%2A+a_%7Bm2%7D+%26+...+%26k+%2A+a_%7Bmn%7D+%5Cend%7Bbmatrix%7D)

![[公式]](https://www.zhihu.com/equation?tex=5%2A%5Cbegin%7Bbmatrix%7D+4+%26+3+%26+-1+%26+4+%5C%5C+5+%26+-3+%26+1+%26+6+%5Cend%7Bbmatrix%7D+%3D+%5Cbegin%7Bbmatrix%7D+20+%26+15+%26+-5+%26+20+%5C%5C+25+%26+-15+%26+5+%26+30+%5Cend%7Bbmatrix%7D)

矩阵的运算和向量的一致（向量就是一种特殊的矩阵）

---



**乘法**:

**只有当第一个矩阵的列数和另一个矩阵的行数相等时才能进行相乘**

*m*×*n* 矩阵 ![[公式]](https://www.zhihu.com/equation?tex=%5Cmathbf%7BA%7D) 和 *n*×*p* 矩阵 ![[公式]](https://www.zhihu.com/equation?tex=%5Cmathbf%7BB%7D) 相乘，会得到一个 *m*×*p* 矩阵 ![[公式]](https://www.zhihu.com/equation?tex=%5Cmathbf%7BC%7D) ，记为 ![[公式]](https://www.zhihu.com/equation?tex=%5Cmathbf%7BC%7D+%3D+%5Cmathbf%7BA%7D%5Cmathbf%7BB%7D) 。

例如：

![[公式]](https://www.zhihu.com/equation?tex=%5Cbegin%7Bbmatrix%7D+1+%26+3+%26+5+%5C%5C+2+%26+4+%26+6+%5Cend%7Bbmatrix%7D+%2A+%5Cbegin%7Bbmatrix%7D+7+%26+9+%5C%5C+8+%26+0+%5C%5C+-1+%26+1+%5Cend%7Bbmatrix%7D+%3D+%5Cbegin%7Bbmatrix%7D+1%2A7%2B3%2A8%2B5%2A-1+%26+1%2A9%2B3%2A0%2B5%2A1+%5C%5C+2%2A7%2B4%2A8%2B6%2A-1+%26+2%2A9%2B4%2A0%2B6%2A1+%5Cend%7Bbmatrix%7D+%3D+%5Cbegin%7Bbmatrix%7D+26+%26+14+%5C%5C+40+%26+24+%5Cend%7Bbmatrix%7D)

上式中2乘3的矩阵A和3乘2的矩阵B像乘后就变成了2乘2的矩阵C

结果中的第一行第二列，就是前者的第一行1,3,5和后者的第二列9,0,1互相相乘然后相加。类似的就是矩阵的乘法运算

#### 矩阵和向量相乘

向量用矩阵表示的话，是属于一个n*1的矩阵，例如二维向量为 ![[公式]](https://www.zhihu.com/equation?tex=%5Cbegin%7Bbmatrix%7D+x%5C%5C+y+%5Cend%7Bbmatrix%7D) ，三维向量为 ![[公式]](https://www.zhihu.com/equation?tex=%5Cbegin%7Bbmatrix%7D+x%5C%5C+y%5C%5C+z+%5Cend%7Bbmatrix%7D)因此一个 m * 2 的矩阵可以乘以一个二维向量，m * 3 的矩阵可以乘以一个三维向量。而相乘的运算和矩阵的相乘运算相同。



---

#### 转置

像把矩阵 ![[公式]](https://www.zhihu.com/equation?tex=A) 的行和列互相交换所产生的矩阵称为A的转置矩阵（标记为 ![[公式]](https://www.zhihu.com/equation?tex=A%5ET) )，这一过程称为矩阵的转置。

![[公式]](https://www.zhihu.com/equation?tex=%5Cbegin%7Bbmatrix%7D+a_%7B11%7D+%26+a_%7B12%7D+%26+...+%26a_%7B1n%7D+%5C%5C+a_%7B21%7D+%26+a_%7B22%7D+%26+...+%26a_%7B2n%7D+%5C%5C+...+%26+...+%26+...+%26...+%5C%5C+a_%7Bm1%7D+%26+a_%7Bm2%7D+%26+...+%26a_%7Bmn%7D+%5Cend%7Bbmatrix%7D%5E%7BT%7D+%3D+%5Cbegin%7Bbmatrix%7D+a_%7B11%7D+%26+a_%7B21%7D+%26+...+%26a_%7Bm1%7D+%5C%5C+a_%7B12%7D+%26+a_%7B22%7D+%26+...+%26a_%7Bm2%7D+%5C%5C+...+%26+...+%26+...+%26...+%5C%5C+a_%7B1n%7D+%26+a_%7B2n%7D+%26+...+%26a_%7Bmn%7D+%5Cend%7Bbmatrix%7D)

![[公式]](https://www.zhihu.com/equation?tex=%5Cbegin%7Bbmatrix%7D+1+%26+3+%26+5+%26+7+%5C%5C+2+%26+4+%26+6+%26+8+%5Cend%7Bbmatrix%7D%5E%7BT%7D+%3D+%5Cbegin%7Bbmatrix%7D+1+%26+2+%5C%5C+3+%26+4%5C%5C+5+%26+6%5C%5C+7+%26+8+%5Cend%7Bbmatrix%7D)

---

#### 方阵的行列式

方阵是行数与列数相等的矩阵

由阶方阵**A所有元素按各元素的位置不变构成的**

行列式**,** 称为**方阵A的行列式,** 记作 |A| 或 det(**A).** 

---

#### 矩阵的秩

k阶子式：

![img](https://pic2.zhimg.com/80/v2-5a03ab5583977dca1d81a90bfe37edc9_1440w.png)

用一个动图来表示二阶子式

![img](https://pic4.zhimg.com/v2-70dd6969541d34c4d63840f2c143e59b_b.webp)

**注意：k阶子阶是一个行列式**

定义

![img](https://pic3.zhimg.com/80/v2-cd3e7c44e296290500ebdd086f245912_1440w.png)

意思**就是非零子式的最高阶数就是秩**

---

#### 矩阵的特征值与特征向量

**定义**

假设我们有一个n阶的矩阵A以及一个实数![[公式]](https://www.zhihu.com/equation?tex=%5Clambda)，使得我们可以找到一个非零向量x，满足：

![[公式]](https://www.zhihu.com/equation?tex=Ax%3D%5Clambda+x+%5C%5C)

如果能够找到的话，我们就称![[公式]](https://www.zhihu.com/equation?tex=%5Clambda)是矩阵A的特征值，非零向量x是矩阵A的特征向量。

---

#### 协方差

一般情况下我们会用标准差和方差，用来处理统计数据，但是标准差和方差一般是用来描述一维数据的，现实生活我们常常遇到含有多维数据的数据集，这个时候就该使用到协方差了。

  **协方差可以通俗的理解为：两个变量在变化过程中是同方向变化？还是反方向变化？同向或反向程度如何？**

+ 你变大，同时我也变大，说明两个变量是同向变化的，这时协方差就是正的。

+ 你变大，同时我变小，说明两个变量是反向变化的，这时协方差就是负的。

  从数值来看，协方差的数值越大，两个变量同向程度也就越大。反之亦然。

  协方差矩阵，就只是将所有变量的协方差关系用矩阵的形式表现出来而已。通过矩阵这一工具，可以更方便地进行数学运算。

  **求解协方差矩阵的步骤**
  举个例子，矩阵 X 按行排列：

  ![img](http://latex.codecogs.com/gif.latex?X%20=%20%5Cbegin%7Bbmatrix%7D1%20&2%20%20&3%20%5C%5C%20%203&1%20%20&1%20%5Cend%7Bbmatrix%7D=%5Cbegin%7Bbmatrix%7Dc_1%20&c_2%20%20&%20c_3%5Cend%7Bbmatrix%7D)

  1. 求每个维度的平均值

  ![img](http://latex.codecogs.com/gif.latex?%5Cbar%7Bc%7D%20=%5Cbegin%7Bbmatrix%7D2%20&1.5%20%20&2%20%5Cend%7Bbmatrix%7D=%20%5Cbegin%7Bbmatrix%7D%5Cbar%7Bc_1%7D%20&%5Cbar%7Bc_2%7D%20%20&%5Cbar%7Bc_3%7D%20%5Cend%7Bbmatrix%7D)

  2. 将 X 的每一列减去平均值

  ![img](http://latex.codecogs.com/gif.latex?X=%5Cbegin%7Bbmatrix%7D-1%20&0.5%20%20&1%20%5C%5C%201%20&%20-0.5%20&-1%20%5Cend%7Bbmatrix%7D)

  其中：

  ![img](http://latex.codecogs.com/gif.latex?c_i=c_i-%5Cbar%7Bc_i%7D)

  协方差矩阵为

  ![img](http://latex.codecogs.com/gif.latex?cov%20=%5Cfrac%7B1%7D%7Bm-1%7DX%5E%7BT%7DX=%5Cfrac%7B1%7D%7B2-1%7D%20%5Cbegin%7Bbmatrix%7D%202&%20-1%20&%20-2%5C%5C%20-1%20&0.5%20%20&1%20%5C%5C%20%20-2&1%20%20&2%20%5Cend%7Bbmatrix%7D)

  由以上的解法推及到其他的协方差矩阵

  

---

### 可逆矩阵

####定义

对于![[公式]](https://www.zhihu.com/equation?tex=n)阶矩阵![[公式]](https://www.zhihu.com/equation?tex=%5Cmathbf+A)，如果有一个![[公式]](https://www.zhihu.com/equation?tex=n)阶矩阵![[公式]](https://www.zhihu.com/equation?tex=%5Cmathbf+B)，使
![[公式]](https://www.zhihu.com/equation?tex=%5Cmathbf%7BAB%7D%3D%5Cmathbf%7BBA%7D%3D%5Cmathbf+E+%5C%5C) 其中E为单位矩阵，则说矩阵![[公式]](https://www.zhihu.com/equation?tex=%5Cmathbf+A)是**可逆**的，并把矩阵![[公式]](https://www.zhihu.com/equation?tex=%5Cmathbf+B)称为![[公式]](https://www.zhihu.com/equation?tex=%5Cmathbf+A)的**逆矩阵。**

如果矩阵**A是可逆的,** 那么**A的逆矩阵是唯一的.**记为A的-1次方

#### 性质

1. A的逆矩阵的逆矩阵还是A。
2. 可逆矩阵A的转置矩阵AT可逆，并且（AT）-1=（A-1）T 。
3. 两个可逆矩阵乘积依然是可逆的。

---

###矩阵的求逆

#### 待定系数法

矩阵A=
1, 2
-1,-3
假设所求的逆矩阵为
a,b
c,d
则
![这里写图片描述](https://img-blog.csdn.net/20180808105805480?)
从而可以得出方程组
a + 2c = 1
b + 2d = 0
-a - 3c = 0
-b - 3d = 1
解得
a=3; b=2; c= -1; d= -1

---



### 线性方程组

线性方程组Ax=B

当B=0时称为齐次线性方程组，不等于0时为非齐次线性方程组

#### 用行初等变换求解线性方程组

解线性方程组**相当于用行初等变换化简增广矩阵。**

**行初等变换**

| ![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/tab/tab1.jpg) |                                                              | ![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/tab/tab4.jpg) |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/tab/tab4-2.jpg) | **定义：**下述三种变换统称为矩阵的初等行变换． 　　(1)换法变换：对换矩阵的两行．对换 ![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/0603/image032.gif)两行，记作![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/0603/image033.gif)． 　　(2)倍法变换：用非零数乘矩阵某一行的每个元素．第![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/0603/image016.gif)行乘![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/0603/image034.gif)，记作![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/0603/image035.gif)． 　　(3)消法变换：用数乘矩阵某一行的每个元素后加到另一行的对应元素上．第![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/0603/image017.gif)行的![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/0603/image034.gif)倍加到第![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/0603/image016.gif)行上，记作![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/0603/image036.gif)． | ![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/tab/tab5.jpg) |
| ![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/tab/tab8.jpg) | ![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/tab/tab9.jpg) | ![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/tab/tab11.jpg) |

解法：

将原矩阵通过行初等变换化为行阶梯形矩阵型来求解

**例如**　设三元线性方程组为![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/0603/image052.gif)　　其增广矩阵为![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/0603/image005.gif)，　　试将此增广矩阵化为行最简形．　
　　**解**　![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/0603/image053.gif)

　　　　　　　　　　　　 ![img](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/images/0603/image056.gif)

　　　　　　　　　　　　　

---



### 常见的距离

####**欧式距离**

欧氏距离也称欧几里得距离或欧几里得度量，**是一个通常采用的距离定义，它是在m维空间中两个点之间的真实距离。**在二维和三维空间中的欧氏距离的就是两点之间的距离。

**二维空间的公式**

　　![\rho=\sqrt{\left(x_2-x_1\right)^2+\left(y_2-y_1\right)^2}](https://wiki.mbalib.com/w/images/math/d/2/4/d249fd353a924b3f70bb7fc921e4366d.png)，![\left|X\right|=\sqrt{x_2^2+y_2^2}](https://wiki.mbalib.com/w/images/math/b/0/c/b0ca8970beb28bf7bfe37bdbe3785aed.png)。其中，ρ为点![\left(x_2,y_2\right)](https://wiki.mbalib.com/w/images/math/8/1/e/81e3261a84683e1ffc2e9ffd42c305fb.png)与点![\left(x_1,y_1\right)](https://wiki.mbalib.com/w/images/math/0/4/3/043489d7738fc08b5b85e3ab0fb7dbd1.png)之间的欧氏距离；![\left|X\right|](https://wiki.mbalib.com/w/images/math/2/a/a/2aa636102e6144b6c287672ec23d3f91.png)为点![\left(x_2,y_2\right)](https://wiki.mbalib.com/w/images/math/8/1/e/81e3261a84683e1ffc2e9ffd42c305fb.png)到原点的欧氏距离。 　　

**三维空间的公式**

　　![\rho=\sqrt{\left(x_2-x_1\right)^2+\left(y_2-y_1\right)^2+\left(z_2-z_1\right)^2}](https://wiki.mbalib.com/w/images/math/b/2/5/b25047912f63203ff50e3afc9f1a786e.png)

　　![\left|X\right|=\sqrt{x_2^2+y_2^2+z_2^2}](https://wiki.mbalib.com/w/images/math/d/7/3/d734d3dfd5f555fe4a25c6454dbbcebf.png) 　　

**n维空间的公式**

　　![d(x,y):=\sqrt{(x_1-y_1)^2+(x_2-y_2)^2+\cdots+(x_n-y_n)^2}=\sqrt{\sum_{i=1}^n(x_i-y_i)^2}](https://wiki.mbalib.com/w/images/math/f/d/6/fd67b246c3f6b5478664deb9a8413f5b.png) 　　

####**闵氏距离**

闵氏距离不是一种距离，而是一组距离的定义，是对多个距离度量公式的概括性的表述。

+ 闵氏距离定义：
+ 两个n维变量a(x11,x12,…,x1n)与b(x21,x22,…,x2n)间的闵可夫斯基距离定义为：

![闵式距离n维](https://static.oschina.net/uploads/img/201611/14200244_FCpG.png)

其中p是一个变参数：

当p=1时，就是曼哈顿距离；

当p=2时，就是欧氏距离；

当p→∞时，就是切比雪夫距离。

因此，根据变参数的不同，闵氏距离可以表示某一类/种的距离。

**闵氏距离**就是一个对曼哈顿距离，欧式距离，切比雪夫距离的一个概括，并用公式来给这三种距离一个变化的公式，当其中变量为特殊的值时，为三种距离中的一种

####**余弦值相似度**

余弦距离，也称为余弦相似度，是用向量空间中两个向量夹角的余弦值作为衡量两个个体间差异的大小的度量。

余弦值越接近1，就表明夹角越接近0度，也就是两个向量越相似，这就叫"余弦相似性"。

![img](https://img-blog.csdn.net/20131111174457453)

上图两个向量a,b的夹角很小可以说a向量和b向量有很高的的相似性，极端情况下，a和b向量完全重合。如下图：

![img](https://img-blog.csdn.net/20131111174725421)

如上图二：可以认为a和b向量是相等的，也即a，b向量代表的文本是完全相似的，或者说是相等的。如果a和b向量夹角较大，或者反方向。如下图

![img](https://img-blog.csdn.net/20131111174803906)

如上图三: 两个向量a,b的夹角很大可以说a向量和b向量有很低的的相似性，或者说a和b向量代表的文本基本不相似

但是上述的三个图都只是对于图片的描述；我们要将其推广到所有数据中

![img](https://img-blog.csdn.net/20131111175458906)

当数据是n维的

![img](https://img-blog.csdn.net/20131111175544093)

在我们进行现实数据分析时，可以将文字数据转换成一个个向量的形式并带入公式，计算余弦值相似度中心化

**句子A：这只皮靴号码大了。那只号码合适**

***句子B*：这只皮靴号码不小，那只更合适**

怎样计算上面两句话的相似程度？

基本思路是：如果这两句话的用词越相似，它们的内容就应该越相似。因此，可以从词频入手，计算它们的相似程度。

第一步，分词**。**

**句子A：这只/皮靴/号码/大了。那只/号码/合适。**

**句子B：这只/皮靴/号码/不/小，那只/更/合适。**

第二步，列出所有的词。

**这只，皮靴，号码，大了。那只，合适，不，小，很**

第三步，计算词频。

**句子A：这只1，皮靴1，号码2，大了1。那只1，合适1，不0，小0，更0**

**句子B：这只1，皮靴1，号码1，大了0。那只1，合适1，不1，小1，更1**

第四步，写出词频向量。

　　**句子A：(1，1，2，1，1，1，0，0，0)**

　　**句子B：(1，1，1，0，1，1，1，1，1)**

到这里，问题就变成了如何计算这两个向量的相似程度。我们可以把它们想象成空间中的两条线段，都是从原点（[0, 0, ...]）出发，指向不同的方向。两条线段之间形成一个夹角，如果夹角为0度，意味着方向相同、线段重合,这是表示两个向量代表的文本完全相等；如果夹角为90度，意味着形成直角，方向完全不相似；如果夹角为180度，意味着方向正好相反。因此，我们可以通过夹角的大小，来判断向量的相似程度。夹角越小，就代表越相似。

**使用上面的公式(4)**

![img](https://img-blog.csdn.net/20131111190818687) 

计算两个句子向量

**句子A：(1，1，2，1，1，1，0，0，0)**

**和句子B：(1，1，1，0，1，1，1，1，1)的向量余弦值来确定两个句子的相似度。**

**计算过程如下：**

![img](https://img-blog.csdn.net/20131111190905937)

####**Min-Max标准化**

**数据的标准化:**

将数据按比例缩放，使之落入一个小的特定区间，一般目的在于：去除数据的单位限制，转化为无量纲的纯数值，便于不同单位或量级的指标能够进行比较和加权。

**Min-Max标准化**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200114123120129.png)
Min-Max标准化是指对原始数据进行线性变换，将值映射到[0，1]之间

1. 其中max为样本数据的最大值，min为样本数据的最小值。
2. 这种方法有一个缺陷就是当有新数据加入时，可能导致max和min的变化，需要重新定义

####**Box-Cox转换**

 由于线性回归是基于正态分布的前提假设，所以对其进行统计分析时，需经过数据的转换，使得数据符合正态分布。

而Box-Cox转换就是一个将因变量进行变换，使其符合正态分布

数学公式
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210322171433183.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NoZW5oZXBn,size_16,color_FFFFFF,t_70)



---

### 统计知识

####**t检验**

t检验，又称为student t检验，主要用于样本含量较小（例如n < 30），总体标准差σ未知的正态分布。

1.单样本T检验

用于比较一组数据与一个特定数值之间的差异情况。

2.配对样本的T检验

用于检验有一定对应关系的样本之间的差异情况，需要两组样本数相等。

常见的使用场景有：

①同一对象处理前后的对比（同一组人员采用同一种减肥方法前后的效果对比）；

②同一对象采用两种方法检验的结果的对比（同一组人员分别服用两种减肥药后的效果对比）；

③配对的两个对象分别接受两种处理后的结果对比（两组人员，按照体重进行配对，服用不同的减肥药，对比服药后的两组人员的体重）。

3.独立样本的T检验

独立样本与配对样本的不同之处在于独立样本T检验两组数据的样本个数可以不等。

####**f检验**

样本[标准偏差](https://baike.baidu.com/item/标准偏差)的平方，即：

S的平方=∑(![img](https://bkimg.cdn.bcebos.com/formula/4675185d7b4028ecceae6b1456352cd4.svg)\-![img](https://bkimg.cdn.bcebos.com/formula/d2915a8862acfd688a64650caee8f2e7.svg))的平方/(n-1)

两组数据就能得到两个S的平方值

F=S的平方/S的平方'

然后计算的F值与查表得到的F表值比较，如果

F < F表 表明两组数据没有显著差异；

F ≥ F表 表明两组数据存在显著差异。

####**正态检验**

**正态检验主要用于检验一个数据集是否服从正态分布**

1. 从描述性统计方法的角度来说，要检验数据是否服从正态分布，可以计算“数据分布”和“标准正态分布模型”之间的拟合优度，若拟合性较差，即认为数据不服从正态分布；

2. 从概率统计方面，即假设检验的角度来说，数据是否服从正态分布可以通过与“数据服从正态分布”这样一个零假设进行假设检验计算，构建相关统计量来计算出检验结果；

3. 从贝叶斯统计的角度来说，该方法本身并不检验其正态性，而是计算这批数据来自于服从μ、σ正态分布总体的可能性更大，还是来自于其他分布总体的可能性更大。

####**卡方检验**

+ 卡方分布

卡方分布是一种连续概率分布。
 如果一个随机变量![Z](https://math.jianshu.com/math?formula=Z)服从标准正态分布，即![Z\sim N(0,1)](https://math.jianshu.com/math?formula=Z%5Csim%20N(0%2C1))，那么![Z^2](https://math.jianshu.com/math?formula=Z%5E2)就服从自由度为1的卡方分布。记作![Z^2 \sim \chi^2_1](https://math.jianshu.com/math?formula=Z%5E2%20%5Csim%20%5Cchi%5E2_1) 或者 ![Z^2 \sim \chi^2(1)](https://math.jianshu.com/math?formula=Z%5E2%20%5Csim%20%5Cchi%5E2(1))
 而如果![Z_1,Z_2,\cdots , Z_k](https://math.jianshu.com/math?formula=Z_1%2CZ_2%2C%5Ccdots%20%2C%20Z_k)都服从标准正态分布，那么它们的平方和服从自由度为![k](https://math.jianshu.com/math?formula=k)的卡方分布，记作：
 ![Z_1^2+Z_2^2+\cdots +Z_k^2 \sim \chi^2_k](https://math.jianshu.com/math?formula=Z_1%5E2%2BZ_2%5E2%2B%5Ccdots%20%2BZ_k%5E2%20%5Csim%20%5Cchi%5E2_k)
 或者写作![Z_1^2+Z_2^2+\cdots +Z_k^2 \sim \chi^2(k)](https://math.jianshu.com/math?formula=Z_1%5E2%2BZ_2%5E2%2B%5Ccdots%20%2BZ_k%5E2%20%5Csim%20%5Cchi%5E2(k))。
 对于非负自变量![x](https://math.jianshu.com/math?formula=x)的自由度为![k](https://math.jianshu.com/math?formula=k)的卡方分布的概率密度函数 (简称"pdf")：
 ![f(x)=\dfrac{x^{k/2-1}e^{-x/2}}{2^{k/2}\Gamma(k/2)}](https://math.jianshu.com/math?formula=f(x)%3D%5Cdfrac%7Bx%5E%7Bk%2F2-1%7De%5E%7B-x%2F2%7D%7D%7B2%5E%7Bk%2F2%7D%5CGamma(k%2F2)%7D)

+ 卡方检验分为**拟合度的卡方检验**和**卡方独立性检验**。

  **卡方拟合优度检验**

  卡方统计的公式： ![[公式]](https://www.zhihu.com/equation?tex=%E5%8D%A1%E6%96%B9%3D%5Cchi%5E%7B2%7D%3D%5CSigma%5Cfrac%7B%5Cleft%28+f_%7Bo%7D+-f_%7Be%7D%5Cright%29%5E%7B2%7D%7D%7Bf_%7Be%7D%7D)

  公式中O代表observation，即实际频数；E代表Expectation，即期望频数。

  **卡方独立性检验**

  公式和卡方拟合优度相同，自由度为： ![[公式]](https://www.zhihu.com/equation?tex=df%3D%28R-1%29%28C-1%29)

  其中，R为行数row，C为列数column

---

### 最小二乘法

小二乘法的主要思想是通过确**定未知参数（**通常是一个参数矩阵），来使得真实值和预测值的误差（也称残差）平方和最小

计算公式为 ![[公式]](https://www.zhihu.com/equation?tex=E%3D%5Csum_%7Bi%3D0%7D%5Ene_i%5E2%3D%5Csum_%7Bi%3D1%7D%5En%28y_i-%5Chat%7By_i%7D%29%5E2) ，其中 ![[公式]](https://www.zhihu.com/equation?tex=y_i) 是真实值， ![[公式]](https://www.zhihu.com/equation?tex=%5Chat+y_i) 是对应的预测值。

**最小二乘法就是用来测算我们预测的值和我们通过实践得到的值之间的误差**，E的值与越小说明预测的越准。

##总结：

数学内容中的线性代数学起来相对简单，但是对于统计学的内容看起来非常抽象，经常出现不理解的概念学起来相当吃力。基本属于就稍微了解了一个用途的状态。
