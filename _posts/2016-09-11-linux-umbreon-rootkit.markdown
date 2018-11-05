---  
layout: post  
title: "信安武林 | 去吧，皮卡丘！"
date: 2016-09-11
categories:  传媒信安     
comments: true
description:   如今是个电子现金时代，大家身上都不会装大量现金，这种时代特征让小偷这个职业似乎走向了陌路。可是，如果小偷这个职业也与时俱进，进化出一只能偷走你电子现金的无形之手，又该如何防范呢？
tags:
    - 传媒信安
---  
火遍全球的一款游戏Pokemon不仅成功造就了一大批走路低头族，其话题度也一直在游戏界中居高不下，无论是被指“间谍软件”，还是从贾斯汀·比伯到希拉里·克林顿的青睐，一直热议傍身。

这不，Pokemon的一名忠实粉丝就以Pokemon的月精灵Umbreon为主题开发出一个新的Linux rootkit病毒。

![](http://127.0.0.1:4000//resources/images/f1.gif) 

这确定不是Pokemon在信安界的一次广告植入？？？

该新闻首先由TrendMicro的前瞻性威胁研究小组曝出，他们从一个可信任的合作伙伴那里获得了这个新的rootkit病毒家族样本 (ELF_UMBREON family)。

鹅妹子因！！！好想知道这个小伙伴是谁？

![](http://127.0.0.1:4000//resources/images/f2.jpg) 

该病毒目标就是针对Linux系统，包括嵌入式设备和其他任何运行Intel和ARM处理器的系统。

Umbreon的开发始于2015年年初，但开发者VXer至少自2013年就开始在地下进行网络犯罪，Umbreon早已被地下论坛和IRC频道的地下工作者说是防不胜防的。

**那么Umbreon是如何做到逃避检测、隐于无形的呢？**

### 不容小觑的ring3级别rootkit

![](http://127.0.0.1:4000//resources/images/f3.jpg) 

rootkit因其难被检测而被标为病毒界的顽固分子，深藏功与名，目的就是要在与管理员、分析师、用户、扫描器、电脑医生以及系统工具过完招后，成功驻留下来。当然，rootkit并不是真正的隐逸者，而是会植入一个后门、使用命令控制服务器（C&C server，即command&control server）来控制和监听被感染机器。

当然，代码的运行模式可以分为以下几个等级：

* 用户模式（ring3）
* 内核模式（ring0）
* 虚拟机管理程序（ring-1）
* 系统管理模式（ring-2）

通过在一些母板或其他设备上运行该rootkit，研究人员发现它是一个ring3级别的病毒，虽然级数越低，越难检测和防御，但不代表一个ring3级别的rootkit就很好对付哟！

![](http://127.0.0.1:4000//resources/images/f4.jpg) 

ring3 rootkit（或用户态高级木马）不会加载内核（新）对象到系统（运行时）。

> ring3的rootkit不需要以驱动程序模式运行，没有运行在ring0级别的代码，通常在稳定性和兼容性方面会比ring0级别rootkit更好。换句话来说，ring3级别的木马更容易实现与系统中其他程序“和平共处”，很少造成系统运行“卡、慢、顿”，从而避免系统管理员通过常规性能监控发现系统异常。

但是它可以利用hook技术调用系统提供给应用程序执行重要操作的的核心库功能的接口，例如文件读写操作、生成进程或者通过网络发送数据包。

### 跨平台，宝宝就是这么任性

该rootkit纯c语言编写，除了一些扩展工具是用Python和bash脚本编写的。

研究者发现它可以在x86、x86-64以及ARM（树莓派就使用了ARM架构的CPU）三个平台上成功运行，当然，ring3级别代码本来就不依赖于特定平台，十分便携。

这么做，当然是开发者有意为之啦，嘿嘿，就是这么任性！

![](http://127.0.0.1:4000//resources/images/f4.gif) 

### 江湖必杀技之后门认证

安装过程中，Umbreon创建一个空的Linux用户以便于攻击者可以控制系统，该后门账户可以通过任何Linux可插入认证模块（PAM）支持的认证方式通过认证，包括SSH。

这个用户有一个特殊的组ID（GID），用于该rootkit检查是否有攻击者试图进入系统。当然，在/etc/passwd下是看不到这个用户的，因为libc（C标准库）功能函数已经被Umbreon给hook了。

下图显示的是后门帐号通过SSH成功登入系统显示的欢迎界面~~~

![](http://127.0.0.1:4000//resources/images/f5.png) 

### Espeon后门程序

Espeon中文是**太阳精灵**的意思，总之，为了凑一对，这位粉丝开发者真是辛苦了。。。

![](http://127.0.0.1:4000//resources/images/f6.jpg) 

Espeon这是个纯用C语言编写的基于libpcap的后门程序，当已认证用户连接它时，会生成一个shell。它可以通过指令连接到一个攻击者的机器，作为一个绕过防火墙的反向shell。

Espeon可以捕捉到所有到达被害主机的主以太网接口的TCP流量，一旦接收到具有特殊字段的数据包，它就会回连到这个数据包的源IP地址，以下列出了Espeon设置的自动回连触发条件包含的报文特征字段：

* Sequence number (SEQ)：0xc4
* Acknowledgement number (ACK)：0xc500
* IP Identification (ID)：0x0fb1

攻击者会在发送给目标机器的数据包中设置这些条件，如果这三个值都匹配，后门就会回连到这个IP地址。

### 如何检测Umbreon？

正所谓山外有山、天外有天，黑客外除了有黑客，还有正义之士！！！

![](http://127.0.0.1:4000//resources/images/f7.jpg) 

咳咳~直接切入正题哈，你会发现Linux系统中大多数的工具都是用c语言编写的，甚至用Perl、Python、Ruby、PHP等其他脚本语言编写的最终会都调用GNU C库包装它们的接口（用c编写的），因为Umbreon的库hook了libc功能函数，所以为了检测Umbreon，必须开发出一个不用libc的可靠工具。

有一个方法就是开发一个小工具，可以列举出Umbreon rootkit调用了Linux系统内核的文件夹的内容。这样就可以绕过任何Umbreon安装的恶意的c库，如果输出包含一个或多个名字以libc.so开始，紧跟着一个随机整数的文件，这就表示你这个系统已经中招了！！！

当然，大牛们已经编写出了可以检测这个病毒**YARA 规则**~~~，[下载](http://documents.trendmicro.com/assets/20160905-umbreon-yara.txt)

![](http://127.0.0.1:4000//resources/images/f8.jpg) 

那么问题来了！神马是YARA 规则呢？

> 萌主科普：YARA 规则可基于文本或二进制模式创建恶意软件家族描述信息，是帮助恶意软件研究人员识别和分类恶意软件样本的开源工具，属于一种静态分析工具。

YARA的规则可以复杂和强大到支持通配符、大小写敏感字符串、正则表达式、特殊符号以及规则的按条件与或非组合。具体可以应用到恶意软件的基于签名的检测、VirusTotal私有API使用自己编写的规则与样本进行匹配、配置ClamAV数据库的扩展功能以支持自己提供YARA规则等。

### 删除指导手册（跟着我左手右手一个慢动作）

Umbreon是一个ring3（用户级别）的rootkit，因此是可以将其删除的。但是，可能比较棘手，对于没有经验的用户这么做可能会破坏系统，并把它变成一个不可恢复的状态。如果你是一只壕并且有足够的勇气来进行，最简单的方式是用Linux的LiveCD启动你那被感染的机器，并按照以下步骤：

* 在/usr目录下挂载分区，需要写操作的权限。
* 更改文件前先备份备份。
* 删除文件/etc/ld.so.<随机生成的字符串>。
* 删除目录/usr/lib/libc.so.<随机生成的字符串>。
* 恢复文件的属性/usr/share/libc.so.<random>.<arch>.*.so并删除它们。
* 补丁loader库以便再次使用/etc/ld.so.preload。
* 卸载分区并重新正常启动系统。

举一个真实的栗子（请注意文件名会有所不同，因为是恶意软件随机选择的）。以下，/dev/sda1目录是包含分区/usr的。

> mount /dev/sda1 /mnt
   rm -f /mnt/etc/ld.so.khVrkEQ
   rm -rf /mnt/usr/lib/libc.so.41762810374176281037/
   chattr -ai /mnt/usr/share/libc.so.4176281037.*
   rm -f /mnt/usr/share/libc.so.4176281037.*
   sed -i 's:/etc/ld\.so\.khVrkEQ:/etc/ld.so.preload:' /lib/x86_64-linux-gnu/         ld-2.19.so
   umount /mnt
  reboot

<font color = "red">**到此，这个ring3级别的rootkit也只是和大家大致的讲了一讲，此次事件盟主感觉还是学到了不少东西哒~~~**</font>

没看懂？

没关系！

遇到不认识的技术术语**Google**一下就知道啦！

##### 参考文献

* [Pokemon-fan VXer developed the Linux Umbreon rootkit](http://securityaffairs.co/wordpress/51003/breaking-news/linux-umbreon-rootkit.html)
* [Pokémon-themed Umbreon Linux Rootkit Hits x86, ARM Systems](http://blog.trendmicro.com/trendlabs-security-intelligence/pokemon-themed-umbreon-linux-rootkit-hits-x86-arm-systems/)
* [Signature-Based Detection With YARA](https://securityintelligence.com/signature-based-detection-with-yara/)
* [Yara - GitHub Pages](http://virustotal.github.io/yara/)
* [command-and-control server (C&C server)](http://whatis.techtarget.com/definition/command-and-control-server-CC-server)