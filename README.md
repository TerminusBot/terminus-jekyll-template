# terminus-jekyll-template

基于 [kiko-now](https://github.com/AWEEKJ/kiko-now) 项目，针对中文做了若干优化，增加了置顶、搜索、GitHub Corner 等功能。

仅仅配置 `_config.yml` 文件即可。

反馈或功能添加请前往 https://2049bbs.xyz/

仓库地址 TerminusBot/terminus-jekyll-template
使用此模板的网站

* https://terminus2049.github.io/
* https://terminus2049.github.io/1984bbs/

### 使用指南

1. 注册 GitHub
2. fork https://github.com/TerminusBot/terminus-jekyll-template
3. 在 Settings 中打开 GitHub Page，source 选择“master branch”
4. 在 Settings 中将项目名称改为 Blog，
修改 fork 后的仓库，将 `_config.yml` 中第 68 行 baseurl: # /Terminus 改为 baseurl: Blog，修改注释中的其他信息，没有的留空。about 页面修改 `about.md` 文件即可。

然后就可以通过 `https://<username>.github.io/Blog` 访问。写文章的办法就是按照 [\_posts](https://github.com/TerminusBot/terminus-jekyll-template/tree/master/_posts) 文件夹中的格式写就行，当然你需要了解一点 [Markdown](https://www.jianshu.com/p/q81RER) 语法。

### 名称来源

> 在审判中，谢顿说出他的预言，语惊四座。他计划领导众多学者编辑一本包含全人类知识的《银河百科全书》，以此减缓帝国殒落的后遗症。委员会得知他的计划并非颠覆帝国的阴谋诡计后，将哈里·谢顿的团队连同他的计划放逐到银河系的边缘端点星。

## 本地预览

```
gem install bundler jekyll
gem install jekyll-paginate
gem install jekyll-seo-tag
gem install jekyll-sitemap
git clone --depth=1 https://github.com/Terminus2049/Terminus2049.github.io.git
cd terminus2049.github.io
jekyll serve
```

### 开源程序

- 博客模板 [kiko-now](https://github.com/AWEEKJ/kiko-now)
- 字体方案 <http://cosx.org>
- [GitHub Corners](http://tholman.com/github-corners/)
- [pangu.js](https://github.com/vinta/pangu.js)

### 联系我们

GitHub: [TerminusBot](https://github.com/TerminusBot)

Twitter: [2049bbs](https://www.twitter.com/2049bbs)

Forum: [2049bbs.xyz](https://2049bbs.xyz/)

Telegram: [Terminus2049](https://t.me/terminus_9402)

Email: terminus2049@protonmail.com
