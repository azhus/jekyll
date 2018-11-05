---  
layout: post  
title: "只需10分钟，轻松模拟一次APT攻击"
date: 2017-02-28
categories:  信息安全科普     
comments: true
description:   今天小编将为大家安利一款信息安全教育套装软件，包含了从基于网页的远程控制工具到勒索软件，全面而实用。
tags:
    - 信息安全科普  
---  
今天小编将为大家安利一款[信息安全教育套装软件](http://shinosec.com)，包含了从基于网页的远程控制工具到勒索软件，全面而实用。

![](http://127.0.0.1:4000//resources/images/a1.png) 

#### SHinoBOT

ShinoBOT是一款RAT（远程访问木马）模拟器，我们可以通过ShinoC2（C＆C服务器）远程控制被感染的机器，并执行任意的Windows命令，比如：上传、下载文件，截屏等你所需要模拟的所有APT攻击。

#### SHinoLocker

ShinoLocker是一款勒索软件模拟器。ShinoLocker和实际ramsomware之间的区别是，我们可以免费获取到解密密钥。

#### SHinoEncode

ShinoEncode是在ShinoBOT及其C2通信，以及其他ShinoXXX中出现字符串混淆时为了避免模式匹配检测而使用的一种编码方式。

#### SHinoProxy

ShinoProxy是一个重定向ShinoBOT流量的PHP程序。其目的主要是利用ShinoBOT.com的黑名单来逃避检测。

#### SHinoBuilder

我们可以利用ShinoBuilder自定义ShinoBOT家族的恶意软件模拟器，改变C＆C URL，更改用户代理等，而且每当我们创建一个新的二进制文件时，它会使用ShinoEncode改变二进制的静态字符串。

#### SHinoProxy

我们可以利用ShinoProxy自定义Shino家族的的恶意软件模拟器，改变C＆C URL，更改用户代理等。

#### SHinoCAPTCHA

ShinoCAPTCHA是一个不需要数据库，出站连接，cookie的基于PHP的验证码。

#### SHinoVis

ShinoVis是一个可视化的聚类数据。例如，如果你有一个恶意软件列表和CSV以及与其相关的C＆C列表，你可以复制粘贴到ShinoViS来查看这些数据的关系。

#### SHinoBOT套件

ShinoBOT套件是一个恶意软件包，其中包含了RAT仿真器（ShinoBOT.exe），Downloader/Dropper(ShinoDownloader.exe)，加密，C&C服务器(ShinoC2)，软件交付服务器（ShinoMAL.mooo.com），诱骗文件等等，并且所有的这些都是定制的。我们可以利用ShinoBOT套件来创建属于自己的恶意软件，而且还可以利用它来模拟最近的针对性的攻击。

对于为什么使用SHinoBOT套件，官方文档给出了以下的理由：

* 目前有一系列新的安全工具用来检测或响应未知威胁，例如：
 * 基于Sandbox的恶意软件检测系统
 * ETDR（端点威胁检测和响应）
 * SIEM（安全信息和事件管理器）
 * 安全分析/网络取证

* 但是这些新产品很难被评估，例如：
 * 可以通过签名检测到已知的恶意软件，却没有提到未知的恶意软件
 * 可以模拟逼真的APT，但却需要掌握高技能，花费大量的时间及金钱

**作为该软件的重头戏，ShinoBOT可以被用来模拟一次复杂的APT攻击，而且全程仅需短短的10分钟**

![](http://127.0.0.1:4000//resources/images/a2.jpg) 

**听起来有点厉害哦~**


在攻击之前，首先需要完成如下的准备工作：

* 一个诱饵文件（大小<50KB）
* 一个合法的文本文件
* 从ShinoSec.Com上下载ShinoBOT套件

##### STEP1：加密RAT

![](http://127.0.0.1:4000//resources/images/a3.png) 

* 执行ShinoBOTSuite.exe
* 选择RAT
* 可以通过Set Ascii设置加密密钥或密码
* 点击[加密]和[下一步]

##### STEP2：上传RAT

![](http://127.0.0.1:4000//resources/images/a4.png) 

* 选择上传服务器（默认为ShinoMal.mooo.com）
* 点击[上传]和[下一步]

提示：加密的RAT隐藏在小猫图像中，因此你可以将其
上传到一些图像共享服务器而不是ShinoMal.mooo.com

##### STEP3:创建下载器

![](http://127.0.0.1:4000//resources/images/a5.png) 

* 选择诱饵文件
* 点击[创建下载器]和[下一步]

##### STEP4：上传下载器

![](http://127.0.0.1:4000//resources/images/a6.png) 
* 选择上传服务器
* 点击[上传]和[下一步]

##### STEP5：创建EXPLOIT

![](http://127.0.0.1:4000//resources/images/a7png) 

* 选择图标路径
* 点击[创建]和[退出]
* 之后将在桌面上出现快捷方式

ShinoBOT套件包含加密，隐写，DGA（用于RAT SHinoBOT.exe），快捷方式攻击，图标伪装等。但无论如何，它是非常安全的。你可以在钓鱼邮件中发送快捷方式，大多数邮件服务器都允许ZIP文件夹上的快捷方式。当受害者点击快捷方式便会被RAT感染而不被检测到。

**以上便是今天的安利内容~如果想要更直观的了解它的工作流程还可以登陆到官网观看ShinoBOT的使用视频教程哦~**

#### 参考文献：

[shinosec](http://shinosec.com)