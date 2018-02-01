---
title: Git 搭建 blog
tags: git
---

# Git 搭建 blog

------

终于，我开始写博客了，希望记下研究过程中的学习心得，激励自己不断进步~~~
那么如何搭建blog呢，大体步骤：

> * 安装node.js
> * 安装配置git
> * 安装配置hexo
> * 关联 Hexo 与 GitHub Pages

------

## 安装 node js

一路next的安装过程： https://nodejs.org/en/

## 安装配置 git

 - 安装git：https://git-scm.com/
 - 配置git: https://help.github.com/articles/error-permission-denied-publickey/
 - 测试git:
 -ssh -T git@GitHub.com
 -The authenticity of host 'GitHub.com (207.97.227.239)' can't be established.RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.Are you sure you want to continue connecting (yes/no)?
-yes
-Hi your name! You've successfully authenticated, but GitHub does not provide shell access.
 - 设置用户信息:
git config --global user.name "username"
git config --global user.email  "user@example.com"
 - 创建仓库：username.github.io
 
    **至此，可访问user name.github.io**

---

## 安装配置 hexo

 - npm install hexo-cli -g
/* fail：
1. 通过config命令：npm config set registry https://registry.npm.taobao.org 
    	npm info underscore （如果上面配置正确这个命令会有字符串response）
 2. 命令行指定：npm --registry https://registry.npm.taobao.org info underscore
 3. 编辑 ~/.npmrc 加入下面内容：registry = https://registry.npm.taobao.org
*/
 - hexo init blog
 - cd blog
 - npm install
 - hexo g
 - hexo s
 **至此，打开http://localhost:4000/即可看到一篇内置blog**
/* fail:
1. http://localhost:4000/无法加载：npm install hexo-server --save 安装server端口被占用，重新设置：hexo s -p 3600
2. 安装hexo 报错 command not found
原因：PATH配置得不对
解决：选择『环境变量』，『系统变量』：C:\Program Files\nodejs；『用户环境变量』Path：C:\Users\s94983\AppData\Roaming\npm，在『用户环境变量』部分的Path下再追加C:\Program Files\nodejs，然后重启git bash
*/
 
## hexo 常用命令
hexo generate (hexo g) 生成静态文件，会在当前目录下生成一个public的文件夹
	hexo server (hexo s) 启动本地web服务，用于博客的预览
	hexo deploy (hexo d) 部署播客到远端（比如github, heroku等平台）
	hexo new "postName" 新建文章
	hexo new page "pageName" 新建页面
	hexo d -g 生成部署
	hexo s -g 生成预览
	hexo -v 查看版本信息

------
## 关联 Hexo 与 GitHub Pages

 - 修改hexo总目录下的_config.yml文件：

	deploy:
  		type: git
  		repo: git@github.com:username/username.github.io.git
  		branch: master
 - hexo clean
 - hexo g
 - hexo d
  **至此，可访问 https://username.github.io**
/* fail:
npm install hexo-deployer-git --save
*/


----------


感谢阅读！ 

