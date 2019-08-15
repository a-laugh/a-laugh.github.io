---
title: 使用 Hexo 和 NexT 搭建博客
categories:
- 工具
tags:
- 工具
- 博客
---
曾用过多个在线博客，也尝试过 org-mode ，甚至写过一个能从 POD 文档生成静态博客的小工具，但无可否认还是 Hexo+NexT 最简洁漂亮 ;-)

## 安装

### 使用 nvm 安装 Node.js

``` bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | sh
```

安装完成后，重启终端并执行下列命令即可安装 Node.js。

``` bash
nvm install stable
```

参考: [安装 Node.js](https://hexo.io/zh-cn/docs/#%E5%AE%89%E8%A3%85-Node-js)

### 安装 Hexo

``` bash
npm install -g hexo-cli
```

参考: [安装 Hexo](https://hexo.io/zh-cn/docs/#%E5%AE%89%E8%A3%85-Hexo)

## 建站
安装 Hexo 完成后，执行下列命令，Hexo 将会在指定文件夹中新建所需要的文件。

``` bash
hexo init <folder>
cd <folder>
npm install
```

参考: [建站](https://hexo.io/zh-cn/docs/setup)

### 安装 NexT 主题

``` bash
cd your-hexo-site
git clone https://github.com/iissnan/hexo-theme-next themes/next
```

参考: [NexT 主题](http://theme-next.iissnan.com/getting-started.html)

## 配置
**站点配置文件**: 根目录下的 _config.yml
**主题配置文件**: 主题目录下的 _config.yml

### 启用 NexT 主题
修改**站点配置文件**，查找关键词 theme ，并修改主题为 next

```
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next
```

修改**主题配置文件**，查找关键词 scheme ，并修改模式为 Mist

```
# ---------------------------------------------------------------
# Scheme Settings
# ---------------------------------------------------------------

# Schemes
#scheme: Muse
scheme: Mist
#scheme: Pisces
#scheme: Gemini
```

### 设置语言
修改**站点配置文件**，查找关键词 language ，并修改语言为 zh-Hans

```
language: zh-Hans
```

### 设置菜单
修改**主题配置文件**，查找关键词 menu ，增删菜单内容

```
# ---------------------------------------------------------------
# Menu Settings
# ---------------------------------------------------------------

# When running the site in a subdirectory (e.g. domain.tld/blog), remove the leading slash from link value (/archives -> archives).
# Usage: `Key: /link/ || icon`
# Key is the name of menu item. If translate for this menu will find in languages - this translate will be loaded; if not - Key name will be used. Key is case-senstive.
# Value before `||` delimeter is the target link.
# Value after `||` delimeter is the name of FontAwesome icon. If icon (with or without delimeter) is not specified, question icon will be loaded.
menu:
  home: / || home
  about: /about/ || user
  tags: /tags/ || tags
  categories: /categories/ || th
  #archives: /archives/ || archive
  #schedule: /schedule/ || calendar
  #sitemap: /sitemap.xml || sitemap
  #commonweal: /404/ || heartbeat
```

在 hexo 根目录下，执行以下命令，添加对应的标签页

```
hexo new page about
hexo new page tags
hexo new page categories 
```

### 设置头像
修改**主题配置文件**，查找关键词 avatar ，并修改头像的链接地址

```
# Sidebar Avatar
# in theme directory(source/images): /images/avatar.gif
# in site  directory(source/uploads): /uploads/avatar.gif
avatar: /images/a-laugh.jpg
```

### 设置站点描述
修改**站点配置文件**，查找关键词 Site ，并修改站点标题、描述等

```
# Site
title: 思悟
subtitle: -好奇-感受-思考-
description: 生命的故事
keywords:
author: a-laugh
language: zh-Hans
timezone:
```

### 设置首页显示
修改**主题配置文件**，查找关键词 auto_excerpt ，并修改显示配置

```
# Automatically Excerpt. Not recommend.
# Please use <!-- more --> in the post to control excerpt accurately.
auto_excerpt:
  enable: true
  length: 150
```

### 本地搜索
在 hexo 根目录下，执行以下命令

``` bash
npm install hexo-generator-searchdb --save
```

修改**主题配置文件**，查找关键词 local_search ，并修改搜索配置

```
# Local search
# Dependencies: https://github.com/flashlab/hexo-generator-search
local_search:
  enable: true
  # if auto, trigger search by changing input
  # if manual, trigger search by pressing enter key or search button
  trigger: auto
  # show top n results per article, show all results by setting to -1
  top_n_per_article: 1
```

### 设置 RSS
在 hexo 根目录下，执行以下命令

``` bash
npm install hexo-generator-feed --save
```

修改**站点配置文件**，追加 feed 信息

```
# 设置 RSS
feed:
  type: rss2
  path: rss2.html
  limit: 5
  hub:
  content: 'true'
```

### 设置代码高亮
修改**站点配置文件**，查找关键词 highlight ，并修改高亮配置

```
highlight:
  enable: true
  line_number: true
  auto_detect: true
  tab_replace:
```

### 优化 URL
修改**站点配置文件**，查找关键词 URL ，并修改URL配置

```
# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: https://a-laugh.github.io
root: /
permalink: :year-:month-:day/:title.html
permalink_defaults:
```

参考: [Github+Hexo一站式部署个人博客](https://chloneda.github.io/blog/hexo-blog/)

### 设置评论
修改**主题配置文件**，查找关键词 Valine ，并修改评论配置

```
# Valine.
# You can get your appid and appkey from https://leancloud.cn
# more info please open https://valine.js.org
valine:
  enable: true
  appid: BSGB3XyPlFvU9hc9NCKWOs4l-MdYXbMMI # your leancloud application appid
  appkey: zGMgeVbw0YwY5IWkycywg4bn # your leancloud application appkey
  notify: false # mail notifier , https://github.com/xCss/Valine/wiki
  verify: false # Verification code
  placeholder: 你是怎么想的？ # comment box placeholder
  avatar: mm # gravatar style
  guest_info: nick,mail,link # custom comment header
  pageSize: 10 # pagination size
```

参考: [为你的 Hexo 加上评论系统- Valine](https://blog.csdn.net/blue_zy/article/details/79071414)

## 部署

### 分支策略
- master 分支：存放博客静态网页
- hexo 分支：存放博客源文件

修改**站点配置文件**，查找关键词 Deployment ，并修改部署配置

```
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: https://github.com/a-laugh/a-laugh.github.io.git
  branch: master
```

### 部署脚本
利用 deploy.sh 脚本一键部署，提高部署效率，脚本放至 hexo 根目录中

``` bash
#!/bin/bash
DIR=`dirname $0`

# Generate blog
hexo clean
hexo generate
sleep 5

# Deploy
hexo deploy
sleep 5

# Push hexo code
git add .
current_date=`date "+%Y-%m-%d %H:%M:%S"`
git commit -m "Blog updated: $current_date"

sleep 2
git push origin hexo

echo "=====>Finish!<====="
```

参考: [Github+Hexo 一站式部署个人博客](https://chloneda.github.io/blog/hexo-blog/)

## 恢复
本地资料丢失或其他主机搭建博客步骤

- 拷贝 hexo 分支源码到本地: git clone -b hexo git@github.com:a-laugh/a-laugh.github.io.git
- 安装 hexo 及各类插件
- 本地安装调试

参考: [Github+Hexo 一站式部署个人博客](https://chloneda.github.io/blog/hexo-blog/)
