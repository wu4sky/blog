---
title: tomcat-config
tags: Tomcat
categories: 开发
description: Tomcat配置
indexing: true
hide: false
date: 2025-03-04 16:43:36
updated: 2025-03-04 16:43:36
---

### Tomcat 配置修改

#### Tomcat 服务配置修改

##### 1.bin 包下的配置文件

![image-20250304164535849](../tomcat-config/image-20250304164535849.png)

![image-20250304164636510](../tomcat-config/image-20250304164636510.png)



##### 2.conf 包下⽂件

![image-20250304164742379](../tomcat-config/image-20250304164742379.png)

![image-20250304164807622](../tomcat-config/image-20250304164807622.png)



####  老平台的配置文件修改

##### 1.wabapps 包 配置修改

![image-20250304165022494](../tomcat-config/image-20250304165022494.png)

![image-20250304165116268](../tomcat-config/image-20250304165116268.png)

![image-20250304165129481](../tomcat-config/image-20250304165129481.png)

![image-20250304165405754](../tomcat-config/image-20250304165405754.png)

![image-20250304165540456](../tomcat-config/image-20250304165540456.png)

![image-20250304165610027](../tomcat-config/image-20250304165610027.png)



​			-------------------------- 以上 Tomcat 独立的 配置 ----------------------------------------

### idea 导入项目配置参考

#### 项目配置信息

![image-20250304165949836](../tomcat-config/image-20250304165949836.png)

![image-20250304170007059](../tomcat-config/image-20250304170007059.png)

![image-20250304170019376](../tomcat-config/image-20250304170019376.png)

![image-20250304170909553](../tomcat-config/image-20250304170909553.png)

![image-20250304170956070](../tomcat-config/image-20250304170956070.png)

![image-20250304171012305](../tomcat-config/image-20250304171012305.png)



#### Maven 配置

![image-20250304170141976](../tomcat-config/image-20250304170141976.png)

![image-20250304170158353](../tomcat-config/image-20250304170158353.png)



#### 导入项目后的配置

![image-20250304170237749](../tomcat-config/image-20250304170237749.png)

![image-20250304170251493](../tomcat-config/image-20250304170251493.png)

![image-20250304170306582](../tomcat-config/image-20250304170306582.png)

![image-20250304170324091](../tomcat-config/image-20250304170324091.png)

#### 需要生成 war 包的配置

![image-20250304170418540](../tomcat-config/image-20250304170418540.png)

​	开发包

![image-20250304170454924](../tomcat-config/image-20250304170454924.png)



###  idea 集成的Tomcat的 VM options：

-Xms2048M -Xmx2048M -XX:PermSize=512M -XX:MaxPermSize=512M - Dfile.encoding=UTF-8

![image-20250304170637566](../tomcat-config/image-20250304170637566.png)

![image-20250304170651605](../tomcat-config/image-20250304170651605.png)



### 项目如果是Maven 项目，注意 pom.xml 

![image-20250304170723746](../tomcat-config/image-20250304170723746.png)
