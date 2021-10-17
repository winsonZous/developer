## 常见面试内容

1. delete、drop、truncate 三者区别
    删除表可以清除表中的数据或者删除表结构
   
2. 内连接外连接
- 内连接
- 外连接
    - 左外连接
    - 右外连接

3. 数据库中的排名问题
mysql中主要是三种解法
3.1 用limit
SET N:=N-1 limit N
3.2 子查询

3.3 表连接（笛卡尔积）
解法的主要思想是排名为N,那么存在N-1条记录小于该排名
```
 SELECT 
          e1.salary
      FROM 
          employee e1 Inner Join  employee e2 ON e1.salary <= e2.salary
      GROUP BY 
          e1.salary
      HAVING 
          count(DISTINCT e2.salary) = N
```

4. 数据库中寻找最值问题