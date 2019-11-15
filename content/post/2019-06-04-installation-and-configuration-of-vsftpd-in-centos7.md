---
title: CentOS7下安装配置vsftp服务器(pub) 
author: 黄俭
date: '2019-06-04'
slug: installation-and-configuration-of-vsftpd-in-centos7
categories:
  - Course
tags:
  - Tips
---
1. 介绍两处资源
    - 信息工程学院FTP站
       
        ftp://10.20.133.16

    - 一个关于服务器配置的日本网站

        https://www.server-world.info/en/

1. rpm方式安装vsftpd
    - 从因特网上下载vsfptd的RPM包，必应搜索vsftpd，进入网站https://pkgs.org/download/vsftpd ，选择CentOS7适用的版本，文件名为vsftpd-3.0.2-25.el7.x86_64.rpm.
    - 安装
     ```shell
      # rpm -Uvh vsftpd-3.0.2-25.el7.x86_64.rpm
     ```
1. 启动vsftpd
    ```shell
     # systemctl start vsftpd
    ```
1. 修改配置文件（115行改为YES,124行改为NO）并重启vsftpd，修改前先备份，这是一个好习惯

    ```shell
     # cp /etc/vsftpd/vsftpd.conf /etc/vsftpd/vsftpd_bak.conf
     # vim /etc/vsftpd/vsftpd.conf
    ```

    ```shell
     # systemctl restart vsftpd
    ```
1. 关闭Linux防火墙并重新启动vsftpd
   
    ```shell
     # systemctl stop firewalld.service
    ```

1. 拷贝一份文件到FTP的目录下并用浏览器测试FTP站点，FTP资源默认目录
    ```shell
        /var/ftp/pub
    ```
