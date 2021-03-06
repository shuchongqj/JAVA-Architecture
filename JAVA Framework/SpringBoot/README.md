


<a href="https://ibb.co/2YkyBM6"><img src="https://i.ibb.co/FqDKtYW/spring-boot-v2-5ef5f719b1c3a169a948430159d940a5-r.jpg" alt="spring-boot-v2-5ef5f719b1c3a169a948430159d940a5-r" border="0"></a>

# 搭建环境

[IDEA下从零开始搭建SpringBoot工程](https://blog.csdn.net/u013248535/article/details/55100979)|[建立SpringBoot工程的几种方法](#建立SpringBoot工程的几种方法)|
---|---|

# SpringBoot 基础知识
[SpringBoot注解](https://github.com/stevenli91748/JAVA-Architecture/blob/master/JAVA%20Framework/SpringBoot/SpringBoot注解/README.md)|[springboot基本原理(知识点)](https://blog.csdn.net/z446981439/article/details/103822257)|[SpringBoot实现原理](https://blog.csdn.net/qq_38417983/article/details/81128299)|[Spring Boot要如何学习](https://www.zhihu.com/question/53729800/answer/311948415)
---|---|---|---|

[Springboot启动原理解析](https://zhuanlan.zhihu.com/p/60475611)|[基于Spring Boot项目构建流水线](https://www.bilibili.com/video/av90883375?from=search&seid=1134316332664179526)|[Idea 平台下实现 spring boot 项目 热部署](https://www.bilibili.com/video/av93414618?from=search&seid=1134316332664179526)|[Spring boot项目导入 环境配置](https://www.bilibili.com/video/av45976433?from=search&seid=1134316332664179526)|[如何创建Spring Boot项目脚手架](https://www.bilibili.com/video/av92630366?from=search&seid=1134316332664179526)|
---|---|---|---|---|

[Spring boot 项目打成war包部署到远程服务器tomcat](https://www.bilibili.com/video/av78310165?from=search&seid=1134316332664179526)|[六分钟演示SpringBoot部署到腾讯云绑定域名](https://www.bilibili.com/video/av59319568?from=search&seid=1976421999597493025)|[RESTfull API简单项目的快速搭建](https://www.bilibili.com/video/av13224378?from=search&seid=10786600269014143134)|
---|---|---|

# 启动流程

主要步骤首先要配置environment，然后准备context上下文，包括执行applicationContext的后置处理、初始化initializer、通知listener处理
contextPrepared和contextLoaded事件。最后执行refreshContext，也就是前面介绍过的AbstractApplicationContext类的refresh方法。

PrepareEnvironment|CreateApplicationContext|PostProcessApplicationContext|
---|---|---|

applyinitializers|listeners.contextPrepared|listeners.contextLoaded|refreshContext|
---|--|---|---|

# 配置文件

然后要知道在Spring Boot中有两种上下文，一种是bootstrap, 另外一种是application。

bootstrap是应用程序的父上下文，也就是说bootstrap会先于applicaton加载。bootstrap主要用于从额外的资源来加载配置信息，还可以在本地外部配置文件中解密属性。bootstrap里面的属性会优先加载，默认也不能被本地相同配置覆盖。

bootstrap|application|
---|---|

# 特色模块

starter是springboot提供的无缝集成功能的一种方式，使用某个功能时开发者不需要关注各种依赖库的处理，不需要具体的配置信息，由Spring Boot自动配置进行

bean的创建。例如需要使用web功能时，只需要在依赖中引入spring-boot-starter-web即可。

actuator是用来对应用程序进行监视和管理，通过restful api请求来监管、审计、收集应用的运行情况。

devtools提供了一系列开发工具的支持，来提高开发效率。例如热部署能力等。

CLI就是命令行接口，是一个命令行工具，支持使用Groovy脚本，可以快速搭建spring原型项目。


starter|actuator|devtools|cli|
---|---|---|---|



# 实验

* [基于SpringBoot开发一套完整的项目](https://github.com/stevenli91748/JAVA-Architecture/blob/master/JAVA%20Framework/SpringBoot/实验/基于SpringBoot开发一套完整的项目.md)
* [一个列子让你弄懂SpringBoot实现后台框架的搭建](https://blog.csdn.net/qq_33883389/article/details/81322481)
* [基于springboot+bootstrap+mysql+redis搭建一套完整的权限架构](https://github.com/stevenli91748/JAVA-Architecture/blob/master/JAVA%20Framework/SpringBoot/实验/基于springboot%2Bbootstrap%2Bmysql%2Bredis搭建一套完整的权限架构.md)
* [SpringBoot2.0集成WebSocket，实现后台向前端推送信息](https://blog.csdn.net/moshowgame/article/details/80275084)
* [想要快速上手 Spring Boot？看这些教程就足够了](https://blog.csdn.net/dgqvhtlwq472235338/article/details/101415016)
* [使用Spring Boot+Dubbo+Zookeeper搭建第一个分布式项目(详细介绍如何搭建分布式项目，上篇)](https://blog.csdn.net/weixin_42146366/article/details/90268062)
* [使用Spring Boot+Dubbo+Zookeeper搭建第一个分布式项目(详细介绍如何搭建分布式项目，下篇)](https://blog.csdn.net/weixin_42146366/article/details/90268555)

* [分布式Restful SpringBoot骨架搭建](https://blog.csdn.net/songxinjianqwe/article/details/77478385)
* [SpringBoot+SpringSession+Redis实现session共享及单点登录](https://blog.csdn.net/xjj1040249553/article/details/82658889)


# 目录

 * [Spring Boot概述](#Spring-Boot概述)
 * [建立Spring Boot工程的几种方法](#建立SpringBoot工程的几种方法)

### 知识点

SpringBoot快速上手应用

SpringBoot核心配置详解

SpringBoot集成MyBatis  Redis  ActiveMQ、

RabbitMQ  Dubbo等

SpringBoot计策模板引擎Thymeleaf Freemarker

SpringBoot核心注解详解

Spring启动器starter原理深入分析

### Spring Boot概述

其优点是简化了 Spring 相关组件的配置，实现自动配置，降低了项目搭建的复杂度，使开发变得更加简便，从而提升开发效率。Spring Boot 本身并不提供 Spring 框架的核心特性以及扩展功能，只是用于快速、敏捷地开发新一代基于 Spring 框架的应用程序。

 

Spring Boot 并不是用来替代 Spring 的解决方案，而是和 Spring 框架紧密结合用于提升 Spring 开发者体验的工具。同时它集成了大量常用的第三方库配置，如 Jackson、JDBC、Mongo、Redis、Mail 等，Spring Boot 应用中这些第三方库几乎可以零配置的开箱即用（out-of-the-box），大部分的 Spring Boot 应用都只需要非常少量的配置代码，开发者能够更加专注于业务逻辑。

 

也就是说，Spring Boot 只是起到一个承载的作用，辅助你简化项目搭建的过程。如果承载的是 Web 项目，使用 Spring MVC 作为 MVC 框架，那么整个业务工作流程还是由 Spring MVC 来完成的，因此 Spring Boot 并不能替代 Spring MVC，它只是简化了 Spring MVC 的相关配置，Spring Boot 帮你完成了很多底层工作。

### 建立SpringBoot工程的几种方法

* [1. Spring官方的构建页面来生成项目](http://blog.didispace.com/spring-boot-learning-1/)
* [2. 使用Intellij中的Spring Initializr来快速构建Spring Boot/Cloud工程](http://blog.didispace.com/spring-initializr-in-intellij/)
* [3. 使用Cloud Studio在线编写、调试和管理Spring Boot应用](http://blog.didispace.com/studio-coding-spring-boot-app/#)
* [4. 通过Maven来手工构建](https://blog.csdn.net/u013248535/article/details/55100979)
* [5. 通过脚手架等方式快速搭建]()
* [一站式SpringBoot for NoSQL Study Tutorial 开发教程学习手册](https://www.cnblogs.com/starcrm/p/9667830.html)



# Spring Boot视频
 * [SpringBoot2.0+Shiro+Jwt+SpringDataJpa前后端分离的Saas多租户平台开发](https://www.bilibili.com/video/av75572951/?spm_id_from=333.788.videocard.4)
 * [千锋Java：好评如潮SpringBoot](https://www.bilibili.com/video/av45733135?from=search&seid=15871128637146048672)
 * [千锋 Java微服务架构（Spring Boot + Spring Cloud）](https://www.bilibili.com/video/av36042649?from=search&seid=15871128637146048672)
 * [SpringBoot实战教程（好评如潮）](https://www.bilibili.com/video/av45617671/?spm_id_from=333.788.videocard.0)
 * [SpringBoot 原理分析与知识点详解 （IDEA版）](https://www.bilibili.com/video/av52867311/?spm_id_from=333.788.videocard.13)
 * [教程：IDEA部署springboot程序到docker上](https://www.bilibili.com/video/av40407605/?spm_id_from=333.788.videocard.11)
 * [尚硅谷SpringBoot整合篇](https://www.bilibili.com/video/av23284778/?spm_id_from=333.788.videocard.7)
 * [尚硅谷SpringBoot核心技术课程完整版](https://www.bilibili.com/video/av46503510/?spm_id_from=333.788.videocard.0)
 * [SpringBoot视频教程(idea版)_2019权威教程](https://www.bilibili.com/video/av38657363?from=search&seid=2329343007218467895)
 * [SpringBoot2.0+Shiro+Jwt+SpringDataJpa框架的Saas多租户基于前后端分离进行开发](https://www.bilibili.com/video/av75572951?from=search&seid=553876227072387657)
 * [Spring boot 项目打成war包部署到远程服务器tomcat](https://www.bilibili.com/video/av78310165/?spm_id_from=333.788.videocard.0)
 * [SpringBoot项目实战 视频教程全集](https://www.bilibili.com/video/av62800055/?spm_id_from=333.788.videocard.8)
 * [Spring Boot+FastDFS实现分布式图片服务器视频](https://www.bilibili.com/video/av58752724/?spm_id_from=333.788.videocard.7)
 * [黑马乐优商城12月份完整版【锋哥版】](https://www.bilibili.com/video/av74750602/?spm_id_from=333.788.videocard.9)
 * [4小时学会Spring Boot+Vue前后端分离开发](https://www.bilibili.com/video/av85793766?from=search&seid=25718754058418816)
 
# 有用的参考
  * [Springboot+websocket+vue的聊天程序（项目源代码+部署教程+讲解）](https://www.jianshu.com/p/9b7f2e56276a)
  * [Spring和SpringBoot比较，解惑区别](https://blog.csdn.net/weixin_43770982/article/details/88977526?depth_1-utm_source=distribute.pc_relevant.none-task&utm_source=distribute.pc_relevant.none-task)
  * [Spring Boot面试题（2020最新版）](https://blog.csdn.net/ThinkWon/article/details/104397299)
  * [Spring Boot 学习资料汇总](http://www.ityouknow.com/springboot/2015/12/30/springboot-collect.html)
  * [纯洁的微笑---Spring Boot](http://www.ityouknow.com/spring-boot.html)
  * [Springboot项目搭建（前端到数据库，超详细）](https://blog.csdn.net/sunnyzyq/article/details/86711708?depth_1-utm_source=distribute.pc_relevant.none-task&utm_source=distribute.pc_relevant.none-task)
  * [Spring Boot 学习Sample](https://github.com/ityouknow/spring-boot-examples)
  * [构建微服务：Spring boot 入门篇系列--能够系统性的学习](https://www.cnblogs.com/ityouknow/p/5662753.html)
  * [快速学习SpringBoot技术栈](https://www.jianguoyun.com/p/De_2rM0Q3o_SBhiu1Dw#)
  * [SpringBoot注解最全详解(整合超详细版本)](https://blog.csdn.net/weixin_40753536/article/details/81285046)
  * [Spring Boot 精选课程](https://github.com/ityouknow/spring-boot-leaning)
  * [Spring Boot中使用Swagger2构建强大的RESTful API文档](http://blog.didispace.com/springbootswagger2/)
  * [SpringBoot工作机制概述](https://blog.csdn.net/m0_37962779/article/details/78957309)
  * [在 Spring Boot 项目中使用 Swagger 文档](https://www.ibm.com/developerworks/cn/java/j-using-swagger-in-a-spring-boot-project/index.html)
  * [一篇文章带你搞懂 SpringBoot与Swagger整合](https://blog.csdn.net/itguangit/article/details/78978296)

  * [Spring Boot Tutorial](https://github.com/ganchaoyang/spring-tutorial)
  * [Springboot 整合 Mybatis 的完整 Web 案例](https://zhuanlan.zhihu.com/p/25959187)
  * [SpringBoot常用注解大全](https://zhuanlan.zhihu.com/p/59110902)
  * [SpringBoot 究竟是如何跑起来的?](https://zhuanlan.zhihu.com/p/54146400)
  * [spring boot和SSM开发中有什么区别？](https://www.zhihu.com/question/284488830/answer/618537039?utm_source=wechat_session&utm_medium=social&utm_oi=991812777480134656)
  * [Spring Boot基础教程--优先](http://blog.didispace.com/Spring-Boot基础教程/)
  * [Spring Boot 2.0 新特性学习](http://blog.didispace.com/Spring-Boot-2-0-feature/)
  * [SpringBoot布道系列](https://www.jianshu.com/p/964370d9374e)
  * [Spring Boot 从入门到上瘾](https://www.jianshu.com/c/fc788f631211)
  * [SpringBoot构建web项目](http://objcoding.com/2017/05/03/SpringBoot/)
  * [SpringBoot自动化配置源码分析](http://objcoding.com/2018/01/30/The-principle-of-Spring-Boot-automation-configuration/)
  * [自定义SpringBoot Starter](http://objcoding.com/2018/02/02/Costom-SpringBoot-Starter/)
  * [IDEA下从零开始搭建SpringBoot工程](https://blog.csdn.net/u013248535/article/details/55100979)
  * [十分钟搞定SpringBoot 和Redis 实战整合](https://blog.csdn.net/WYpersist/article/details/81221100)
  * [Docker下redis与springboot三部曲之一：极速体验](https://blog.csdn.net/boling_cavalry/article/details/78991422)
  * [Docker下redis与springboot三部曲之二：安装redis主从和哨兵](https://blog.csdn.net/boling_cavalry/article/details/78995407)
  * [Docker下redis与springboot三部曲之三：springboot下访问redis哨兵](https://blog.csdn.net/boling_cavalry/article/details/79041129)
  * [Spring Boot写后台接口](https://blog.csdn.net/qq_29370483/article/details/79043972)
  * [SpringBoot项目结构介绍](https://blog.csdn.net/zhou6282610/article/details/87868857)
  * [SpringBoot系列之三_一个完整的MVC案例](https://blog.csdn.net/hanhf/article/details/76713838)
  * [spring boot和SSM开发中有什么区别？](https://www.zhihu.com/question/284488830/answer/618290880?utm_source=wechat_session&utm_medium=social&utm_oi=991812777480134656)
  * [spring boot 实战（干货）](https://blog.csdn.net/qq_27384769/article/details/79439844)
  * [SpringBoot内容聚合---非常强大](https://mp.weixin.qq.com/s?__biz=MzI4Njc5NjM1NQ==&mid=2247488811&idx=2&sn=0d054027651bef114ae6bec5a8f62359&chksm=ebd62a07dca1a3111269692dd9b0a5ab8af7d2038b8ec6600a057573364e76db1332adc5fd46&scene=21)
 * [SpringBoot 在IDEA中实现热部署(实用版)](https://www.jianshu.com/p/f658fed35786)
 * [springboot项目快速搭建](https://blog.csdn.net/wjg8209/article/details/94546110#comments)
* [SpringBoot多数据源中的分布式事务](https://blog.csdn.net/weixin_37158722/article/details/103224786)
* [创建Spring Boot项目的几种方式总结](https://www.cnblogs.com/chansblogs/p/9293360.html)
* [在Docker环境构建、打包和运行Spring Boot应用](http://dockone.io/article/9530)
* [SpringBoot+Maven 多模块项目的构建、运行](https://www.jb51.net/article/140772.htm)
* [使用SpringBoot整合ssm项目的实例详解](https://www.jb51.net/article/150315.htm)
* [spring boot整合mybatis利用Mysql实现主键UUID的方法](https://www.jb51.net/article/136207.htm)
* [SpringBoot整合Elasticsearch并实现CRUD操作](https://www.jb51.net/article/136153.htm)
* [SpringBoot整合Shiro实现登录认证的方法](https://www.jb51.net/article/135255.htm)
* [Spring Boot整合mybatis并自动生成mapper和实体实例解析](https://www.jb51.net/article/139659.htm)
* [Spring boot Mybatis 整合（完整版](https://www.jb51.net/article/146932.htm)
* [springboot与mybatis整合实例详解(完美融合)](https://www.jb51.net/article/91800.htm)
* [springboot+springmvc+mybatis项目整合](https://www.jb51.net/article/137563.htm)
* [SpringBoot整合MyBatis逆向工程及 MyBatis通用Mapper实例详解](https://www.jb51.net/article/123822.htm)
* [详解Spring Boot整合Mybatis实现 Druid多数据源配置](https://www.jb51.net/article/109452.htm)
* [springboot整合mybatis将sql打印到日志的实例详解](https://www.jb51.net/article/130734.htm)
* [Springboot整合支付宝沙箱支付（支付和退款）](https://www.jianshu.com/p/b256e62fb3c9)
* [SpringBoot 创建定时任务（配合数据库动态执行）](https://www.jianshu.com/p/fd863dc561b3)
* [Springboot项目配置https](https://www.jianshu.com/p/3e1b4695bf77)

