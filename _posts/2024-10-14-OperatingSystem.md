---
title: OperatingSystem
date: 2024-10-14 12:37:10 +0800
categories: [note, OperatingSystem]
tags: [note, OperatingSystem]     # TAG names should always be lowercase
typora-root-url: ./..
typora-copy-images-to: ./..\assets\img\2024-10-14-OperatingSystem
---

## 操作系统的概念、功能

定义：操作系统是指控制和管理整个计算机系统的硬件和软件资源，并合理地组织调度计算机的工作和资源的分配，以提供给用户和其他软件方便的接口和环境最基本的系统软件。

①是系统资源的管理者②向上层提供易用的服务③是最接近硬件的一层软件

![image-20241014124148844](/assets/img/2024-10-14-OperatingSystem/image-20241014124148844.png)

![image-20241014124440095](/assets/img/2024-10-14-OperatingSystem/image-20241014124440095.png)

封装思想：操作系统把一些硬件功能封装成简单易用的服务，使用户能更方便地使用计算机

用户无需关心底层硬件的原理，只需要对操作系统发出命令即可

功能和目标：向上层提供方便易用的服务

图形化用户接口Graphical User Interface，GUI

联机命令接口=交互式命令接口（用户说一句，系统做一步）

脱机命令接口=批处理命令接口（用户说一句，系统做一堆）

程序接口，程序进行系统调用

![image-20241014125212007](/assets/img/2024-10-14-OperatingSystem/image-20241014125212007.png)

![image-20241014125358112](/assets/img/2024-10-14-OperatingSystem/image-20241014125358112.png)

### 操作系统的特性

![image-20241014130526079](/assets/img/2024-10-14-OperatingSystem/image-20241014130526079.png)

#### 并发

两个或多个事件在同一时刻同时发生。

![image-20241014125629879](/assets/img/2024-10-14-OperatingSystem/image-20241014125629879.png)

4个以上应用程序仍需要并发运行

#### 共享

![image-20241014125818668](/assets/img/2024-10-14-OperatingSystem/image-20241014125818668.png)

![image-20241014130018392](/assets/img/2024-10-14-OperatingSystem/image-20241014130018392.png)

并发和共享互为存在条件

#### 虚拟

![image-20241014130122729](/assets/img/2024-10-14-OperatingSystem/image-20241014130122729.png)

![image-20241014130157605](/assets/img/2024-10-14-OperatingSystem/image-20241014130157605.png)

没有并发，虚拟性没有意义

#### 异步

多个程序并发执行时资源有限，进程的执行不是一贯到底的，断续执行推进

拥有并发性才会有异步性

### 操作系统的发展

![image-20241014131434186](/assets/img/2024-10-14-OperatingSystem/image-20241014131434186.png)

![image-20241014131420755](/assets/img/2024-10-14-OperatingSystem/image-20241014131420755.png)

#### 手工操作阶段

用户独占全机，人机速度矛盾导致资源利用率低

#### 单道批处理系统

![image-20241014130825017](/assets/img/2024-10-14-OperatingSystem/image-20241014130825017.png)

内存中只有一道程序运行，仍有大量时间等待IO

#### 多道处理系统

![image-20241014131039384](/assets/img/2024-10-14-OperatingSystem/image-20241014131039384.png)

#### 分时操作系统

计算机以时间片为单位轮流为各个用户/作业服务，各个用户可通过终端与计算机进行交互

用户请求可以被即时响应，解决了人机交换问题，对各个用户/作用是公平的，不能优先处理紧急任务

#### 实时操作系统 

![image-20241014131401918](/assets/img/2024-10-14-OperatingSystem/image-20241014131401918.png)

### 操作系统的运行机制

指令就是(CPU)能识别、执行的最基本命令

内核程序组成了操作系统内核kernel，内核是操作系统最重要核心的部分，是最接近硬件的部分，是必不可少的部分，GUI未包含在内核

