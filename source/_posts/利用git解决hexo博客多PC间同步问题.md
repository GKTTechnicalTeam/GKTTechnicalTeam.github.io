---
title: 利用git解决hexo博客多PC间同步问题 
date: 2016-10-8 14:21:29   
categories: 任垣宇   
tag: github
toc: true  
---

# 业务场景
单位和家里两PC，同时都想更新blog。而由于hexo没有后台，而且全部文件都在本地生成，所以如果公司电脑上发表了A文章后回家又写了篇B文章，在家里上传后你会发现只有B文章而A文章没了（因为家里的PC上没有A文章的md文件），所以多台电脑同时用来写文章的时候，需要解决备份问题。

#解决方案
- git

优点：部署完成后更新方便，hexo 更新完后只需要再更新全站到git即可
缺点：部署过程相对比较麻烦，对新手不友好

#配置过程
1. 上传blog到git
	
- 删除文件夹内原有的.git缓存文件夹并编辑.gitignore文件
	- 初始化仓库
	- blog根目录下执行以下代码：
	> 	git init
		git remote add origin <server>
		<server>是指在线仓库的地址。origin是本地分支,remote add操作会将本地仓库映射到云端

2. 将git的内容同步到本地
 
	> 	git add .  #添加blog目录下所有文件，注意有个`.`（`.gitignore`声明过的文件不包含在内)
		git commit -m "first commit" #添加更新说明
		git push -u origin master #推送更新到云端服务器

3. 更新文章后的同步操作
4. 