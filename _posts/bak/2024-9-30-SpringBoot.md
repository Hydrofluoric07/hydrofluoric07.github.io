---
title: SpringBoot笔记
date: 2024-09-30 8:49:00 +0800
categories: [note, SpringBoot]
tags: [sringBoot, note]     # TAG names should always be lowercase
typora-copy-images-to: ./..\assets\img\2024-9-27-SpringBoot
typora-root-url: ./..
---

## 运维实用篇

### 工程打包与运行

![image-20240930085429704](/assets/img/2024-9-27-SpringBoot/image-20240930085429704.png)

![image-20240930090518697](/assets/img/2024-9-27-SpringBoot/image-20240930090518697.png)

### Linux部署

![image-20240930130011108](/assets/img/2024-9-27-SpringBoot/image-20240930130011108.png)

### 配置

![image-20240930130418373](/assets/img/2024-9-27-SpringBoot/image-20240930130418373.png)

优先级：

![image-20240930131618377](/assets/img/2024-9-27-SpringBoot/image-20240930131618377.png)

## 开发实用篇

### 热部署

![image-20240930134229829](/assets/img/2024-9-27-SpringBoot/image-20240930134229829.png)

![image-20240930134306299](/assets/img/2024-9-27-SpringBoot/image-20240930134306299.png)

IDEA可以设置自动热部署

![image-20240930134959263](/assets/img/2024-9-27-SpringBoot/image-20240930134959263.png)

修改热部署范围：

![image-20240930135156805](/assets/img/2024-9-27-SpringBoot/image-20240930135156805.png)

关闭热部署，防止配置覆盖

![image-20240930135621603](/assets/img/2024-9-27-SpringBoot/image-20240930135621603.png)

### 配置高级

![image-20240930142914822](/assets/img/2024-9-27-SpringBoot/image-20240930142914822.png)

![image-20240930143220811](/assets/img/2024-9-27-SpringBoot/image-20240930143220811.png)

![image-20240930143253656](/assets/img/2024-9-27-SpringBoot/image-20240930143253656.png)

![image-20241002103523273](/assets/img/2024-9-27-SpringBoot/image-20241002103523273.png)

宽松绑定不支持@Value引用单个属性方式

### 计量单位

![image-20241002104508670](/assets/img/2024-9-27-SpringBoot/image-20241002104508670.png)

### bean属性校验

![image-20241002105301852](/assets/img/2024-9-27-SpringBoot/image-20241002105301852.png)

![image-20241002105312188](/assets/img/2024-9-27-SpringBoot/image-20241002105312188.png)

![image-20241002105321875](/assets/img/2024-9-27-SpringBoot/image-20241002105321875.png)

### 进制数据转换

![image-20241002110945084](/assets/img/2024-9-27-SpringBoot/image-20241002110945084.png)

### 测试

![image-20241003101618257](/assets/img/2024-9-27-SpringBoot/image-20241003101618257.png)

加载测试配置范围配置应用于小范围测试环境![image-20241003102005309](/assets/img/2024-9-27-SpringBoot/image-20241003102005309.png)

![image-20241003103127428](/assets/img/2024-9-27-SpringBoot/image-20241003103127428.png)

![image-20241003161054680](/assets/img/2024-9-27-SpringBoot/image-20241003161054680.png)

还可进行响应头、响应体、响应头匹配

![image-20241003162343855](/assets/img/2024-9-27-SpringBoot/image-20241003162343855.png)

![image-20241003163005992](/assets/img/2024-9-27-SpringBoot/image-20241003163005992.png)

### 数据层解决方案

![image-20241003163829095](/assets/img/2024-9-27-SpringBoot/image-20241003163829095.png)

![image-20241003163855126](/assets/img/2024-9-27-SpringBoot/image-20241003163855126.png)

![image-20241003164928667](/assets/img/2024-9-27-SpringBoot/image-20241003164928667.png)

SpringBoot提供了三种内嵌的数据库，H2，HSQL，Derby

![image-20241003165334939](/assets/img/2024-9-27-SpringBoot/image-20241003165334939.png)

![image-20241003165554140](/assets/img/2024-9-27-SpringBoot/image-20241003165554140.png)

![image-20241003170609968](/assets/img/2024-9-27-SpringBoot/image-20241003170609968.png)

#### Redis

导入spring-boot-starter-data-redis，配置，注入RedisTemplate，使用

![image-20241004155913932](/assets/img/2024-9-27-SpringBoot/image-20241004155913932.png)

