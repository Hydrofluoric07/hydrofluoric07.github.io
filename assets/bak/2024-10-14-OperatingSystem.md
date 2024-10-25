---
title: OperatingSystem
date: 2024-10-14 12:37:10 +0800
categories: [note, OperatingSystem]
tags: [note, OperatingSystem]     # TAG names should always be lowercase
typora-root-url: ./..
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

#### 时间片轮转调度算法RR

![image-20241015084012761](/assets/img/2024-10-14-OperatingSystem/image-20241015084012761.png)

![image-20241015083404421](/assets/img/2024-10-14-OperatingSystem/image-20241015083404421.png)

时间片为5时：

![image-20241015083753713](/assets/img/2024-10-14-OperatingSystem/image-20241015083753713.png)

进程调度、切换是有时间代价的（保存、恢复运行环境)，若时间片太小，会导致进程切换过于频繁，系统会花大量的时间来处理进程切换，从而导致实际用于进程执行的时间比例减少

#### 优先级调度算法

![image-20241015084728973](/assets/img/2024-10-14-OperatingSystem/image-20241015084728973.png)

![image-20241015084653232](/assets/img/2024-10-14-OperatingSystem/image-20241015084653232.png)

![image-20241015084225166](/assets/img/2024-10-14-OperatingSystem/image-20241015084225166.png)

![image-20241015084353622](/assets/img/2024-10-14-OperatingSystem/image-20241015084353622.png)

#### 多级反馈队列调度算法

![image-20241015084805930](/assets/img/2024-10-14-OperatingSystem/image-20241015084805930.png)

![image-20241015085346368](/assets/img/2024-10-14-OperatingSystem/image-20241015085346368.png)

![image-20241015085049821](/assets/img/2024-10-14-OperatingSystem/image-20241015085049821.png)

![image-20241015085501909](/assets/img/2024-10-14-OperatingSystem/image-20241015085501909.png)

#### 多级队列调度算法

![image-20241015085829906](/assets/img/2024-10-14-OperatingSystem/image-20241015085829906.png)

### 进程同步、互斥

进程的异步性：各并发执行的进程以各自独立、不可预知的速度向前推进

![image-20241015090138342](/assets/img/2024-10-14-OperatingSystem/image-20241015090138342.png)

![image-20241015090304494](/assets/img/2024-10-14-OperatingSystem/image-20241015090304494.png)

![image-20241015090608057](/assets/img/2024-10-14-OperatingSystem/image-20241015090608057.png)

 ![image-20241015090722168](/assets/img/2024-10-14-OperatingSystem/image-20241015090722168.png)

![image-20241015090730583](/assets/img/2024-10-14-OperatingSystem/image-20241015090730583.png)

### 进程互斥的软件实现方法

![image-20241015090857389](/assets/img/2024-10-14-OperatingSystem/image-20241015090857389.png)

![image-20241015090952119](/assets/img/2024-10-14-OperatingSystem/image-20241015090952119.png)

#### 单标志法

![image-20241015091154118](/assets/img/2024-10-14-OperatingSystem/image-20241015091154118.png)

只能按P0→P1→P0→P1→...这样轮流访问。这种必须“轮流访问”带来的问题是，如果此时允许入临界区的进程是P0,而P0一直不访问临界区，那么虽然此时临界区空闲，但是并不允许P1访问，违反了空闲让进

#### 双标志先检查法

![image-20241015091608335](/assets/img/2024-10-14-OperatingSystem/image-20241015091608335.png)

若按照①⑤②⑥③⑦.的顺序执行，P0和P1将会同时访问临界区，双标志先检查法的主要问题是：违反“忙则等待”原则。

并发可能导致同时访问临界区

原因：检查和上锁两过程间可能发生进程切换

#### 双标志后检查法

![image-20241015091956906](/assets/img/2024-10-14-OperatingSystem/image-20241015091956906.png)

若按照①⑤②⑥…的顺序执行，P0和P1将都无法进入临界区
，双标志后检查法解决了“忙则等待”的问题，但是又违背了“空闲让进”和“有限等待”原则，会因各进程都长期无法访问临界资源而产生“饥饿”现象。

#### Peterson算法

![image-20241015093605496](/assets/img/2024-10-14-OperatingSystem/image-20241015093605496.png)

![image-20241015093613189](/assets/img/2024-10-14-OperatingSystem/image-20241015093613189.png)

### 进程互斥的硬件实现方法

#### 中断屏蔽

![image-20241015093859161](/assets/img/2024-10-14-OperatingSystem/image-20241015093859161.png)

#### TestAndSet指令

![image-20241015094308965](/assets/img/2024-10-14-OperatingSystem/image-20241015094308965.png)

#### Swap指令

![image-20241015094428535](/assets/img/2024-10-14-OperatingSystem/image-20241015094428535.png)

![image-20241015094436868](/assets/img/2024-10-14-OperatingSystem/image-20241015094436868.png)

### 互斥锁

![image-20241015094814309](/assets/img/2024-10-14-OperatingSystem/image-20241015094814309.png)

![image-20241015094825476](/assets/img/2024-10-14-OperatingSystem/image-20241015094825476.png)

### 信号量机制

![image-20241015095120408](/assets/img/2024-10-14-OperatingSystem/image-20241015095120408.png)

![image-20241015095351333](/assets/img/2024-10-14-OperatingSystem/image-20241015095351333.png)

#### 整型信号量

![image-20241015095835993](/assets/img/2024-10-14-OperatingSystem/image-20241015095835993.png)

#### 记录型信号量

![image-20241015100116876](/assets/img/2024-10-14-OperatingSystem/image-20241015100116876.png)

![image-20241015100430084](/assets/img/2024-10-14-OperatingSystem/image-20241015100430084.png)

![image-20241015100636541](/assets/img/2024-10-14-OperatingSystem/image-20241015100636541.png)

![image-20241015100757353](/assets/img/2024-10-14-OperatingSystem/image-20241015100757353.png)

