---
layout: post
title:  "VMware 配置固定ip"
categories: 教程
tags: VMware
author: Ko_teiru
---

* content
{:toc}


> 本文参考自 [VMware配置虚拟机静态IP地址的方法](https://www.jb51.net/article/118745.htm) 
>
> 主要用于解决 VMware 虚拟机频繁变动 IP 的问题
>
> 就算是更改 VMware 内的 DHCP 租期，也是指标不治本的一种方法，一劳永逸不好吗？










## Windows 端配置

首先打开 VMware 的 **编辑 > 虚拟网络编辑器**

记住 `VMnet8` 的**子网网段** 与 **网关 ip**

进入 `Window` 的**控制面板 > 网络和 Internet > 网络连接**

双击打开 VMnet8，单击 **属性**，双击 **Internet 协议版本 4 (TCP/IPv4)**

---

`ip 地址` 填 **子网 ip+1**，比如子网 ip 为：192.168.2.0，那么这里就填：192.168.2.1

`子网掩码` 直接填上面记住的，一般为`255.255.255.0`

`默认网关` 也是直接填上面记住的，一般为 **子网 ip+2**，如：192.168.2.2

*PS : dns 的配置不用管*

---

至此，配置结束

> 但是！还有一件事



右键你的虚拟机，设置，确保只有一个网络驱动器在线。说人话就是把 **网络驱动器2** 的 *已连接* 和 *启动时连接* **全部取消勾选！**  

另外，手动选择**网络驱动器**的网络连接为：`自定义 > VMnet8(NAT 模式)`

## Linux 端配置

进入存放网络配置的文件夹

```sh
cd /etc/sysconfig/network-scripts/
```

查看网卡名称

```sh
ip addr
```

会出现如下的信息，其中展示了当前虚拟机的网卡信息。

其中，我们要记住`2：`处的网卡名以及它下一行的 link/ether 值（MAC，为 `ff:ff:ff:ff:ff:ff` 格式）

```sh
$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno16777736: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:0c:29:6d:1a:d5 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::20c:29ff:fe6d:1ad5/64 scope link 
       valid_lft forever preferred_lft forever
3: eno33554960: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:0c:29:6d:1a:df brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.100/24 brd 192.168.2.255 scope global dynamic eno33554960
       valid_lft 50sec preferred_lft 50sec
    inet6 fe80::20c:29ff:fe6d:1adf/64 scope link 
       valid_lft forever preferred_lft forever
```

看向`2: `处，`eno16777736` 即为网卡名，重命名 `ifcfg-enp0s3` 为 `ifcfg-网卡名`

```
mv ifcfg-enp0s3 网卡名
# 例如
mv ifcfg-enp0s3 ifcfg-eno16777736
```

另外再记住上面那里的 `link/ether` 后面的值，这就是 `MAC` 地址

编辑配置文件 `vim ifcfg-xxxxx`，加入如下信息，如有重复，覆盖即可（手动删除原本重复行）

> 有些文件给值加了双引号，你也可以加上双引号保持美观，但双引号并不影响文件生效

```
ONBOOT=yes
BOOTPROTO=static
HWADDR=#MAC地址
IPADDR=#想要的固定ip
GATEWAY=#VMnet的网关ip
```

`reboot` 就完事了，重启完了再 `ifconfig` 看看有没有生效
