---
layout: post
title: "Joint Denoise Compressed Sensing based Deformable Attention"
date: 2025-05-17
---

在传统的压缩感知模型中，待采样信号被认为是一个理想模型，其不考虑噪声的存在。


然而，实际应用中总是会收到噪声的干扰。

噪声存在会干扰图像重构效果，如果模型不考虑噪声的话

根据信息的压缩性，噪声信号和实际的信号往往是不相关的，

压缩和去噪本质上都是去除无效信息，因此可以做一个联合模型

传统的去噪模型会将图像细节当成噪声一起去除，导致丢失了应有的细节

根据图像的非局部自相似性，图像细节在一幅图片中往往存在多处重复，而噪声往往是不相关的，因此可以利用这个特点设计网络区分噪声

本研究提出了联合去噪压缩感知，在本模型中，附加在图像上的噪声被考虑到模型中，利用神经网络，考虑非局部自相似性，达到联合去噪压缩感知


$$
y=Ax+b
$$


$$
x=min_x||Ax-y||^2+\lambda TV(x)
$$


# 参考

## SENet
> [Squeeze-and-Excitation Networks](https://arxiv.org/pdf/1709.01507)\
> https://blog.csdn.net/Evan123mg/article/details/80058077\

## BM3D

> https://blog.csdn.net/qq_33552519/article/details/108632146

## Deformable Attention

> https://zhuanlan.zhihu.com/p/578074694

## Slide Attention




## 非局部相似性