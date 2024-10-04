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
