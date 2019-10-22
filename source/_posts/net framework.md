---
title: 如何解决win10 Net framework 安装失败的问题
tags: 技术
---



精简版的win10经常缺失各种net framework框架，而net framework框架又是许多程序运行所必备的组件，因此解决此问题至关重要!

### 准备

- 一个完整的win10安装镜像，可以从[MSDN_i tell you](https://msdn.itellyou.cn/)下载。
- 一段代码，**注意此处的E需要修改成你电脑中加载镜像后的镜像盘符**.
`dism.exe /online /enable-feature /featurename:netfx3 /Source:E:\sources\sxs` 

### 操作步骤

1. 加载win10.iso系统镜像。
![加载镜像](nfw1.png)

2. 打开powershell（管理员），复制代码 ，**注意代码中E的替换**
![Powershell](nfw2.png)

3. 运行代码即可
![运行代码](nfw3.png)

### 更多操作

作者试验了多种方法，最终上述方法可行，希望可以帮助到您。如果此种方法不行，可参考[知乎](https://zhuanlan.zhihu.com/p/33467631)，祝顺利~