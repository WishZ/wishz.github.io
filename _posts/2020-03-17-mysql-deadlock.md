---
title:  "MySQL 死锁的产生与解决方案 "
tags: Redis
---

MySQL 死锁的产生与解决方案
<!--more-->
#### MySQL 数据库事物必备的标准特征
> 原子性(atomicity)：一个事物必须被视为一个不可分割的最小工作单元，整个事物中的所有操作要么全部成功提交，要么全部回滚，对于一个事物来说，不能只执行其中的一部分操作。

> 一致性(consistency)：数据库总是从一个一致性状态转换到另一个一致性状态。

> 隔离性(isolation)：通常来说，一个事物所做的修改在最终提交前，对其他事物是不可见的。对不同的事物隔离级别有不同体现。

> 持久性(durability)：一旦事物提交，则其所做的修改会永久的保存到数据库中。

#### MySQL 数据库隔离级别
```


```

#### MySQL 处理死锁的方式


#### 应用层避免死锁的方式
