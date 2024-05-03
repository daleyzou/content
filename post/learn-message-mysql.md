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

#### 大事务执行时间过滤 用于查找持续时间超过 60s 的事务
```
select * from information_schema.innodb_trx where TIME_TO_SEC(timediff(now(),trx_started))>60
```

#### 普通索引 VS 唯一索引
可以选择的情况下， 尽量选择普通索引， 配置 change buffer 使用， 避免随机加载磁盘页到内存中

#### 索引查询条件
```
explain select * from t where a between 10 and 10000;
show index from t;
analyze t;
start transaction with consistent snapshot;
select * from t where (a between 1 and 1000)  and (b between 50000 and 100000) order by b limit 1;
explain select * from t where (a between 1 and 1000)  and (b between 50000 and 100000) order by (b,a) limit 1;

/* 打开 optimizer_trace，只对本线程有效 */
SET optimizer_trace='enabled=on'; 
SELECT to_location_code  FROM `ess_adapter_task_detail` order by rand() limit 3;
/* 查看 OPTIMIZER_TRACE 输出 */
SELECT * FROM `information_schema`.`OPTIMIZER_TRACE`
```
#### innodb 控制刷新脏页
```
innodb_io_capacity 这个参数控制写入磁盘io
这个值我建议你设置成磁盘的 IOPS。磁盘的 IOPS 可以通过 fio 这个工具来测试
fio -filename=$filename -direct=1 -iodepth 1 -thread -rw=randrw -ioengine=psync -bs=16k -size=500M -numjobs=10 -runtime=10 -group_reporting -name=mytest

查询脏页的比例
select VARIABLE_VALUE into @a from global_status where VARIABLE_NAME = 'Innodb_buffer_pool_pages_dirty';
select VARIABLE_VALUE into @b from global_status where VARIABLE_NAME = 'Innodb_buffer_pool_pages_total';
select @a/@b;

nodb_flush_neighbors 参数为 1 时，会导致 如果跟它相邻的数据页也还是脏页的话，也会被放到一起刷
```
#### select 查询表的总行数
select count(*) vs select count(1) vs select count(id) 

#### MySQL 变量
```
max_length_for_sort_data： 排序时的数据长度
tmp_table_size：内存临时表的大小
```


