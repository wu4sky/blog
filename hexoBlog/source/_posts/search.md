---
title: search搜索
date: 2025-01-23 13:04:22
updated: 2025-01-23 13:04:22
tags: 查询
categories: 博客
description: fluid主题下的搜索功能
---

本地搜索功能

npm install hexo-generator-search --save



_config.xml 配置新增加

search:
  path: search.xml
  field: post
  format: html
  limit: 10000

search:
  path: search.xml
  field: post
  format: html
  limit: 10000
  placeholder: Search



​	还需要一个前端搜索功能 

npm install hexo-search --save

搜索数据库

npm install hexo-generator-searchdb --save

解释：

- `path`: 生成的搜索数据库文件的路径。
- `field`: 搜索的字段，通常设置为 `post`。
- `format`: 生成的文件格式，通常设置为 `html`。
- `limit`: 搜索结果的最大数量
- `placeholder`: 搜索框的占位符文本
