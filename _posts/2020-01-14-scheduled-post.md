---
layout: post
title: 未来的文章-添加插件和高级功能
date: 2020-01-14
categories: Archive
tags: 示例
description: 未来的文章-添加插件和高级功能-创建于2020-01-12-但会直到2020-01-14再发布
---

这篇文章介绍一些常见的扩展

## 小插件

### 1. 回到首页

对于习惯发长文的朋友来说，这个功能十分方便。已经包括在主页中，无需任何配置。如果你想改变按钮的样式，请参考 [这里](https://github.com/vfeskov/vanilla-back-to-top), 修改本项目中 `_include/back-to-top.html` 文件。

### 2. 社交分享

社交网络的分享按钮能帮助你快速增长自己的受众，不过很多第三方社交分享按钮，例如shareaholic, addthis等都有跟踪代码，可能泄漏读者的隐私。
因此鼓励采用非第三方javascript的社交分享按钮。
目前包括了两种
#### 1. jquery social share buttons
你只需要在`_config.yml` 文件中的改成这样
```yml
sharebuttons:
  jquery: true
  nojavascript: false
```
#### 2. 无javascript的分享按钮
来自 [https://sharingbuttons.io](https://sharingbuttons.io), 只需要将`_config.yml` 文件中的以下部分改为
```yml
sharebuttons:
  jquery: false
  nojavascript: true
```
你可以看到默认开启的是无javascript的分享按钮。

## 计划发布
有时候你可能提前写好博文，想等到某一天再发布，jekyll 也支持这个功能，但Github Page默认不支持，要开启该功能，要在`_config.yml`中添加一行`future: false`，否则未来日期的博文会被直接发布。
