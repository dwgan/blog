---
layout: post
title: "如何在Ubuntu上部署内网穿透，实现远程访问"
date: 2024-06-26
---

内网穿透有几种主要方案，按照技术分为**端口映射**、**动态 DNS**、**反向代理**、**VPN**、**Ngrok**、**frp**等，无论哪种技术，都需要一个公网IP作为中转。

按照具体部署方式，主要分为：

1、向内网穿透服务提供商购买内网穿透服务，通过厂商的带有公网IP的VPS进行代理，一般按照流量、带宽、节点数进行付费。该方案实现起来相对方便，由于都是公用带宽，所以用户体验一般，同时安全性相对可靠。

2、向VPS服务商购买带有公网IP的VPS，然后在VPS上搭建代理服务，一般按照VPS配置按年付费。该方式安全性高，用户体验好，对技术要求较高。

![architecture.png](https://cdn.jsdelivr.net/gh/dwgan/PicGo/img/architecture.png)

3、使用免费的内网穿透，一些厂商会提供免费的服务用于吸引用户，例如：Sakura、Cpolar。该方案免费，但不适合要求较高的应用。

这里主要是用于控制家居的开关，因此数据量非常小，同时考虑到成本，这里尝试了后两种方案。

# 自建frp服务器

参考这个[网站](https://github.com/mvscode/frps-onekey)
参考这个[网站](https://www.ioiox.com/archives/79.html)


# frp客户端配置

获取frp[客户端](https://github.com/fatedier/frp/releases)，注意尽可能和服务端的版本保持一致

```
wget https://github.com/fatedier/frp/releases/download/v0.50.0/frp_0.50.0_linux_amd64.tar.gz

tar -xvf frp_0.50.0_linux_amd64.tar.gz

mv frp_0.50.0_linux_amd64 frpc

cd frpc

vi frpc.ini
```
按照如下格式填写

```shell
[common]
server_addr = [公网IP]
server_port = [默认是7000]
tcp_mux = true
protocol = tcp
user = [用户名]
token = [验证密钥]
dns_server = 114.114.114.114

[rdp] # 隧道的标识，不能重复
type = tcp
local_ip = 192.168.0.199
local_port = 5000
remote_port = 25000
use_encryption = true
use_compression = true
```
