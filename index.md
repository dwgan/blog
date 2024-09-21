---
layout: default
title: Home
---



Hi there. Welcome to my blog. This blog contains some topic that I recently interested in, including **Deep Learning**, and **Internet of Thing**.

You are also welcome to visit my [**CSDN Blog**](https://dwgan.blog.csdn.net/), which is about **Embedded Development**  and **Compressed Sensing**.



# **Deep Learning**

In recent years, deep learning technology have dramatically change the world. The rapid rise of ChatGPT has changed how people solve problems and strengthened the positive view of artificial intelligence. This change has brought a lot of investment into the field, attracting more researchers to AI. New technologies are appearing every month, increasing competition in the industry. As a result, professionals need to keep updating their skills to avoid falling behind.

Since I have experience on Image Compressed Sensing, I turned my interest to Deep Image Processing. I am recently interested in newest model that can perform Efficient Representation and Low Complexity. I have kept updating newest model that recent proposed, like [Mamba](https://arxiv.org/abs/2312.00752), [KAN](https://arxiv.org/abs/2404.19756) etc.



## Deep Compressed Sensing

To optimize the information representation efficiency, we explore the newest space state model and employ it to image representation. [Learn more]({{ site.baseurl }}{% post_url 2024-06-28-Mamba %})





## Super Server Platform

To maximize the efficient usage of GPUs, I built a Super Server Platform for multiple online user, which is based on **Linux Container**. [Learn more](https://dwgan.github.io/super-server-platform/)

<p align="center">
	<img src="https://dwgan.top/PicGo/img/202406211933798.png" alt="image-20240117221213953" style="zoom:35%;" />
</p>




# **Smart Industrial**

As a System Application Engineer at ST, my recent work mainly focus on Smart Home / Building Automation. Our mission is design more system solution for customers using our ST's products including MCUs (e.g. STM32 serials), converters (e.g. DC-DC, signal converter). One of serials that we recently focus on is STKNX. KNX is a international standard protocol in smart home automation field, which provides a full standard from physical layer to application layer. The full standard allow easy use without considering the compatibility of the products, realizing plug and play.

Here are some topics that I recently focus on



## STM32MP1

In this project, we explored the advantage of STM32MPU to design powerful development platform with lower price. The STM32MP157 is a heterogeneous system architecture with an A7 core and an M4 core. The A7 core can run a Linux system and execute high-performance tasks such as human-machine interfaces (HMI), video encoding/decoding, and providing USB and Ethernet interfaces. The M4 core can run real-time tasks such as motor control and sensor data acquisition. [Learn more](https://www.st.com/en/microcontrollers-microprocessors/stm32-arm-cortex-mpus.html)

<p align="center">
  <img src="https://dwgan.top/PicGo/img/202409210037469.png" style="zoom: 33%;" />
</p>


## STKNX RFID Reader

RFID is one of the most widely used radio frequency communication technologies today, playing an important role in areas such as payment and security. We aim to integrate it into smart industrial and smart home applications. Our team has provided a demo that showcases RFID communication and serves as a reference solution for smart industrial and smart home systems, primarily based on ST's microchips. [Learn more](https://github.com/dwgan/STKNX-RFID-Reader)

<p align="center">
  <img src="https://dwgan.top/PicGo/img/image-20240628185032085.png" style="zoom: 18%;" />
</p>


## STKNX CO2 Sensor

This project provides a reference solution of connecting sensors into KNX system via UART. [learn more](https://github.com/dwgan/STKNX_CO2Sensor)

<p align="center">
	<img src="https://dwgan.top/PicGo/img/image-20240628185247365.png" alt="image-20240117221213953" style="zoom:15%;" />
</p>



## STKNX Charging Station

Nowadays, EV car are more and more popular, but the number of EV charge station is under development. One of the most serious reason is that different suppliers of EV chargers are not able to put together in a system since different suppliers own their own private protocol. 

We introduce KNX into the system, which allow different EV charger from different suppliers exchange data if they use KNX protocol. This platforms  will help to have more EV chargers more long term in terms of sustainability because in a system integrators will not care about the the supplier of EV charger, but they are just they just need to be concerned that the EV charger is compliant to can existing standard. And today existing standard already have all this available to be deployed for energy management system and in particular EV chargers that will help again the deployment of more EV. [Learn more](https://github.com/dwgan/STKNX_ChargeStation)

<p align="center">
  <img src="https://dwgan.top/PicGo/img/image-20240711175747573.png" style="zoom: 60%;" />
</p>


## NAT traversal

In order to realize smart home / building automation, including remote control and data storage, we employ a Synology based data center. To realize remote data monitor, we need to explore data interface to Internet while keep safety of our data. We build our own NAT traversal server to provide the interface. [Learn more]({{ site.baseurl }}{% post_url 2024-06-26-How-to-enploy-NAT-traversa-on-Synology %})

<p align="center">
  <img src="https://dwgan.top/PicGo/img/202409210040470.png" style="zoom: 50%;" />
</p>


## How to manage files on computer

[Learn more]({{ site.baseurl }}{% post_url 2024-06-29-How-to-manage-files-on-computer %})

