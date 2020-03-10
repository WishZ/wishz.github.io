---
title:  "PHP 类的静态数据成员"
tags: io asynchronous socket signal  
---

最近看学堂在线`C++`视频，遇到一个类的静态成员例子，由此想到`PHP`中的静态成员
<!--more-->

代码如下：
``` php
<?php

class test {
    static $a = 0;

    public $b = 0;
    
    public function __construct()
    {
        self::$a++;
        $this->b++;
    }
}


new test();

new test();

new test();

var_dump(test::$a);//3

var_dump((new test())->b);//1

```


