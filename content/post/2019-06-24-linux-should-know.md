---
title: Linux应知应会
author: 黄俭
date: '2019-06-24'
slug: linux-should-know
categories:
  - Course
tags:
  - Lesson
---

1. 用户，文件及目录操作
    - 文件列表命令，-l 选项显示列表详细信息（每项一行），-a选项显示隐藏文件
       
       ```shell
       # ls -l -a
       ```
    - 切换目录命令，cd，接 ~ 表示回自己的主目录，接 .. 表示切换至上层目录，接 - 表示回上次的操作目录
    
      ```shell
       # cd  ~
       # cd ..
       # cd -
       ```
    - 显示当前路径命令(绝对路径)，pwd
    
       ```shell
       # pwd
       ```
    - 用户的添加，密码设置及删除
    
       ```shell
       # useradd  username '添加用户'
       # passwd username  '给某一用户设置密码'
       # userdel  username '删除某一用户'
       ```
    - 切换用户命令，su
    
       ```shell
       # su  username
       ```
    - 建立及删除子目录
    
       ```shell
       # mkdir  yourdir  "新建子目录"
       # rmdir  yourdir  "删除一个空的子目录"
       # rm -rf  yourdir "强制删除一个非空子目录，谨慎操作"
       ```
    - 文件复制，移动及删除
    
       ```shell
       # cp file1 file2 "复制file1到当前目录下，并重命名为file2"
       # cp file1  /mnt/myusb/  "复制file1到绝对路径/mnt/myusb/下"
       # cp /mnt/myusb/file1   .  "复制绝对路径下的file1到当前目录下"
       # cp file1  ../file2   "复制file1到上层目录下，并重命名为file2"
       # rm  file1 "删除file1"
       # mv  file1  file2  "将file1改名为file2"
       # mv  file1  /mnt/myusb/file2 "将file1移动至绝对路径/mnt/myusb/下，并重命名为file2"
       ```
       
1. 可移动磁盘的挂载及卸载
    - 在VMware中将U盘接入CentOS
    - 使用dmesg命令确定U盘的设备名
    - 在/mnt/目录下，建立一个子目录，以供将来挂载U盘使用
           
       ```shell
       # mkdir /mnt/myusb
       ```
    - 挂载
    
       ```shell
       # mount  /dev/devicename  /mnt/myusb
       ```
    - 卸载
    
       ```shell
       # umount  /mnt/usb/
       ```
1. 其它命令
    - 显示磁盘使用情况的 df 命令
    
       ```shell
       # df -h
       ```
    - 查找文件命令 find
    
       ```shell
       # find / -name "filename"
       ```
    - 更改文件或文件夹属性
       
       ```shell
       # chown username:groupname  Directoryname
       # chmod  755    Directoryname
       ```
    - 文件打包及解压缩命令
    
       ```shell
       # tar czvf file.tar.gz  Directoryname  "压缩并打包某文件夹下所有内容"
       # tar xzvf file.tar.gz  "解压缩"
       ```
    - C语言编译命令
    
       ```shell
       # gcc -o hello  file.c "编译C语言文件file.c，并生成可执行文件hello"
       # ./hello  "运行刚才生成的可执行文件"
       ```
    - 查系统信息
    
       ```shell
       # inxi -Fxzd
       ```
    - 查显示分辨率
    
       ```shell
       # xrandr --verbose
       ```
    - 网络相关
    
       ```shell
       # ifconfig "显示网卡配置信息"
       # service network restart "重启网络"
       # ping www.baidu.com "测试网络联通情况"
       # systemctl stop firewalld.service "关闭防火墙"
       # uuidgen  ens33 "获取网卡ens33的id"
       ```
1. 一些关键配置文件的位置
    - 网卡配置文件
    
       ```shell
       # cd /etc/sysconfig/network-scripts/
       ```
       
       下面为静态IP地址配置
       
       ```bash
       TYPE=Ethernet
       PROXY_METHOD=none
       BROWSER_ONLY=no
       BOOTPROTO=none
       DEFROUTE=yes
       IPV4_FAILURE_FATAL=no
       IPV6INIT=yes
       IPV6_AUTOCONF=yes
       IPV6_DEFROUTE=yes
       IPV6_FAILURE_FATAL=no
       IPV6_ADDR_GEN_MODE=stable-privacy
       NAME=ens33
       UUID=4e29e972-b486-489a-9afa-7604d902bc01
       DEVICE=ens33
       ONBOOT=yes
       IPADDR="192.168.0.251"
       PREFIX="24"
       GATEWAY="192.168.0.1"
       DNS1="222.172.200.68"
       ZONE=public
       ```
       
       下面为动态DHCP网卡地址配置
       
       ```bash
       TYPE=Ethernet
       PROXY_METHOD=none
       BROWSER_ONLY=no
       BOOTPROTO=dhcp
       DEFROUTE=yes
       IPV4_FAILURE_FATAL=no
       IPV6INIT=yes
       IPV6_AUTOCONF=yes
       IPV6_DEFROUTE=yes
       IPV6_FAILURE_FATAL=no
       IPV6_ADDR_GEN_MODE=stable-privacy
       NAME=ens33
       UUID=4e29e972-b486-489a-9afa-7604d902bc01
       DEVICE=ens33
       ONBOOT=yes
       ```
       
       
    - vsftp服务配置文件
    
       ```shell
       # cd /etc/vsftpd/vsftpd.conf
       ```
    - http网页服务配置文件
    
       ```shell
       # vim /etc/httpd/conf/httpd.conf
       ```
    - php配置文件
    
       ```shell
       # vim /etc/php.ini
       ```
 - yum的常用操作看[这里](https://www.tecmint.com/20-linux-yum-yellowdog-updater-modified-commands-for-package-mangement/#:~:text=YUM%20%28Yellowdog%20Updater%20Modified%29%20is%20an%20open-source%20command-line,remove%20or%20search%20software%20packages%20on%20a%20system.)