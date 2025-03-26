---
title: clone_gitee
tags: clone_gitee
categories: gitee
description: 克隆gitee其他仓库项目
indexing: true
hide: false
date: 2025-03-25 15:13:37
updated: 2025-03-25 15:13:37
---



### 前提:已经创建了gitee 目标项目，且是使用ssh 进行操作的（配置了密钥）

### 克隆gitee 仓库

#### 1.克隆项目:克隆所有的分支、标签和提交记录

~~~
使用 --mirror 参数确保克隆所有的分支、标签和提交记录

git clone --mirror git@gitee.com:Liu_Liu_xin/alipay.git
~~~



#### 2.进入克隆号的项目

~~~
cd 项目名 
lg:
cd alipay.git
~~~



#### 3.将远程地址更改为新的目标仓库地址

~~~
git remote set-url origin https://gitee.com/jp_scientific/choice.git
lg：
git remote set-url origin git@gitee.com:wu4sky/all_clone_test1.git
~~~



#### 4.将所有的提交、分支和标签推送到新的 Gitee 仓库

~~~
git push --mirror
~~~



#### 5：验证迁移是否成功

1. 迁移完成后，访问新仓库 `https://gitee.com/jp_scientific/choice`。

2.  新地址： https://gitee.com/wu4sky/all_clone_test1.git

3. 检查所有分支、标签和提交历史是否已经成功迁移。

   



#### 注意事项

1. 确保你的操作账户对两个仓库具有必要的访问权限。
2. 目标仓库在推送时需要为空仓库，如果它已经存在内容，推送可能会失败。
3. 如果需要在新仓库中设置 Webhooks、Issues、Wiki 等功能，需要手动进行这些设置，因为这些配置不会被迁移



[参考博客](https://blog.csdn.net/Roy_yyds/article/details/144747832)