### 用信号量机制实现进程互斥、同步、前驱关系

#### 实现进程互斥

![image-20241015101258833](/assets/img/2024-10-14-OperatingSystem/image-20241015101258833.png)

#### 实现进程同步

![image-20241015101409855](/assets/img/2024-10-14-OperatingSystem/image-20241015101409855.png)

![image-20241015101627471](/assets/img/2024-10-14-OperatingSystem/image-20241015101627471.png)

#### 实现前驱关系

![image-20241015101822903](/assets/img/2024-10-14-OperatingSystem/image-20241015101822903.png)

![image-20241015102032845](/assets/img/2024-10-14-OperatingSystem/image-20241015102032845.png)

### 生产者消费者问题

![image-20241015104820533](/assets/img/2024-10-14-OperatingSystem/image-20241015104820533.png)

![image-20241015105027407](/assets/img/2024-10-14-OperatingSystem/image-20241015105027407.png)

![image-20241015105130437](/assets/img/2024-10-14-OperatingSystem/image-20241015105130437.png)

![image-20241015105305458](/assets/img/2024-10-14-OperatingSystem/image-20241015105305458.png)

![image-20241015105541257](/assets/img/2024-10-14-OperatingSystem/image-20241015105541257.png)

![image-20241015105636754](/assets/img/2024-10-14-OperatingSystem/image-20241015105636754.png)

### 多生产者多消费者问题

![image-20241015105808872](/assets/img/2024-10-14-OperatingSystem/image-20241015105808872.png)

生产者生产的、消费者消费的都不同

![image-20241015110056219](/assets/img/2024-10-14-OperatingSystem/image-20241015110056219.png)

![image-20241015110836511](/assets/img/2024-10-14-OperatingSystem/image-20241015110836511.png)

![image-20241015110403038](/assets/img/2024-10-14-OperatingSystem/image-20241015110403038.png)

![image-20241015110503211](/assets/img/2024-10-14-OperatingSystem/image-20241015110503211.png)

缓冲区大于1就需要设置一个互斥信号量mutex来互斥访问缓冲区

![image-20241015110621237](/assets/img/2024-10-14-OperatingSystem/image-20241015110621237.png)

![image-20241015110808501](/assets/img/2024-10-14-OperatingSystem/image-20241015110808501.png)

### 吸烟者问题

![image-20241015111036989](/assets/img/2024-10-14-OperatingSystem/image-20241015111036989.png)

![image-20241015111251448](/assets/img/2024-10-14-OperatingSystem/image-20241015111251448.png)

![image-20241015111352826](/assets/img/2024-10-14-OperatingSystem/image-20241015111352826.png)

![image-20241015111555081](/assets/img/2024-10-14-OperatingSystem/image-20241015111555081.png)

 ![image-20241015111658620](/assets/img/2024-10-14-OperatingSystem/image-20241015111658620.png)

### 读者-写者问题

![image-20241015122441833](/assets/img/2024-10-14-OperatingSystem/image-20241015122441833.png)

两类进程：读进程、写进程

互斥关系：写进程--写进程、写进程--读进程，读进程间不存在互斥问题

![image-20241015122852391](/assets/img/2024-10-14-OperatingSystem/image-20241015122852391.png)

![image-20241015122911364](/assets/img/2024-10-14-OperatingSystem/image-20241015122911364.png)

潜在的问题：只要有读进程还在读，写进程就要一直阻塞等待，存在饥饿问题，在这个算法中读进程是优先的

![image-20241015123819751](/assets/img/2024-10-14-OperatingSystem/image-20241015123819751.png)

![image-20241015124004744](/assets/img/2024-10-14-OperatingSystem/image-20241015124004744.png)

### 哲学家进餐问题

![image-20241015124205364](/assets/img/2024-10-14-OperatingSystem/image-20241015124205364.png)

![image-20241015124309777](/assets/img/2024-10-14-OperatingSystem/image-20241015124309777.png)

如何防止死锁发生：

1. 可以对哲学家施加限制条件，如最多运行四个哲学家同时进餐，可以保证至少以为哲学家拿到左右筷子
2. 要求技术号哲学家先拿左边再拿右边，偶数号相反，可以保证相邻两个哲学家吃饭，一个可以拿起一只筷子，另一只直接阻塞，避免了占有一只等待另一只
3. 仅当左右筷子都可用才允许拿筷子 

