---
title: RockerMQ-summary
date: 2024-10-13 18:05:10 +0800
categories: [interview, RockerMQ]
tags: [interview, RockerMQ]     # TAG names should always be lowercase
typora-root-url: ./..
typora-copy-images-to: ./..\assets\img\2024-10-12-RocketMQ-summay
---



## 初识RocketMQ

![RocketMQ基本模型](https://rocketmq.apache.org/zh/assets/images/RocketMQ%E5%9F%BA%E6%9C%AC%E6%A8%A1%E5%9E%8B-ebcf3458d04b36f47f4c9633c1e36bf7.png)

存储消息Topic的 **代理服务器**( **Broker** )，是实际部署过程对应的代理服务器

对Topic进行分区为MessageQueue，水平扩展消息写入能力，ConsumerGroup扩展消息的消费能力

### 模型

![RocketMQ部署架构](https://rocketmq.apache.org/zh/assets/images/RocketMQ%E9%83%A8%E7%BD%B2%E6%9E%B6%E6%9E%84-ee0435f80da5faecf47bca69b1c831cb.png)

### Producer

构建并传输消息到服务端的运行实体，通常集成在业务系统中

### Consumer

接收并处理消息的运行实体，通常集成在业务系统中

### NameServer

一个简单的 Topic 路由注册中心，支持 Topic、Broker 的动态注册与发现，功能：

broker管理：接收broker集群注册信息作为路由信息基本数据

路由信息管理：保存路由信息和用于客户端查询的队列信息，producer和consumer通过nameserver知道整个集群的路由信息从而进行消息的投递和消费

### [Broker](https://rocketmq.apache.org/zh/docs/4.x/introduction/02whatis#%E4%BB%A3%E7%90%86%E6%9C%8D%E5%8A%A1%E5%99%A8-broker)

负责消息的存储、投递和查询以及服务高可用保证

### Message

#### topic

要发送的消息的主题，标识同一类业务逻辑的消息，通过 Topic 对不同的业务消息进行分类

#### **body** 

消息的存储内容

#### Tag

业务上用来归类的标识，可以理解为二级分类，用来进一步区分某个 Topic 下的消息分类

## 功能特性

### 消息类型

#### [普通消息](https://rocketmq.apache.org/zh/docs/featureBehavior/01normalmessage)

最基础的消息

微服务异步解耦（上游订单系统将用户下单支付这一业务事件封装成独立的普通消息并发送至Apache RocketMQ服务端，下游按需从服务端订阅消息并按照本地消费逻辑处理下游任务）、数据集成传输（离线日志收集）

#### 定时/延时消息

服务端根据消息设置的定时时间在某一固定时刻将消息投递给消费者消费

分布式定时调度（实现各类精度的定时任务）、任务超时处理

#### 顺序消息

上游的事件变更需要按照顺序传递到下游进行处理

撮合交易（股票交易对于出价相同的交易单，坚持按照先出价先交易的原则）、数据实时增量同步

#### 事务消息

保证核心业务和多个下游业务的执行结果完全一致![事务消息](https://rocketmq.apache.org/zh/assets/images/transflow-0b07236d124ddb814aeaf5f6b5f3f72c.png)

1. 生产者将消息发送至Apache RocketMQ服务端。
2. Apache RocketMQ服务端将消息持久化成功之后，向生产者返回Ack确认消息已经发送成功，此时消息被标记为"暂不能投递"，这种状态下的消息即为半事务消息。
3. 生产者开始执行本地事务逻辑。
4. 生产者根据本地事务执行结果向服务端提交二次确认结果（Commit或是Rollback），服务端收到确认结果后处理逻辑如下：
    - 二次确认结果为Commit：服务端将半事务消息标记为可投递，并投递给消费者。
    - 二次确认结果为Rollback：服务端将回滚事务，不会将半事务消息投递给消费者。
5. 在断网或者是生产者应用重启的特殊情况下，若服务端未收到发送者提交的二次确认结果，或服务端收到的二次确认结果为Unknown未知状态，经过固定时间后，服务端将对消息生产者即生产者集群中任一生产者实例发起消息回查。 **说明** 服务端回查的间隔时间和最大回查次数，请参见[参数限制](https://rocketmq.apache.org/zh/docs/introduction/03limits)。
6. 生产者收到消息回查后，需要检查对应消息的本地事务执行的最终结果。
7. 生产者根据检查到的本地事务的最终状态再次提交二次确认，服务端仍按照步骤4对半事务消息进行处理

### 消息发送重试和流控机制

#### 发送重试

因为网络故障、服务异常等原因导致调用失败需要发送重试

- 同步发送：调用线程会一直阻塞，直到某次重试成功或最终重试失败，抛出错误码和异常。
- 异步发送：调用线程不会阻塞，但调用结果会通过异常事件或者成功事件返回

#### 流控机制

系统容量或水位过高， Apache RocketMQ 服务端会通过快速失败返回流控错误来避免底层资源承受过高压力。

### 消费者分类

#### PushConsumer

#### PullConsumer

#### SimpleConsumer

### 消息过滤

#### Tag标签过滤

#### SQL属性过滤

### 消费模式

#### 集群消费模式

任意一条消息只需要被消费组内的任意一个消费者处理

![集群消费模式](https://rocketmq.apache.org/zh/assets/images/%E9%9B%86%E7%BE%A4%E6%B6%88%E8%B4%B9%E6%A8%A1%E5%BC%8F-7f4462d200247db35ca90bb67df7c9b1.png)

#### 广播消费模式

每条消息需要被消费组的每个消费者处理的场景，每个消费者都会收到订阅Topic的全量消息

分配策略：包括平均分配策略（默认）、机房优先分配策略、一致性hash分配策略等

### 负载均衡

#### 消息粒度

![消息粒度负载](https://rocketmq.apache.org/zh/assets/images/clustermode-dfd781d08bc0c69111841bda537aa302.png)

#### 队列粒度

![队列级负载均衡原理](https://rocketmq.apache.org/zh/assets/images/clusterqueuemode-ce4f88dc594c1237ba95db2fa9146b8c.png)

### 存储和清理机制