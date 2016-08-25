---
layout: post
title: "使用 Charles 获取 https 的数据"
date:   2016-08-24 18:27:24 -0700
categories: himdd update
---

我使用的 Charles 版本是 4.0，获取下载地址[https://www.charlesproxy.com/download/](https://www.charlesproxy.com/download/)，下面进入正题：

如果英文比较好，看这里[https://www.charlesproxy.com/documentation/using-charles/ssl-certificates/](https://www.charlesproxy.com/documentation/using-charles/ssl-certificates/)

## 配置 Charles 根证书 (参见英文文档 Mac OS X ）

* "首先打开 Charles" -> "SSL Proxying" ->"Install Charless Root Certificate"

* 之后会弹出钥匙串。系统默认是不信任 Charles 的证书的，此时对证书右键，在弹出的下拉菜单中选择 "显示简介" -> "使用此证书时" -> "把使用系统默认改为始终信任。
 
*然后关闭，就会发现 charles 的证书已经被信任了

## 在移动设备上配置证书 (参见英文文档 iOS devices ）
* "Proxy" -> "Proxy settings..." -> 查看端口（一般为8888）
* 查看本机ip 自己百度吧
* 在移动设备的wlan设置代理。
* 然后打开手机的浏览器，输入 http://www.charlesproxy.com/getssl，（这是文档上给出的iOS devices 的方法，经验证android也是ok） 然后下载安装证书。如果是老版，那么把链接换成https://www.charlesproxy.com/documentation/additional/legacy-ssl-proxying/，点击安装 itself 后面的 here 就可以了。 
* Proxy" -> "SSL Proxy settings..." -> "SSL Proxying" ->"勾选Enable SSL Proxying" ->"点击添加，弹出下面的对话框，Host 表示你要抓取的 ip 地址或是链接，Port 填写 443"

## 应该可以看到https的数据
 折腾了半天发现网上已经有前人给出教程了,如果想看图的同学 [点击](http://www.jianshu.com/p/235bc6c3ca77)
