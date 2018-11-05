---  
layout: post  
title: "OpenSSL漏洞引爆，超1100万HTTPS网站躺枪！"
date: 2016-03-02
categories:  传媒信安     
comments: true
description: 继今年1月28日OpenSSL爆出私钥恢复漏洞后，OpenSSL又再次爆出DROWN攻击（淹没攻击）漏洞，这将1100万的HTTPS网站置于险境。小编组即刻展开激烈讨论，看了看国内老百姓普遍访问的网站还有多少没有打补丁。前方高能预警！！！
tags:
    - 传媒信安
---  
![](http://127.0.0.1:4000//resources/images/Q7.jpg) 

<font color='red'>继今年1月28日OpenSSL爆出私钥恢复漏洞后，OpenSSL又再次爆出DROWN攻击（淹没攻击）漏洞，这将1100万的HTTPS网站置于险境。小编组即刻展开激烈讨论，看了看国内老百姓普遍访问的网站还有多少没有打补丁。前方高能预警！！！</font>

![](http://127.0.0.1:4000//resources/images/Q8.jpg) 

![](http://127.0.0.1:4000//resources/images/Q9.jpg) 

经小编亲测，发现淘宝taobao.com没有问题，支付宝alipay.com有一个二级域名有漏洞，360也及时发现该新闻而安然无恙，但是以京东jd.com、腾讯qq.com、百度baidu.com为首的都已经将测试网页染成一片红色。

<font color='red'>那么下面小编就为大家介绍介绍这次的漏洞以及如何测试并防范！</font>

首先，这是一种新的致命的OpenSSL安全漏洞，该漏洞会影响HTTPS和依靠SSL和TLS等服务，也就是一些互联网安全的必要加密协议。这些协议允许每个人在互联网上浏览网页，使用电子邮件，网上购物时没有第三方能够读取通信发送即时消息。

之所以被称为**淹没**，是因为今日披露的OpenSSL中的安全漏洞可以允许攻击者低成本的破解加密和读取或窃取敏感的通信，包括密码，信用卡号码，商业秘密或财务数据。根据漏洞发现者测量的结果表明33％的HTTPS被测试站点存在该漏洞，很容易受到攻击。

## 攻击者可以获得什么？
用户和服务器之间的任何通信。这通常包括，但不限于，用户名和密码，信用卡号，电子邮件，即时消息，以及敏感文件。在一些常见的场景，攻击者还可以冒充一个安全的网站和拦截或更改用户看到的内容。

## 我们的网站这么脆弱？
现在流行的服务器和客户端使用TLS加密，然而，由于错误配置，许多服务器仍然支持SSLv2，这是一种古老的协议，实践中许多客户端已经不支持使用SSLv2。

DROWN攻击威胁到还在支持SSLv2的服务端和客户端，他允许攻击者通过发送probe到支持SSLv2的使用相同密钥的服务端和客户端解密TLS通信。

![](http://127.0.0.1:4000//resources/images/Q10.jpg) 

允许SSLv2连接，比想象中的要常见，由于错误配置和不当的默认配置，我们调查17%的HTTPS服务器一直支持SSLv2连接

私钥被使用于其他支持SSLv2连接的服务，许多公司不允许使用相同的证书和私钥在他的web和email服务，例如，下面这个案例,如果email服务支持SSLv2，但是web服务不支持，攻击者能够利用email服务的SSLv2漏洞切断到web服务器的TLS的连接。

![](http://127.0.0.1:4000//resources/images/Q11.png) 

## 如何测试该漏洞？
<font color='red'>可以通过https://test.drownattack.com/?site=你的站点来查看是否受影响</font>

![](http://127.0.0.1:4000//resources/images/Q12.png) 


## 怎么保护我自己？
##### 作为服务器管理员：
确保你的私钥不适用于其他的支持SSLv2服务，包括web，smtp，imap，pop服务等。禁止服务器端的SSLv2支持。如果是OpenSSL，可以参考安装最新的补丁和操作辅导。


```
https://www.openssl.org/blog/blog/2016/03/01/an-openssl-users-guide-to-drown/
```


Microsoft IIS (Windows Server)：IIS 7和以上的版本默认已经禁止了SSLv2。

详细的漏洞描述原理报告：https://drownattack.com/

##### 作为广大的草根用户：
我们能做的只有​暂停对这些存在漏洞的服务网站的访问，直到厂商修复了这些漏洞，坐等我们的更新通知~

小编发完这篇，也要收起手机、收起电脑，去学习啦，做一个安静的学霸程序媛，各位看完点赞转发后，也赶紧洗洗睡吧！

###### 参考文献：
The Hacker News：


```
http://thehackernews.com/2016/03/drown-attack-openssl-vulnerability.html
```


DROWN ATTACK 官网：https://drownattack.com/