---
layout: post
title: 未来的文章-添加插件和高级功能
date: 2020-01-14
categories: Archive
tags: 示例
comments: true
description: 未来的文章-添加插件和高级功能-创建于2020-01-12-但会直到2020-01-14再发布
---

这篇文章介绍如何添加一些常见的插件和功能扩展。

* 无数字的目录
{:toc}

## 功能插件

### 1. 回到首页

对于习惯发长文的朋友来说，这个功能十分方便。已经包括在主页中，无需任何配置。如果你想改变按钮的样式，请参考 [这里](https://github.com/vfeskov/vanilla-back-to-top), 修改本项目中 `_include/back-to-top.html` 文件。

### 2. 社交分享

社交网络的分享按钮能帮助你快速增长自己的受众，不过很多第三方社交分享按钮，例如shareaholic, addthis等都有跟踪代码，可能泄漏读者的隐私。
因此鼓励采用非第三方javascript的社交分享按钮。
目前包括了两种
#### 2.1 jquery social share buttons
你只需要在`_config.yml` 文件中的改成这样
```yml
sharebuttons:
  jquery: true
  nojavascript: false
```
#### 2.2 无javascript的分享按钮 （推荐）
来自 [https://sharingbuttons.io](https://sharingbuttons.io), 只需要将`_config.yml` 文件中的以下部分改为
```yml
sharebuttons:
  jquery: false
  nojavascript: true
```
你可以看到默认开启的是无javascript的分享按钮。

### 3. 安全的流量统计

#### 3.1 基于[FreeCounterStat](https://www.freecounterstat.com)的非javascript计数器
页脚包含一个uBlock Origin认证安全的网页点击计数器，博客每获得一次点击就会累加1，这对博主而言可以大概的知道自己网站的访问量。配置方法如下：

首先，到[FreeCounterStat](https://www.freecounterstat.com)申请一个新的计数器。第三步完成后，将产生的非javascript代码中的图片编号复制，例如
```html
<a href="https://www.freecounterstat.com" title="free hit counters">
  <img src="https://counter1.wheredoyoucomefrom.ovh/private/freecounterstat.php?c=ghfqhne7z87531aunzg4cqds8kfcekpa" border="0" title="free hit counters" alt="free hit counters">
</a>
```
将上述代码中的字符串 `ghfqhne7z87531aunzg4cqds8kfcekpa` 复制到 `_config.yml` 中的 `webcounterimg: ghfqhne7z87531aunzg4cqds8kfcekpa` 即可.

这种方法只能获得大致的点击率，并不能提供较详细的流量分析，例如每日流量、各个页面的访问量、交叉来源等。

#### 3.2 基于javascript但不使用cookies的流量分析 [Ticksel](https://www.ticksel.com)
我们主要利用这两个浏览器插件来检测第三方跟踪代码：[NoScript](https://noscript.net/) 和 [uBlockOrigin](https://github.com/gorhill/uBlock)。前者可以禁止网页上的javascripts, 后者则封锁包括javascript、图片等任何可能侵犯隐私的插件。

[Ticksel](https://www.ticksel.com)实现流量分析靠javascript，当javascript被禁止时则靠图片。根据Ticksel的官方网站描述，其javascript元素不使用cookies、保持对网页访问者的隐私友好、并尊重浏览器的Do Not Track标识。同时Ticksel的分析数据也是通过非对称密钥加密存放在其服务器上，也就是说你的数据除了你自己，即便是Ticksel的后台也无法访问。

使用方法：第一步先注册Ticksel会员, 第二步产生Tags，第三步配置跟踪代码（主要是选择加什么Tag）这样通过不同的Tag，你可以在一个地方对自己的多个网站进行流量分析，第四步将跟踪代码复制到你的网页。对于Jekyll Kiko-now来说，可已将跟踪代码放到 `_include/footer.html`中进而布置到所有页面。

具体可参考我们的[流量分析项目](https://github.com/diymysite/analytics)及其[演示站点](https://diymysite.github.io/analytics).

**注意：一般来说，为保护自己的隐私，请仅在Tor环境下打开未知或实验性链接。**

如果你安装了uBlock Origin的话，可以看到uBlock Origin并没有封锁Ticksel，说明uBlock认为Ticksel是安全的。事实上因为Ticksel对隐私的保护的注重，很多ad blocker都不封锁Ticksel的流量分析脚本。

## 评论区
推荐使用gitalk模块将Github Issue作为评论区，具体设置请参考[这里](https://github.com/gitalk/gitalk/blob/master/readme-cn.md)。注意，申请好的clientID等参数放到`_config.yml`中，如下：

```yaml
gitalk:
  clientID: ac14c26bcf8a16e03567
  clientSecret: 443574e2aa0e8bccf03adac267a82fdaa0a346c2
  repo: blog
  owner: diymysite
  admin:
    - DamoresClub
    - TerminusBot
    - chinatimeline
    - diymysite
```

另外，要开启评论区的页面的YAML参数区设置`comments: ture`, 参考本页
```yaml
---
layout: post
title: 未来的文章-添加插件和高级功能
date: 2020-01-14
categories: Archive
tags: 示例
comments: true
description: 未来的文章-添加插件和高级功能-创建于2020-01-12-但会直到2020-01-14再发布
---
```

## 计划发布
有时候你可能提前写好博文，想等到某一天再发布，jekyll 也支持这个功能，但Github Page默认不支持，要开启该功能，要在`_config.yml`中添加一行`future: false`，否则未来日期的博文会被直接发布。

计划发布需要利用Github Action，这里我们用以下代码CI代码实现除每次push作为触发之外，还会每日自动build两次，这样就可以把设定在‘未来’的post定期发布了。
```yaml
name: Jekyll Deploy

on:
  push:
    branches:
      - master
  schedule:
    - cron: '1,30 6 * * *'

jobs:
  build_and_deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1
      - name: Build & Deploy to GitHub Pages
        env:
          GITHUB_TOKEN: ${ secrets.ACCESS_TOKEN }
          GITHUB_REPOSITORY: ${ secrets.GITHUB_REPOSITORY }
          GITHUB_ACTOR: ${ secrets.GITHUB_ACTOR }
        uses: BryanSchuetz/jekyll-deploy-gh-pages@master
```

注意:
1. 你需要先申请一个Personal Access Token, 在项目的settings-->secret中添加一个新的secret,名字叫ACCESS_TOKEN数值是生成的Token.
2. 这个发布脚本会将build好的站点发布到gh-pages分支中，所以需要你在项目的settings-->General-->Github Pages里面设置发布分支为gh-pages.
3. 在`_config.yml`中加上`destination: build`避免编译出错
4. 因为Github Action自身的局限，这种计划发布功能仅适用于repo page (类似https://username.github.io/blog/) 而 **无法用于 User Page (类似https://username.github.io/)** .