![image-20241014131944347](/assets/img/2024-10-14-OperatingSystem/image-20241014131944347.png)

#### 用户态、内核态

为区分出指令类型，CPU划分成两种状态

![image-20241014132119907](/assets/img/2024-10-14-OperatingSystem/image-20241014132119907.png)

#### 如何实现内核态、用户态的切换

![image-20241014132415175](/assets/img/2024-10-14-OperatingSystem/image-20241014132415175.png)

![image-20241014132433764](/assets/img/2024-10-14-OperatingSystem/image-20241014132433764.png)

### 中断和异常

![image-20241014132707929](/assets/img/2024-10-14-OperatingSystem/image-20241014132707929.png)

#### 中断的类型

##### 内中断

与当前执行的指令有关，中断信号来源于CPU内部，若当前执行的指令是非法的，则会引发一个中断信号

如试图在用户态执行特权指令、执行除法指令时发现除数为0

、应用程序想请求操作系统内核的服务，会执行陷入指令，该指令会引发一个内部中断信号

执行“陷入指令”trap，意味着应用程序主动地将CPU控制权还给操作系统内核。“系统调用”就是通过陷入指令完成的，不是特权指令

##### 外中断

与当前执行的指令无关，中断信号来源于CPU外部

如时钟中断，时钟部件每隔一个时间片（如50ms)会给CPU
发送一个时钟中断信号，操作系统内核决定接下来让另一个应用程序上CPU运行、I/O中断输入输出任务完成

![image-20241014134450452](/assets/img/2024-10-14-OperatingSystem/image-20241014134450452.png)

#### 中断机制基本原理

![image-20241014134556982](/assets/img/2024-10-14-OperatingSystem/image-20241014134556982.png)

![image-20241014134607211](/assets/img/2024-10-14-OperatingSystem/image-20241014134607211.png)

### 系统调用

![image-20241014134817925](/assets/img/2024-10-14-OperatingSystem/image-20241014134817925.png)

#### 与库函数区别

![image-20241014134915373](/assets/img/2024-10-14-OperatingSystem/image-20241014134915373.png)

涉及系统调用的库函数是对系统调用的封装

![image-20241014135025754](/assets/img/2024-10-14-OperatingSystem/image-20241014135025754.png)

![image-20241014135113202](/assets/img/2024-10-14-OperatingSystem/image-20241014135113202.png)

通过系统调用的方式向操作系统内核提出共享资源服务请求

#### 系统调用的过程

![image-20241014135449761](/assets/img/2024-10-14-OperatingSystem/image-20241014135449761.png)

![image-20241014135605288](/assets/img/2024-10-14-OperatingSystem/image-20241014135605288.png)

### 操作系统的体系结构

#### 大内核和微内核

![image-20241014135648339](/assets/img/2024-10-14-OperatingSystem/image-20241014135648339.png)

![image-20241014135810404](/assets/img/2024-10-14-OperatingSystem/image-20241014135810404.png)

![image-20241014135836970](/assets/img/2024-10-14-OperatingSystem/image-20241014135836970.png)

![image-20241014135911020](/assets/img/2024-10-14-OperatingSystem/image-20241014135911020.png)

![image-20241014140053241](/assets/img/2024-10-14-OperatingSystem/image-20241014140053241.png)

![image-20241014140122787](/assets/img/2024-10-14-OperatingSystem/image-20241014140122787.png)

#### 分层结构

![image-20241014140656132](/assets/img/2024-10-14-OperatingSystem/image-20241014140656132.png)

#### 模块化

![image-20241014140723235](/assets/img/2024-10-14-OperatingSystem/image-20241014140723235.png)

#### 外核

![image-20241014141210741](/assets/img/2024-10-14-OperatingSystem/image-20241014141210741.png)

![image-20241014140305853](/assets/img/2024-10-14-OperatingSystem/image-20241014140305853.png)

### 操作系统的引导

开机时如何让操作系统运行起来

