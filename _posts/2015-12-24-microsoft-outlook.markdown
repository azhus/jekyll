---  
layout: post  
title: "Microsoft Outlook曝最新漏洞，可允许远程执行代码"
date: 2015-12-24
categories:  传媒信安     
comments: true
description:  微软于近期12月8日修复了一些较为严重的安全漏洞，并且更新了 Microsoft Office 的套件，解决了一系列的安全问题。
tags:
    - 传媒信安
--- 
![](http://127.0.0.1:4000//resources/images/Z1.png) 

以下内容翻译汇编自：affairs

微软于近期12月8日修复了一些较为严重的安全漏洞，并且更新了 Microsoft Office 的套件，解决了一系列的安全问题。然而，其中的一个缺陷，CVE-2015-6172漏洞，可以通过将一个“特制的 Microsoft Office 文件“发送给用户，使得攻击者可远程代码执行。

Microsoft安全公告如下：


---

此次更新解决了 Microsoft Office 中的安全漏洞。如果用户打开特制的Microsoft Office文件，最严重的漏洞可能允许远程执行代码。成功利用这些漏洞，可以使攻击者在当前用户目录下运行任意代码。而拥有较小权限的用户帐户受到的影响可能会比拥有管理员权限的用户所受影响要小得多。


---

该漏洞主要影响范围涉及到Outlook 2007/2010/2013/2016 等版本。

 正如安全研究员Haifei Li 在一篇名为“BadWinMali：隐藏在 Microsoft Outlook中的企业级攻击向量”的文章中提到，攻击者能够利用上述漏洞，通过邮件发送特定的office文档，利用微软的对象连接和嵌入技术（OLE）以及TNEF技术来绕过Outlook多重安全防护层面（如在沙盒中进行文件预览等），从而进行攻击。

TNEF 以 application/ms-tnef 类型的 MIME 附件的形式出现在邮件中。该附件的名称为 Winmail.dat。它包含完整的邮件内容以及所有附加文件。只有 MAPI 客户端（如 Outlook）能够对 Winmail.dat 附件进行解码。非 MAPI 客户端无法对 TNEF 进行解码，并且可能将 Winmail.dat 显示为典型但无用的文件。

 HaiFei写道， “当winmail.dat文件中PidTagAttachMethod的值被设置为ATTACH_OLE（6）时，该附件（另外一个文件包含着winmail.dat文件）将会被当作一个 OLE对象使用。接着，攻击者可以创建一个TNEF编码的电子邮件并将其发送给目标用户以发动攻击。

他指出，“这个特性可以允许我们建立一个TNEF编码的邮件并将其发送给用户，当用户读取邮件时，嵌入的OLE对象就会被自动加载” 。根据测试，各种OLE对象可通过电子邮件加载；这会带来很大的安全问题。


![](http://127.0.0.1:4000//resources/images/Z2.png) 

依赖于这种技术的网络钓鱼攻击是很危险的。

“由于Flash 0day 漏洞容易为攻击者所获取，那么通过启用了OLE的TNEF邮件中植入一个Flash exp，当受害者阅读邮件时，攻击者便能够实现任意代码执行。我们通过使用Flash OLE 对象作为一个测试样本，也成功实现了代码运行，但还需要提到的是其他的OLE对象也有可能被攻击者利用。”

Haifei还提出，该漏洞也可以通过电子邮件，而不是附件的内容引发，因为Outlook会自动认为.msg文件是“安全的”，并在Outlook邮件视图中打开它们，而不是沙盒。这意味着嵌入电子邮件的OLE内容将被自动打开。

目前应当尽快下载补丁，并关闭Microsoft Outlook中的邮件预览窗格。

Haifei建议为注册表键值增加一个“Office kill-bit”来阻止flash内容通过OLE自动打开。也就是限制CLSID:D27CDB6E-AE6D-11cf-96B8-444553540000来实现。

```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\Common\COM Compatibility\{D27CDB6E-AE6D-11cf-96B8-444553540000}]"Compatibility Flags”=dword:00000400
```


[阅读原文](http://securityaffairs.co/wordpress/42875/security/microsoft-outlook-mailbomb-attacks.html#rd?sukey=7f8f3cb2e9b0da455c0f530173fe62293467bca2fd0a6d2d52a53784c5a1d0d0f54244ca51a02e5bb1f04609779fb5dc)