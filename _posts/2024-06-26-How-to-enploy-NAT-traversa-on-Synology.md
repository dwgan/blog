---
layout: post
title: "如何在群晖上部署内网穿透，实现Home Assistant的远程访问"
date: 2024-06-26
---

**HomeAssistant**是一个开源的的智能家居平台，通过它可以很方便实现对智能家居的远程监测和控制。

**群晖**NAS提供了一个很丰富的生态，可以很方便快捷的部署数据存储服务。

将**HomeAssistant**部署到群晖上可以很方便快捷的进行数据管理。

然而，系统本身只能在局域网下访问，给**远程控制**带来了一些不便。

内网穿透（NAT 穿透）技术可以将局域网下的特定端口映射到公网，从而实现互联网无障碍访问，实现真正的**智能家居**。

本文主要介绍如何在群晖上部署内网穿透服务。

## 一、方案选择

内网穿透有几种主要方案，按照技术分为**端口映射**、**动态 DNS**、**反向代理**、**VPN**、**Ngrok**、**frp**等，无论哪种技术，都需要一个公网IP作为中转。

按照具体部署方式，主要分为：

1、向VPS服务商购买带有公网IP的VPS，然后在VPS上搭建代理服务，一般按照VPS配置按年付费。该方式安全性高，用户体验好，对技术要求较高。

2、向内网穿透服务提供商购买内网穿透服务，通过厂商的带有公网IP的VPS进行代理，一般按照流量、带宽、节点数进行付费。该方案实现起来相对方便，由于都是公用带宽，所以用户体验一般，同时安全性相对可靠。

3、使用免费的内网穿透，一些厂商会提供免费的服务用于吸引用户，例如：Sakura、Cpolar。该方案免费，但不适合要求较高的应用。

这里主要是用于控制家居的开关，因此数据量非常小，同时考虑到成本，这里采用了第三种方案，采用Cpolar提供的免费服务。

## 二、安装过程

### 2.1 下载安装包

1、cpolar群晖套件下载地址：https://www.cpolar.com/synology-cpolar-suite

2、没有DS923的型号，这里选择DS920+替代。

![image-20240627154924012](https://raw.githubusercontent.com/dwgan/PicGo/main/img/image-20240627154924012.png)

3、选择手动安装并且上传

![image-20240627155013558](https://raw.githubusercontent.com/dwgan/PicGo/main/img/image-20240627155013558.png)

![image-20240627155033781](https://raw.githubusercontent.com/dwgan/PicGo/main/img/image-20240627155033781.png)

4、点击同意并且完成

![image-20240627155041301](https://raw.githubusercontent.com/dwgan/PicGo/main/img/image-20240627155041301.png)

![image-20240627155131327](https://raw.githubusercontent.com/dwgan/PicGo/main/img/image-20240627155131327.png)



5、在已安装中找到cpolar

![image-20240627155151390](https://raw.githubusercontent.com/dwgan/PicGo/main/img/image-20240627155151390.png)



6、打开cpolar的网址进入dashboard

![image-20240627155206262](https://raw.githubusercontent.com/dwgan/PicGo/main/img/image-20240627155206262.png)

7、登录已注册的cpolar账号（如果没有请先注册），注意：第一次登录的账号将被记录到系统中，再次更改需要重新安装

![image-20240627155215194](https://raw.githubusercontent.com/dwgan/PicGo/main/img/image-20240627155215194.png)

### 2.2 配置网络

1、配置Home Assistant的IP和端口，IP可以在群晖中找到，端口默认是8123

![image-20240627155230215](https://raw.githubusercontent.com/dwgan/PicGo/main/img/image-20240627155230215.png)

![image-20240627155248867](https://raw.githubusercontent.com/dwgan/PicGo/main/img/image-20240627155248867.png)

2、配置群晖的端口为5001

![image-20240627155300755](https://raw.githubusercontent.com/dwgan/PicGo/main/img/image-20240627155300755.png)

3、可以在状态->在线隧道列表中找到配置好的连接

![image-20240627155307914](https://raw.githubusercontent.com/dwgan/PicGo/main/img/image-20240627155307914.png)

4、使用浏览器连接，可以打开群晖管理界面以及home assistant界面

![image-20240627155314709](https://raw.githubusercontent.com/dwgan/PicGo/main/img/image-20240627155314709.png)

![image-20240627155331985](https://raw.githubusercontent.com/dwgan/PicGo/main/img/image-20240627155331985.png)

完结！

## 参考

> [如何在群晖系统中安装cpolar（群晖7.X版） - cpolar 极点云官网](https://www.cpolar.com/blog/how-to-install-cpolar-on-a-synology-system-cfah-version-7-x)