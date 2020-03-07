---
title: 第二次上Linux課製作虛擬機鏡像
author: 黃儉
date: '2020-03-06'
slug: linux-VMware-files-2nd-Version
categories:
  - Course
tags:
  - Tips
---

時光飛逝，轉眼一年將盡，又到了上《Linux應用實踐》這門課了。這一年當中，Linux發行版CentOS有了較大的變化，更新到了CentOS8，7系列不會再更新，只是延續幾年的維護時間。

上官網看了一下，最新的CentOS 7的版本是1908. 算下來是CentOS 7.7 維護期延至2020年6月30日。

下面說一下安裝過程，差不多一年沒有操作，其實有些生疏了。注：我的VMware虛擬機版本：12.5.2 build-4638234。

1. 下載光盤鏡像，最小安裝，ISO文件大小約900MB。

1. 要上網，先將下面配置文件中最後一行ONBOOT改爲yes

1. 安裝net-tools以使用命令ifconfig

1. 安裝vim，並配置vimrc文件

1. 安裝wget, zip, unzip

1. 安裝gcc

1. 安裝traceroute，說明書參見[這裏](https://www.cnblogs.com/rigid/p/6904860.html?utm_source=itdadao&utm_medium=referral)。
   
1. 試了一下靜態配置網卡，DNS要設爲192.168.127.2才可以連網

1. ifup, ifdown, ip  addr命令複習，常用軟件安裝看[這裏](https://blog.csdn.net/xixingzhe2/article/details/82882098)。其中lrzsz是以前沒用過的，還有htop

1. 更換國內源，並去除“重複源”之警告，參見[這裏](https://blog.csdn.net/wy_bk/article/details/89648052)。

1. 更新系統，參見[這裏](https://www.linuxidc.com/Linux/2019-08/159843.htm)。

1. Mac下有一個archey命令，可以文本方式顯示系統概覽，Linux Mint下有screenfetch，但CentOS的庫中沒有。不過，有網友在Github中做了個單機版，可以在CentOS7中運行。參見[這裏](https://www.cnblogs.com/liangjiongyao/p/10134513.html)，剛開始讀不出顯卡型號，因爲缺少lspci命令，裝就好了。參見[這裏](https://blog.csdn.net/hl449006540/article/details/79778748)。然後，screenfetch可以結合scrot命令來進行截屏。參見[這裡](https://www.howtoforge.com/tutorial/how-to-take-screenshots-in-linux-with-scrot/)。

1. lrzsz要結合Xshell來運作，上傳下載小文檔很方便。

1. 最後發兩張screenfetch的圖

![](/post/2020-03-06-linux-VMware-files-2nd-Version_files/screenfetch.jpg)

下面這個是家中一台老機器的。

![](/post/2020-03-06-linux-VMware-files-2nd-Version_files/2020-03-07-085132_734x441_scrot.png)