![image-20241015125157658](https://s2.loli.net/2024/10/15/XLguMHeBYzns7yC.png)

![image-20241015125252894](/assets/img/2024-10-14-OperatingSystem/image-20241015125252894.png)

### 管程

引入管程：编写程序困难，易出错

![image-20241015161925744](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015161925744.png)

![image-20241015162201791](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015162201791.png)

![image-20241015162651862](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015162651862.png)

![image-20241015162749402](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015162749402.png)

![image-20241015162759285](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015162759285.png)

### 死锁

在并发环境下，各进程因竞争资源而造成的一种互相等待对方手里的资源，导致各进程都阻塞，都无法向前推进的现象，就是“死锁“
发生死锁后若无外力干涉这些进程都将无法向前推进

![image-20241015163401932](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015163401932.png)

![image-20241015163725428](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015163725428.png)

![image-20241015163853771](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015163853771.png)

![image-20241015163945708](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015163945708.png)

![](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015163945708.png)

### 死锁的处理策略

##### 静态策略-预防死锁

###### 破坏互斥条件

![image-20241015173002045](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015173002045.png)

###### 破坏不剥夺条件

![image-20241015173215948](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015173215948.png)

###### 破坏请求和保持条件

![image-20241015173411982](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015173411982.png)

###### 破坏循环等待条件

![image-20241015173741832](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015173741832.png)

![image-20241015173817626](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015173817626.png)

##### 动态策略-避免死锁

![image-20241015182554665](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015182554665.png)

![image-20241015182724298](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015182724298.png)

![image-20241015182859759](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015182859759.png)

![image-20241015182945767](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015182945767.png)

![image-20241015183041115](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015183041115.png)

![image-20241015183314102](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015183314102.png)

![image-20241015183427699](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015183427699.png)

![image-20241015183526128](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015183526128.png)

##### 死锁的检测和解除

###### 死锁的检测

![image-20241015184124951](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015184124951.png)

![image-20241015184241679](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015184241679.png)

###### 死锁的解除

![image-20241015184457249](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015184457249.png)

![image-20241015184510736](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015184510736.png)

## 内存

### 基础知识

![image-20241015184926328](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015184926328.png)

![image-20241015185928053](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015185928053.png)

#### 装入方式

##### 绝对装入

![image-20241015190103442](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015190103442.png)

##### 可重定位装入

![image-20241015190242271](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015190242271.png)

##### 动态运行时装入

![image-20241015190426041](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015190426041.png)

![image-20241015190617841](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015190617841.png)

#### 链接的三种方式

![image-20241015190721652](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015190721652.png)

![image-20241015190729463](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015190729463.png)

### 内存管理

![image-20241015191144447](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015191144447.png)

![image-20241015191343530](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015191343530.png)

4.操作系统需要提供内存保护功能，保护各进程在各自的存储空间内运行，互不干扰

内存保护方法：

1. 在CPU中设置一对上下限寄存器，存放上下限，访问前检查是否越界
2. ![image-20241015191807383](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015191807383.png)

![image-20241015191903720](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015191903720.png)

### 覆盖技术

![image-20241015192052132](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015192052132.png)

![image-20241015192257808](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015192257808.png)

### 交换技术

![image-20241015192521396](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015192521396.png)

![image-20241015192801310](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015192801310.png)

![image-20241015192821782](https://gitee.com/HF2648/pic-bed-hydrofluoric07/raw/master/img/image-20241015192821782.png)

### 连续分配管理方式

#### 单一连续分配

![image-20241016084422484](/assets/img/2024-10-14-OperatingSystem/image-20241016084422484.png)

#### 固定分区分配

![image-20241016084635155](/assets/img/2024-10-14-OperatingSystem/image-20241016084635155.png)

![image-20241016084828264](/assets/img/2024-10-14-OperatingSystem/image-20241016084828264.png)

#### 动态分区分配

![image-20241016085007008](/assets/img/2024-10-14-OperatingSystem/image-20241016085007008.png)

![image-20241016085115267](/assets/img/2024-10-14-OperatingSystem/image-20241016085115267.png)

![image-20241016085757993](/assets/img/2024-10-14-OperatingSystem/image-20241016085757993.png)

![image-20241016085905952](/assets/img/2024-10-14-OperatingSystem/image-20241016085905952.png)

### 动态分区分配算法

#### 首次适应算法

![image-20241016090143787](/assets/img/2024-10-14-OperatingSystem/image-20241016090143787.png)

#### 最佳适应算法

![image-20241016090405315](/assets/img/2024-10-14-OperatingSystem/image-20241016090405315.png)

#### 最坏适应算法

![image-20241016090540011](/assets/img/2024-10-14-OperatingSystem/image-20241016090540011.png)

#### 邻近适应算法

![image-20241016090839146](/assets/img/2024-10-14-OperatingSystem/image-20241016090839146.png)

![image-20241016090849677](/assets/img/2024-10-14-OperatingSystem/image-20241016090849677.png)

### 基本分页存储管理

![image-20241016102947081](/assets/img/2024-10-14-OperatingSystem/image-20241016102947081.png)

![image-20241016103436962](/assets/img/2024-10-14-OperatingSystem/image-20241016103436962.png)

![image-20241016103341976](/assets/img/2024-10-14-OperatingSystem/image-20241016103341976.png)

![image-20241016103610837](/assets/img/2024-10-14-OperatingSystem/image-20241016103610837.png)

![image-20241016103932352](/assets/img/2024-10-14-OperatingSystem/image-20241016103932352.png)

![image-20241016104126753](/assets/img/2024-10-14-OperatingSystem/image-20241016104126753.png)

![image-20241016104210953](/assets/img/2024-10-14-OperatingSystem/image-20241016104210953.png)

![image-20241016104220966](/assets/img/2024-10-14-OperatingSystem/image-20241016104220966.png)

### 基本地址变换机构

实现逻辑地址转换到物理地址

![image-20241016104755600](/assets/img/2024-10-14-OperatingSystem/image-20241016104755600.png)

![image-20241016105043017](/assets/img/2024-10-14-OperatingSystem/image-20241016105043017.png)

![image-20241016105300562](/assets/img/2024-10-14-OperatingSystem/image-20241016105300562.png)

![image-20241016105435898](/assets/img/2024-10-14-OperatingSystem/image-20241016105435898.png)

![image-20241016105515159](/assets/img/2024-10-14-OperatingSystem/image-20241016105515159.png)

### 具有块表的地址变换机构

快表，又称联想寄存器(TLB,ttranslation lookaside buffer),是一种访问速度比内存快很多的高速缓存(TLB不是内存！)，用来存放最近访问的页表项的副本，可以加速地址变换的速度。内存中的页表常称为慢表。

![image-20241016110401878](/assets/img/2024-10-14-OperatingSystem/image-20241016110401878.png)

![image-20241016110649693](/assets/img/2024-10-14-OperatingSystem/image-20241016110649693.png)

![image-20241016110726359](/assets/img/2024-10-14-OperatingSystem/image-20241016110726359.png)

时间局部性：如果执行了程序中的某条指令，那么不久后这条指令很有可能再次执行；如果某个数据被访问过，不久之后该数据很可能再次被访问。（因为程序中存在大量的循环）

空间局部性：一旦程序访问了某个存储单元，在不久之后，其附近的存储单元也很有可能被访问。（因为很多数据在内存中都是连续存放的)

可能连续访问同一个页表

![image-20241016110942783](/assets/img/2024-10-14-OperatingSystem/image-20241016110942783.png)

### 两级页表

![image-20241016180247995](/assets/img/2024-10-14-OperatingSystem/image-20241016180247995.png)

![image-20241016180431513](/assets/img/2024-10-14-OperatingSystem/image-20241016180431513.png)

![image-20241016180759173](/assets/img/2024-10-14-OperatingSystem/image-20241016180759173.png)

![image-20241016180910830](/assets/img/2024-10-14-OperatingSystem/image-20241016180910830.png)

![image-20241016181007826](/assets/img/2024-10-14-OperatingSystem/image-20241016181007826.png)

![image-20241016181158378](/assets/img/2024-10-14-OperatingSystem/image-20241016181158378.png)

![image-20241016181231456](/assets/img/2024-10-14-OperatingSystem/image-20241016181231456.png)

### 基本分段存储管理

![image-20241016181454565](/assets/img/2024-10-14-OperatingSystem/image-20241016181454565.png)

![image-20241016181648332](/assets/img/2024-10-14-OperatingSystem/image-20241016181648332.png)

![image-20241016181852953](/assets/img/2024-10-14-OperatingSystem/image-20241016181852953.png)

![image-20241016182259697](/assets/img/2024-10-14-OperatingSystem/image-20241016182259697.png)

![image-20241016182505070](/assets/img/2024-10-14-OperatingSystem/image-20241016182505070.png)

![image-20241016182603879](/assets/img/2024-10-14-OperatingSystem/image-20241016182603879.png)

![image-20241016182721208](/assets/img/2024-10-14-OperatingSystem/image-20241016182721208.png)

![image-20241016182806610](/assets/img/2024-10-14-OperatingSystem/image-20241016182806610.png)

![image-20241016182821790](/assets/img/2024-10-14-OperatingSystem/image-20241016182821790.png)

### 段页式管理方式

![image-20241016183155530](/assets/img/2024-10-14-OperatingSystem/image-20241016183155530.png)

![image-20241016183234148](/assets/img/2024-10-14-OperatingSystem/image-20241016183234148.png)

![image-20241016183338373](/assets/img/2024-10-14-OperatingSystem/image-20241016183338373.png)

![image-20241016183528065](/assets/img/2024-10-14-OperatingSystem/image-20241016183528065.png)

![image-20241016183719792](/assets/img/2024-10-14-OperatingSystem/image-20241016183719792.png)

![image-20241016183746114](/assets/img/2024-10-14-OperatingSystem/image-20241016183746114.png)

### 虚拟内存

 ![image-20241016184140852](/assets/img/2024-10-14-OperatingSystem/image-20241016184140852.png)

![image-20241016184456192](/assets/img/2024-10-14-OperatingSystem/image-20241016184456192.png)

![image-20241016184620976](/assets/img/2024-10-14-OperatingSystem/image-20241016184620976.png)

![image-20241016184644915](/assets/img/2024-10-14-OperatingSystem/image-20241016184644915.png)

### 请求分页存储管理

![image-20241016185016797](/assets/img/2024-10-14-OperatingSystem/image-20241016185016797.png)

![image-20241016185154863](/assets/img/2024-10-14-OperatingSystem/image-20241016185154863.png)

![image-20241016185323890](/assets/img/2024-10-14-OperatingSystem/image-20241016185323890.png)

![image-20241016185423632](/assets/img/2024-10-14-OperatingSystem/image-20241016185423632.png)

![image-20241016185528844](/assets/img/2024-10-14-OperatingSystem/image-20241016185528844.png)

![image-20241016185640635](/assets/img/2024-10-14-OperatingSystem/image-20241016185640635.png)

![image-20241016185832746](/assets/img/2024-10-14-OperatingSystem/image-20241016185832746.png)

在具有快表机构的请求分页系统中，访问一个逻辑地址
时，若发生缺页，则地址变换步骤是：查快表（未命中）一一查慢表（发现未调入内存）一一调页（调入的页面对应的表项会直接加入快表)一一查快表（命中)一一访问目标内存单元

