---
layout: post
title: 多表如何查询
categories: sql
description: 多表如何查询
keywords: sql
---

## 【题目】
现在有两个表，“学生表”记录了学生的基本信息，有“学号”、“姓名”。

“成绩”表记录了学生选修的课程，以及对应课程的成绩。

这两个表通过“学号”进行关联。

现在要查找出所有学生的学号，姓名，课程和成绩。

![](/images/posts/sql/sql-select.png)

【解题思路】
1.确定查询结果

题目要求查询所有学生的姓名，学号，课程和成绩信息

select 学号,姓名,课程,成绩

查询结果的列名“学号”、“姓名”，在“学生”表里，列名“课程”、“成绩”在“成绩”表里，所以需要进行多表查询。

2.哪种联结呢？

涉及到多表查询，在之前的课程《从零学会sql：多表查询》里讲过需要用到联结。

多表的联结又分为以下几种类型：

1）左联结（left join），联结结果保留左表的全部数据

2）右联结（right join），联结结果保留右表的全部数据

3）内联结（inner join），取两表的公共数据

这个题目里要求“所有学生”，而“所有学生”在“学生”表里。为什么不在“成绩”表里呢？

如果有的学生没有选修课程，那么他就不会出现在“成绩”表里，所以“成绩”表没有包含“所有学生”。

所以要以“学生”表进行左联结，保留左边表（学生表）里的全部数据。

from 学生信息表 as a left join 成绩表 as b

3.两个表联结条件是什么？

两个表都有“学号”，所以联结条件为学号。

on a.学号=b.学号

4.最终sql


select a.学号,a.姓名,b.课程,b.成绩
from 学生 as a
left join 成绩 as b
on a.学号=b.学号;

![](/images/posts/sql/sql-biao.jpg)


【本题考点】
考察多表联结，以及如何选择联结的类型。记住课程里讲过的下面这张图，遇到多表联结的时候从这张图选择对于的sql。

![](/images/posts/sql/sql-select-kaodian.jpg)

【举一反三】
有下面两个表

![](/images/posts/sql/sql-juyifansan.jpg)


编写一个 SQL 查询，满足条件：无论 person 是否有地址信息，都需要基于上述两表提供 person 的以下信息：

FirstName, LastName, City, State

【思路】

从表的结构可以看出，表1（Person）是人的姓名信息，表2（Address）是人的地址信息。

1）查询结果是两个表里的列名，所以需要多表查询

2）考虑到有的人可能没有地址信息，要是查询结构要查所有人，需要保留表1（Person）里的全部数据，所以用左联结（left join）

3）两个表联结条件：两个表通过personId产生联结。

【参考答案】


select FirstName, LastName, City, State
from Person left join Address
on Person.PersonId = Address.PersonId;
