---
title: Hexo博客的多终端管理常用命令，Push & Pull
date: 2019-10-23 16:32:37
tags: hexo
categrioes: 技术
---

Github page可以静态托管hexo生成的网页文件，因此可以把Hexo分割成**静态网页文件**和**本地环境文件**。我们就是要**利用Github的分布式管理功能**把本地环境文件托管到Github仓库中的一个分支上（hexo），以实现master存放静态网页文件，hexo存放本地环境文件。

## 条件准备

### 环境搭建
- 无论在任何终端，进行同步更新操作的前提就是部署工作环境，即需要安装node.js和git.exe。
- 已经与Github完成了对接和SSH认证，具体看[入坑指南](https://mountaintai.github.io/2019/10/22/hexo-enter/)
- 在Github上新建分支Hexo，并设定为默认分支

### 与Github仓库对接
 这里面一个很关键的隐藏文件夹 .git。是远程仓库和本地关联的标记文件！
``` javascript
git init  初始化本地仓库 (如果从仓库中clone下来的，已经包含.git文件，不需此步）
git remote add origin git@github.com:mountaintai/mountaintai.github.io  添加远程主机
git remote rm origin  如果提示无法新建，可用此命令删除
```
## Push（上传） & Pull（下载）

### Push
``` javascript
git add .   把所有的本地文件添加的缓存目录
git commit -m "description"   添加更细说明
git push origin hexo:hexo   把本地的hexo推送到远端的hexo
```

### Pull（下载）
``` javascript
git pull origin hexo:hexo   从远程仓库把分支拉下来并合并
git pull   如果已经连接好，可以直接用此命令
npm install  完善本地工作环境（新机器用）
```
## 多终端体会
无论是何种终端，首先就是环境的搭建。之后就利用Push和Pull的方法，进行Hexo分支的更新。**推送文章前，先推送分支，之后在推送文章。**

## 心得
- 如果Hexo分支有内容，建议新机器首先用git clone的方法下载到本地，然后npm install配置完整的工作环境，这样就可以直接实现push与pull命令的使用。而不用再次和远端建立联系。
- 清空Hexo ：git clone远程的hexo分支，然后把其中的文件全部删除，只保留.git（隐藏文件夹）。然后用push的方法推送，即可清空远程仓库。
- Push&Pull的用法详情，参考[此篇文章](http://www.ruanyifeng.com/blog/2014/06/git_remote.html)