#### MongoDB

MongoDB是一个开源、高性能、无模式的文档型数据库，NoSQL数据库产品中的一种，是最像关系型数据库的非关系型数据库

适用数据特征：永久性存储与临时存储相结合、修改频度较高

![image-20241004161618104](/assets/img/2024-9-27-SpringBoot/image-20241004161618104.png)

![image-20241004161631922](/assets/img/2024-9-27-SpringBoot/image-20241004161631922.png)

导入spring-boot-starter-data-mongodb，配置，注入MongoTemplate使用

#### ElasticSearch

![image-20241004172644769](/assets/img/2024-9-27-SpringBoot/image-20241004172644769.png)

![image-20241004172610187](/assets/img/2024-9-27-SpringBoot/image-20241004172610187.png)

![image-20241004172738898](/assets/img/2024-9-27-SpringBoot/image-20241004172738898.png)

1、导入spring-boot-starter-data-elasticsearch，配置，注入ElasticSearchRestTemplate

2、导入elasticsearch-rest-high-level-client，初始化RestHighLevelClient

![image-20241004173712597](/assets/img/2024-9-27-SpringBoot/image-20241004173712597.png)

![image-20241004173752470](/assets/img/2024-9-27-SpringBoot/image-20241004173752470.png)

@BeforeEach、@AfterEach是SpringBoot Test提供的

![image-20241004173807373](/assets/img/2024-9-27-SpringBoot/image-20241004173807373.png)

![image-20241004174749041](/assets/img/2024-9-27-SpringBoot/image-20241004174749041.png)

![image-20241004174817189](/assets/img/2024-9-27-SpringBoot/image-20241004174817189.png)

![image-20241004174827700](/assets/img/2024-9-27-SpringBoot/image-20241004174827700.png)

![image-20241004175526641](/assets/img/2024-9-27-SpringBoot/image-20241004175526641.png)

![image-20241004175540822](/assets/img/2024-9-27-SpringBoot/image-20241004175540822.png)

### SpringBoot缓存

缓存是一种介于数据永久存储介质与数据应用之间的数据临时存储介质，可以有效的减少低速数据读取过程的次数（例如磁盘IO），提高系统性能，还可以提供临时的数据存储空间

导入spring-boot-starter-cache，启动类@EnableCaching

![image-20241004181104748](/assets/img/2024-9-27-SpringBoot/image-20241004181104748.png)

缓存中存在返回值，否则执行方法，注意对应类需要被容器管理

#### 使用ehcache

导入，配置pom.xml、ehcache.xml

#### 数据淘汰策略

![image-20241007083111605](/assets/img/2024-9-27-SpringBoot/image-20241007083111605.png)

#### 使用Redis

导入，配置pom.xml

#### 使用memcached

![image-20241007083924192](/assets/img/2024-9-27-SpringBoot/image-20241007083924192.png)

![image-20241007084815357](/assets/img/2024-9-27-SpringBoot/image-20241007084815357.png)

#### 使用jetcache

对SpringCache:进行了封装，在原有功能基础上实现了多级缓存、缓存统计、自动刷新、异步调用、数据报表等功能

![image-20241007085202172](/assets/img/2024-9-27-SpringBoot/image-20241007085202172.png)

![image-20241007091218714](/assets/img/2024-9-27-SpringBoot/image-20241007091218714.png)

![image-20241007091301252](/assets/img/2024-9-27-SpringBoot/image-20241007091301252.png)

![image-20241007091327515](/assets/img/2024-9-27-SpringBoot/image-20241007091327515.png)

![image-20241007091341932](/assets/img/2024-9-27-SpringBoot/image-20241007091341932.png)

启用方法注解

![image-20241007092413248](/assets/img/2024-9-27-SpringBoot/image-20241007092413248.png)

![image-20241007092504165](/assets/img/2024-9-27-SpringBoot/image-20241007092504165.png)

#### j2cache

一个缓存整合框架，可以提供缓存的整合方案，使各种缓存搭配使用，自身不提供缓存功能

### Spring任务

#### Quartz

![image-20241007094723850](/assets/img/2024-9-27-SpringBoot/image-20241007094723850.png)

![image-20241007095553578](/assets/img/2024-9-27-SpringBoot/image-20241007095553578.png)

![image-20241007095609247](/assets/img/2024-9-27-SpringBoot/image-20241007095609247.png)

#### Task

@EnableScheduling

