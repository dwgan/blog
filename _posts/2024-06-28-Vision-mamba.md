---
layout: post
title: "Vision mamba"
date: 2024-06-28
---

## Introduction

Mamba的横空出世打破了Transformer在深度学习作为主要backbone的局面，给研究者提供了一种新的思路，他的线性复杂度和处理超长序列信息的能力正是它能够挑战Transformer的底气。在序列模型中，例如语音、文本、DNA序列等大多数信号都是因果信号，而Mamba又是基于RNN的，因此这种因果序列信息对于Mamba这个模型天生地更加友好。

然而，在深度学习任务中，还有一大部分的信号都是图像信号，而图像信号天生属于非因果信号，如果直接采用Mamba这种因果网络来处理图像信息，那么将无法避免的出现网络的图像信息强行加入因果特性，例如先输入网络的图像块会随着信息的输入而被渐渐遗忘，使得图像某个部分的信号被人为的认为更加重要（实际上它们应该是同等重要的），即使是LSTM、Mamba也只是减缓了这种遗忘速度。

目前大多数将Mamba应用于图像处理的网络大多数都是采用多向扫描的机制来减缓网络因果性对于图像信号的影响，这种做法可以应用于不太需要关注较长距离的以来的任务，例如分割、分类。然而，一方面这种多向扫描虽然能够缓解因果性但是依然存在一定的非因果性，例如从四周往中间的扫描方式更加关注中间的像素，另一方面对于图像压缩这种需要对整个图像全局关注的任务，因果网络这种特天生不匹配。

另一种是加窗口，在窗口内认为是时不变的，

能否添加一个参数来学习图像的重要性

Attention机制这种天生具有非因果特性的网络和图像中的要求十分匹配，然而它对于大图像具有二次复杂度，这又使得它无法处理超大的图像，这种矛盾能够通过借鉴两者的优势得到一个结合的网络，既具有非因果特性又具有线性的复杂度？



## Some tutorial:

