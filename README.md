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
