---
title: npm-or-other命令文档
tags: npm
categories: 前端语言
description: 关于npm或其他命令使用
indexing: true
hide: false
date: 2025-01-28 01:05:06
updated: 2025-01-28 01:05:06
---
### 关于 npm 命令使用

###### 1.当前项目包含的插件
``` yaml
 npm list --depth=0
```
###### 2.全局包含的插件
``` yaml
 npm list -g --depth=0
 npm list -g hexo-cli
 npm list hexo-cli
 npx hexo --version
```
###### 3.安装插件到当前项目
``` yaml
 npm install --save-dev electron-builder
```
###### 4.安装插件到全局
``` yaml
 npm install -g electron-builder
 指定版本:
 npm i -g hexo-cli@4.3.2
```
###### 5.卸载当前项目插件
``` yaml
npm uninstall --save-dev electron-builder
```
###### 6.卸载全局插件
``` yaml
npm uninstall -g electron-builder
	当前的:
npm uninstall --save-dev electron-builder
```
###### 7.查看当前项目node_modules依赖安装位置
``` yaml
npm root
```
###### 8.查看全局node_modules依赖安装位置
``` yaml
npm root -g
```
###### 9.清除指定依赖
``` yaml
rm -rf node_modules/electron-builder
```
### electron-builder插件 
``` yaml
全局安装:
npm install -g electron-builder
当前项目:
npm install --save-dev electron-builder
```
[参考](https://blog.csdn.net/github_39132491/article/details/144499135)、[参考2](https://www.jianshu.com/p/db650673266f)

###### ⚠️1.如果全局安装存在，但是未链接到当前项目，可以手动链接
``` yaml
npm link electron-builder
```
###### 2.验证是否安装成功
``` yaml
electron-builder --version
or
npx electron-builder --version
```
###### 3.打包命令
``` yaml
macO:
npm run build -- -m
    1.在非macOS环境下无法直接打包macOS应用
    2.macOS打包需要安装Xcode，并确保正确配置了签名证书(如要分发到App Stroe或签名应用)
指定具体的格式 ，例如dmg和zip:
npm run build -- -m dmg zip
打包Windows:
npm run build -- -w
指定具体的格式，例如nsis和portable:
npm run build -- -w nsis portable
    1.在非 Windows 环境下可以使用 Wine 模拟 Windows 环境打包。
    2.确保配置了正确的图标文件（.ico）和签名证书（如果需要分发签名的应用）
Linux:
npm run build -- -l
指定具体的目标格式，例如AppImage和deb:
npm run build -- -l AppImage deb
    1.确保开发环境安装了 Linux 系统依赖（如 fakeroot、dpkg 等）
打包 macOS,Windows,Lin:
npm run build -- -mwl
具体格式:
npm run build -- -mwl dmg nsis AppImage
```
### git配置 
``` yaml
查询全局config信息:
git config --global --list
设置config配置:
git config --global user.email "you@example.com"
git config --global user.name "you"
```






### 其他

[package.json配置信息](https://www.jianshu.com/p/15e5ac3e78ca?v=1731982940748)

