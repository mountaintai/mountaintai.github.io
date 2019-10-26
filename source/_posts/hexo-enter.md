---
title: github/hexo博客入坑指南
date: 2019-10-22 21:27:29
tags: hexo 搭建
categories: 技术
---

感谢这个互联网时代，可以让每个人自由发挥！也感谢这个时代的大神，让小白可以拥有自己的博客！
## hexo本地环境搭建

### 基本环境介绍

- 运行平台：windows10
- node.js：version 9.11.1
- git.exe :version 2.23.0
- nodepad++: version 9.0 （用于编辑.yml文件）
node.js/git.exe可在[度盘](https://pan.baidu.com/s/1ZLkLG6TpKPOYR6Iy5JtoMQ)直接下载，提取码：t8rm。

### 环境搭建

1. 安装node.js，一路默认即可！
2. 安装git.exe，一路默认即可！
3. 安装nodepad++，一路默认即可！

安装后在任意文件夹点击右键可出现下图：
![git bash here](1.jpg)

### 安装hexo及npm组件

1. 在任意硬盘下新建文件夹，作为博客的根目录，并进入该文件夹
2. 在该文件中右键，并运行 Git Bash Here
3. 安装hexo，运行如下命令（二选一即可）
``` javascript
npm install hexo --save
npm i hexo-cli -g
```

>**坑1**： 如果在bash命令行中无法运行npm相关命令，检查电脑全局环境变量配置
> ![](2.jpg)

4. 初始化hexo环境，即可开始进行hexo博客的本地撰写（hexo g）和预览（hexo s）

``` javascript
hexo init
```
## Github的连接与博客推送

### 前期准备
注册Github账号，并新建库resporitory，命名为：你的用户名.github.io。新建库的setting中，下拉找到theme，选择任意主题即可，具体参考[韦阳的博客](https://godweiyang.com/2018/04/13/hexo-blog/#toc-heading-1)。

### Github连接

- 向Github自报家门，运行以下代码
``` javascript
git config --global user.name "你的Github用户名"
git config --global user.email "你的Github邮箱
```

- 本地ssh密钥生成与预览
``` javascript
ssh-keygen -t rsa -C "your email"   
cat ~/.ssh/id_rsa.pub               
```
ssh的生成一路enter即可！

- 复制命令行中出现的密钥代码，粘贴到Github网站>头像>setting>SSH and GPG keys>SSH Keys，新建，标题任意，内容为命令行中带代码。
![](3.png)

- 验证是否成功
``` javascript
ssh -T git@github.com
```
验证成功，在命令中会有**sucessfully**的字样！

> **坑2**：在验证中会出现Are you sure you want to continue connecting (yes/no/[fingerprint])? 的提示，务必填写yes后，再enter，继续之后的操作！

### Hexo博客推送

- 安装插件，如果没有反应，多试几次！
``` javascript
npm install hexo-deployer-git
```
- 设置根目录下的_config.yml文件，在最后deploy处添加：
deploy:
空格空格 type:空格 git
空格空格repository:空格 https://github.com/你的用户名/你的用户名.github.io
空格空格branch: 空格master

### hexo写博客相关命令

为了使图文并茂，此处需安装一个插件：npm install hexo-asset-image --save。
- 博客新建：hexo new "title"
- 博客生成：hexo g
- 博客本地预览： hexo s
- 博客上传到Github： hexo d

## 最后，还会见

- 主题推荐[NEXT](https://github.com/theme-next/hexo-theme-next.git)，关于如何配置，我会在新的博客中记录。
- 搭建的过程看了许多大牛的文章，收益匪浅。尤其是[韦阳的博客](https://godweiyang.com/2018/04/13/hexo-blog/#toc-heading-1)还给予了微信的指导，十分感谢。本文也列出了我参考的博客文章，希望对其他人有所帮助。
  -	[simon96](https://www.simon96.online/2018/11/10/hexo-env/)
  -	[eternalzttz](http://eternalzttz.com/hexo-next.html)
  -	[reuixiy](https://io-oi.me/tech/hexo-next-optimization/)