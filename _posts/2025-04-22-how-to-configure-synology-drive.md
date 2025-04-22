---
layout: post
title: "Windows下配置Synology Drive使用教程"
date: 2025-04-22
---

### 一、获取客户端

点击该[链接](https://global.synologydownload.com/download/Utility/SynologyDriveClient/3.5.2-16111/Windows/Installer/x86_64/Synology%20Drive%20Client-3.5.2-16111-x64.exe)现在Synology Drive Client并安装

### 二、配置客户端

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

### 三、客户端使用

像使用Onedrive一样，将文件放到Synology Drive的文件夹下，等待同步完成，即表示文件同步到了服务器。

