---
description: 视图是从一个或多个表导出来的表，是一种虚拟存在的表。
---

# 视图

## 视图简介

### 视图的含义

视图是一种虚拟的表，是从数据库中一个或多个表中导出来的表。视图还可以从已经存在的视图的基础上定义。数据库中值存放的视图的定义，而并没有存放视图中的数据。这些数据存放在原来的表中。

### 视图的作用

* 使操作简单化；
* 增加数据的安全性；
* 提高表的逻辑独立性；

## 创建视图

### 创建视图的语法形式

```sql
CREATE [ALGORITHM={UNDEFINED|MERGE|TIMETABLE}]
        VIEW 视图名 [(属性清单)]
        AS SELECT语句
        [WITH [CASCADED|LOCAL] CHECK OPTION];
```

* CASCADED表示更新视图时要满足所有相关视图和表的条件；
* LOCAL表示只需要满足视图本身定义的条件即可；
* WITH CHECK OPTION表示更新视图时要保证在该视图的权限范围之内；

{% hint style="info" %}
使用该语句创建视图时，最好加上WITH CHECK OPTION和CASCADED参数，以保证数据的安全性。
{% endhint %}

{% hint style="info" %}
创建视图时，需要有CREATE VIEW和SELECT权限。可以通过相关语句查询。
{% endhint %}

### 查看视图

```sql
DESCRIBE 视图名;
```

### 查看视图信息

查看基本信息：

```sql
SHOW TABLE STATUS LIKE '视图名';
```

查看详细信息：

```text
SHOW CREATE VIEW 视图名;
```

查看所有视图的详细信息：

```text
SELECT * FROM information_schema.views;
```

## 修改视图

### CREATE OR REPLACE VIEW

其参数与创建视图的参数是一样的，把开头的CREATE换成CREATE OR REPLACE即可。

### ALTER语句修改视图

其参数与创建视图的参数是一样的，把开头的CREATE 换成ALTER即可。

## 更新视图

更新视图是指通过视图来INSERT、UPDATE、DELETE**表**中的数据。

```sql
UPDATE 视图名 SET ...
```

## 删除视图

删除视图时，只会删除视图的定义，不会删除数据。

```sql
DROP VIEW [IF EXISTS] 视图名列表 [RESTRICT|CASCADE]
```

* IF EXISTS参数判断视图是否存在，如果存在才执行，不存在就不执行；
* 用户必须有DROP权限才能删除视图；















