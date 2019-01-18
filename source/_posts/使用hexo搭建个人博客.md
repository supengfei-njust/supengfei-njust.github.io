---
title: 使用hexo搭建个人博客
date: 2019-01-18 11:02:58
tags: hexo
---
## 方案选择
使用hexo发布博客到github比较简单，但要将博客源码文件也上传到github用于同步，方便在其他电脑上也能进行博客的编辑，则有如下两种方案可以选择：
- 采用两个repo，一个存放hexo生成的静态博客文件，另一个存放博客源文件
- 采用一个repo，建立两个分支，一个master分支存放hexo生成的静态博客文件，另一个hexo（自己命名）分支存放博客源文件

第二种方案更加简洁干净，最终选择采用第二种方案
## 具体步骤
1. 在github中新建一个repo，repo名称为username.github.io，此处username为用户名，并使用README初始化;
2. 新建一个hexo分支，并将hexo分支设置为默认分支；
3. 在本地使用如下命令新建一个博客源文件并将其与github远程仓库username.github.io相绑定；

```bash
$ hexo init <folder>    //初始化，folder为博客文件目录
$ cd <folder>
$ npm install 
```
修改博客源文件中_config.yml中的deploy配置选项：
```
deploy：
  type：git           //采用git进行控制
  repo：https://github.com/username/username.github.io.git //修改为自己建立的远程仓库
  branch：master      //分支为master
```
4. 生成静态博客文件并部署到远程仓库；

```bash
$ hexo generate
$ hexo deploy 
```
此时静态网页文件便已上传到github仓库的master分支中，同时博客被部署在github pages上，hexo分支中只有一个README文件。
5. 使用git clone将远程仓库的hexo分支克隆到本地；
6. 将博客源文件拷贝到克隆下来的分支文件中；
7. 在本地分支文件中使用如下命令将博客源文件上传到远程仓库的hexo分支中；

```bash
$ git add .               //将所有的博客文件加入git跟踪
$ git commit -m "init"    //提交到本地仓库
$ git push origin hexo    //提交到远程仓库 
```
## hexo常用命令
```bash
$ hexo new [layout] <title>  //创建新文章
$ hexo clean                 //清除缓存文件和已生成的静态文件
$ hexo server                //启动本地服务器，默认为：http://localhost:4000/
```
