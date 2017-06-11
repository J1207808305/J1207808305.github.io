---
layout: post
title:  "Bootloader 笔记"
date:   2017-03-14 18:51:34 +0800
author:     "Johnny"
catalog: true
header-img: "img/post-bg-rwd.jpg"
tags:
    - 技术
    - STM32
---

# STM32 bootloader(基于USART) 笔记 #

>本文主要介绍基于Ymodem下的Bootloader的相关知识，包括X,Y,Z modem的发展历史，STM32 Bootloader 启动流程分析，最后给出一份代码供参考(在github上)，欢迎大家frok，如果你有更好的想法，欢迎给我发pull request。

#目录#

<!-- MarkdownTOC -->

- [Bootloader 主要模块及API](#bootloader-主要模块及api)
- [USART 接口](#usart-接口)
- [flash 接口](#flash-接口)
- [加密\(AES_ECB\) 接口](#加密aesecb-接口)
- [Bootloader 注意事项](#bootloader-注意事项)
- [潜在bug](#潜在bug)

<!-- /MarkdownTOC -->

## Bootloader 主要模块及API ##

## USART 接口 ##

在usart.c文件中，是Bootloader的USART初始化的程序，其中宏USE_USART1与USE_USART2为可选的usart升级端口

## flash 接口 ##

STM32L151C8 采用每256bytes为一页的分页机制，对flash的擦除与读写操作在ymodem.c文件中

## 加密(AES_ECB) 接口 ##

加密相关的代码均在宏 USE_ENCRYPT 之间

## Bootloader 注意事项 ##

## 潜在bug ##

1、采用1024字节传输可能会出现解密错误，初步测试可能为内存问题，已经解决，但稳定性还需要大量测试。

>一些的结构还在整理，这里只是相关的主要模块。