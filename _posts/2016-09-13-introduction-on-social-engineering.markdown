---  
layout: post  
title: "欺骗的艺术——黑客的社会工程学"
date: 2016-09-13
categories:  传媒信安     
comments: true
description:   这次我们不研究算法编码漏洞挖掘，研究你 ：）
tags:
    - 传媒信安
---  
话说近日一位选修密码学的同学晒了课本——


![](http://127.0.0.1:4000//resources/images/e1.jpg) 

什么？这也可以？

![](http://127.0.0.1:4000//resources/images/e2.jpg) 

转念一想，还真是合情合理，无法反驳。

**事实上，人，才是信息安全链路里最脆弱的一个环节：**

![](http://127.0.0.1:4000//resources/images/e3.png) 

可能硬件软件全部更新，防火墙全无漏洞，技术人员兢兢业业，千里之堤却最终毁于人这一环。

而作为黑客，还有更为优雅的攻击姿势。不用威胁、勒索、折磨别人，也不用施展什么“购买密钥攻击”，**我们称之为，社会工程学。**

在维基百科里，社会工程学的定义是：

>**通过与他人的合法地交流，来使其心理受到影响，做出某些动作或者是透露一些机密信息的方式。这通常被认为是一种欺诈他人以收集信息、行骗和入侵计算机系统的行为。**

一个不需要高超编码技术的攻击，一个不再钻研于算法漏洞而仅仅是利用人性弱点的攻击，有时竟会成为最有效的手段。

或许你曾遭遇过社会工程学，或许你至今还没意识到自己遭遇了社会工程学；也许你自认意志坚定不会轻易被骗，也许你向来谨慎周密不相信会让人有空可钻。那么不妨一起来看看，
##人都有哪些可以利用的弱点？

#### 1. 人的懒惰——弱口令：
* 手机号/生日/纪念日（很容易猜啊(￢_￢)）
* 123456/888888/000000（死定了啦！）
* 名字（……加上数字也没用啊喂！）
* 全小写英文单词（password哈哈哈哈哈哈！）

比如这样——

![](http://127.0.0.1:4000//resources/images/eee.png) 


![](http://127.0.0.1:4000//resources/images/e4.jpg) 


还有——

* **多个账号使用相同密码**（暴露了一个，等同于裸奔。或者你自己没暴露，网站被拖库：CSDN  明文密码库/天涯明文密码库等等）

说到拖库，要知道我们的个人信息被泄露了多少，就不用新闻举例了，直接来个网址吧，戳这个—>** [社工库——找回你丢失的密码…密码……](http://www.xiumima.com/)**![](http://127.0.0.1:4000//resources/images/ee.png) 


#### 2. 人的粗心——机密信息管理不当
* 用软件自带的“记住密码”功能
* 账号密码记在本子上/文本文档/注释/邮件里

![](http://127.0.0.1:4000//resources/images/eeee.png) 

![](http://127.0.0.1:4000//resources/images/e5.jpg) 

黑客还能怎样能获取信息呢？
* 装个隐藏摄像头，观察你和你的密码。
* 翻垃圾箱。（你的快递单都撕了吗？）


![](http://127.0.0.1:4000//resources/images/e6.jpg) 



#### 3. 人的贪心——馅饼就是陷阱：
* 同学，扫个二维码吗？扫码送礼物哦~
* 哇，这里有个免费WiFi！

**啊，GG**

![](http://127.0.0.1:4000//resources/images/e7.jpg) 


## 黑客还能怎么骗你？

#### 1. 接近你，跟你交朋友
**然后问到/看到/捡到你的密码。**

哦，他们会怎么跟你交朋友？
这个嘛…
* 会聊天
* 长得好看
* 长得好看
* 长得好看

#### 2. 装作你的BOSS/保安/老师/师哥师姐…
**然后很急地问你密码。**

要知道，有变声软件这种存在，来电显示也可以被篡改。


![](http://127.0.0.1:4000//resources/images/e8.png) 

#### 3. 谈话中一点小小的暗示

因为…
* 大多数人对陌生人比较有礼貌
* 部分专业人士有炫耀的欲望
* 被称赞后人们通常会越说越起劲
* 人们通常比较诚实，没感到威胁时问什么答什么
* 人们对貌似关心自己的人会很友善


## 最后…

![](http://127.0.0.1:4000//resources/images/e8.gif) 

嗯，以及，如果你看到一个文件，名字是“千万不要点我！”，我相信总有人会忍不住点开的…然后GG

可是，这确乎已经是坦诚无比啊！


![](http://127.0.0.1:4000//resources/images/e9.jpg) 



---

### 一些细思极恐的网站

* [找回你](http://www.zhaohuini.com/)——找回你注册过哪些网站
* [Whois查询](http://whois.chinaz.com/)——就是一个用来查询域名是否已经被注册，以及注册域名的详细信息的数据库（如域名所有人、域名注册商、域名注册日期和过期日期等）。通过域名Whois服务器查询，可以查询域名归属者联系方式，以及注册和到期时间。
* [豆瓣人肉搜索](https://cse.google.com/cse/home?cx=011499735007354739784:5deh4xhzc6e) 
* **[查开房记录](http://www.zhaokaifang.com/)——汉庭、如家、七天等，据说有 2000 万条记录。**


![QQ图片20160829191628.jpg](/storage/app/uploads/public/57d/7cf/6ec/57d7cf6ecc62c157099824.jpg)



---
### 书籍推荐：
##### 《反欺骗的艺术》 (凯文.米特尼克著)




---
参考资料：

http://www.tripwire.com/state-of-security/security-awareness/5-social-engineering-attacks-to-watch-out-for/

https://en.wikipedia.org/wiki/Social_engineering_(security)

https://www.zhihu.com/topic/19596249/hot