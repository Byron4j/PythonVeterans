## purpose

- Syntax
- Object-Oriented Program 
- Module Program 模块编程
- Game Program 游戏
- Computer Simulation 仿真





#### syntax

- 不需要明确的声明类型来保留内存空间:name = "Maxsu"
- 允许同时为多个变量分配单个值:a = b = c = 1
- 可以将多个对象分配给多个变量:a, b, c = 10, 20, "maxsu"

###### 数值

- 数值类型：int(有符号整数)；float(浮点实值)；complex(复数)
- python3中所有整数都是长整数
- var1 = 10
- del var1 ： <font color=red size=5>del</font> 删除数字对象的引用


###### 字符串

- 单引号或双引号标识。使用片段运算符<font color=red size=5>[]</font>、<font color=red size=5>[:]</font>获取子集。索引0为始，-1为终。 []包前不包后。

- <font color=red size=5>+</font> 是连接运算符， <font color=red size=5>*</font> 是重复运算符。

<pre>
>>> str = 'yiibai.com'
>>> print ('str[0] = ',str[0])
str[0] =  y
>>> print ('str[2:5] = ',str[2:5])
str[2:5] =  iba
>>> print ('str[2:] = ',str[2:])
str[2:] =  ibai.com
>>> print ('str[-1] = ',str[-1])
str[-1] =  m
>>> print ('str * 2 = ',str * 2)
str * 2 =  yiibai.comyiibai.com
>>> print ('str + "TEST" = ',str + "TEST")
str + "TEST" =  yiibai.comTEST

</pre>

###### 列表

- 一个列表包含用逗号分隔包括并括在方括号<font color=red size=5>[]</font>中的项目。类似于java中的List的toString()方法输出。 形如：<font color=red size=5>list = [1, 2, 3]</font>。

- 列表的使用方式和字符串类似：使用 []、[:] 来访问，索引从 0 开始， -1 表示最后一个元素的索引。 + 是列表连接符， * 是重复运算符。

- 列表的大小和元素可以变更

- Python列表的所有项可以是不同的数据类型

<pre>
>>> list = [ 'yes', 'no', 786 , 2.23, 'minsu', 70.2 ]
>>> list
['yes', 'no', 786, 2.23, 'minsu', 70.2]
>>> tinylist = [100, 'maxsu']
>>> print ('list = ', list)
list =  ['yes', 'no', 786, 2.23, 'minsu', 70.2]
>>> print ('list[0] = ',list[0])
list[0] =  yes
>>> print ('list[1:3] = ',list[1:3])
list[1:3] =  ['no', 786]
>>> print ('list[2:] = ',list[2:])
list[2:] =  [786, 2.23, 'minsu', 70.2]
>>> print ('list[-3:-1] = ',list[-3:-1])
list[-3:-1] =  [2.23, 'minsu']
>>> print ('tinylist * 2 = ',tinylist * 2)
tinylist * 2 =  [100, 'maxsu', 100, 'maxsu']
>>> print ('list + tinylist = ', list + tinylist)
list + tinylist =  ['yes', 'no', 786, 2.23, 'minsu', 70.2, 100, 'maxsu']
</pre>


###### 集合

- 集合和数学上的集合表示方法一致，大括号{}括起来，多个元素逗号隔开
- 集合中的元素是唯一的

<pre>
>>> set1 = {1, 2, 3}
>>> type(set1)
&lt;class 'set'>

>>> set2 = {1, 1, 1, 1, 2, 3, 3, 2}
>>> set2
{1, 2, 3}
</pre>

###### 元组

- 元组以 <font color=red size=5>()</font> 括起来，按逗号分隔开的多个值集合。

- 元组无法更新。可以认为是"只读的列表"。 元组可以认为是一个"列表集合"的引用，可以指向不同的"列表集合",但指向的目标"列表集合"不能被修改。     

- 元组使用方式和列表、字符串一样：也是使用 []来获取元素.

<pre>
>>> tuple = ( 'maxsu', 786 , 2.23, 'yiibai', 70.2  )
>>> print ('tuple[-3:-1] = ', tuple[-3:-1])
tuple[-3:-1] =  (2.23, 'yiibai')
>>> tuple[1] = 'new item value'  ##元组不能变更
Traceback (most recent call last):
  File "<pyshell#295>", line 1, in <module>
    tuple[1] = 'new item value'
TypeError: 'tuple' object does not support item assignment
</pre>

###### 字典

