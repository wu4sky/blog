---
title: amb-project-init-idea
tags: idea
categories: 项目初始化
description: 安必兴idea项目导入初始化
indexing: true
hide: false
date: 2025-03-04 09:28:07
updated: 2025-03-04 09:28:07
---

​	ambition 导入idea 项目初始化

1、根据获取的项目类型导入idea后，先设置jdk版本、Maven 路径

![image-20250304093422011](../amb-project-init-idea/image-20250304093422011.png)

![image-20250304094230004](../amb-project-init-idea/image-20250304094230004.png)

 maven 配置【可以不用】输入内容：`-DarchetypeCatalog=internal`

![image-20250304094801514](../amb-project-init-idea/image-20250304094801514.png)



2、项目配置

1. project

![image-20250304100355479](../amb-project-init-idea/image-20250304100355479.png)

2. modules 

​	2.1sources 设置文件类型属性

![image-20250304100744675](../amb-project-init-idea/image-20250304100744675.png)

​	2.2paths ,此为 src 源码编译后的路径输出位置

![image-20250304100834047](../amb-project-init-idea/image-20250304100834047.png)

​	2.3 dependencies 项目的lib 包引入

![image-20250304101147422](../amb-project-init-idea/image-20250304101147422.png)

​	2.4需要一个web ，配置的是项目中存在的 web.xml

![image-20250304101253003](../amb-project-init-idea/image-20250304101253003.png)

![image-20250304101739147](../amb-project-init-idea/image-20250304101739147.png)

3. artifacts 工件配置，根据开发还是打包，选择不同的type

![image-20250304102054536](../amb-project-init-idea/image-20250304102054536.png)

![image-20250304102142772](../amb-project-init-idea/image-20250304102142772.png)

4. 引入项目需要的lib

![image-20250304102220986](../amb-project-init-idea/image-20250304102220986.png)

5. 再次查询此配置路径是否正确

![image-20250304102257535](../amb-project-init-idea/image-20250304102257535.png)

6. 初始编译项目，有根据提示进行处理

![image-20250304103240139](../amb-project-init-idea/image-20250304103240139.png)  



3、Tomcat 启动项目

1.添加Tomcat

![image-20250304103623858](../amb-project-init-idea/image-20250304103623858.png)

![image-20250304103646464](../amb-project-init-idea/image-20250304103646464.png)

![image-20250304104343788](../amb-project-init-idea/image-20250304104343788.png)

![image-20250304104745449](../amb-project-init-idea/image-20250304104745449.png)

![image-20250304103756920](../amb-project-init-idea/image-20250304103756920.png)

![image-20250304104118995](../amb-project-init-idea/image-20250304104118995.png)

![image-20250304104152973](../amb-project-init-idea/image-20250304104152973.png)

2.添加Tomcat的工件及路径 （按需配置）

![image-20250304103848475](../amb-project-init-idea/image-20250304103848475.png)

![image-20250304104011280](../amb-project-init-idea/image-20250304104011280.png)

3.添加输出log日志

![image-20250304104235379](../amb-project-init-idea/image-20250304104235379.png)

![image-20250304104544758](../amb-project-init-idea/image-20250304104544758.png)



​	可以启动项目了，以上参考，根据自己项目情况修改




参考别人的项目
## 参考

[^1]: [idea项目导入](https://blog.csdn.net/thinkingmyself/article/details/100125784)

[^2]:[Maven初始](https://blog.csdn.net/qq_42057154/article/details/106114515?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-1-106114515-blog-140355461.235^v43^pc_blog_bottom_relevance_base2&spm=1001.2101.3001.4242.2&utm_relevant_index=2)

[^3]: [idea项目导入](https://blog.csdn.net/qq_69304031/article/details/141090800?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-1-141090800-blog-127661994.235^v43^pc_blog_bottom_relevance_base2&spm=1001.2101.3001.4242.2&utm_relevant_index=2)