![image-20241007100523046](/assets/img/2024-9-27-SpringBoot/image-20241007100523046.png)

![image-20241007100533457](/assets/img/2024-9-27-SpringBoot/image-20241007100533457.png)

### Spring邮件

![image-20241007100922369](/assets/img/2024-9-27-SpringBoot/image-20241007100922369.png)

![image-20241007101651831](/assets/img/2024-9-27-SpringBoot/image-20241007101651831.png)

![image-20241007101708405](/assets/img/2024-9-27-SpringBoot/image-20241007101708405.png)

### Spring消息

同步消息、异步消息

![image-20241007102941921](/assets/img/2024-9-27-SpringBoot/image-20241007102941921.png)

企业级应用中广泛使用的三种异步消息传递技术JMS、AMQP、MQTT

![image-20241007103323256](/assets/img/2024-9-27-SpringBoot/image-20241007103323256.png)

![image-20241007103632325](/assets/img/2024-9-27-SpringBoot/image-20241007103632325.png)

#### 案例

![image-20241007103911900](/assets/img/2024-9-27-SpringBoot/image-20241007103911900.png)

#### Active MQ

![image-20241007110357760](/assets/img/2024-9-27-SpringBoot/image-20241007110357760.png)

![image-20241007110443985](/assets/img/2024-9-27-SpringBoot/image-20241007110443985.png)

![image-20241007110455969](/assets/img/2024-9-27-SpringBoot/image-20241007110455969.png)

![image-20241007110507834](/assets/img/2024-9-27-SpringBoot/image-20241007110507834.png)

#### Rabit MQ

![image-20241007145641193](/assets/img/2024-9-27-SpringBoot/image-20241007145641193.png)

导入spring-boot-statter-amqp，配置

##### 直连交换机模式

![image-20241007150720488](/assets/img/2024-9-27-SpringBoot/image-20241007150720488.png)

![image-20241007150735681](/assets/img/2024-9-27-SpringBoot/image-20241007150735681.png)

![image-20241007150753910](/assets/img/2024-9-27-SpringBoot/image-20241007150753910.png)

![image-20241007150814336](/assets/img/2024-9-27-SpringBoot/image-20241007150814336.png)

![image-20241007150826384](/assets/img/2024-9-27-SpringBoot/image-20241007150826384.png)

##### 主题交换机模式

![image-20241007151521631](/assets/img/2024-9-27-SpringBoot/image-20241007151521631.png)

![image-20241007151545089](/assets/img/2024-9-27-SpringBoot/image-20241007151545089.png)

![image-20241007151623104](/assets/img/2024-9-27-SpringBoot/image-20241007151623104.png)

![image-20241007151631446](/assets/img/2024-9-27-SpringBoot/image-20241007151631446.png)

#### RocketMQ

![image-20241007151846972](/assets/img/2024-9-27-SpringBoot/image-20241007151846972.png)

![image-20241007152040939](/assets/img/2024-9-27-SpringBoot/image-20241007152040939.png)

![image-20241007152525916](/assets/img/2024-9-27-SpringBoot/image-20241007152525916.png)

![image-20241007152539839](/assets/img/2024-9-27-SpringBoot/image-20241007152539839.png)

导入rocketmq-spring-boot-starter

![image-20241007153346734](/assets/img/2024-9-27-SpringBoot/image-20241007153346734.png)

![image-20241007153402308](/assets/img/2024-9-27-SpringBoot/image-20241007153402308.png)

![image-20241007153417529](/assets/img/2024-9-27-SpringBoot/image-20241007153417529.png)

![image-20241007153425471](/assets/img/2024-9-27-SpringBoot/image-20241007153425471.png)

#### Kafka

![image-20241007153832214](/assets/img/2024-9-27-SpringBoot/image-20241007153832214.png)

![image-20241007153901634](/assets/img/2024-9-27-SpringBoot/image-20241007153901634.png)

![image-20241007154024738](/assets/img/2024-9-27-SpringBoot/image-20241007154024738.png)

导入spring-kafka

![image-20241007155928237](/assets/img/2024-9-27-SpringBoot/image-20241007155928237.png)

![image-20241007155936430](/assets/img/2024-9-27-SpringBoot/image-20241007155936430.png)

![image-20241007155945272](/assets/img/2024-9-27-SpringBoot/image-20241007155945272.png)

### 监控

![image-20241007160119999](/assets/img/2024-9-27-SpringBoot/image-20241007160119999.png)

