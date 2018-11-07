# 数据库
* [MySQL vs MongoDB](#compare)

> Resources:   
 [NoSQL Databases Explained](https://www.mongodb.com/nosql-explained?jmp=footer)


## <a id="compare">MySQL vs MongoDB</a>

> 事务关系支持？    
> 分布式存储  
> 3C

* [Mongodb 与 MySQL对比](https://www.cnblogs.com/web-fusheng/p/6884759.html)

**主键(_id)影响:**

```
指定主键 vs 不指定主键
MongoDB充分利用内存作为缓存，当数据溢出内存时再写入磁盘
所以不指定主键时，Mongodb会根据计算机特征值、时间、进程ID和随机数来生成唯一_id
如果指定主键的话，MongoDB会遍历所有的数据，包括读磁盘，所以效率远低于不指定_id
MySQL的效率受此影响不大。
```
