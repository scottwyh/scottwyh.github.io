---
layout:     post
title:      Anaconda+Pytorch_gpu+Pycharm安装与配置
subtitle:    计算机系统-win10
date:       2020-03-24
author:     Captain Nemo
header-img: img/20200324-1-bg.jpg
catalog: true
tags:
    - 环境配置
---


## 前言
 推开Pytorch的大门，瞭望全新的世界，首先需要搭建Pytorch的环境，下面分享win10下搭建Pytorch环境的详细过程，涉及到Anaconda、Pycharm、Cuda、Cudnn、pytorch几个方面。
 
## 安装Anaconda
Anaconda是为方便Python的使用而建立的的软件包全家桶，共含有250多个工具包，含有多版本的Python解释器，且能够建立强大的虚拟环境。
![](https://github.com/scottwyh/scottwyh.github.io/blob/master/img/20200324-2-anaconda.png)
-[下载链接](https://www.anaconda.com/distribution/#download-section)

> 选择windows->python3.7->64位进行下载，下载完成后双击运行。
> 1.点击next;
>
> 2.点击I Agree;
>
> 3.选择使用用户（Install for: Just me还是All Users，假如你的电脑有好几个 Users ，才需要考虑这个问题.其实我们电脑一般就一个 User，就我们一个人使用，如果你的电脑有多个用户，选择All Users，我这里直接 All User），点击next，使用默认安装路径，点击next;
>
> 4.勾选第一项，将anaconda添加到环境变量中（安装过程中需要将路径加入环境变量，这样可以直接在cmd命令行调用，如果你已经安装Python环境，这里勾选时会变红，提示系统已有Python环境，如果写入PATH，那么可能会替代原环境（原Python保留，只是命令行调用为新安装的）。可以不勾选，在安装程序中选择即可），install。
![](https://github.com/scottwyh/scottwyh.github.io/blob/master/img/20200324-2-anaconda-2.png)
>
> 等待安装完成即可。


