
Python的数据库接口标准是Python DB-API。大多数Python数据库接口遵循这个标准。

### DB API
DB API为尽可能使用Python结构和语法处理数据库提供了最低标准。API包括以下内容：

- 导入API模块。
- 获取与数据库的连接。
- 发出SQL语句和存储过程。
- 关闭连接


## 连接mysql

### PyMySQL

PyMySQL是从Python连接到MySQL数据库服务器的接口。 它实现了Python数据库API v2.0，并包含一个纯Python的MySQL客户端库。 PyMySQL的目标是成为MySQLdb的替代品。

PyMySQL参考文档：[http://pymysql.readthedocs.io/](http://pymysql.readthedocs.io/)

PyMySQL 的项目 : [https://github.com/PyMySQL/PyMySQL/](https://github.com/PyMySQL/PyMySQL/)

### 安装pymysql

使用pip安装pymysql。  如果你的pip不能使用，请自行搜索先安装pip。

>pip install PyMySQL


#### pymysql的使用

##### 建表

<pre>
CREATE TABLE `users` (
    `id` int(11) NOT NULL AUTO_INCREMENT,
    `email` varchar(255) COLLATE utf8_bin NOT NULL,
    `password` varchar(255) COLLATE utf8_bin NOT NULL,
    PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin
AUTO_INCREMENT=1 ;
</pre>


##### 示例

<pre>
import pymysql.cursors

# Connect to the database
connection = pymysql.connect(host='localhost',
                             user='user',
                             password='passwd',
                             db='db',
                             charset='utf8mb4',
                             cursorclass=pymysql.cursors.DictCursor)

try:
    with connection.cursor() as cursor:
        # Create a new record
        sql = "INSERT INTO `users` (`email`, `password`) VALUES (%s, %s)"
        cursor.execute(sql, ('webmaster@python.org', 'very-secret'))

    # connection is not autocommit by default. So you must commit to save
    # your changes.
    connection.commit()

    with connection.cursor() as cursor:
        # Read a single record
        sql = "SELECT `id`, `password` FROM `users` WHERE `email`=%s"
        cursor.execute(sql, ('webmaster@python.org',))
        result = cursor.fetchone()
        print(result)
finally:
    connection.close()
</pre>


输出：
>{'password': 'very-secret', 'id': 1}


#### 使用方式

- 引入模块 ： ```import pymysql```
- 建立SB连接： ```conn = pymysql.connect("localhost","root","123456","test", cahrset="utf8" )```
- 获取可以操作数据库的游标： ```cursor = conn.cursor()```
- 使用执行SQL语句返回受影响的行数(非查询语句)： ```count = cursor.execute("SELECT VERSION()")```
- 获取查询结果集： ```data = cursor.fetchone()```
- 开启事务： ```conn.begin()```
- 提交事务： ```conn.commit()```
- 回滚事务：  ```conn.rollback()```
- 关闭DB连接： ```conn.close()```


#### 读取操作

可以使用游标的```fetchone()```方法获取单条记录或```fetchall()```方法从数据库表中获取多个值。

- fetchone() - 它获取查询结果集的下一行。 结果集是当使用游标对象来查询表时返回的对象。

- fetchall() - 它获取结果集中的所有行。 如果已经从结果集中提取了一些行，则从结果集中检索剩余的行。

- rowcount - 这是一个只读属性，并返回受execute()方法影响的行数。





### 示例

<pre>
# encoding=utf-8
'''
指定UTF-8编码方式一：# -*- coding: UTF-8 -*-
方式二： # encoding=utf-8
@author: BYRON.Y.Y
第一个python连接mysql程序是=示例

建表语句：
CREATE TABLE `employer` (
  `id` INT(11) PRIMARY KEY AUTO_INCREMENT,
  `name` VARCHAR(30) DEFAULT NULL,
  `age` INT(11) DEFAULT NULL,
  `gender` CHAR(1) DEFAULT NULL
) ENGINE=INNODB DEFAULT CHARSET=utf8;
'''
import pymysql
import random


class MyClass(object):
    '''
    classdocs
    '''


    def __init__(self, params):
        '''
        Constructor
        '''
    if __name__ == "__main__":
        """connection = pymysql.connect(host='localhost',
                             user='user',
                             password='passwd',
                             db='db',
                             charset='utf8mb4',
                             cursorclass=pymysql.cursors.DictCursor);"""
        conn = pymysql.connect("localhost","root","11111111","mypydb", charset="utf8" ) #获取DB连接
        
        # 获取游标，可以进行数据库操作
        cursor = conn.cursor() # 
        
        # SELECT 执行查询
        cursor.execute("select * from employer")
        # 获取查询结果集
        resultset = cursor.fetchall()
        for ele in range(len(resultset)):
            print(resultset[ele])
         
        hello =    '李白' + str(random.randint(1000,2000))
            
        # 插入    
        cursor.execute("insert into employer(name, age, gender) values(" + hello + ", 24, 'M')")
        # 提交事务--使INSERT生效
        conn.commit()
        
        # UPDATE 操作
        cursor.execute("update employer set name = 'TXZ' where id = 1 ")
        # 提交事务--使UPDATE生效
        conn.commit()
        
        
        
</pre>