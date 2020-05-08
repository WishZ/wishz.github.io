---
title:  "docker 的一些常用命令"
tags: docker
---

记录一下docker的常用命令
<!--more-->

> 显示所有容器IP地址：

```shell
docker inspect --format='{{.Name}} - {{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $(docker ps -aq)
```

> 停止所有容器

```shell
 docker stop $(docker ps -a -q) 或者 docker stop $(docker ps -aq)
```

> 删除所有容器

```shell
 docker rm $(docker ps -a -q) 或者 docker rm $(docker ps -aq) 
```

> 删除所有image 


```shell
docker rmi $(docker images -q)
```

> 强制删除image

```shell
docker rmi -f $(docker images -q)
```