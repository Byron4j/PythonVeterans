
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
        
        # 开启事务
        conn.begin()
        
        # 获取游标，可以进行数据库操作
        cursor = conn.cursor() # 
        
        """
        可以使用fetchone()方法获取单条记录或fetchall()方法从数据库表中获取多个值。

fetchone() - 它获取查询结果集的下一行。 结果集是当使用游标对象来查询表时返回的对象。

fetchall() - 它获取结果集中的所有行。 如果已经从结果集中提取了一些行，则从结果集中检索剩余的行。

rowcount - 这是一个只读属性，并返回受execute()方法影响的行数。
        """
        
        # SELECT 执行查询
        cursor.execute("select * from employer")
        # 获取查询结果集
        resultset = cursor.fetchall()
        for ele in range(len(resultset)):
            print(resultset[ele])
         
        hello =    '李白' + str(random.randint(1000,2000))
            
        sql = "insert into employer(name, age, gender) values('" + hello + "', 24, 'M')"
        # 插入    
        print("插入条数:" + str(cursor.execute(sql)))
        # 提交事务--使INSERT生效
        conn.commit()
        
        # UPDATE 操作
        cursor.execute("update employer set name = 'TXZ' where id = 1 ")
        # 提交事务--使UPDATE生效
        conn.commit()
        
        # 演示回滚案例
        try:
            # 插入    
            cursor.execute("insert into employer values(1, '" + hello + "', 24, 'M')")
            # 提交事务--使INSERT生效
            conn.commit()
        except:
            conn.rollback()
            print("插入数据异常，回滚事务!")
        finally:
            conn.close()
            print("关闭数据库连接.")
        
        
        
</pre>




### 数据库连接对象 Connection


 pymysql.conn(*args) 方法返回一个数据库连接对象: Connection, 在模块 connections里面。

我们可以看看数据库连接对象的源码（仅仅看一下构造函数，理解一下各个参数的含义）:


构造函数的参数：```
class pymysql.connections.Connection(host=None, user=None, password='', database=None, port=0, unix_socket=None, charset='', sql_mode=None, read_default_file=None, conv=None, use_unicode=None, client_flag=0, cursorclass=<class 'pymysql.cursors.Cursor'>, init_command=None, connect_timeout=10, ssl=None, read_default_group=None, compress=None, named_pipe=None, no_delay=None, autocommit=False, db=None, passwd=None, local_infile=False, max_allowed_packet=16777216, defer_connect=False, auth_plugin_map={}, read_timeout=None, write_timeout=None, bind_address=None, binary_prefix=False)
```

<pre>




class Connection(object):
    """
    表示一个关于mysql服务器的套接字连接，获取该连接的方式是通过调用connect()方法建立应用程序到mysql服务器的连接。

    connect()接受的参数列表:

    : host: mysql服务器地址
    : user: 用户名
    : password: 密码
    : database: 指定连接的数据库，无则不指定特定的数据库.
    : port: mysql端口. (默认: 3306)
    : bind_address: 当客户端有多个网络接口时，请指定连接到主机的接口。参数可以主机名或IP地址.
    : unix_socket: 可选地，您可以使用unix套接字而不是tcp/ip.
    : charset: 数据库连接的字符集（'utf8'等）
    : sql_mode:  设置SQL_MODE(该术语参见mysql帮助文档) .
    : read_default_file: m设置ysql服务读取的配置文件，默认为：my.cnf
    : cursorclass: 自定义游标类.
    : init_command: 在建立连接时运行的初始SQL语句（比如 select 1）.
    : connect_timeout: 在连接时抛出异常之前的超时. (默认: 10, 最小: 1, 最大: 31536000)
    : ssl:mysqlsslset（）参数相似.
    : read_default_group: Group to read from in the configuration file.
    : compress: 不支持
    : named_pipe: 不支持
    : autocommit: 自动提交事务模式. None 表示mysql服务器默认的. (默认: False)
    : local_infile: 布尔值用于启用LOAD DATA本地命令.(默认: False)
    : max_allowed_packet: 以字节发送给服务器的最大数据包大小. (默认: 16MB).
    : defer_connect: 不要显式地连接在一起——等待连接调用.(default: False)
    : auth_plugin_map: 对一个处理插件的类的插件名称的阻止.
        将会把数据库连接对象作为构造器的参数.该类需要一个身份验证方法，获取身份验证包.  对于对话框插件，可以使用prompt（echo、prompt）方法（如果没有认证方法）从用户返回一个字符串。(实验)
    : db: 数据库的别名
    : passwd: 密码的别名
    : binary_prefix: 在字节和bytearray中添加二进制前缀.(default: False)
    """

    _sock = None
    _auth_plugin_name = ''
    _closed = False

    def __init__(self, host=None, user=None, password="",
                 database=None, port=0, unix_socket=None,
                 charset='', sql_mode=None,
                 read_default_file=None, conv=None, use_unicode=None,
                 client_flag=0, cursorclass=Cursor, init_command=None,
                 connect_timeout=10, ssl=None, read_default_group=None,
                 compress=None, named_pipe=None, no_delay=None,
                 autocommit=False, db=None, passwd=None, local_infile=False,
                 max_allowed_packet=16*1024*1024, defer_connect=False,
                 auth_plugin_map={}, read_timeout=None, write_timeout=None,
                 bind_address=None, binary_prefix=False):
        # 构造器函数体
	    ...
</pre>

#### Connection 的方法、属性

- 