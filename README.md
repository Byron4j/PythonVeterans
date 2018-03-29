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

###### 元组

- 

###### 字典

