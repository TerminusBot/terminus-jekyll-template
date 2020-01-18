---
layout: post
title: 计划发布-为什么要建这个博客
date: 2020-01-17
categories: Archive
tags: 示例
comments: true
description: 计划发布的文章，顺便谈谈常见问题
---


这里提供无需服务器、域名、完全开源、无第三方跟踪代码、容易上手的个人网站模板，尤其适合政治敏感的公益项目，例如这些[Awesome Social Impact Projects](https://github.com/Terminus2049/Awesome-Social-Impact)，或[【编程随想】](https://program-think.blogspot.com)那样的匿名活动家。

## 1 博客 部落格 Blog
基于Jekyll和Github Pages的个人博客，在保证安全性的前提下，提供各种小插件和小功能，让你的博客易于管理。最初由[TerminusBot](https://github.com/terminusbot/)对kiko-now主题的改造增强，DIY My Site在此基础上进一步增强。 
- 代码仓库 [https://github.com/diymysite/blog](https://github.com/diymysite/blog)
- Demo: [https://diymysite.github.io/blog/](https://diymysite.github.io/blog/) 

## 2 流量分析
流量分析对业务经营开展很重要，但目前主流的流量分析插件对用户的隐私保护不好，会过多搜集用户隐私信息，因此这里试图找到隐私友好的流量分析插件。
- 代码仓库 [https://github.com/diymysite/analytics](https://github.com/diymysite/analytics)
- （请在Tor环境下访问）Demo [https://diymysite.github.io/analytics/](https://diymysite.github.io/analytics/)

## 常见问题
一 **为什么推荐用Github Page搭建网站？**
1. **完全免费** 不需要购买服务器、虚拟主机、域名、以及CDN服务。
2. **优良性能** Github作为最大的代码托管商，它的基础设施的性能非常优秀。
3. **匿名性** 因为Github可以用匿名邮箱注册，且建站不需要花钱，因此党国无法通过任何手段查到你是谁，只要你自己不说。
4. **穿墙** GFW用DNS污染github.io的特定子域名，墙内的小伙伴有多种方式免翻墙直接访问你的网站，DNS-over-HTTPS 或者git clone你的项目到本地浏览。
5. **可移植** 你可以在Gitlab, Bitbucket等代码托管商建立自动备份仓库，整个网站的代码完全由你控制。
6. **分享发现** 在Github上，很多人可以通过关键词、Star、Fork等方式发现并分享你的网站。

二 **第三方跟踪代码有什么风险？**
1. 第三方跟踪代码可能会跟踪网站访问者的隐私信息，例如IP地址、操作系统、点击、甚至是实时的动作，可能泄露访问者身份，这对政治敏感网站而言很不好。
2. 第三方跟踪代码可能会大大降低页面的加载速度。
