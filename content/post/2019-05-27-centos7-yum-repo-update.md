---
title: 机房老版本CentOS7更新yum源
author: 黄俭
date: '2019-05-27'
slug: centos7-yum-repo-update
categories:
  - Course
tags:
  - Tips
---
0. 准备工作
    - 机房因为DNS服务器的问题，可能下载不了网易和阿里云的repo，建议如下操作
       - 打开网卡配置文件
          ```shell
          # vi /etc/sysconfig/network-scripts/ifcfg-ens33
          ```
       - 在DNS1="10.1.2.14"下面加一行
        ```shell
         DNS2="222.172.200.68"
        ```
       - 重启网卡服务
       ```shell
        # service network restart
       ```

1. 确认是超级用户Root

    ```shell
    $ su
    ```
2. 进入yum安装源的配置目录，新建一个repo_bak目录，用于保存系统中原来的repo文件
    ```shell
    # cd /etc/yum.repos.d/
    # mkdir repo_bak
    # mv *.repo repo_bak/
    ```
3. 在CentOS中配置使用网易和阿里的开源镜像
    - 到网易和阿里开源镜像站点下载系统对应版本的repo文件
   
    ```shell
     # wget http://mirrors.aliyun.com/repo/Centos-7.repo
     # wget http://mirrors.163.com/.help/CentOS7-Base-163.repo
     # ls
       Centos-7.repo  CentOS-Base-163.repo  repo.bak
    ```
4. 清除系统yum缓存并生成新的yum缓存

    ```shell
     # yum clean all     # 清除系统所有的yum缓存
     Loaded plugins: fastestmirror, langpacks
     Repository base is listed more than once in the configuration
     Repository updates is listed more than once in the configuration
     Repository extras is listed more than once in the configuration
     Repository centosplus is listed more than once in the configuration
     Cleaning repos: base extras updates
     Cleaning up everything
     Cleaning up list of fastest mirrors

     # yum makecache     # 生成yum缓存
      Loaded plugins: fastestmirror, langpacks
      Repository base is listed more than once in the configuration
      Repository updates is listed more than once in the configuration
      Repository extras is listed more than once in the configuration
      Repository centosplus is listed more than once in the configuration
      base                                                                                  | 3.6 kB  
    ```
5. 测试安装源
    ```shell
     # yum -y install ImageMagick
     # yum -y groupinstall "Development tools"
    ```
