---
title: Ubuntu中安装卸载软件的几种命令
date: 2019-03-22 16:15:21
tags: 
- Ubuntu
categories: 
- Linux
---
## 1. 在终端中使用apt-get安装的软件
- 安装软件：sudo apt-get install softname
- 卸载软件：sudo apt-get remove softname
- 卸载并清除配置：sudo apt-get --purge softname
- 更新软件信息数据库：sudo apt-get update
- 进行系统升级：sudo apt-get upgrade, sudo apt-get disupgrade
- 搜索软件包：sudo apt-cache search softname

## 2. 安装deb包使用的方法
- 安装deb软件包：dpkg -i xxx.deb
- 删除软件包：dpkg -r xxx.deb
- 删除软件并清除配置：dpkg -r --purge xxx.deb
- 查看软件包信息：dpkg -info xxx.deb
- 查看文件拷贝详情：dpkg -L xxx.deb
- 查看系统中已安装软件包信息：dpkg -I
- 重新配置软件包：dpkg -reconfigure xxx.deb

## 3. 卸载源代码编译的软件
```bash
$ cd <source_folder>    
$ make clean
$ ./configure
$ make uninstall
$ rm -rf <source_folder>
```
## 4. 清理系统
- sudo apt-get autoclean
- sudo apt-get clean
- sudo apt-get autoremove