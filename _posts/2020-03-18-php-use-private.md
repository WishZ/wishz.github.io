---
title:  "php call方法使用"
tags: Redis
---

php 使用 call 方法调用类里面的私有方法
<!--more-->

代码如下：
``` php
class B {
    private $b = 1;
}

$getPrivateProperty = function ($property) {
    return $this->$property;
};

$b = $getPrivateProperty->call(new B(),'b');
var_dump($b);//1
```