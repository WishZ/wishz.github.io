---
title:  "macos 抓包工具 charles 的使用"
tags: charles
---

macos 抓包工具 charles 的使用
<!--more-->

### 对浏览器 http 抓包

1. 打开 工具栏 =》 proxy =》 Proxy Settings
2. 开启 Enable transparent HTTP proxying 
3. macOS 栏下开启 Enable macOS proxy
4. 浏览器浏览http网站 即可抓包

### 对浏览器 https 抓包

1. 安装证书 点击 Help -- SSL Proxying -- Install Charles Root Certificate
2. 安装后默认是不信任状态 ， 在钥匙串中 ， 双击刚才安装的证书 点开左边的信任 ，选择始终信任，弹出账户密码验证
3. 在 charles 中选中 https 链接 ， 鼠标右键，选择 Enable SSL Proxying , 即可抓包，查看数据

### 对手机端抓包
1. 点击 Help -- SSL Proxying -- Install Charles Root Certificate on a Mobile Device or Remote Browser
2. 手机端与 mac 处于同一 wifi  , 设置代理IP:charles 点击Help -- Local IP Addresses 查看IP , 端口号使用 工具栏 =》 proxy =》 Proxy Settings 中配置的HTTP端口号
3. 点击 Help -- SSL Proxying -- Install Charls Root Certificate On a Mobile Device or Remote Browser 按照提示在手机端安装证书并设置信任证书

