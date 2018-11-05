---  
layout: post  
title: "Windows软件攻防知识体系"
date: 2016-03-04
categories:  课程体系     
comments: true
tags:
    - 课程体系
---  
一、Windows编程基础
1、C语言基础
2、系统接口：Windows API
（1）基础系统API：文件操作、GUI
（2）回调机制
（3）进程、线程、多线程、线程同步
（4）网络(socket)
（5）其他
（6）有效使用文档
3、工具
（1）Visual Studio
（2）SDK及命令行工具
（3）Windbg
（4）虚拟机

二、软件攻防基础
1、汇编与C语言对应关系基础
（1）调用堆栈及函数调用过程
（2）标志寄存器及条件跳转指令
2、缓冲区溢出基本原理
（1）缓冲区溢出原理
（2）shellcode
3、计算机体系结构相关
（1）线程和CPU、线程切换原理
（2）内存属性、内存分页机制和虚拟内存管理
（3）x86体系架构的优先级、操作系统内核态及用户态
4、Windows系统机制相关
（1）Copy On Write
（2）Windows进程管理：
（3）PEB
（4）TEB
（5）PE加载 动态连接
（6）API hook
（7）内存分页、虚拟内存管理

三、Windows内核编程
1、基本原理：x86体系架构的优先级划分ring0-ring3
2、工具：DDK、Visual Studio、Windbg、虚拟机
3、驱动加载接口
4、内核API

四、漏洞挖掘技术
1、Fuzzing
2、符号执行