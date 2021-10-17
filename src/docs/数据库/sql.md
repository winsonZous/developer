在线练习网站:https://sqlzoo.net

select基本查询
给定一个模式（table,view）
一个对象表示一行，table存储了一个类的很多对象

select column from table where condition

column为字符串,condition可以用
1、 column like '%' 
2、column = value 
3、column in (value,value,value)

column 为数字类型
1、column < value
2、column between value and value

column查询出来的结果，可以加减乘除例如area、population再作为结果显示
condition 之间可以用and、or来连接

### 数据库中主要包括的数据类型为字符串、数值型、日期和时间
mysql
数值型: INT、BIGINT、DECIMAL(P,D)
日期和时间: DATETIME、TIMESTAMP
字符串: VARCHAR、BLOB

oracle
数值型:Number()

### 关键字
like
distinct 去重
ALL >= ALL与<= ALL 在嵌套子查询中十分常见
limit n子句表示查询结果返回前n条数据

offset n表示跳过x条语句

MYSQL中LIMIT关键字
limit y offset x 分句表示查询结果跳过 x 条数据，读取前 y 条数据


### 基本函数
column 加减乘除操作
1、ROUND 展示保留展示位，ROUND(x,y)
存在一个数,对应四舍五入关系
假设: x=9     5    2    7.   1
     y=-3    -2   -1   0    1
结果: r=10000 9500 9530 9527 9527.1
2、LEN(字符串) 字符串长度

3、LEFT(string,offset) 从0开始截取字符串

聚合函数
面对一张表的多行记录，可以进行求和、求最大值、求最小值、计数、求平均数等操作
4、COUNT() 
统计某个字段的数量，排除NULL值

字符串函数CONCAT
CONCAT(A,B)

字符串替换函数关键字
coalesce(column)




### 基本语句
1、查询语句
SELECT column
FORM table/view
JOIN table/View
ON condition
WHERE condition
GROUP BY column 
Having condition
ORDER BY column desc/esc
limit (offset,offset)

单表查询最重要的是把condition从题目/需求中分离出来
对于数字 等值=, > ,<,>=,<=, <>，between
划重点 <>表示不等于，和 IS NULL 、 IS NOT NULL 操作符来与NULL值比较
对于字符串 等值=,like ‘regex’
等值的多个匹配用IN，多个排除用NOT IN
order by的特殊用法
order by column desc,column;
ORDER BY subject IN ('Physics','Chemistry'),subject,winner;
subject IN ('Physics','Chemistry')将会返回0、1


2、条件语句
CASE 
WHEN condition
THEN
ELSE
WHEN condition
THEN
ELSE value
END

3、嵌套子查询
3.1 内模式运算结果以后依然是内模式，当结果为1行记录时，内模式可以当作一个值使用，我们用=连接即可
如果子查询记录有多条，我们可以用IN
3.2 内层子查询可以引用外层查询的变量
嵌套子查询类似于双层循环
3.3 嵌套子查询基本用法
可以用IN来连接、>=、<=来连接子查询结果
如果查询结果只有一个，那么直接相当于一个value

4、HAVING子句主要是对分组后的组进行过滤，HAVING子句主要是聚合函数
对行数据进行过滤通常在WHERE子句以后

5、 表连接子句
JOIN table1 ON table2
充分理解ER关系（1...*），是做好表连接查询的关键