BIOS，Basic Input/Output System

![image-20241014141950690](/assets/img/2024-10-14-OperatingSystem/image-20241014141950690.png)

### 虚拟机

![image-20241014142221051](/assets/img/2024-10-14-OperatingSystem/image-20241014142221051.png)

![image-20241014142816374](/assets/img/2024-10-14-OperatingSystem/image-20241014142816374.png)

第二类内核态“部分”：VM驱动

![image-20241014142800014](/assets/img/2024-10-14-OperatingSystem/image-20241014142800014.png)

![image-20241014143451895](/assets/img/2024-10-14-OperatingSystem/image-20241014143451895.png)

## 进程管理

### 进程的概念

程序：是静态的，就是个存放在磁盘里的可执行文件，就是一系列的指令集合。
进程(Process):是动态的，是程序的一次执行过程，同一个程序多次执行会对应多个进程

![image-20241014150231033](/assets/img/2024-10-14-OperatingSystem/image-20241014150231033.png)

![image-20241014150254994](/assets/img/2024-10-14-OperatingSystem/image-20241014150254994.png)

![image-20241014150913130](/assets/img/2024-10-14-OperatingSystem/image-20241014150913130.png)

进程是动态的，进程实体（进程映像，可以理解为进程执行过程中某一个时间的快照）是静态的
进程实体反应了进程在某一时刻的状态（如：++后，x=2)

#### 进程的特征

![image-20241014151029211](/assets/img/2024-10-14-OperatingSystem/image-20241014151029211.png)

![image-20241014151040520](/assets/img/2024-10-14-OperatingSystem/image-20241014151040520.png)

### 进程的状态和状态转换

#### 创建态、就绪态

![image-20241014151246607](/assets/img/2024-10-14-OperatingSystem/image-20241014151246607.png)

#### 运行态

![image-20241014151400562](/assets/img/2024-10-14-OperatingSystem/image-20241014151400562.png)

#### 阻塞态

![image-20241014151454585](/assets/img/2024-10-14-OperatingSystem/image-20241014151454585.png)

#### 终止态

![image-20241014151614102](/assets/img/2024-10-14-OperatingSystem/image-20241014151614102.png)

#### 状态转换

![image-20241014151940418](/assets/img/2024-10-14-OperatingSystem/image-20241014151940418.png)

![image-20241014152030241](/assets/img/2024-10-14-OperatingSystem/image-20241014152030241.png)

#### 进程的组织

##### 链接方式

![image-20241014152141125](/assets/img/2024-10-14-OperatingSystem/image-20241014152141125.png)

![image-20241014152152035](/assets/img/2024-10-14-OperatingSystem/image-20241014152152035.png)

##### 索引方式

![image-20241014152229979](/assets/img/2024-10-14-OperatingSystem/image-20241014152229979.png)

![image-20241014152241989](/assets/img/2024-10-14-OperatingSystem/image-20241014152241989.png)

![image-20241014152254398](/assets/img/2024-10-14-OperatingSystem/image-20241014152254398.png)

### 进程控制

进程控制的主要功能是对系统中的所有进程实施有效的管理，它具有创建新进程、撤销已有进程、实现进程状态转换等功能。

#### 实现

用原语实现，原语是一种特殊的程序，它的执行具有原子性
即这段程序的运行必须一气呵成，不可中断

为什么进程控制要一气呵成，不可中断

PCB state与所在队列不一致，会影响操作系统工作

![image-20241014152718649](/assets/img/2024-10-14-OperatingSystem/image-20241014152718649.png)

![image-20241014153033863](/assets/img/2024-10-14-OperatingSystem/image-20241014153033863.png)

#### 进程控制相关原语

![image-20241014153231412](/assets/img/2024-10-14-OperatingSystem/image-20241014153231412.png)

![image-20241014153505438](/assets/img/2024-10-14-OperatingSystem/image-20241014153505438.png)