显示监控信息的服务器：用于获取服务信息，并显示对应的信息
运行的服务：启动时主动上报，告知监控服务器自己需要受到监控

#### Spring Boot Admin

服务端导入spring-boot-admin-starter-server，注解@EnableAdminServer，客户端导入spring-boot-admin-starter-client

![image-20241007162546796](/assets/img/2024-9-27-SpringBoot/image-20241007162546796.png)

![image-20241007162950846](/assets/img/2024-9-27-SpringBoot/image-20241007162950846.png)

![image-20241007163612579](/assets/img/2024-9-27-SpringBoot/image-20241007163612579.png)

![image-20241007163647863](/assets/img/2024-9-27-SpringBoot/image-20241007163647863.png)

可以为info、health、metrics等自定义指标控制

![image-20241007170101755](/assets/img/2024-9-27-SpringBoot/image-20241007170101755.png)

## 原理篇

### bean的加载方式

#### 方式1

![image-20241008075046590](/assets/img/2024-9-27-SpringBoot/image-20241008075046590.png)

 #### 方式2![image-20241008075927294](/assets/img/2024-9-27-SpringBoot/image-20241008075927294.png)

![image-20241008075942073](/assets/img/2024-9-27-SpringBoot/image-20241008075942073.png)

#### 方式3![image-20241008080341477](/assets/img/2024-9-27-SpringBoot/image-20241008080341477.png)

##### FactoryBean接口

![image-20241008080858945](/assets/img/2024-9-27-SpringBoot/image-20241008080858945.png)

![image-20241008081230826](/assets/img/2024-9-27-SpringBoot/image-20241008081230826.png)

##### ProxyBeanMethods

![image-20241008081857217](/assets/img/2024-9-27-SpringBoot/image-20241008081857217.png)

默认值为true，通过book()获取的对象实际上是同一个对象

#### 加载方式4

无侵入式

![image-20241008082352549](/assets/img/2024-9-27-SpringBoot/image-20241008082352549.png)

![image-20241008082542947](/assets/img/2024-9-27-SpringBoot/image-20241008082542947.png)

#### 加载方式5

![image-20241008082942873](/assets/img/2024-9-27-SpringBoot/image-20241008082942873.png)

#### 加载方式6

可以根据条件加载什么类型bean

![image-20241008083746802](/assets/img/2024-9-27-SpringBoot/image-20241008083746802.png)

#### 加载方式7

![image-20241008085445912](/assets/img/2024-9-27-SpringBoot/image-20241008085445912.png)

#### 加载方式8

![image-20241008090108683](/assets/img/2024-9-27-SpringBoot/image-20241008090108683.png)

![image-20241008090142974](/assets/img/2024-9-27-SpringBoot/image-20241008090142974.png)

### bean的加载控制

bean的加载控制指根据特定情况对bean进行选择性加载以达到适用于项目的目标。

编程形式：

![image-20241008091134391](/assets/img/2024-9-27-SpringBoot/image-20241008091134391.png)

注解形式：

@Conditional注解及其子注解，匹配类、环境等

### bean依赖属性控制

![image-20241008093539727](/assets/img/2024-9-27-SpringBoot/image-20241008093539727.png)

![image-20241008093626626](/assets/img/2024-9-27-SpringBoot/image-20241008093626626.png)

![image-20241008093642761](/assets/img/2024-9-27-SpringBoot/image-20241008093642761.png)

业务bean应尽量避免设置强制加载，而是根据需要导入后加载，降低spring容器管理bean的强度

### 自动配置原理

![image-20241008094148010](/assets/img/2024-9-27-SpringBoot/image-20241008094148010.png)

![image-20241008101814535](/assets/img/2024-9-27-SpringBoot/image-20241008101814535.png)

![image-20241008102325776](/assets/img/2024-9-27-SpringBoot/image-20241008102325776.png)

![image-20241008102354730](/assets/img/2024-9-27-SpringBoot/image-20241008102354730.png)

![image-20241008102420602](/assets/img/2024-9-27-SpringBoot/image-20241008102420602.png)

### 自定义starter

![image-20241008125359789](/assets/img/2024-9-27-SpringBoot/image-20241008125359789.png)

![image-20241008125415427](/assets/img/2024-9-27-SpringBoot/image-20241008125415427.png)

### SpringBoot启动过程

![image-20241009104154387](/assets/img/2024-9-27-SpringBoot/image-20241009104154387.png)

![image-20241009180316615](/assets/img/2024-9-27-SpringBoot/image-20241009180316615.png)