![image-20241016185949762](/assets/img/2024-10-14-OperatingSystem/image-20241016185949762.png)

### 页面置换算法

![image-20241016191338013](/assets/img/2024-10-14-OperatingSystem/image-20241016191338013.png)

#### 最佳置换算法OPT

![image-20241016191907670](/assets/img/2024-10-14-OperatingSystem/image-20241016191907670.png)

#### 先进先出置换算法FIFO

![image-20241016192130079](/assets/img/2024-10-14-OperatingSystem/image-20241016192130079.png)

#### 最近最久未使用LRU

![image-20241016192303227](/assets/img/2024-10-14-OperatingSystem/image-20241016192303227.png)

算法性能好，实现困难，开销大

#### 时钟置换算法CLOCK

![image-20241016192555101](/assets/img/2024-10-14-OperatingSystem/image-20241016192555101.png)

![image-20241016193001955](/assets/img/2024-10-14-OperatingSystem/image-20241016193001955.png)

![image-20241016193140395](/assets/img/2024-10-14-OperatingSystem/image-20241016193140395.png)

### 页面分配策略、抖动、工作集

![image-20241016193502940](/assets/img/2024-10-14-OperatingSystem/image-20241016193502940.png)

![image-20241016193733716](/assets/img/2024-10-14-OperatingSystem/image-20241016193733716.png)

![image-20241016193912848](/assets/img/2024-10-14-OperatingSystem/image-20241016193912848.png)![image-20241016194054628](/assets/img/2024-10-14-OperatingSystem/image-20241016194054628.png)

![image-20241016194145108](/assets/img/2024-10-14-OperatingSystem/image-20241016194145108.png)

![image-20241016194310184](/assets/img/2024-10-14-OperatingSystem/image-20241016194310184.png)

![image-20241016194359499](/assets/img/2024-10-14-OperatingSystem/image-20241016194359499.png)

### 内存映射文件

