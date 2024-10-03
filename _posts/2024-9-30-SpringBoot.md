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

#### 整合Redis

导入spring-boot-starter-data-redis，配置，注入RedisTemplate，使用
