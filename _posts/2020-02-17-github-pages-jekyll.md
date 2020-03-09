---
title:  "使用github pages + jekyll 搭建个人网站"
tags: github jekyll
---

一直想记录一下自己的成长轨迹，于是就搭一个博客，好在Github提供了一个平台，省去了备案的麻烦，可以集中精神搞好自己的网站。

<!--more-->
#### 创建 github 账号
若无github账号，在[此处](https://github.com)进行注册<br />

#### 新建仓库
使用github管理个人网站时，对应的仓库命名是有要求的，必须以username.github.io命名，username是github用户名，此时网站对应的代码仓库分支为master

#### 选择主题
github有很多模板主题提供选择，相关代码会自动生成，目前本博客使用的是第三方模板，点[此处](https://github.com/kitian616/jekyll-TeXt-theme)可浏览<br />


#### 关于 jekyll
jekyll 是一种静态站点生成工具，是发表文章的过程简化为添加并撰写一篇markdown文档
相关内容查看[官方文档](https://jekyllcn.com/docs/home/)


#### 以下是遇到的一些坑
1.本地使用的是Windows10 + ubuntu的linux子系统，最好不是使用`sudo apt-get install jekyll`来安装jekyll ，这样会导致后面遇到各种版本不匹配问题
  ```
  # 先卸载
  sudo apt remove jekyll
  sudo apt autoremove
  which jekyll
  sudo rm /usr/local/bin/jekyll
  # 重新开始安装
  sudo apt-get install ruby-dev
  sudo gem install jekyll
  sudo gem install bundler
  ```
2.给gem bundle添加国内代理 不然特别慢
  ```
  gem sources --add https://gems.ruby-china.com --remove https://rubygems.org/
  bundle config 'mirror.https://rubygems.org' 'https://gems.ruby-china.com'
  ```
3.进入username.github.io项目目录
  ```
  sudo apt-get install libmysqlclient-dev
  sudo bundle install
  sudo bundle update listen
  #启动服务
  bundle exec jekyll server
  #如要预览草稿
  bundle exec jekyll server --drafts
  ```
4.服务启动后 打开 http://127.0.0.1:4000/ 就可以在本地预览效果~