![image-20241014153620748](/assets/img/2024-10-14-OperatingSystem/image-20241014153620748.png)

![image-20241014154236969](/assets/img/2024-10-14-OperatingSystem/image-20241014154236969.png)

进程切换时保存PC、PSW、IR等寄存器内的信息，便于切换回时状态恢复

![image-20241014154352115](/assets/img/2024-10-14-OperatingSystem/image-20241014154352115.png)

### 进程的通信

进程间通信(Inter-Process Communication,IPC)是指两个进程之间产生数据交互。

![image-20241014154655211](/assets/img/2024-10-14-OperatingSystem/image-20241014154655211.png)

#### 共享存储

![image-20241014154916695](/assets/img/2024-10-14-OperatingSystem/image-20241014154916695.png)

基于数据结构的共享：如共享空间里只能放一个长度为10的数组。这种共享方式速度慢、限制多，是一种低级通信方式
基于存储区的共享：操作系统在内存中划出一块共享存储区，数据的形式、存放位置都由通信进程控制，而不是操作系统。这种共享方式速度很快，是一种高级通信方式。

#### 消息传递

![image-20241014155229132](/assets/img/2024-10-14-OperatingSystem/image-20241014155229132.png)

**直接通信方式**：指定了接收对象

![image-20241014155453888](/assets/img/2024-10-14-OperatingSystem/image-20241014155453888.png)

msg：P->Q的PCB的消息队列->Q

**间接通信方式**：

![image-20241014155814299](/assets/img/2024-10-14-OperatingSystem/image-20241014155814299.png)

#### 管道通信

与共享存储区别：消息读有顺序

![image-20241014162428030](/assets/img/2024-10-14-OperatingSystem/image-20241014162428030.png)

![image-20241014162838658](/assets/img/2024-10-14-OperatingSystem/image-20241014162838658.png)

### 线程

程序执行流的最小单位，进程间可以并发，进程内的线程也可以并发

引入线程后进程只作为除CPU外的系统资源的分配单位（如打印机，内存地址空间都是分配给进程的）

![image-20241014163808738](/assets/img/2024-10-14-OperatingSystem/image-20241014163808738.png)

![image-20241014163953994](/assets/img/2024-10-14-OperatingSystem/image-20241014163953994.png)

### 线程的实现方式和多线程模型

#### 实现方式

![image-20241014164156389](/assets/img/2024-10-14-OperatingSystem/image-20241014164156389.png)



用户级线程

![image-20241014164431496](/assets/img/2024-10-14-OperatingSystem/image-20241014164431496.png)

内核级线程

![image-20241014164659472](/assets/img/2024-10-14-OperatingSystem/image-20241014164659472.png)

多线程模型

一对一模型

![image-20241014164754335](/assets/img/2024-10-14-OperatingSystem/image-20241014164754335.png)

多对一模型

![image-20241014164901916](/assets/img/2024-10-14-OperatingSystem/image-20241014164901916.png)

多对多模型

![image-20241014165104624](/assets/img/2024-10-14-OperatingSystem/image-20241014165104624.png)

![image-20241014165113895](/assets/img/2024-10-14-OperatingSystem/image-20241014165113895.png)

### 线程的状态与转换

![image-20241014165227361](/assets/img/2024-10-14-OperatingSystem/image-20241014165227361.png)

![image-20241014165535874](/assets/img/2024-10-14-OperatingSystem/image-20241014165535874.png)

### 调度的概念、层次

当有大量任务需要处理而资源有限时，需要确定某种规则来决定处理任务的顺序

#### 高级调度（作业调度）

按一定的原则从外存的作业后备队列中挑选一个作业调入内存，并创建进程，每个作业只调入一次同时建立PCB，调出一次同时撤销PCB

#### 低级调度（进程调度/处理机调度）

![image-20241014170316265](/assets/img/2024-10-14-OperatingSystem/image-20241014170316265.png)

#### 中级调度