Memory-Mapped Files，内存映射文件一一操作系统向上层程序员提供的功能（系统调用），方便程序员访问文件数据，方便多个进程共享同一个文件

![image-20241016194717121](/assets/img/2024-10-14-OperatingSystem/image-20241016194717121.png)

![image-20241016194931932](/assets/img/2024-10-14-OperatingSystem/image-20241016194931932.png)

多个进程可以映射同一个文件，实现共享

在物理内存中，一个文件对应同一份数据，当一个进程修改文件数据时，另一个进程可以立马“看到“

![image-20241016195054079](/assets/img/2024-10-14-OperatingSystem/image-20241016195054079.png)

## 文件系统

### 初识文件管理

文件是一组有意义数据/信息的集合

![image-20241017075936156](/assets/img/2024-10-14-OperatingSystem/image-20241017075936156.png)

#### 一个文件有哪些属性

![image-20241017080300797](/assets/img/2024-10-14-OperatingSystem/image-20241017080300797.png)

#### 文件内部数据如何组织起来

无结构文件（如文本文件)一一由一些二进制或字符流组成，又称“流式文件“

有结构文件（如数据库表）一一由一组相似的记录组成，又称“记录
式文件”

记录是一组相关数据项的集合

数据项是文件系统中最基本的数据单位

![image-20241017080511076](/assets/img/2024-10-14-OperatingSystem/image-20241017080511076.png)

#### 文件间怎么组织起来的

![image-20241017080636332](/assets/img/2024-10-14-OperatingSystem/image-20241017080636332.png)

#### 操作系统向上提供的功能

![image-20241017080839919](/assets/img/2024-10-14-OperatingSystem/image-20241017080839919.png)

#### 文件如何放在外存

![image-20241017081019335](/assets/img/2024-10-14-OperatingSystem/image-20241017081019335.png)

![image-20241017081159258](/assets/img/2024-10-14-OperatingSystem/image-20241017081159258.png)

### 文件的逻辑结构

![image-20241017081557239](/assets/img/2024-10-14-OperatingSystem/image-20241017081557239.png)

#### 顺序文件

![image-20241017081733562](/assets/img/2024-10-14-OperatingSystem/image-20241017081733562.png)

串结构：不按关键字

![image-20241017082032748](/assets/img/2024-10-14-OperatingSystem/image-20241017082032748.png)

#### 索引文件

![image-20241017082326228](/assets/img/2024-10-14-OperatingSystem/image-20241017082326228.png)

#### 索引顺序文件

![image-20241017082506896](/assets/img/2024-10-14-OperatingSystem/image-20241017082506896.png)

![image-20241017082609874](/assets/img/2024-10-14-OperatingSystem/image-20241017082609874.png)

![image-20241017082648322](/assets/img/2024-10-14-OperatingSystem/image-20241017082648322.png)

![image-20241017082714936](/assets/img/2024-10-14-OperatingSystem/image-20241017082714936.png)

### 文件目录

![image-20241017083101226](/assets/img/2024-10-14-OperatingSystem/image-20241017083101226.png)

FCB实现了文件名和文件之间的映射，使用户可以按名存取

![image-20241017083252738](/assets/img/2024-10-14-OperatingSystem/image-20241017083252738.png)

#### 单级目录结构

![image-20241017083349871](/assets/img/2024-10-14-OperatingSystem/image-20241017083349871.png)

#### 两级目录结构

![image-20241017083432917](/assets/img/2024-10-14-OperatingSystem/image-20241017083432917.png)

#### 多级目录结构

![image-20241017083625474](/assets/img/2024-10-14-OperatingSystem/image-20241017083625474.png)

已经打开目录对应的目录表已经调入内存，可以将它设置为当前目录，就有了相对路径

树形目录结构方便对文件进行分类，层次结构清晰，进行文件的管理和保护，但不便于实现文件的共享，因此提出了“无环图目录结构”。

#### 无环图目录结构

![image-20241017083921022](/assets/img/2024-10-14-OperatingSystem/image-20241017083921022.png)

共享文件不同于复制文件，在共享文件中，由于各用户指向的是同一个文件，只要其中一个用户修改了文件数据，那么所有用户都可以看到文件数据的变化。

#### 索引节点（FCB的改进）

![image-20241017084210408](/assets/img/2024-10-14-OperatingSystem/image-20241017084210408.png)

![image-20241017084239073](/assets/img/2024-10-14-OperatingSystem/image-20241017084239073.png)

![image-20241017084250724](/assets/img/2024-10-14-OperatingSystem/image-20241017084250724.png)

### 文件的物理结构

#### 文件分配方式--管理非空闲存储块

![image-20241017084635732](/assets/img/2024-10-14-OperatingSystem/image-20241017084635732.png)

##### 连续分配

![image-20241017084815730](/assets/img/2024-10-14-OperatingSystem/image-20241017084815730.png)

![image-20241017084949827](/assets/img/2024-10-14-OperatingSystem/image-20241017084949827.png)
物理上采用连续分配的文件不方便拓展。

物理上采用连续分配，存储空间利用率低，会产生难以利用的磁盘碎片可以用紧凑来处理碎片，但是需要耗费很大的时间代价。

##### 链接分配

###### 隐式链接

![image-20241017085405871](/assets/img/2024-10-14-OperatingSystem/image-20241017085405871.png)

###### 显式链接

![image-20241017085724967](/assets/img/2024-10-14-OperatingSystem/image-20241017085724967.png)

![image-20241017085907788](/assets/img/2024-10-14-OperatingSystem/image-20241017085907788.png)

![image-20241017085935117](/assets/img/2024-10-14-OperatingSystem/image-20241017085935117.png)

##### 索引分配

![image-20241017090233050](/assets/img/2024-10-14-OperatingSystem/image-20241017090233050.png)

![image-20241017090344108](/assets/img/2024-10-14-OperatingSystem/image-20241017090344108.png)![image-20241017090634344](/assets/img/2024-10-14-OperatingSystem/image-20241017090634344.png)

