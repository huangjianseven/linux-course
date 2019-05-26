---
title: Linux下通过编译源代码的方式安装软件（未完待续）
author: 黄俭
date: '2019-05-26'
slug: linux-software-install-from-source-code
categories:
  - Course
tags:
  - Lesson
---
1. 安装对象：bb

2. 步骤
    - 通过yum安装编译环境
    
       ```shell
       # yum -y groupinstall "Development tools"

       # yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel
       
       ```