---
layout: post
title: "Windows下配置Synology Drive使用教程"
date: 2025-04-22
---

### 一、获取客户端

[下载链接](https://www.synology.cn/zh-cn/dsm/feature/drive)

若安卓用户无法使用官方版本，可以选择[备用版](https://www.ddooo.com/softdown/249769.htm)


### 二、Windows客户端配置

1、 配置NAS地址，用户名及密码

<p align="center">
  <img src="https://cdn.jsdelivr.net/gh/dwgan/PicGo/img/image-20250422114413383.png" style="zoom: 50%;" />
  <br>
</p>

2、由于没有配置HTTPS，这里选择Proceed Anyway即可

<p align="center">
  <img src="https://cdn.jsdelivr.net/gh/dwgan/PicGo/img/image-20250422114510622.png" style="zoom: 50%;" />
  <br>
</p>

3、选择同步任务，本地端和服务器端会自动实现实时文件同步

<p align="center">
  <img src="https://cdn.jsdelivr.net/gh/dwgan/PicGo/img/image-20250422114549050.png" style="zoom: 50%;" />
  <br>
</p>

4、配置本地和服务器的映射文件夹，注意本地文件夹可以取消勾选`创建空的SynologyDrive文件夹`选项

<p align="center">
  <img src="https://cdn.jsdelivr.net/gh/dwgan/PicGo/img/image-20250422114637779.png" style="zoom: 50%;" />
  <br>
</p>

5、出现如下界面说明设置完成，转圈说明正在同步

<p align="center">
  <img src="https://cdn.jsdelivr.net/gh/dwgan/PicGo/img/image-20250422114837495.png" style="zoom: 36%;" />
  <br>
</p>

### 三、ISO与Android客户端配置

与Windows版本不同，ISO客户端的登录端口是群晖默认后台登陆的端口，我这里是5000的内网穿透端口

安卓用户打开客户端会提示更新，更新后点完成，不要点打开！

### 四、客户端使用


像使用Onedrive一样，将文件放到Synology Drive的文件夹下，等待同步完成，即表示文件同步到了服务器。