- 字典是哈希表类型，由键值对组成。类似于javascript的对象
- 字典由大括号(<font color=red size=5>{}</font>)括起来，可以使用方括号(<font color=red size=5>[]</font>)分配和访问值
- 字典就是一个json串的形式
- 字典中的元素没有顺序,类似java的hashMap

<pre>
>>> dic = {}
>>> dic['one'] = 'This is one'
>>> dic
{'one': 'This is one'}
>>> dic['two'] = 'This is two'
>>> dic
{'one': 'This is one', 'two': 'This is two'}
>>> dic[2]
Traceback (most recent call last):
  File "<pyshell#312>", line 1, in <module>
    dic[2]
KeyError: 2
>>> dic[2] = 'This is three'
>>> dic
{'one': 'This is one', 'two': 'This is two', 2: 'This is three'}
</pre>


###### 数据类型转换

- 有时候，可能在内置类型之间进行数据转换。只需使用类型名称作为函数即可。

<pre
>>> int('123', )
123
>>> int('10', 8)
8
>>> float('12.34')
12.34
>> list=[1,2,2,3]
>>> list
[1, 2, 2, 3]
>>> set(list)  ##该方式可以将列表list中的元素去重
{1, 2, 3}
>>> list = [(1,2), (3,4)]
>>> list
[(1, 2), (3, 4)]
>>> dict(list)  ##参数必须是(key, value)元组的序列
{1: 2, 3: 4}
>>> chr(65)  ##要求传入int类型的参数
'A'
</pre>



##### 运算

###### 算术运算

- <font color=red size=5>**</font> 幂运算符
- <font color=red size=5>//</font> 地板除运算符：操作数的除法，结果是删除小数点后的商。

<pre>
>>> 9 //2 ##结果为整数，则直接截取掉商后面的小数部分
4
>>> - 11 // 3  ##结果为负数，向下取整截取掉小数部分
-4
</pre>

###### 逻辑运算符

- and 都为真则为真，其余为假 
- or 有一个为真则为真
- not 反转操作数的逻辑状态，a 为假， not a 则为真

###### 按位运算符

位运算符是将操作数（二进制形式）执行逐位运算， <font color=red size=5>bin()</font>可用于获取整数的二进制运算

- & 按位与
- | 按位或
- ~ 相反
- ^ 异或
- << 二进制左移
- \>> 二进制右移

- ~a = a - 1

<pre>
>>> a = 1
>>> a << 1
2
>>> a >> 1
0
</pre>

###### 成员运算符

成员运算符常用于 测试给定值是否为序列中的成员例如字符串、列表或元组。

- <font color=red size=5>in</font> 在指定序列中可以找到变量的值，则返回True
- <font color=red size=5>not in</font> 在指定序列中找不到变量的值，则返回True

<pre>
>>> a = 2
>>> b = 3
>>> list = [1, 2, 5, 7]
>>> if ( a in list ):
	print("a is a element of list")
else: print("a is not a element of list")

a is a element of list
</pre>

###### 身份运算符

身份运算符用于比较两个对象在内存中的位置。

- is 指向相同的对象，返回True
- is not 指向的是不同的对象，返回True
- id()返回对象在内存中的位置

<pre>
>>> a = 20
>>> b = 20
>>> a is b
True
>>> id(a)
1559733952
>>> id(b)
1559733952
>>> id(a) == id(b)
True
>>> a is not b
False
</pre>

##### 决策（分支）

- if 表达式为True，则执行语句
- else if表达式为False时，会执行else的语句
- <font color=red size=5>elif</font>   用于检查多个表达式是否为True

格式如下：
<pre>
if 表达式1:
    代码段1
elif 表达式2:
    代码段2
elif 表达式3:
    代码段3
else:
    代码段4
</pre>


<pre>
>>> a = 60
>>> if(a >= 90): print("优秀")
elif(a < 90 and a >= 80): print("良好")
else: print("一般")

一般
>>> a = 97
>>> if(a >= 90): print("优秀")
elif(a < 90 and a >= 80): print("良好")
else: print("一般")

优秀
>>> a = 88
>>> if(a >= 90): print("优秀")
elif(a < 90 and a >= 80): print("良好")
else: print("一般")

良好
</pre>


##### 循环语句

###### <font color=red size=5>while

python 支持循环语句相关联的else语句。</font>
<pre>
####whlie实例
>>> cnt = 3
>>>> while ( cnt > 0 ) :
	print("cnt value is:" , cnt)
	cnt -= 1

	
cnt value is: 3
cnt value is: 2
cnt value is: 1

#### 循环 + else 语句的结合实例
>>> count = 0
>>> while count < 5:
   print (count, " is  less than 5")
   count = count + 1