![image-20241014170435084](/assets/img/2024-10-14-OperatingSystem/image-20241014170435084.png)

#### 七状态模型

![image-20241014170606286](/assets/img/2024-10-14-OperatingSystem/image-20241014170606286.png)

![image-20241014170654859](/assets/img/2024-10-14-OperatingSystem/image-20241014170654859.png)

![image-20241014170716235](/assets/img/2024-10-14-OperatingSystem/image-20241014170716235.png)

### 进程调度的时机、切换与过程、调度方式

#### 时机

![image-20241014173459555](/assets/img/2024-10-14-OperatingSystem/image-20241014173459555.png)

![image-20241014171343574](/assets/img/2024-10-14-OperatingSystem/image-20241014171343574.png)

![image-20241014171503609](/assets/img/2024-10-14-OperatingSystem/image-20241014171503609.png)

普通临界区访问的临界资源不会直接影响到操作系统内核的管理工作，因此在访问普通临界区时可以进行调度与切换

#### 进程调度方式

![image-20241014173608156](/assets/img/2024-10-14-OperatingSystem/image-20241014173608156.png)

![image-20241014173824493](/assets/img/2024-10-14-OperatingSystem/image-20241014173824493.png)

![image-20241014173834136](/assets/img/2024-10-14-OperatingSystem/image-20241014173834136.png)

### 调度程序和闲逛进程

![image-20241014174153768](/assets/img/2024-10-14-OperatingSystem/image-20241014174153768.png)

![image-20241014174207885](/assets/img/2024-10-14-OperatingSystem/image-20241014174207885.png)

![image-20241014174300584](/assets/img/2024-10-14-OperatingSystem/image-20241014174300584.png)

### 调度算法的评价指标

#### CPU利用率

![image-20241014174453554](/assets/img/2024-10-14-OperatingSystem/image-20241014174453554.png)

#### 系统吞吐量

![image-20241014174524014](/assets/img/2024-10-14-OperatingSystem/image-20241014174524014.png)

#### 周转时间

![image-20241014174629443](/assets/img/2024-10-14-OperatingSystem/image-20241014174629443.png)

![image-20241014174745977](/assets/img/2024-10-14-OperatingSystem/image-20241014174745977.png)

#### 等待时间

![image-20241014174903212](/assets/img/2024-10-14-OperatingSystem/image-20241014174903212.png)

#### 响应时间

从用户提交请求到首次产生响应所用的时间

![image-20241014175005817](/assets/img/2024-10-14-OperatingSystem/image-20241014175005817.png)

### 调度算法--早期批处理系统

![image-20241014175147977](/assets/img/2024-10-14-OperatingSystem/image-20241014175147977.png)

#### 先来先服务FCFS

![image-20241014175805221](/assets/img/2024-10-14-OperatingSystem/image-20241014175805221.png)

![image-20241014175556918](/assets/img/2024-10-14-OperatingSystem/image-20241014175556918.png)

#### 短作业优先SJF

![image-20241014180826209](/assets/img/2024-10-14-OperatingSystem/image-20241014180826209.png)

![image-20241014180154953](/assets/img/2024-10-14-OperatingSystem/image-20241014180154953.png)

![image-20241014180444278](/assets/img/2024-10-14-OperatingSystem/image-20241014180444278.png)

![image-20241014180535379](/assets/img/2024-10-14-OperatingSystem/image-20241014180535379.png)

![image-20241014180711793](/assets/img/2024-10-14-OperatingSystem/image-20241014180711793.png)

#### 高响应比优先HRRN

![image-20241014180912279](/assets/img/2024-10-14-OperatingSystem/image-20241014180912279.png)

![image-20241014181406802](/assets/img/2024-10-14-OperatingSystem/image-20241014181406802.png)

![image-20241014181156994](/assets/img/2024-10-14-OperatingSystem/image-20241014181156994.png)

![image-20241014181439767](/assets/img/2024-10-14-OperatingSystem/image-20241014181439767.png)