![image-20241017090902181](/assets/img/2024-10-14-OperatingSystem/image-20241017090902181.png)

采用K层索引结构，且顶级索引表未调入内存，则访问一个数据块只需要K+1次读磁盘操作

![image-20241017091057535](/assets/img/2024-10-14-OperatingSystem/image-20241017091057535.png)

若顶级索引表还没读入内存
访问0~7号逻辑块：两次读磁盘，访问8~263：三次读磁盘，访问264~65799：四次读磁盘，小文件只需要少量次读磁盘

![image-20241017091308191](/assets/img/2024-10-14-OperatingSystem/image-20241017091308191.png)

![image-20241017091346762](/assets/img/2024-10-14-OperatingSystem/image-20241017091346762.png)

#### 文件存储空间管理--管理空闲存储块

![image-20241017093107878](/assets/img/2024-10-14-OperatingSystem/image-20241017093107878.png)

##### 空闲表法

![image-20241017093300006](/assets/img/2024-10-14-OperatingSystem/image-20241017093300006.png)

##### 空闲链表法

![image-20241017093544604](/assets/img/2024-10-14-OperatingSystem/image-20241017093544604.png)

![image-20241017093643264](/assets/img/2024-10-14-OperatingSystem/image-20241017093643264.png)

![image-20241017093810531](/assets/img/2024-10-14-OperatingSystem/image-20241017093810531.png)

##### 位示图法

![image-20241017094128018](/assets/img/2024-10-14-OperatingSystem/image-20241017094128018.png)

![image-20241017094202325](/assets/img/2024-10-14-OperatingSystem/image-20241017094202325.png)

##### 成组链接法

![image-20241017094402882](/assets/img/2024-10-14-OperatingSystem/image-20241017094402882.png)

![image-20241017094519779](/assets/img/2024-10-14-OperatingSystem/image-20241017094519779.png)

![image-20241017094935380](/assets/img/2024-10-14-OperatingSystem/image-20241017094935380.png)

![image-20241017095116779](/assets/img/2024-10-14-OperatingSystem/image-20241017095116779.png)

![image-20241017095208894](/assets/img/2024-10-14-OperatingSystem/image-20241017095208894.png)

![image-20241017095308014](/assets/img/2024-10-14-OperatingSystem/image-20241017095308014.png)

![image-20241017095321269](/assets/img/2024-10-14-OperatingSystem/image-20241017095321269.png)

### 逻辑结构和物理结构

用户视角：使用逻辑地址

操作系统将（逻辑块号，块内偏移量）转变为（物理块号，块内偏移量）

![image-20241017092520678](/assets/img/2024-10-14-OperatingSystem/image-20241017092520678.png)


![image-20241017092632415](/assets/img/2024-10-14-OperatingSystem/image-20241017092632415.png)

![image-20241017092726021](/assets/img/2024-10-14-OperatingSystem/image-20241017092726021.png)

![image-20241017092735065](/assets/img/2024-10-14-OperatingSystem/image-20241017092735065.png)

### 文件的基本操作

#### 创建文件

![image-20241017101744049](/assets/img/2024-10-14-OperatingSystem/image-20241017101744049.png)

#### 删除文件

![image-20241017101842220](/assets/img/2024-10-14-OperatingSystem/image-20241017101842220.png)

#### 打开文件

![image-20241017102024098](/assets/img/2024-10-14-OperatingSystem/image-20241017102024098.png)

![image-20241017102126370](/assets/img/2024-10-14-OperatingSystem/image-20241017102126370.png)

#### 关闭文件

![image-20241017102259411](/assets/img/2024-10-14-OperatingSystem/image-20241017102259411.png)

#### 读文件

![image-20241017102543782](/assets/img/2024-10-14-OperatingSystem/image-20241017102543782.png)

#### 写文件

![image-20241017102520880](/assets/img/2024-10-14-OperatingSystem/image-20241017102520880.png)

![image-20241017102559538](/assets/img/2024-10-14-OperatingSystem/image-20241017102559538.png)

### 文件共享

![image-20241017102758012](/assets/img/2024-10-14-OperatingSystem/image-20241017102758012.png)

#### 硬链接

![image-20241017102925976](/assets/img/2024-10-14-OperatingSystem/image-20241017102925976.png)

#### 软链接

![image-20241017103026457](/assets/img/2024-10-14-OperatingSystem/image-20241017103026457.png)

![image-20241017103218429](/assets/img/2024-10-14-OperatingSystem/image-20241017103218429.png)

### 文件保护

#### 口令保护

![image-20241017103410642](/assets/img/2024-10-14-OperatingSystem/image-20241017103410642.png)

#### 加密保护

![image-20241017103555124](/assets/img/2024-10-14-OperatingSystem/image-20241017103555124.png)

#### 访问控制

![image-20241017103712539](/assets/img/2024-10-14-OperatingSystem/image-20241017103712539.png)![image-20241017103808185](/assets/img/2024-10-14-OperatingSystem/image-20241017103808185.png)

![image-20241017103846245](/assets/img/2024-10-14-OperatingSystem/image-20241017103846245.png)

### 文件系统的层次结构

![image-20241017104203611](/assets/img/2024-10-14-OperatingSystem/image-20241017104203611.png)

![image-20241017104401280](/assets/img/2024-10-14-OperatingSystem/image-20241017104401280.png)

### 文件系统的全局结构

![image-20241017104501882](/assets/img/2024-10-14-OperatingSystem/image-20241017104501882.png)

![image-20241017104527354](/assets/img/2024-10-14-OperatingSystem/image-20241017104527354.png)

i节点区：存放索引节点

![image-20241017104831177](/assets/img/2024-10-14-OperatingSystem/image-20241017104831177.png)

### 虚拟文件系统

![image-20241017105156379](/assets/img/2024-10-14-OperatingSystem/image-20241017105156379.png)

![image-20241017105235195](/assets/img/2024-10-14-OperatingSystem/image-20241017105235195.png)

