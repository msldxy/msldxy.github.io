# <div align="center">唐凌_JAVA开发工程师<div>

## 个人信息

 - 唐凌/男/1996/18813298644/msldxy@163.com
 - 华南理工大学软件学院
 - Github：http://github.com/msldxy 
 - 期望职位：Java工程师
 - 期望薪资：面议
 - 期望城市：成都
 - 到岗时间：1周内到岗

<hr>

## 专业技能
- 工具：starUML、xmind、Jmeter等；
- 代码：有良好的编程习惯，对底层感兴趣，了解常用的数据结构及算法；
- 前端相关：HTML、CSS、JavaScript、Jquery、VUE、element UI；
- 后端框架：Spring、SpringMVC、Mybatis框架，了解Sring Security、Spring Boot、Spring Task、Spring Cloud等；
- 架构：分布式架构Dubbo+zookeeper，
- 熟悉linux常用命令；
- 数据库相关：MySQL/redis/MongoDB；
- 版本管理、文档和自动化部署工具：Svn/Git

<hr>

## 工作经历

<h3 style="float:left;">广州华多网络科技有限公司</h3><h3 style="float:right;">2017年11月 ~ 2018年3月</h3>
<br><br><br>
岗位：黑盒测试<br>
职责：<br>
1. 参与测试用例编写与评审；<br>
2. 执行部分模块的测试；<br>
3. 提交以及跟踪bug；<br><br>

<h3 style="float:left;">传智播客</h3><h3 style="float:right;">2019年3月 ~ 2019年9月</h3>
<br><br><br>
岗位：Java学徒<br>
职责：<br>
1. 对JavaSE进行系统的学习<br>
2. 学习了Javaweb的基础知识<br>
3. 了解学习了主流框架<br>
4. 完成项目的编写和部署。
<hr>

## 项目经验

### 开心斗

负责一款手机软件“开心斗”的测试，这款软件目前主要是一个玩小游戏的平台。对从6.0.0到6.5.0的版本中的包括首页广场、IM、个人信息等页面功能进行了测试：
* 根据产品文档编写测试用例并评审；
* 使用TestLink执行测试操作；
* 通过jira进行bug的管理：提交以及定期跟踪和验证；
* 在产品上“快乐大本营”推广之前一个月，临时组成一个小组，对大约30个小游戏进行了包括功能测试、兼容测试等，最后成功发布。

### 青橙

开发环境：IDEA+Tomcat+Mysql+Redis+Maven+JDK8
技术选型：SpringMvc+Spring+Mybatis+Dubbox+Zookeeper+Redis
项目周期：2018.8-2019.5
项目描述：青橙购物平台是一个 B2B2C 数据商品平台，主要业务是为人们提供一个选购物品或者销售物品的平台。系统采用 SOA 分布式架构，将不同的功能模块划分为多个子系统，其中包括网站前台系统，搜索系统，订单系统，购物车系统，用户系统，CAS 单点登陆，管理员系统等。系统采用 ssm+dubbo+zookeeper 实现 SOA 架构以及后端功能模块，同时也使用其他多种技术完成整个项目的功能，比如 redis，ActiveMQ，elasticsearch全文检索技术等。
职责描述:
1. 登录拦截：后台使用Spring Security进行登录拦截，如果未登录只能进入到登陆页面；
2. 后台数据统计报表：利用Spring Task创建定时任务，在每晚1点执行统计，将前一天的销售数据统计出来并存入数据库，使用了echarts来展现相应时段的销售数据，通过漏斗图和折线图展示下单量和成交率等；
3. 超时未支付订单：使用延迟消息队列方案，具体为使用“死信交换机”。设置ttl，将满足死信的放入死信交换机中，然后再获取与死信交换机绑定的死信队列，对队列中的订单进行是否支付的判断，然后根据结果进行不同的操作；
4. 负责全组的版本管理，在gitee上进行。包括初始仓库以及后面总共六个人各自的commit、push、pull request、以及最后的merge等；

<hr>

## 致谢
感谢您花时间阅读我的简历，期待能有机会和您共事。
