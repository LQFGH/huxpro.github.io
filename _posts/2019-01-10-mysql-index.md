---
layout:     post
title:      "MySql高级技术-索引"
subtitle:   "索引"
date:       2019-01-05 19:00:00
author:     "LQFGH"
header-img: "img/post-mysql.jpg"
header-mask: 0.3
catalog:    true
tags:
  - mysql高级
---


## 基本语法

***



#### **查看某张表的索引**

```sql
SHOW INDEX FROM employees;
```

#### **创建**

```sql
ALTER TABLE employees ADD INDEX inx_emp_nameEmail (last_name,email);

CREATE INDEX inx_emp_nameEmail ON employees(last_name,email);
```

#### **删除**

```sql
DROP INDEX inx_emp_nameEmail ON employees;
```

#### **查看**

```sql
SHOW INDEX FROM employees;
```



## 哪些情况需要建立索引

***



1. 主键自动建立索引
2. 频繁作为查询条件的字段需要建立索引
3. 与其他表相互关联的字段
4. 频繁更新的字段不适合建立索引，更新时还需要更新索引
5. where条件里用不到的字段不建立索引
6. 单值索引/组合索引选择。  高并发情况下倾向于建立组合索引
7. 查询中排序的字段，通过索引可以大大提高访问速度
8. 查询中统计或者分组字段



## 索引分析