else:
   print (count, " is not less than 5")

   
0  is  less than 5
1  is  less than 5
2  is  less than 5
3  is  less than 5
4  is  less than 5
5  is not less than 5
</pre>


###### for 循环

for 循环可以遍历任何序列的项目，如列表或字符串等。基本语法如下：

<pre>
for 交互变量 in 序列:
    执行语句
</pre>


range() 是一个可以对一系列数字进行迭代的函数，可以生成一个算数进化的迭代器。

<pre>
>>> list()  #获取一个空列表
[]
>>> list(range(5)) #使用list()函数将range转换为列表
[0, 1, 2, 3, 4]
>>> range(5) #生成一个0-4的迭代器
range(0, 5)

### for循环打印迭代器
>>> for var in list(range(5)):
   print (var)

   
0
1
2
3
4

### for循环打印字符串的每个字符
>>> for letter in 'Python':     # traversal of a string sequence
    print ('Current Letter :', letter)

    
Current Letter : P
Current Letter : y
Current Letter : t
Current Letter : h
Current Letter : o
Current Letter : n



### 按序列索引迭代
>>> fruits = ['banana', 'apple',  'mango']
>>> for idx in range(len(fruits)):
	print("元素", idx, "值为:", fruits[idx])

	
元素 0 值为: banana
元素 1 值为: apple
元素 2 值为: mango
</pre>

如果else语句与for循环一起使用，则只有在for循环正常终止(而不是遇到break语句)时才执行else块。

如果else语句与while循环一起使用，则在条件变为false时执行else语句。


**for循环正常运行终止，则后面执行else语句:**
<pre>
>>> numbers = [11,33,55,39,55,75,37,21,23,41,13]
>>> for num in numbers:
    if num%2 == 0:
        print ('the list contains an even number')
        break
else:
    print ('the list doesnot contain even number')

    
the list doesnot contain even number
</pre>



**for循环非正常终止，是break终止的，不会执行else语句:**
<pre>
>>> numbers = [11,33,55,39,55,75,37,21,23,41,13]
>>> for num in numbers:
    if num%2 != 0:
        print ('the list contains an even number')
        break
else:
    print ('the list doesnot contain even number')

    
the list contains an even number
</pre>

**嵌套循环实例：**

<pre>
>>> for i in range(1,11):
    for j in range(1,11):
        k=i*j
        print (k, end=' ') #指定间隔符为 ' '
    print()

    
1 2 3 4 5 6 7 8 9 10 
2 4 6 8 10 12 14 16 18 20 
3 6 9 12 15 18 21 24 27 30 
4 8 12 16 20 24 28 32 36 40 
5 10 15 20 25 30 35 40 45 50 
6 12 18 24 30 36 42 48 54 60 
7 14 21 28 35 42 49 56 63 70 
8 16 24 32 40 48 56 64 72 80 
9 18 27 36 45 54 63 72 81 90 
10 20 30 40 50 60 70 80 90 100 


#实例2
>>> for i in range(1, 4):
	for j in range(1, 4):
		print( i * j, end = '\t') #指定间隔符为 '\t'
	print()

	
1	2	3	
2	4	6	
3	6	9
</pre>



打印九九乘法表：
<pre>
>>> # 打印九九乘法表
for i in range(1, 10):
	for j in range(1, 10):
		if(j <= i):
			print(i, "*", j, "=" , i * j, end = ' ')
		else:
			break
	print()

	
1 * 1 = 1 
2 * 1 = 2 2 * 2 = 4 
3 * 1 = 3 3 * 2 = 6 3 * 3 = 9 
4 * 1 = 4 4 * 2 = 8 4 * 3 = 12 4 * 4 = 16 
5 * 1 = 5 5 * 2 = 10 5 * 3 = 15 5 * 4 = 20 5 * 5 = 25 
6 * 1 = 6 6 * 2 = 12 6 * 3 = 18 6 * 4 = 24 6 * 5 = 30 6 * 6 = 36 
7 * 1 = 7 7 * 2 = 14 7 * 3 = 21 7 * 4 = 28 7 * 5 = 35 7 * 6 = 42 7 * 7 = 49 
8 * 1 = 8 8 * 2 = 16 8 * 3 = 24 8 * 4 = 32 8 * 5 = 40 8 * 6 = 48 8 * 7 = 56 8 * 8 = 64 
9 * 1 = 9 9 * 2 = 18 9 * 3 = 27 9 * 4 = 36 9 * 5 = 45 9 * 6 = 54 9 * 7 = 63 9 * 8 = 72 9 * 9 = 81
</pre>
