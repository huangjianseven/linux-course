---
title: CentOS7下安装配置vsftp服务器标准版
author: 黄俭
date: '2019-06-27'
slug: centos7-vsftpd-configure-standard
categories:
  - Course
tags:
  - Lesson
---

1. 安装vsftpd
    - rpm方式或yum方式均可
    

1. 关闭SELinux，并立即重启

1. 关闭防火墙: systemctl stop firewalld.service

1. 启动ftp服务：systemctl start vsftpd

1. 测试匿名访问是否成功

1. 新建一个用户，用于上传文件，并设置密码，资源目录位于/var/ftp/huang/
  
1. 更改资源目录的权限: chomd 755 /var/ftp/huang/



1. 防止pam过度验证: vim /etc/pam.d/vsftpd

1. chroot设置:vim /etc/vsftpd/vsftpd.conf

    ```bash
     chroot_local_user=YES
     chroot_list_enable=YES
     chroot_list_file=/etc/vsftpd/chroot_list
    
    ```

    新建chroot_list文件，并将ftproot加入到第一行

    ```shell
     # cd /etc/vsftpd
     
     # vim chroot_list
    
    ```

1. 重启vsftpd: systemctl restart vsftpd

1. 命令行测试上传下载