[CUDA学习第18课：Blelloch扫描算法以及如何选择扫描算法_哔哩哔哩_bilibili](https://www.bilibili.com/video/av94750027/?vd_source=9527f83dc4c2583f0a86df8c039ce605)

[State Space Duality (Mamba-2) Part I - The Model | Tri Dao](https://tridao.me/blog/2024/mamba2-part1-model/)



## State Space Model (SSM)

 (NeurIPS 2020 Spotlight) HiPPO: Recurrent Memory with Optimal Polynomial Projections [Paper](https://arxiv.org/abs/2008.07669) [Code](https://github.com/HazyResearch/hippo-code) ![Stars](https://img.shields.io/github/stars/HazyResearch/hippo-code)

 (ICLR 2022) S4: Efficiently Modeling Long Sequences with Structured State Spaces [Paper](https://arxiv.org/abs/2111.00396v3) [Code ](https://github.com/state-spaces/s4)![Stars](https://img.shields.io/github/stars/state-spaces/s4)

 (ICLR 2023) H3: Hungry Hungry Hippos: Toward Language Modeling with State Space Models [Paper](https://arxiv.org/abs/2212.14052) [Code](https://github.com/HazyResearch/H3) ![Stars](https://img.shields.io/github/stars/HazyResearch/H3)

(Arxiv 24.05.26) A Unified Implicit Attention Formulation for Gated-Linear Recurrent Sequence Models [Paper](https://arxiv.org/abs/2405.16504) [Code](https://github.com/Itamarzimm/UnifiedImplicitAttnRepr) ![Stars](https://img.shields.io/github/stars/Itamarzimm/UnifiedImplicitAttnRepr)

(Arxiv 24.05.27) The Expressive Capacity of State Space Models: A Formal Language Perspective [Paper](https://arxiv.org/abs/2405.17394) [Code](https://github.com/LeapLabTHU/MLLA) ![Stars](https://img.shields.io/github/stars/LeapLabTHU/MLLA)

**(Arxiv 24.05.31, ICML24, Mamba-2) Transformers are SSMs: Generalized Models and Efficient Algorithms Through Structured State Space Duality** [Paper](https://arxiv.org/abs/2405.21060)  [Code](https://github.com/state-spaces/mamba) ![Stars](https://img.shields.io/github/stars/state-spaces/mamba)

**(Arxiv 24.06.04) GrootVL: Tree Topology is All You Need in State Space Model** [Paper](https://arxiv.org/abs/2406.02395) [Code](https://github.com/EasonXiao-888/GrootVL) ![Stars](https://img.shields.io/github/stars/EasonXiao-888/GrootVL)

**(Arxiv 24.06.12) An Empirical Study of Mamba-based Language Models** [Paper](https://arxiv.org/abs/2406.07887)

## Mamba

**(Arxiv 23.12.01) Mamba: Linear-Time Sequence Modeling with Selective State Spaces** [Paper](https://arxiv.org/abs/2312.00752) [Code](https://github.com/state-spaces/mamba) ![Stars](https://img.shields.io/github/stars/state-spaces/mamba)

(Arxiv 24.01.08) MoE-Mamba: Efficient Selective State Space Models with Mixture of Experts [Paper](https://arxiv.org/abs/2401.04081) 

(Arxiv 24.01.24) MambaByte: Token-free Selective State Space Model [Paper](https://arxiv.org/abs/2401.13660) [Code](https://github.com/lucidrains/MEGABYTE-pytorch) ![Stars](https://img.shields.io/github/stars/lucidrains/MEGABYTE-pytorch)

(Arxiv 24.01.31) LOCOST: State-Space Models for Long Document Abstractive Summarization [Paper](https://arxiv.org/abs/2401.17919) [Code](https://github.com/flbbb/locost-summarization) ![Stars](https://img.shields.io/github/stars/flbbb/locost-summarization)

(Arxiv 24.02.01) BlackMamba: Mixture of Experts for State-Space Models [Paper](https://arxiv.org/abs/2402.01771) [Code](https://github.com/Zyphra/BlackMamba) ![Stars](https://img.shields.io/github/stars/Zyphra/BlackMamba)

(Arxiv 24.02.06) Can Mamba Learn How to Learn? A Comparative Study on In-Context Learning Tasks [Paper](https://arxiv.org/abs/2402.04248) 

(Arxiv 24.02.08) Mamba-ND: Selective State Space Modeling for Multi-Dimensional Data [Paper](https://arxiv.org/abs/2402.05892) 

(Arxiv 24.02.15) Hierarchical State Space Models for Continuous Sequence-to-Sequence Modeling [Paper](https://arxiv.org/abs/2402.10211) [Code](https://github.com/raunaqbhirangi/hiss) ![Stars](https://img.shields.io/github/stars/raunaqbhirangi/hiss)

(Arxiv 24.02.19) Pan-Mamba: Effective pan-sharpening with State Space Model [Paper](https://arxiv.org/abs/2402.12192) [Code](https://github.com/alexhe101/Pan-Mamba) ![Stars](https://img.shields.io/github/stars/alexhe101/Pan-Mamba)

(**CVPR24**) State Space Models for Event Cameras [Paper](https://arxiv.org/abs/2402.15584) [Code](https://github.com/uzh-rpg/ssms_event_cameras) ![Stars](https://img.shields.io/github/stars/uzh-rpg/ssms_event_cameras)

(Arxiv 24.02.26) DenseMamba: State Space Models with Dense Hidden Connection for Efficient Large Language Models [Paper](https://arxiv.org/abs/2403.00818) [Code ](https://github.com/WailordHe/DenseSSM)![Stars](https://img.shields.io/github/stars/WailordHe/DenseSSM)

(Arxiv 24.03.03) The Hidden Attention of Mamba Models [Paper](https://arxiv.org/abs/2403.01590) [Code ](https://github.com/AmeenAli/HiddenMambaAttn)![Stars](https://img.shields.io/github/stars/AmeenAli/HiddenMambaAttn)

(Arxiv 24.03.08) MamMIL: Multiple Instance Learning for Whole Slide Images with State Space Models [Paper](https://arxiv.org/abs/2403.05160) 

(Arxiv 24.03.11) MambaMIL: Enhancing Long Sequence Modeling with Sequence Reordering in Computational Pathology [Paper](https://arxiv.org/abs/2403.06800) [Code](https://github.com/isyangshu/MambaMIL) ![Stars](https://img.shields.io/github/stars/isyangshu/MambaMIL)

(Arxiv 24.03.12) Motion Mamba: Efficient and Long Sequence Motion Generation with Hierarchical and Bidirectional Selective SSM [Paper](https://arxiv.org/abs/2403.07487) [Code](https://github.com/steve-zeyu-zhang/MotionMamba) ![Stars](https://img.shields.io/github/stars/steve-zeyu-zhang/MotionMamba)

(Arxiv 24.03.13) ClinicalMamba: A Generative Clinical Language Model on Longitudinal Clinical Notes [Paper](https://arxiv.org/abs/2403.05795)

(Arxiv 24.03.26) State Space Models as Foundation Models: A Control Theoretic Overview [Paper](https://arxiv.org/abs/2403.16899) 

(Arxiv 24.03.28) Jamba: A Hybrid Transformer-Mamba Language Model [Paper](https://arxiv.org/abs/2403.19887) [Code](https://huggingface.co/ai21labs/Jamba-v0.1) 

(Arxiv 24.03.29) HARMamba: Efficient Wearable Sensor Human Activity Recognition Based on Bidirectional Selective SSM [Paper](https://arxiv.org/abs/2403.20183) 

(Arxiv 24.04.07) VMambaMorph: a Visual Mamba-based Framework with Cross-Scan Module for Deformable 3D Image Registration [Paper](https://arxiv.org/abs/2404.05105) [Code](https://github.com/ziyangwang007/VMambaMorph) ![Stars](https://img.shields.io/github/stars/ziyangwang007/VMambaMorph)

(Arxiv 24.04.12) SpectralMamba: Efficient Mamba for Hyperspectral Image Classification [Paper](https://arxiv.org/abs/2404.08489) [Code](https://github.com/danfenghong/SpectralMamba) ![Stars](https://img.shields.io/github/stars/danfenghong/SpectralMamba)

\(**Arxiv 24.05.13) MambaOut: Do We Really Need Mamba for Vision?** [Paper](https://arxiv.org/abs/2405.07992) [Code](https://github.com/yuweihao/MambaOut) ![Stars](https://img.shields.io/github/stars/yuweihao/MambaOut) 

(Arxiv 24.05.19) NetMamba: Efficient Network Traffic Classification via Pre-training Unidirectional Mamba [Paper](https://arxiv.org/abs/2405.11449) 

(Arxiv 24.05.23) EHRMamba: Towards Generalizable and Scalable Foundation Models for Electronic Health Records [Paper](https://arxiv.org/abs/2405.14567) 

(Arxiv 24.05.26) Mamba4KT:An Efficient and Effective Mamba-based Knowledge Tracing Model [Paper](https://arxiv.org/abs/2405.16542) 

(Arxiv 24.05.26) Zamba: A Compact 7B SSM Hybrid Model [Paper](https://arxiv.org/abs/2405.16712) 

(Arxiv 24.05.30) MSSC-BiMamba: Multimodal Sleep Stage Classification and Early Diagnosis of Sleep Disorders with Bidirectional Mamba [Paper](https://arxiv.org/abs/2405.20142) 

## Vision

**(Arxiv 24.01.17) Vision Mamba: Efficient Visual Representation Learning with Bidirectional State Space Model** [Paper](https://arxiv.org/abs/2401.09417) [Code](https://github.com/hustvl/Vim) ![Stars](https://img.shields.io/github/stars/hustvl/Vim)

**(Arxiv 24.01.18) VMamba: Visual State Space Model** [Paper](https://arxiv.org/abs/2401.10166) [Code](https://github.com/MzeroMiko/VMamba) ![Stars](https://img.shields.io/github/stars/MzeroMiko/VMamba)

(Arxiv 24.02.05) Swin-UMamba: Mamba-based UNet with ImageNet-based pretraining [Paper](https://arxiv.org/abs/2402.03302) [Code](https://github.com/JiarunLiu/Swin-UMamba) ![Stars](https://img.shields.io/github/stars/JiarunLiu/Swin-UMamba)

(Arxiv 24.02.06) U-shaped Vision Mamba for Single Image Dehazing [Paper](https://arxiv.org/abs/2402.04139) [Code](https://github.com/zzr-idam/UVM-Net) ![Stars](https://img.shields.io/github/stars/zzr-idam/UVM-Net)

(Arxiv 24.02.23) MambaIR: A Simple Baseline for Image Restoration with State-Space Model [Paper](https://arxiv.org/abs/2402.15648) [Code](https://github.com/csguoh/MambaIR) ![Stars](https://img.shields.io/github/stars/csguoh/MambaIR)

(Arxiv 24.02.24) Res-VMamba: Fine-Grained Food Category Visual Classification Using Selective State Space Models with Deep Residual Learning [Paper](https://arxiv.org/abs/2402.15761) [Code ](https://github.com/ChiShengChen/ResVMamba)![Stars](https://img.shields.io/github/stars/ChiShengChen/ResVMamba)

(Arxiv 24.03.04) MiM-ISTD: Mamba-in-Mamba for Efficient Infrared Small Target Detection [Paper](https://arxiv.org/abs/2403.02148) [Code](https://github.com/txchen-USTC/MiM-ISTD) ![Stars](https://img.shields.io/github/stars/txchen-USTC/MiM-ISTD)

(Arxiv 24.03.15) EfficientVMamba: Atrous Selective Scan for Light Weight Visual Mamba [Paper](https://arxiv.org/abs/2403.09977) [Code](https://github.com/TerryPei/EfficientVMamba) ![Stars](https://img.shields.io/github/stars/TerryPei/EfficientVMamba)

(Arxiv 24.03.15) On the low-shot transferability of [V]-Mamba [Paper](https://arxiv.org/abs/2403.10696) 

(Arxiv 24.03.26) PlainMamba: Improving Non-Hierarchical Mamba in Visual Recognition [Paper](https://arxiv.org/abs/2403.17695) [Code](https://github.com/ChenhongyiYang/PlainMamba) ![Stars](https://img.shields.io/github/stars/ChenhongyiYang/PlainMamba)

(Arxiv 24.03.26) Integrating Mamba Sequence Model and Hierarchical Upsampling Network for Accurate Semantic Segmentation of Multiple Sclerosis Legion [Paper](https://arxiv.org/abs/2403.17432) 

(Arxiv 24.03.27) Gamba: Marry Gaussian Splatting with Mamba for single view 3D reconstruction [Paper](https://arxiv.org/abs/2403.18795) 

(Arxiv 24.03.27) ReMamber: Referring Image Segmentation with Mamba Twister [Paper](https://arxiv.org/abs/2403.17839) 

(Arxiv 24.03.28) RSMamba: Remote Sensing Image Classification with State Space Model [Paper](https://arxiv.org/abs/2403.19654) [Code](https://github.com/KyanChen/RSMamba) ![Stars](https://img.shields.io/github/stars/KyanChen/RSMamba)

(Arxiv 24.04.02) Samba: Semantic Segmentation of Remotely Sensed Images with State Space Model [Paper](https://arxiv.org/abs/2404.01705) [Code](https://github.com/zhuqinfeng1999/Samba) ![Stars](https://img.shields.io/github/stars/zhuqinfeng1999/Samba)

(Arxiv 24.04.03) RS3Mamba: Visual State Space Model for Remote Sensing Images Semantic Segmentation [Paper](https://arxiv.org/abs/2404.02457) [Code](https://github.com/sstary/SSRS) ![Stars](https://img.shields.io/github/stars/sstary/SSRS)

(Arxiv 24.04.03) RS-Mamba for Large Remote Sensing Image Dense Prediction [Paper](https://arxiv.org/abs/2404.02668) [Code](https://github.com/walking-shadow/Official_Remote_Sensing_Mamba) ![Stars](https://img.shields.io/github/stars/walking-shadow/Official_Remote_Sensing_Mamba)

\(Arxiv 24.04.04) ChangeMamba: Remote Sensing Change Detection with Spatio-Temporal State Space Model [Paper](https://arxiv.org/abs/2404.03425) [Code](https://github.com/ChenHongruixuan/MambaCD) ![Stars](https://img.shields.io/github/stars/ChenHongruixuan/MambaCD)

\(Arxiv 24.04.05) Sigma: Siamese Mamba Network for Multi-Modal Semantic Segmentation [Paper](https://arxiv.org/abs/2404.04256) [Code](https://github.com/zifuwan/Sigma) ![Stars](https://img.shields.io/github/stars/zifuwan/Sigma)

\(Arxiv 24.04.09) MambaAD: Exploring State Space Models for Multi-class Unsupervised Anomaly Detection [Paper](https://arxiv.org/abs/2404.06564) [Code](https://github.com/lewandofskee/MambaAD) ![Stars](https://img.shields.io/github/stars/lewandofskee/MambaAD)

\(Arxiv 24.04.15) FreqMamba: Viewing Mamba from a Frequency Perspective for Image Deraining [Paper](https://arxiv.org/abs/2404.09476) 

\(Arxiv 24.04.16) Exploring Learning-based Motion Models in Multi-Object Tracking [Paper](https://arxiv.org/abs/2403.10826) 

\(Arxiv 24.04.17) CU-Mamba: Selective State Space Models with Channel Learning for Image Restoration [Paper](https://arxiv.org/abs/2404.11778) 

\(Arxiv 24.04.17) Text-controlled Motion Mamba: Text-Instructed Temporal Grounding of Human Motion [Paper](https://arxiv.org/abs/2404.11375) 

\(Arxiv 24.04.20) Vim4Path: Self-Supervised Vision Mamba for Histopathology Images [Paper](https://arxiv.org/abs/2404.13222) [Code](https://github.com/AtlasAnalyticsLab/Vim4Path) ![Stars](https://img.shields.io/github/stars/AtlasAnalyticsLab/Vim4Path)

\(Arxiv 24.04.28) Mamba-FETrack: Frame-Event Tracking via State Space Model [Paper](https://arxiv.org/abs/2404.18174) [Code](https://github.com/Event-AHU/Mamba_FETrack) ![Stars](https://img.shields.io/github/stars/Event-AHU/Mamba_FETrack)

\(Arxiv 24.04.28) S2Mamba: A Spatial-spectral State Space Model for Hyperspectral Image Classification [Paper](https://arxiv.org/abs/2404.18213) [Code](https://github.com/PURE-melo/S2Mamba) ![Stars](https://img.shields.io/github/stars/PURE-melo/S2Mamba)

\(Arxiv 24.04.29) Spectral-Spatial Mamba for Hyperspectral Image Classification [Paper](https://arxiv.org/abs/2404.18401) 

\(Arxiv 24.04.29) RSCaMa: Remote Sensing Image Change Captioning with State Space Model [Paper](https://arxiv.org/abs/2404.18895) [Code](https://github.com/Chen-Yang-Liu/RSCaMa) ![Stars](https://img.shields.io/github/stars/Chen-Yang-Liu/RSCaMa)

\(Arxiv 24.05.02) SOAR: Advancements in Small Body Object Detection for Aerial Imagery Using State Space Models and Programmable Gradients [Paper](https://arxiv.org/abs/2405.01726) [Code](https://github.com/yash2629/S.O.A.R) ![Stars](https://img.shields.io/github/stars/yash2629/S.O.A.R)

\(Arxiv 24.05.02) SSUMamba: Spatial-Spectral Selective State Space Model for Hyperspectral Image Denoising [Paper](https://arxiv.org/abs/2405.01828) [Code](https:/github.com/lronkitty/SSUMamba) ![Stars](https://img.shields.io/github/stars/lronkitty/SSUMamba)

\(Arxiv 24.05.05) DVMSR: Distillated Vision Mamba for Efficient Super-Resolution [Paper](https://arxiv.org/abs/2405.03008) [Code](https://github.com/nathan66666/DVMSR) ![Stars](https://img.shields.io/github/stars/nathan66666/DVMSR)

\(Arxiv 24.05.05) AC-MAMBASEG: An adaptive convolution and Mamba-based architecture for enhanced skin lesion segmentation [Paper](https://arxiv.org/abs/2405.03011) [Code](https://github.com/vietthanh2710/AC-MambaSeg) ![Stars](https://img.shields.io/github/stars/vietthanh2710/AC-MambaSeg)

\(Arxiv 24.05.06) Retinexmamba: Retinex-based Mamba for Low-light Image Enhancement [Paper](https://arxiv.org/abs/2405.03349) [Code](https://github.com/YhuoyuH/RetinexMamba) ![Stars](https://img.shields.io/github/stars/YhuoyuH/RetinexMamba)

\(Arxiv 24.05.07) VMambaCC: A Visual State Space Model for Crowd Counting [Paper](https://arxiv.org/abs/2405.03978)

\(Arxiv 24.05.08) Frequency-Assisted Mamba for Remote Sensing Image Super-Resolution [Paper](https://arxiv.org/abs/2405.01699) 

\(Arxiv 24.05.09) Rethinking Efficient and Effective Point-based Networks for Event Camera Classification and Regression: EventMamba [Paper](https://arxiv.org/abs/2405.06116) 

\(Arxiv 24.05.13) GMSR:Gradient-Guided Mamba for Spectral Reconstruction from RGB Images [Paper](https://arxiv.org/abs/2405.07777)  

\(Arxiv 24.05.13) OverlapMamba: Novel Shift State Space Model for LiDAR-based Place Recognition [Paper](https://arxiv.org/abs/2405.07966) 

\(Arxiv 24.05.14) Rethinking Scanning Strategies with Vision Mamba in Semantic Segmentation of Remote Sensing Imagery: An Experimental Study [Paper](https://arxiv.org/abs/2405.08493) 

\(Arxiv 24.05.16) IRSRMamba: Infrared Image Super-Resolution via Mamba-based Wavelet Transform Feature Modulation Model [Paper](https://arxiv.org/abs/2405.09873) [Code](https://github.com/yongsongH/IRSRMamba) ![Stars](https://img.shields.io/github/stars/yongsongH/IRSRMamba)

\(Arxiv 24.05.16) RSDehamba: Lightweight Vision Mamba for Remote Sensing Satellite Image Dehazing [Paper](https://arxiv.org/abs/2405.10030) 

\(Arxiv 24.05.17) CM-UNet: Hybrid CNN-Mamba UNet for Remote Sensing Image Semantic Segmentation [Paper](https://arxiv.org/abs/2405.10530) [Code](https://github.com/XiaoBuL/CM-UNet) ![Stars](https://img.shields.io/github/stars/XiaoBuL/CM-UNet)

\(Arxiv 24.05.16) IRSRMamba: Infrared Image Super-Resolution via Mamba-based Wavelet Transform Feature Modulation Model [Paper](https://arxiv.org/abs/2405.09873) [Code](https://github.com/yongsongH/IRSRMamba) ![Stars](https://img.shields.io/github/stars/yongsongH/IRSRMamba)

\(Arxiv 24.05.20) Mamba-in-Mamba: Centralized Mamba-Cross-Scan in Tokenized Mamba Model for Hyperspectral Image Classification [Paper](https://arxiv.org/abs/2405.12003) [Code](https://github.com/zhouweilian1904/Mamba-in-Mamba) ![Stars](https://img.shields.io/github/stars/zhouweilian1904/Mamba-in-Mamba)

\(Arxiv 24.05.21) 3DSS-Mamba: 3D-Spectral-Spatial Mamba for Hyperspectral Image Classification [Paper](https://arxiv.org/abs/2405.12487) 

\(Arxiv 24.05.23) Multi-Scale VMamba: Hierarchy in Hierarchy Visual State Space Model [Paper](https://arxiv.org/abs/2405.12003) [Code](https://github.com/YuHengsss/MSVMamba) ![Stars](https://img.shields.io/github/stars/YuHengsss/MSVMamba)

\(Arxiv 24.05.23) Scalable Visual State Space Model with Fractal Scanning [Paper](https://arxiv.org/abs/2405.14480) 

\(Arxiv 24.05.23) Mamba-R: Vision Mamba ALSO Needs Registers [Paper](https://arxiv.org/abs/2405.14858) [Code](https://github.com/wangf3014/Mamba-Reg) ![Stars](https://img.shields.io/github/stars/wangf3014/Mamba-Reg)

\(Arxiv 24.05.24) MUCM-Net: A Mamba Powered UCM-Net for Skin Lesion Segmentation [Paper](https://arxiv.org/abs/2405.15925) 

**(Arxiv 24.05.26) Demystify Mamba in Vision: A Linear Attention Perspective** [Paper](https://arxiv.org/abs/2405.16605) [Code](https://github.com/LeapLabTHU/MLLA) ![Stars](https://img.shields.io/github/stars/LeapLabTHU/MLLA)

\(Arxiv 24.05.29) Vim-F: Visual State Space Model Benefiting from Learning in the Frequency Domain [Paper](https://arxiv.org/abs/2405.18679) [Code](https://github.com/yws-wxs/Vim-F) ![Stars](https://img.shields.io/github/stars/yws-wxs/Vim-F)

\(Arxiv 24.05.29) FourierMamba: Fourier Learning Integration with State Space Models for Image Deraining [Paper](https://arxiv.org/abs/2405.19450) 

\(Arxiv 24.06.06) MambaDepth: Enhancing Long-range Dependency for Self-Supervised Fine-Structured Monocular Depth Estimation [Paper](https://arxiv.org/abs/2406.04532) 

\(Arxiv 24.06.09) HDMba: Hyperspectral Remote Sensing Imagery Dehazing with State Space Model [Paper](https://arxiv.org/abs/2406.05700) 

\(Arxiv 24.06.09) Mamba YOLO: SSMs-Based YOLO For Object Detection [Paper](https://arxiv.org/abs/2406.05835) 

\(Arxiv 24.06.09) MHS-VM: Multi-Head Scanning in Parallel Subspaces for Vision Mamba [Paper](https://arxiv.org/abs/2406.05992) [Code](https://github.com/PixDeep/MHS-VM) ![Stars](https://img.shields.io/github/stars/PixDeep/MHS-VM)

\(Arxiv 24.06.11) DualMamba: A Lightweight Spectral-Spatial Mamba-Convolution Network for Hyperspectral Image Classification [Paper](https://arxiv.org/abs/2406.07050) 

\(Arxiv 24.06.11) Autoregressive Pretraining with Mamba in Vision [Paper](https://arxiv.org/abs/2406.07537) [Code](https://github.com/OliverRensu/ARM) ![Stars](https://img.shields.io/github/stars/OliverRensu/ARM)

