---  
layout: post  
title: "NSA/GCHQ利用Juniper网络设备漏洞进行网络监控"
date: 2015-12-29
categories:  传媒信安     
comments: true
description:  Juniper Networks发布紧急更新，修复ScreenOS上一个“未授权代码”。攻击者可以利用该漏洞解密NetScreen设备的VPN流量。
tags:
    - 传媒信安
---  
**Juniper Networks（瞻博网络）现后门：万能密码登录设备、可解密VPN流量**


*Juniper Networks发布紧急更新，修复ScreenOS上一个“未授权代码”。攻击者可以利用该漏洞解密NetScreen设备的VPN流量。*

Juniper网络公司(中文名：瞻博网络)致力于实现网络商务模式的转型。作为全球领先的联网和安全性解决方案供应商，Juniper网络公司对依赖网络获得战略性收益的客户一直给予密切关注。公司的客户来自全球各行各业，包括主要的网络运营商、企业、政府机构以及研究和教育机构等。Juniper网络公司推出的一系列联网解决方案，提供所需的安全性和性能来支持全球最大型、最复杂、要求最严格的关键网络。

Juniper还没有对这个代码漏洞给予任何的评论，但是Juniper的产品已经被从国家安全局的产品目录中筛选了出来。2013年12月，Jacob Appelbaum、Judit Horchert和Christian Stocker在Der Spiegel发表的一篇文章中指出，NSA的FEEDTHROUGH植入是为Juniper防火墙量身定制的，给美国政府留下了一个永久后门，可随时访问这些高端网络设备。NetScreen应用是一款高端企业防火墙和VPN产品，被通信商和数据中心广泛使用，ScreenOS是运行在这些应用的操作系统。

**内部代码审计发现两枚漏洞**

Juniper高级副总裁兼首席信息安全官Bob Worrall称，在最近的内部代码审计过程中发现了两枚漏洞，**影响ScreenOS 6.2.0r15—6.2.0r18，6.3.0r12—6.3.0r20版本**。

**其中一个是未授权代码漏洞，可解密VPN流量；另外一个可允许攻击者通过SSH或者telnet远程管理访问设备。Juniper提到这些系统的访问会被记录，密码认证也会成功，但是攻击者可改变或者删除日志条目。**

“当我们发现这些漏洞时，我们立即对这一问题进行了调查研究，开发并发布最新版本ScreenOS的修复方法。目前为止我们并未收到这两个漏洞被利用的报道，但是我们还是强烈建议用户更新系统。”
SRX以及其他基于Junos的系统不受影响，Junos是该公司用于路由、交换、安全的一个高性能网络操作系统。

**CVE-2015-7755细节：**

利用该漏（hou）洞(men)，攻击者可以通过SSH、Telnet以root身份远程登陆ScreenOS设备，直接获得设备控制权！通过shodan搜索可以发现：目前国内暴露在公网的netscren设备数量为2172！

![](http://127.0.0.1:4000//resources/images/R15.png) 

ssh root@存在漏洞设备的ip后门密码：<<< %s(un='%s') = %u


![](http://127.0.0.1:4000//resources/images/R16.png) 


我们的观点：和斯诺登事件一样，类似的新闻是国产信息安全产业发展的良好的外部事件。使用国外私有商业化的网络设备来构建我国的网络基础设施是把狼外婆请回家当保姆一样的行为，说不定哪天就被反噬了。。。所以呢，事情还是要自己做，革命尚未成功，同学们仍需努力啊~~~

[阅读全文](http://mmbiz.qpic.cn/mmbiz/ibnYD3H5j7LPRCqDiaX7VW9vG1bIppibP0pibInzYFUJiaIMJmWlxd6pGK8M75I9gPJeJe3LNqLOrKMWom2w2UQtyRg/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1)