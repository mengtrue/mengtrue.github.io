---
title: Github Pages Hexo 搭建
date: 2018/5/5
---

Github Pages 是 Github 提供的免费博客空间，Hexo 是一个轻量级的博客框架，支持 Github Pages，由此搭建个人的技术博客，

[已所不欲，勿施于人](http://mengtrue.github.io)

#### 参考

- [Hexo](https://hexo.io/zh-cn/)——博客框架官方手册

- [搭建教程](http://www.lovebxm.com/2017/05/30/buildBlog/)

### 配置环境

1. 搭建 Git 环境

   Git 是一款免费、开源的分布式版本控制系统，从 [Git 官网](https://git-scm.com) 下载安装包进行安装

   - Windows 系统，在任意目录下，右键打开 **Git Bash Here** ，输入 `git —version` ，出现版本号则说明配置成功
   - MAC 系统，在 **终端** 中输入 `git —version` ，出现版本号则说明配置成功

2. 搭建 Node.js 环境

   Hexo 博客框架是基于 Node.js 编写，Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境，可在非浏览器环境下，解释运行 JS 代码。在 [Node.js 官网](https://nodejs.org/en/) 下载 **LTS** 版本安装包，进行安装。在命令提示符下，输入 `node -v` 、`npm -v` ，显示版本号，说明配置成功

3. 配置 Github Pages 环境

   在 Github 中创建仓库，仓库名必须是 `yourname.github.io` ，在浏览器中访问之前创建的仓库 `yourname.github.io` ，若可以正常访问，则配置成功

4. 安装 Hexo

   需要使用 **npm** 安装 Hexo，在命令行或终端中输入

   ```
   npm install -g hexo-cli
   ```

   继续输入 `hexo version` ，若正常显示，则安装成功

   ```
   npm install hexo-deployer-git --save
   ```

### 搭建博客

1. 初始化博客

   ```
   hexo init yourname.github.io
   cd yourname.github.io
   npm install
   ```

   新建完成后，指定文件夹目录如下：

   ```
   .deploy           #需要部署的文件
   node_modules      #Hexo 插件
   public            #生成的静态网页文件
   scaffolds         #模版
   source            #博客正文和其他源文件，404、favicon、CNAME
       _drafts       #草稿
       _posts        #文章
   themes            #主题
   _config.yml       #全局配置文件
   package.json      #npm 依赖等
   ```

2. 运行本地 Hexo 服务

   ```
   hexo server
   ```

   执行成功后，博客网站会在 [http://localhost:4000](http://localhost:4000) 下启动，如果能够正常访问，说明本地博客已经搭建成功

   即后续更新或维护博客，可现在本地查看，进行预览

3. 关联 Hexo 与 Github Pages

   Git 配置个人账户信息，并上传 SSH Key

   在 **_config.yml** 文件中，找到 **Deployment** ，进行如下修改，冒号后面必须加空格

   ```
   # Deployment
   ## Docs: https://hexo.io/docs/deployment.html
   deploy:
     type: git
     repo: git@github.com:yourname/yourname.github.io.git
     branch: master
   ```

4. 提交到 Github Pages

   ```
   // 删除旧的 public 文件
   hexo clean
   
   // 生成新的 public 文件
   hexo generate
   
   // 开始部署
   hexo deploy
   ```

   执行成功后，在浏览器中输入 **https://yourname.github.io** ，查看效果

### 编辑更新博客

1. 添加博客文章

   ```
   hexo new "文章标题"
   ```

   在本地博客文件夹 **source\\_posts** 下可看到新建的 **markdown** 文件，也可以将已存在的文章复制到此文件夹下

2. 部署

   ```
   hexo clean
   hexo generate
   hexo deploy
   ```

   