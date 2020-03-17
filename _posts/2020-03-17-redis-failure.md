---
title:  "Redis 缓存穿透、缓存击穿、缓存雪崩、热点数据失效 "
tags: Redis
---

Redis 缓存穿透、缓存击穿、缓存雪崩、热点数据失效
<!--more-->
#### Redis 缓存穿透
> 查询一条数据库中不存在的数据，缓存和数据库都查询不到这条数据，但是每次请求都会打到数据库上面。

解决：
1. 进行参数过滤，过滤掉此种无意义key
2. 在Redis中存入此key的值为null,后面查询这个key的时候，直接返回null

#### Redis 缓存击穿
> 


#### Redis 缓存雪崩

#### Redis 热点数据失效



参考：
> https://juejin.im/post/5c9a67ac6fb9a070cb24bf34