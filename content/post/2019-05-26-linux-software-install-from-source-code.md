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
1. 安装对象：AA Project演示程序

<img src="/post/2019-05-26-linux-software-install-from-source-code_files/aa.png" alt="" width="80%"/>

2. 步骤
    - 通过yum安装编译环境
    
       ```shell
       # yum -y groupinstall "Development tools"
       # 下面这一步并非必须
       # yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel
       
       ```
    - 下载aa-lib
       - 用wget下载
       ```shell
        # wget http://prdownloads.sourceforge.net/aa-project/aalib-1.2.tar.gz
       ```
       - 解压缩
       
       ```shell
        # tar xzvf aalib-1.2.tar.gz
       ```
       - 编译
       
       ```shell
        # cd aalib-1.2
        # ./configure
        #  make
        #  make install
       
       ```
       - 如果出错则在[这里](/post/2019-05-26-linux-software-install-from-source-code_files/config.sub.zip)下载新版config.sub文件，并替换掉源代码包中的文件
       - 或者，执行下面的命令。参考[这里](https://stackoverflow.com/questions/24909409/configure-error-libtool-configure-failed)
       
       ```shell
       curl 'http://git.savannah.gnu.org/gitweb/?p=config.git;a=blob_plain;f=config.sub;hb=HEAD' > config.sub
       ```
    - 下载bb
       - 用Linux的wget下载
       
       ```shell
        # wget http://prdownloads.sourceforge.net/aa-project/bb-1.2.tar.gz
       ```
       - 解压缩
       
       ```shell
        # tar xzvf bb-1.2.tar.gz
       ```
       - 编译
       
       ```shell
       # cd bb-1.2
       # export CFLAGS="-I/usr/local/include"
       # ./configure
       # make
       ```
       - 如果出错则注释掉textform.c中的长字符串指针或进行删减
       - 运行
       
        ```shell
         # ./bb
        ```
        
        ![](/post/2019-05-26-linux-software-install-from-source-code_files/bb.png)
       