![image-20241017105338731](/assets/img/2024-10-14-OperatingSystem/image-20241017105338731.png)

![image-20241017105530017](/assets/img/2024-10-14-OperatingSystem/image-20241017105530017.png)

![image-20241017105705057](/assets/img/2024-10-14-OperatingSystem/image-20241017105705057.png)

![image-20241017105751256](/assets/img/2024-10-14-OperatingSystem/image-20241017105751256.png)

## 设备管理

### 概念和分类

I/O设备就是可以将数据输入到计算机，或者可以接收计算机输出数据的外部设备，属于计算机中的硬件部件。

![image-20241017110218485](/assets/img/2024-10-14-OperatingSystem/image-20241017110218485.png)

![image-20241017110247879](/assets/img/2024-10-14-OperatingSystem/image-20241017110247879.png)

![image-20241017110325110](/assets/img/2024-10-14-OperatingSystem/image-20241017110325110.png)

![image-20241017110339405](/assets/img/2024-10-14-OperatingSystem/image-20241017110339405.png)

### I/O控制器

![image-20241017110459465](/assets/img/2024-10-14-OperatingSystem/image-20241017110459465.png)

![image-20241017110713678](/assets/img/2024-10-14-OperatingSystem/image-20241017110713678.png)

![image-20241017111012892](/assets/img/2024-10-14-OperatingSystem/image-20241017111012892.png)

![image-20241017111037777](/assets/img/2024-10-14-OperatingSystem/image-20241017111037777.png)

![image-20241017111158903](/assets/img/2024-10-14-OperatingSystem/image-20241017111158903.png)

![image-20241017111224381](/assets/img/2024-10-14-OperatingSystem/image-20241017111224381.png)

### I/O控制方式

需要注意的问题：

1.完成一次读/写操作的流程：
2.CPU千预的频率；
3.数据传送的单位：
4.数据的流向：
5.主要缺点和主要优点。

#### 程序直接控制方式

![image-20241017132321997](/assets/img/2024-10-14-OperatingSystem/image-20241017132321997.png)

![image-20241017132650619](/assets/img/2024-10-14-OperatingSystem/image-20241017132650619.png)

#### 中断驱动方式

![image-20241017132832943](/assets/img/2024-10-14-OperatingSystem/image-20241017132832943.png)

![image-20241017132944975](/assets/img/2024-10-14-OperatingSystem/image-20241017132944975.png)

#### DMA方式

![image-20241017133127861](/assets/img/2024-10-14-OperatingSystem/image-20241017133127861.png)

![image-20241017133304127](/assets/img/2024-10-14-OperatingSystem/image-20241017133304127.png)

![image-20241017133517387](/assets/img/2024-10-14-OperatingSystem/image-20241017133517387.png)

#### 通道控制方式

![image-20241017133639676](/assets/img/2024-10-14-OperatingSystem/image-20241017133639676.png)

![image-20241017133739014](/assets/img/2024-10-14-OperatingSystem/image-20241017133739014.png)

![image-20241017133745726](/assets/img/2024-10-14-OperatingSystem/image-20241017133745726.png)

### I/O软件层次结构

![image-20241017134030324](/assets/img/2024-10-14-OperatingSystem/image-20241017134030324.png)

![image-20241017134145728](/assets/img/2024-10-14-OperatingSystem/image-20241017134145728.png)

![image-20241017134455521](/assets/img/2024-10-14-OperatingSystem/image-20241017134455521.png)

不同设备的内部硬件特性也不同，这些特性只有厂家才知道，因此厂家须提供与设备相对应的驱动程序，CPU执行驱动程序的指令序列，来完成设置设备寄存器，检查设备状态等工作

![image-20241017134657401](/assets/img/2024-10-14-OperatingSystem/image-20241017134657401.png)

![image-20241017134824364](/assets/img/2024-10-14-OperatingSystem/image-20241017134824364.png)

![image-20241017134906324](/assets/img/2024-10-14-OperatingSystem/image-20241017134906324.png)

![image-20241017134929163](/assets/img/2024-10-14-OperatingSystem/image-20241017134929163.png)

### 输入输出管理

#### 输入输出应用程序接口

![image-20241017135910368](/assets/img/2024-10-14-OperatingSystem/image-20241017135910368.png)

![image-20241017135921551](/assets/img/2024-10-14-OperatingSystem/image-20241017135921551.png)

![image-20241017140125945](/assets/img/2024-10-14-OperatingSystem/image-20241017140125945.png)

#### 设备驱动接口

![image-20241017140236352](/assets/img/2024-10-14-OperatingSystem/image-20241017140236352.png)

### I/O核心子系统

![image-20241017140353604](/assets/img/2024-10-14-OperatingSystem/image-20241017140353604.png)

![image-20241017140444079](/assets/img/2024-10-14-OperatingSystem/image-20241017140444079.png)

![image-20241017140527760](/assets/img/2024-10-14-OperatingSystem/image-20241017140527760.png)

### 假脱机技术

![image-20241017140756435](/assets/img/2024-10-14-OperatingSystem/image-20241017140756435.png)

![image-20241017140944581](/assets/img/2024-10-14-OperatingSystem/image-20241017140944581.png)

![image-20241017141219001](/assets/img/2024-10-14-OperatingSystem/image-20241017141219001.png)

虽然系统中只有一个台打印机，但每个进程提出打印请求时，系统都会为在输出井中为其分配一个存储区（相当于分配了一个逻辑设备），使每个用户进程都觉得自己在独占台打印机，从而实现对打印机的共享。
POOLing技术可以把一台物理设备虚拟成逻辑上的多台设备，可将独占式设备改造成共享设备。

![image-20241017141258023](/assets/img/2024-10-14-OperatingSystem/image-20241017141258023.png)

### 设备的分配与回收

![image-20241017144732160](/assets/img/2024-10-14-OperatingSystem/image-20241017144732160.png)

