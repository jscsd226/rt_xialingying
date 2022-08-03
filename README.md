# rt_xialingying
夏令营大作业提交-rt-thread
主要包含：
    QEMU A9 环境下可以跑的软件包。
    并附有测试图片。

​    ***\*QEMU\**** ***\*A9 可以跑的软件包\****



2022.07-2022.08

 

***\*引言\****：本文档主要是使用QEMU A9环境下，测试RT-thread的软件包，并把能够使用此环境运行的软件包进行整理，方便在不具备硬件的条件下开发调试。

（软件包网址参考：

https://github.com/supperthomas/rtthread_software_package_list_show/blob/main/rtthread_softlist.md 在软件包详情页中，都有相关介绍和具体使用、添加方法，本文主要进行实战，列出能够运行的，提供运行截图）

 

***\*步骤\****：1.配置ENV环境（env1.2.4）。2.下载rt-thread源码，进入BSP目录，进入QEMU A9，右键运行ENV环境。3.使用menuconfig选择软件包，保存并退出， pkgs --update 命令更新包到 BSP 中。4.使用scons -j4编译。5.运行.\qemu.bat，调试命令。

## ***\*tools\****

\1. UrlEncode，一个简单易用的Url编解码工具。

在进行网络请求时,经常需要对参数进行UrlEncode编码,本软件包可以比较方便的对参数进行编码以及解码.

URL编码(URL encoding)，也称作百分号编码(Percent-encoding)， 是特定上下文的统一资源定位符 (URL)的编码机制。用于统一资源标识符(URI)的编码，也用于为"application/x-www-form-urlencoded" MIME准备数据， 因为它用于通过HTTP的请求操作(request)提交HTML表单数据。

 

 

![img](file:///C:\Users\tian\AppData\Local\Temp\ksohtml13748\wps1.jpg) 

![img](file:///C:\Users\tian\AppData\Local\Temp\ksohtml13748\wps2.jpg) 

 

2.Memory Performance Testing这是一个运行在 RT-Thread 上的内存性能测试软件包，用于对 ARM CPU 的 内存性能评。

评估不同类型内存的读写性能

对于带有 cache 的 CPU，可用于评估 cache 性能

使用方法: 

在 msh 中运行 <memory_perf 0x10100000 0x100000> 命令

注意事项:

检查内存测试地址与长度是否设置正确

测试内存性能时推荐对比打开 cache 与 关闭 cache 的测试结果

 

![img](file:///C:\Users\tian\AppData\Local\Temp\ksohtml13748\wps3.jpg) 

 

 

 

 

 

 

 

3.mbedtls_bench是 mbedtls 加密算法的性能测试工具，mbedtls 性能测试。分数表示可以处理的块数据量，分数越高意味着性能越好。

 

![img](file:///C:\Users\tian\AppData\Local\Temp\ksohtml13748\wps4.jpg) 

 

4.lwlog:单文件日志打印库。

![img](file:///C:\Users\tian\AppData\Local\Temp\ksohtml13748\wps5.jpg) 

 

\5. logmgr: 日志管理系统功能支持。

该软件包主要用于配置和管理系统中日志相关功能，实现功能如下：

l 支持 ulog 文件后端功能启动；

l 重定向系统 hardfault 和 assert 异常错误回调，添加更多系统异常相关日志输出，包括

函数调用栈日志

内核运行日志

系统负荷监视器日志

当前系统 IPC 状态、内存状态、JS 堆等日志信息

l 支持系统异常时日志输出到 Flash，并在重启后导出到文件功能；

 

![img](file:///C:\Users\tian\AppData\Local\Temp\ksohtml13748\wps6.jpg) 

 

\6. Dhrystone 单片机性能测试小工具。

RT-Thread 上的 MCU/CPU 性能测试小工具，在 menuconfig 里选中软件包后，在 msh 中输入：

msh> dhrystone_test

就可以看到跑分结果了，例如：

 

![img](file:///C:\Users\tian\AppData\Local\Temp\ksohtml13748\wps7.jpg) 

![img](file:///C:\Users\tian\AppData\Local\Temp\ksohtml13748\wps8.jpg) 

 

\7. devmem读写内存/寄存器的工具。

在menuconfig里选中软件包后，在msh上输入devmem查看使用说明。

写内存/寄存器

byte方式写入

devmem 0x600a4000 b 0xa

halfword方式写入

devmem 0x600a4000 h 0xab

word方式写入

devmem 0x600a4000 w 0xabcd

读内存/寄存器

byte方式读取

msh />devmem 0x600a4000 b

0x0a

halfword方式读取

msh />devmem 0x600a4000 h

0x00ab

word方式读取

msh />devmem 0x600a4000 w

0x0000abcd

 

![img](file:///C:\Users\tian\AppData\Local\Temp\ksohtml13748\wps9.jpg) 

![img](file:///C:\Users\tian\AppData\Local\Temp\ksohtml13748\wps10.jpg) 

 

 

\8. CPUU: CPU 使用率统计小工具，目前不支持多核。

每个时间片侦测一次当前线程，如果当前正在运行 idle 线程，空闲计数器自增。一个周期后，计算 IDEL 线程运行时间的占比。

例如：

![img](file:///C:\Users\tian\AppData\Local\Temp\ksohtml13748\wps11.jpg) 

上图展示一个周期内，某个 CPU 上线程时间片信息。假设一个方格代表一个时间片。

一个周期总时间片数 30 tick

idle 总共运行 13 tick

CPU 使用率 = 13 / 30 * 100

msh 命令行输入 usage -l 50，调整 CPU 使用率，使其不低于 50%

 

![img](file:///C:\Users\tian\AppData\Local\Temp\ksohtml13748\wps12.jpg) 

 

9.CoreMark：EEMBC 的单片机性能测试小工具。

![img](file:///C:\Users\tian\AppData\Local\Temp\ksohtml13748\wps13.jpg) 

 

10.anv_trace帮助跟踪代码执行过程。

![img](file:///C:\Users\tian\AppData\Local\Temp\ksohtml13748\wps14.jpg) 

 

 

 

 

 

11.anv_testsuit单元测试框架。

![img](file:///C:\Users\tian\AppData\Local\Temp\ksohtml13748\wps15.jpg) 

 

 

 

 

 

 

 

 

 

