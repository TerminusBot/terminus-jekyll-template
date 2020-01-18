---
layout: post
title: 为博客添加强大的Algolia本地搜索功能
date: 2020-01-20
categories: Archive
tags: 示例
comments: true
description: 计划于2020-01-20发布，介绍如何添加免费的Algolia本地搜索功能
---

原来的搜索功能只能检索标题和description, 这对于很多博主来说是远远不够的。这里介绍添加能搜索所有博客全文的Algolia搜索框。

具体需要添加的代码本博客已经完成，主要参考Algolia的官方文档。这里介绍如何利用本项目已经写好的代码，把搜索功能移植到你自己的博客。

## 配置_config.yml文件
首先，你要注册一个[Algolia](https://www.algolia.com/)免费帐号，注册后进入你的Dashboard --> API Keys这里可以看到自己的 Application ID 和一个 Search-Only API Key 和一个 Admin API Key. 然后在Dashboard-->Indices中创建一个新的Index （比如本博客的Index是 `DIYMYSITE`）。把上述信息添加到 `_config.yml` 中：
```yaml
# _config.html

plugins:
  - jekyll-algolia # 新添加

exclude:
  - vendor  # 新添加

# 新添加
algolia:
  application_id: AQ2NWA6FRT # 换成你的Application ID
  index_name:     DIYMYSITE # 换成你新创建的Index名称
  search_only_api_key: 533d855435d988fee73b330d3df4e41c # 换成你的Search-Only API Key
  files_to_exclude: [404.md, about.md, README.md] # 列举要排除出搜索结果的文件
```
这样就完成了`_config.yml`的配置。

## 配置Travis CI
为了让搜索反应最新的博文内容，每次更新网站内容后需要重新更新你的Index。在本地环境下可以通过以下命令完成。
```bash
ALGOLIA_API_KEY='<Replace Me with your Admin API Key>' bundle exec jekyll algolia
```
这里就需要用到前面的Admin API Key了，这个Key只应该你自己知道，因为它能改写你的所有Index。

我们还可以利用Travis CI将上述操作自动化。首先你要注册[travis-ci.org](https://travis-ci.org)，推荐你用自己的github帐号认证注册，这样就能把你的所有公开仓库自动同步过去。我们的博客代码仓库已经包含了Travis CI的配置文件`.travis.yml`
```yaml
# .travis.yml
# This file should be at the root of your project
language: ruby
cache: bundler
before_install:
  - gem install bundler
script:
  - bundle exec jekyll algolia
branches:
  only:
    # Change this to gh-pages if you're deploying using the gh-pages branch
    - master
rvm:
 - 2.4
```
它将自动执行`bundle exec jekyll algolia`。

最后，你需要在travis-ci.org将你的项目仓库同步过去，并且在项目左侧的“设置settings”中添加环境变量： Name `ALGOLIA_API_KEY`, Value `<Replace Me with your Admin API Key>`。这样设置好后，Travis CI就会在你每次push到github仓库后自动帮你更新索引库（Index）了。

现在，你可以在Travis CI选择‘Trigger build’看看能否编译成功，如果成功那就大功告成了。
