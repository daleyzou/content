---
title: "Learn Message Mysql"
date: 2023-04-17T21:13:01+08:00
draft: false
---


## 相关链接

https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/MySQL%E5%AE%9E%E6%88%9845%E8%AE%B2

https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/MySQL%E5%AE%9E%E6%88%98%E5%AE%9D%E5%85%B8

https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/24%E8%AE%B2%E5%90%83%E9%80%8F%E5%88%86%E5%B8%83%E5%BC%8F%E6%95%B0%E6%8D%AE%E5%BA%93-%E5%AE%8C


## 补充链接

https://pdai.tech/md/db/sql-mysql/sql-mysql-execute.html

## 知识点


### 慢 SQL 分析
[提高 SQL 的性能](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Java%E5%B9%B6%E5%8F%91%E7%BC%96%E7%A8%8B%E5%AE%9E%E6%88%98/32%20%20MySQL%E8%B0%83%E4%BC%98%E4%B9%8BSQL%E8%AF%AD%E5%8F%A5%EF%BC%9A%E5%A6%82%E4%BD%95%E5%86%99%E5%87%BA%E9%AB%98%E6%80%A7%E8%83%BDSQL%E8%AF%AD%E5%8F%A5%EF%BC%9F.md)

### InnoDB存储引擎不直接支持Hash索引，它支持的索引类型包括：
- B+树索引：是InnoDB默认的索引类型，用于支持普通索引和唯一索引。
- 全文索引：用于支持全文搜索功能。
- 空间索引：用于支持空间数据类型的查询。
- 主键索引：用于支持主键查询，实际上是B+树索引的一种特殊形式。
```
-- 全文索引
CREATE TABLE my_table (
    id INT PRIMARY KEY,
    content TEXT,
    FULLTEXT INDEX content_fulltext_idx (content)
) ENGINE=InnoDB;

SELECT * FROM my_table WHERE MATCH(content) AGAINST ('name');

-- 空间索引
CREATE TABLE my_table1 (
    id INT PRIMARY KEY,
    location POINT not null,
    SPATIAL INDEX location_spatial_idx (location)
) ENGINE=InnoDB;

INSERT INTO my_table1 (id, location) VALUES (1, POINT(40, -73));
SELECT * FROM my_table1 WHERE ST_Distance(location, POINT(40, -73)) < 1000;
```

[B+树](https://zhuanlan.zhihu.com/p/27700617)

#### 针对已经存在表数据的情况下， 修改表的字符集
正确修改列字符集的命令应该使用 ALTER TABLE … CONVERT TO…这样才能将之前的列 a 字符集从 UTF8 修改为 UTF8MB4


#### 索引使用情况
可以通过查询表 mysql.innodb_index_stats 查看每个索引的大致情况

可以通过查询表sys.schema_unused_indexes，查看有哪些索引一直未被使用过，可以被废弃

针对已经在查询语句中使用了函数，导致无法使用索引的，可以创建一个函数索引

#### 常用索引使用方式
EXPLAIN FORMAT=tree   可以看到更详细的SQL执行数据

#### 大事务执行时间过滤
```
select * from information_schema.innodb_trx where TIME_TO_SEC(timediff(now(),trx_started))>60
```
