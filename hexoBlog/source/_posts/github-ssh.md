---
title: ssh密钥
date: 2025-01-22 15:41:57
updated: 2025-01-22 15:41:57
tags: ssh密钥
categories: 密钥
description: ssh密钥生成及配置
---
github-ssh

1.创建ssh密钥文件

或 ssh-keygen -t rsa -b 4096 -C "完整的邮箱地址" -f \~/.ssh/id_rsa_ambition

 	ssh-keygen -t rsa -b 4096 -C "完整的邮箱地址" -f C:\Users\ambition\.ssh\id_rsa_ambition

ssh-keygen -t rsa -C "GitHub邮箱" ,三此确认

![image-20250123112728946](../github-ssh/image-20250123112728946.png)

![image-20250123113038376](../github-ssh/image-20250123113038376.png)

![image-20250123112938413](../github-ssh/image-20250123112938413.png)

2.获取公用密码上传github

径 C:\Users${name}/.ssh/id_rsa.pub，并用记事本打开，将内容复制



3.github 的SSH and GPG keys ，点击 New SSH key 创建新的秘钥

4.测试是否连接 

​	ssh -T git@github.com

![image-20250123113153722](../github-ssh/image-20250123113153722.png)

![image-20250123113224161](../github-ssh/image-20250123113224161.png)





ssh -T git@git.ambition-soft.com

ssh -i C:\Users\<YourUsername>\.ssh\id_rsa_ambition git@git.ambition-soft.com



多个秘钥

创建 config文件

Host git.xxx.cn

HostName git.xxx.cn

 User git

IdentityFile ~/.ssh/对应私有密钥

IdentitiesOnly yes

#配置 git.ambition-soft.com ssh -T git@git.ambition-soft.com

Host git.ambition-soft.com
  HostName git.ambition-soft.com
  User git
  IdentityFile ~/.ssh/id_rsa_ambition
  IdentitiesOnly yes

配置 git@github.com ssh -T git@github.com

Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa
  IdentitiesOnly yes



