# 单表访问方法

```sql
CREATE TABLE single_table ( 
   id INT NOT NULL AUTO_INCREMENT, 
   key1 VARCHAR(100), 
   key2 INT, 
   key3 VARCHAR(100), 
   key_part1 VARCHAR(100), 
   key_part2 VARCHAR(100), 
   key_part3 VARCHAR(100), 
   common_field VARCHAR(100), 
   PRIMARY KEY (id), 
   KEY idx_key1 (key1), 
   UNIQUE KEY idx_key2 (key2), 
   KEY idx_key3 (key3), 
   KEY idx_key_part(key_part1, key_part2, key_part3) 
) Engine=InnoDB CHARSET=utf8;
```

## const

设计MySQL的大叔认为通过主键或者唯一二级索引列与常数的等值比较来定位一条记录是像坐火箭一样快的，所以他们把这种通过主键或者唯一二级索引列来定位一条记录的访问方法定义为：const，意思是常数级的，代价是可以忽略不计的。
<img src="./picture/聚簇索引示意图.png" width="" alt="聚簇索引示意图">

> SELECT * FROM single_table WHERE id = 1438;

<img src="./picture/唯一二级索引与聚簇索引示意图.png" width="" alt="聚簇索引示意图">

> SELECT * FROM single_table WHERE key2 = 3841;

## ref

<img src="./picture/普通二级索引与聚簇索引示意图.png" width="" alt="聚簇索引示意图">

> SELECT * FROM single_table WHERE key1 = 'abc';

从图示中可以看出，对于普通的二级索引来说，通过索引列进行等值比较后可能匹配到多条连续的记录，而不是像主键或者唯一二级索引那样最多只能匹配1条记录，所以这种ref访问方法比const差了那么一丢丢，但是在二级索引等值比较时匹配的记录数较少时的效率还是很高的（如果匹配的二级索引记录太多那么回表的成本就太大了），跟坐高铁差不多。

## ref_or_null

<img src="./picture/普通二级索引与聚簇索引示意图.png" width="" alt="聚簇索引示意图">

> SELECT * FROM single_demo WHERE key1 = 'abc' OR key1 IS NULL;

可以看到，上边的查询相当于先分别从idx_key1 索引对应的 B+ 树中找出key1 IS NULL 和 key1 = 'abc' 的两个连续的记录范围，然后根据这些二级索引记录中的id值再回表查找完整的用户记录。

## range

> SELECT * FROM single_table WHERE key2 IN (1438, 6328) OR (key2 >= 38 AND key2 <= 79);

我们当然还可以使用全表扫描的方式来执行这个查询，不过也可以使用二级索引 + 回表的方式执行，如果采用二级索引 + 回表 的方式来执行的话，那么此时的搜索条件就不只是要求索引列与常数的等值匹配了，而是索引列需要匹配某个或某些范围的值。

设计MySQL 的大叔把这种利用索引进行范围匹配的访问方法称之为：range。

## index

> SELECT key_part1, key_part2, key_part3 FROM single_table WHERE key_part2 = 'abc';

由于`key_part2` 并不是联合索引 `idx_key_part` 最左索引列，所以我们无法使用 `ref` 或者 `range` 访问方法来执行个语句。但是这个查询符合下边这两个条件：

- 它的查询列表只有3个列：key_part1 , key_part2 , key_part3 ，而索引 idx_key_part 又包含这三个列。
- 搜索条件中只有key_part2 列。这个列也包含在索引 idx_key_part 中。

也就是说我们可以直接通过遍历idx_key_part 索引的叶子节点的记录来比较 key_part2 = 'abc' 这个条件是否成立，把匹配成功的二级索引记录的key_part1 , key_part2 , key_part3 列的值直接加到结果集中就行了。由于二级索引记录比聚簇索记录小的多（聚簇索引记录要存储所有用户定义的列以及所谓的隐藏列，而二级索引记录只需要存放索引列和主键），而且这个过程也不用进行回表操作，所以直接遍历二级索引比直接遍历聚簇索引的成本要小很多，设计MySQL 的大叔就把这种采用遍历二级索引记录的执行方式称之为：index。
## all