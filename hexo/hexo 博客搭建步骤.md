[TOC]

## hexo 博客搭建

### 1 hexo 安装

> 首先需要安装：[Node.js](https://nodejs.org/en/) 和 [Git](https://git-scm.com/)
>
> 命令行输入 `npm -v` 判断是否成功安装 Node.js
>
> 安装完成之后打开Windows命令行输入以下命令：
>
> `npm install -g hexo-cli`

> **注意：** 如果出现以下错误，输入 `npm cache clean --force` 用于清空缓存

```shell
npm ERR! code Z_BUF_ERROR
npm ERR! errno -5
npm ERR! zlib: unexpected end of file

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\Users\wangqi\AppData\Roaming\npm-cache\_logs\2019-05-13T07_43_17_171Z-debug.log
```

> 最后一行出现 added 225 packages from 434 contributors in 107.693s 即安装成功

### 2 建站

> 首先选择一个文件夹放置博客文件，如：`C:\myblog`
>
> 在命令行中输入以下命令：
>
> `hexo init <folder>`
>
> `cd <folder>`
>
> `npm install`

> 安装完成后的目录如下(可能每个版本略有不同)：

```markdown
<folder>
|-- node_modules
|-- scaffolds
|-- source
|   └── _posts
|-- themes
|-- .gitignore
|-- _config.yml
|-- package.json
└── package-lock.json
```

> **_config.yml：** 为网站的配置信息
>
> **package.json：** 应用程序的信息
>
> **scaffolds：** 模板文件夹。hexo 的模板指新建的 markdown 文件（文章）中默认填充的内容
>
> **source：** 资源文件夹，存放用户资源的文件夹
>
> **themes：** 主题文件夹。 hexo 会根据主题来生成静态页面

### 3 配置文件参考

```yaml
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
# 网站标题
title: wangqicc's blog
# 网站副标题
subtitle:
# 网站描述
description:
# 关键词
keywords:
# 作者名字
author: Wang Qi
# 网站使用的语言
language:
# 网站时区，默认使用电脑时区
timezone:

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
# 网址
url: http://yoursite.com
# 网站根目录
root: /
# 文章的永久链接格式
permalink: :year/:i_month/:i_day/:title/
# 默认值
permalink_defaults:

# Directory
# 资源文件夹
source_dir: source
# 公共文件夹
public_dir: public
# 标签文件夹
tag_dir: tags
# 归档文件夹
archive_dir: archives
# 分类文件夹
category_dir: categories
# include code 文件夹
code_dir: downloads/code
# 国际化 (i18n) 文件夹
i18n_dir: :lang
# 跳过指定文件的渲染
skip_render:

# Writing
# 新文章的文件名称
new_post_name: :title.md # File name of new posts
# 预设布局
default_layout: post
# 把标题转换为 titlecase
titlecase: false # Transform title into titlecase
# 在新标签中打开链接
external_link: true # Open external links in new tab
# 把文件名称转化为 (1) 小写 (2) 大写
filename_case: 0
# 显示草稿
render_drafts: false
# 启动 Asset 文件夹
post_asset_folder: false
# 把链接改为与根目录的相对位址
relative_link: false
# 显示未来的文章
future: true
# 代码块的设置
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:
  
# Home page setting
# path: Root path for your blogs index page. (default = '')
# per_page: Posts displayed per page. (0 = disable pagination)
# order_by: Posts order. (Order by date descending by default)
index_generator:
  path: ''
  per_page: 10
  order_by: -date
  
# Category & Tag
# 默认分类
default_category: uncategorized
# 分类别名
category_map:
# 标签别名
tag_map:

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
# 日期格式
date_format: YYYY-MM-DD
# 时间格式
time_format: HH:mm:ss

# Pagination
## Set per_page to 0 to disable pagination
# 每页显示的文章数量(0 = 关闭分页功能)
per_page: 10
# 分页目录
pagination_dir: page

# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
# 当前主题名称
theme: landscape

# Deployment
## Docs: https://hexo.io/docs/deployment.html
# 部署部分设置
deploy:
  type:
```

### 4 hexo 常用指令

> `hexo init [folder]` ：新建一个网站，没有设置目录的话会在当前文件夹建立网站
>
> `hexo new [layout] <title>`  或 `hexo n <title>`：
>
> 新建一篇文章，默认使用 _config.yml 文件中的 default_layout 参数代替~~，如果标题中含有空格需要使用引号括起来~~。
>
> :shamrock: `hexo generate` 或 `hexo g` ：生成静态文件
>
> `hexo generate -watch` 或 `hexo g -w` ：监视文件变动
>
> :shamrock: ​`hexo server` 或 `hexo s` ：启动服务器预览
>
> :shamrock: ​`hexo deploy` 或 `hexo d` ：部署网站
>
> `hexo g -d` 或 `hexo d -g` ：让 hexo 在生成完毕后自动部署网站

> :shamrock: ​`hexo clean` ：清除缓存文件 (db.json) 和已生成的静态文件 (public)
>
> `hexo list` ：列出网站资料

### 5 集成搜索功能

> `npm install hexo-generator-searchdb --save` ：安装 Local Search
>
> 编辑**站点配置文件**，新增以下内容：
>
> ```yml
> search:
>   path: search.xml
>   field: post
>   format: html
>   limit: 10000
> ```
>
> 编辑**主题配置文件**，启用本地搜索：
>
> ```yml
> # local search
> local_search:
>   enable: true
> ```

### 6 集成评论功能

**step1：**

> 安装 gitalk：`npm i -- save gitalk`

**step2：**

> [register a new OAuth application](https://github.com/settings/applications/new)
>
> 参数说明：
>
> Application name：应用名称，随心情
>
> Homepage URL：网站 url，例如：https://wangqicc.github.io
>
> Application description：网站描述，随心情
>
> Authorization callback URL：回访网站 url，例如：https://wangqicc.github.io

**step3：**

> 在 next 主题评论文件夹 /hexo-theme-next/layout/_third-party/comments 下新建
>
> `gitalk.swig` 文件，复制以下内容：
>
> ```html
> {% if page.comments && theme.gitalk.enable %}
>   <link rel="stylesheet" href="https://unpkg.com/gitalk/dist/gitalk.css">
>   <script src="https://unpkg.com/gitalk/dist/gitalk.min.js"></script>
>   <script type="text/javascript">
>     var gitalk = new Gitalk({
>       clientID: '{{ theme.gitalk.ClientID }}',
>       clientSecret: '{{ theme.gitalk.ClientSecret }}',
>       repo: '{{ theme.gitalk.repo }}',
>       owner: '{{ theme.gitalk.githubID }}',
>       admin: ['{{ theme.gitalk.adminUser }}'],
>       id: location.pathname,
>       distractionFreeMode: '{{ theme.gitalk.distractionFreeMode }}'
>     })
>     gitalk.render('gitalk-container')
>   </script>
> {% endif %}
> ```

**step4：**

> 在文件夹 hexo-theme-next/layout/_third-party 下找到 `comments.swig` 文件，添加以下内容：
>
> ```html
> {% elseif theme.gitalk.enable %}
>   <div class="comments" id="comments">
>     <div id="gitalk-container"></div>
>   </div>
> ```

**step5：**

> 在文件夹 hexo-theme-next/layout 下找到 `index.swig` 文件，添加以下内容：
>
> ```html
> {% include 'gitalk.swig' %}
> ```



### 参考文档

1. [hexo 官方文档](https://hexo.io/zh-cn/docs/)

2. [hexo + github 搭建免费个人博客](http://blog.haoji.me/build-blog-website-by-hexo-github.html?from=xa#zhun-bei-gong-zuo)

3. [gitalk 评论功能](https://github.com/gitalk/gitalk)