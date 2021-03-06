---
title:  "MySQL 基础"
tags: MySQL
---

MySQL 死锁的产生与解决方案
<!--more-->
#### MySQL 数据库事物必备的标准特征

> 原子性(atomicity)：一个事物必须被视为一个不可分割的最小工作单元，整个事物中的所有操作要么全部成功提交，要么全部回滚，对于一个事物来说，不能只执行其中的一部分操作。

> 一致性(consistency)：数据库总是从一个一致性状态转换到另一个一致性状态。

> 隔离性(isolation)：通常来说，一个事物所做的修改在最终提交前，对其他事物是不可见的。对不同的事物隔离级别有不同体现。

> 持久性(durability)：一旦事物提交，则其所做的修改会永久的保存到数据库中。

#### MySQL 数据库隔离级别

##### READ UNCOMMITED (未提交读)

> 事物中的修改，即使没有提交，对其他事物也是可见的，事物中读取未提交的数据，被陈队脏读(Dirty Read)。

##### READ COMMITED (提交读)

> 一个事物从开始直到提交之前，所做的任何修改对其他事物都是不可见的，也可被叫做不可重复读。

##### REPEATABLE READ (可重复读)

> 在同一个事物内的查询都是事物开始时刻一致的，InnoDB 默认级别。在SQL标准中解决了脏读的问题，但是还存在幻读，幻读是指当某个事物在读取某个范围内的记录时，另外一个事物又在该范围内插入了新的记录，当之前的事物再次读取时，会产生幻行。InnoDB 和 XtraDB 存储引擎通过多版本并发控制( MVCC )解决了幻读的问题。

##### SERIALIZABLE (可串行化)

> 强制事物串行执行，避免前面说的幻读问题。会在读取的每一行数据上都加锁，所以可能导致大量的超时和锁争用的问题。

#### MySQL 死锁

> 两个或多个事物在同一资源上相互占用，并请求锁定对方占用的资源，从而导致恶性循环的现象。当多个事物试图以不用的顺序锁定资源时，就可能产生死锁

> InnoDB目前处理死锁的方法是，将持有最少行级排他锁的事物进行回滚

> 死锁发生以后，只有部分或者完全回滚其中一个事物，才能打破死锁。


#### MySQL 多版本并发控制

> 通过保存数据在某个时间点的快照来实现