![image-20241017144918662](/assets/img/2024-10-14-OperatingSystem/image-20241017144918662.png)

#### 静态分配和动态分配

静态分配：进程运行前为其分配全部所需资源，运行结束后归还资源，破坏了“请求和保持”条件，不会发生死锁
动态分配：进程运行过程中动态申请设备资源

![image-20241017145052878](/assets/img/2024-10-14-OperatingSystem/image-20241017145052878.png)

![image-20241017145226007](/assets/img/2024-10-14-OperatingSystem/image-20241017145226007.png)

![image-20241017145312802](/assets/img/2024-10-14-OperatingSystem/image-20241017145312802.png)

![image-20241017145354809](/assets/img/2024-10-14-OperatingSystem/image-20241017145354809.png)

![image-20241017145434945](/assets/img/2024-10-14-OperatingSystem/image-20241017145434945.png)

![image-20241017145558422](/assets/img/2024-10-14-OperatingSystem/image-20241017145558422.png)

缺点：
①用户编程时必须使用“物理设备名”，底层细节对用户不透明，不方便编程
②若换了一个物理设备，则程序无法运行
③若进程请求的物理设备正在忙碌，则即使系统中还有同类型的设备，进程也必须阻塞等待

改进方法：建立逻辑设备名与物理设备名的映射机制，用户编
程时只需提供逻辑设备名

![image-20241017145757781](/assets/img/2024-10-14-OperatingSystem/image-20241017145757781.png)

![image-20241017145832736](/assets/img/2024-10-14-OperatingSystem/image-20241017145832736.png)

![image-20241017145843950](/assets/img/2024-10-14-OperatingSystem/image-20241017145843950.png)

### 缓冲区管理

![image-20241017150044815](/assets/img/2024-10-14-OperatingSystem/image-20241017150044815.png)

![image-20241017150218474](/assets/img/2024-10-14-OperatingSystem/image-20241017150218474.png)

![image-20241017150414898](/assets/img/2024-10-14-OperatingSystem/image-20241017150414898.png)

![image-20241017150647524](/assets/img/2024-10-14-OperatingSystem/image-20241017150647524.png)

![image-20241017150757087](/assets/img/2024-10-14-OperatingSystem/image-20241017150757087.png)

![image-20241017150945703](/assets/img/2024-10-14-OperatingSystem/image-20241017150945703.png)

采用双缓冲策略，处理一个数据块的平均耗时为Max(T,C+M)

![image-20241017151122708](/assets/img/2024-10-14-OperatingSystem/image-20241017151122708.png)

![image-20241017151140189](/assets/img/2024-10-14-OperatingSystem/image-20241017151140189.png)

![image-20241017151413499](/assets/img/2024-10-14-OperatingSystem/image-20241017151413499.png)

![image-20241017151421390](/assets/img/2024-10-14-OperatingSystem/image-20241017151421390.png)

### 磁盘的结构

![image-20241017151615362](/assets/img/2024-10-14-OperatingSystem/image-20241017151615362.png)

![image-20241017151851827](/assets/img/2024-10-14-OperatingSystem/image-20241017151851827.png)

![image-20241017151921428](/assets/img/2024-10-14-OperatingSystem/image-20241017151921428.png)

![image-20241017151947719](/assets/img/2024-10-14-OperatingSystem/image-20241017151947719.png)

### 磁盘调度算法

![image-20241017152337696](/assets/img/2024-10-14-OperatingSystem/image-20241017152337696.png)

![image-20241017152523617](/assets/img/2024-10-14-OperatingSystem/image-20241017152523617.png)

![image-20241017152658193](/assets/img/2024-10-14-OperatingSystem/image-20241017152658193.png)

![image-20241017152926296](/assets/img/2024-10-14-OperatingSystem/image-20241017152926296.png)

![image-20241017153104019](/assets/img/2024-10-14-OperatingSystem/image-20241017153104019.png)![image-20241017153254407](/assets/img/2024-10-14-OperatingSystem/image-20241017153254407.png)

![image-20241017153345929](/assets/img/2024-10-14-OperatingSystem/image-20241017153345929.png)

![image-20241017153355328](/assets/img/2024-10-14-OperatingSystem/image-20241017153355328.png)

### 减少磁盘延迟方法

![image-20241017153559128](/assets/img/2024-10-14-OperatingSystem/image-20241017153559128.png)

交替编号，逻辑上相邻扇区在物理上有一定间隔，可以减少延迟时间

![image-20241017154002964](/assets/img/2024-10-14-OperatingSystem/image-20241017154002964.png)

可以减少磁头移动消耗的时间

![image-20241017154207376](/assets/img/2024-10-14-OperatingSystem/image-20241017154207376.png)

![image-20241017154310985](/assets/img/2024-10-14-OperatingSystem/image-20241017154310985.png)

![image-20241017154321211](/assets/img/2024-10-14-OperatingSystem/image-20241017154321211.png)

### 磁盘管理

![image-20241017155552726](/assets/img/2024-10-14-OperatingSystem/image-20241017155552726.png)

![image-20241017155701820](/assets/img/2024-10-14-OperatingSystem/image-20241017155701820.png)

ROM中只存放很小的自举装入程序，完整的自举程序防止磁盘的启动块（引导块/启动分区）上，启动块位于磁盘的固定位置，开启先运行自举装入程序，找到引导块读入完整的自举程序完成初始化

![image-20241017160029442](/assets/img/2024-10-14-OperatingSystem/image-20241017160029442.png)

![image-20241017160038217](/assets/img/2024-10-14-OperatingSystem/image-20241017160038217.png)

### 固态硬盘SSD

![image-20241017160124819](/assets/img/2024-10-14-OperatingSystem/image-20241017160124819.png)

固态硬盘读/写以页为单位，相当于磁盘一个扇区（闪存翻译层翻译）

![image-20241017160325214](/assets/img/2024-10-14-OperatingSystem/image-20241017160325214.png)

