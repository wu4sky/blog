---
title: sqlServer备份
tags: 备份
categories: 数据库
description: SQL server 数据库定时备份
indexing: true
hide: false
date: 2025-03-20 10:20:37
updated: 2025-03-20 10:20:37
---



## SQL server 数据库定时备份设置

#### 1.SQL Server代理已启用，此为前提

​	确保SQL Server代理已启动。如果显示“Agent XPs disabled”，请按 **Win+R**，输入 **services.msc** 并确定，在服务列表中启用SQL Server代理

![image-20250320102558150](../sqlServer备份/image-20250320102558150.png)



### 使用SQL Server Management Studio（SSMS）是微软SQL Server的集成管理工具操作

#### 2.新建维护计划

![image-20250320102650590](../sqlServer备份/image-20250320102650590.png)

![image-20250320102742873](../sqlServer备份/image-20250320102742873.png)



#### 3.设计维护计划-从工具箱获取维护计划

![image-20250320102849767](../sqlServer备份/image-20250320102849767.png)

![image-20250320102909665](../sqlServer备份/image-20250320102909665.png)

![image-20250320102928861](../sqlServer备份/image-20250320102928861.png)



#### 4.设计计划内容

![image-20250320103006971](../sqlServer备份/image-20250320103006971.png)

![image-20250320103046496](../sqlServer备份/image-20250320103046496.png)

![image-20250320103110138](../sqlServer备份/image-20250320103110138.png)

##### 可以使用其他的配置

![image-20250320103128029](../sqlServer备份/image-20250320103128029.png)



#### 5.设计计划运行时间，保存计划

![image-20250320103301462](../sqlServer备份/image-20250320103301462.png)

![image-20250320103349483](../sqlServer备份/image-20250320103349483.png)



##### 可以在此，添加不同的子计划

![image-20250320103459297](../sqlServer备份/image-20250320103459297.png)



#### 6.设置清理任务

![image-20250320103634915](../sqlServer备份/image-20250320103634915.png)

![image-20250320103700839](../sqlServer备份/image-20250320103700839.png)



### 7.保存后进行计划测试

![image-20250320103847162](../sqlServer备份/image-20250320103847162.png)

![image-20250320103753076](../sqlServer备份/image-20250320103753076.png)

![image-20250320103810946](../sqlServer备份/image-20250320103810946.png)

##### 或者 

![image-20250320103947956](../sqlServer备份/image-20250320103947956.png)



### 参考链接

[ 参考1](https://www.abackup.com/enterprise-backup/how-to-do-automatic-database-backup-666.html)

[参考2](https://blog.csdn.net/weixin_70604753/article/details/143708256)

[参考3](https://www.cnblogs.com/monkey6/p/17839068.html)

[备份恢复](https://blog.csdn.net/wuhao1468348557/article/details/108514985)
