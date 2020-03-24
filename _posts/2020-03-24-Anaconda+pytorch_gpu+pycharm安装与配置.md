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

> 等待安装完成即可。

### 验证是否安装成功
 win+R，输入cmd打开命令窗，输入conda，回车。
 
## 安装pycharm
  Pycharm是一款强大的PythonIDE，拥有调试，语法高亮，Project管理，代码跳转，智能提示，版本控制等功能
  ![](https://github.com/scottwyh/scottwyh.github.io/blob/master/img/20200324-3-pycharm.jpg)

-[下载链接](https://www.jetbrains.com/pycharm/)

> 点击download，选择community（免费）下载，下载完成后运行。（如果下载专业版，可自行破解）
>
> 点击next，然后选择pycharm安装路径（使用默认也可）
>
> 添加到系统变量(Add launchers dir to the PATH)
>
> 点击next，等待安装完成即可。

## 创建Pytorch_gpu虚拟环境
### 安装对应版本的cuda和cudnn
简单来说，CUDA是一个并行运算的一个计算平台，CuDNN是在上面的一个深度神经网络的GPU加速库。
- 若有GPU，需安装cuda和cudnn,首先要查看cuda、cudnn、pytorch之间版本的对应关系，[查看链接](https://pytorch.org/get-started/locally/)
- 我选择的是cuda9.2, 具体来说是cuda_9.2.148_win10[下载链接](https://developer.nvidia.com/cuda-92-download-archive)和cudnn-9.2-windows10-x64-v7.6.5.32[下载链接](https://developer.nvidia.com/rdp/cudnn-download),**cudnn需要注册并登录账号才能下载！**

- 先安装cuda,(1)选择了默认安装路径（默认安装路径C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.2\bin）; （2）选择精简，下一步安装；

验证cuda是否安装成功:
> 输入： cd C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.2\bin
>
>输入：nvcc -V， 若出现Cuda compilation tools, release 9.2类似的语句，则表示安装成功。

- 安装cudnn
> 下载完成后，解压，复制bin、include、lib三个文件夹
>
> 粘贴到cuda安装目录下（如果是默认安装路径，则粘贴到C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.2）

## 下载Pytorch(即:torch和torchvision)
进入[pytorch网站]( https://pytorch.org/get-started/locally/)
选择pip下载，进入run this command里面的[torch和torchvision下载网址](https://download.pytorch.org/whl/torch_stable.html),会看到很多版本，选择对应版本，我选择的是torch-1.2.0+cu92-cp37-cp37m-win_amd64.whl和torchvision-0.4.0+cu92-cp37-cp37m-win_amd64.whl

## 配置pycharm
> 打开pycharm，创建新的项目(file->new project，写个工程名xxx)
>
> 在这个新的项目里面，建一个py脚本(工程名右击，新建：new->python file->写个yyy)
>
> 输入：
>
> import torch
>
> print(torch.__version__)
>
> run,报错，出现“NO module named 'torch'”，因为当前环境中还没有安装pytorch

> 点击下方terminal
>
> 创建虚拟环境，环境名为pytorch_gpu
输入: conda create -n pytorch_gpu python=3.7 (pytorch_gpu是新建环境的名字，也可写成其他任意的）
>
> 如果安装不成功，如下图，则需要输入图中命令先升级conda
>
> 激活环境： conda activate pytorch_gpu,激活成功后，会显示（pytorch_gpu）(venv)
>
> 虚拟环境中安装pytorch:复制pytorch的下载文件存放的路径名，复制该路径名（如D:\softwares\softwares-windows_anaconda_pycharm_pytorch
>
> cd 该路径名（可能会出现的问题：不能进入该目录，[原因与解决办法](https://blog.csdn.net/nanchifeng3190/article/details/86688614)）
>
> 进入该路径名后，输入pip install "torch-1.2.0+cu92-cp37-cp37m-win_amd64.whl"
>
> 等待安装(安装的速度、安装能否成功均与网络快慢密切相关)，待安装成功后
>
> 再输入pip install "torchvision-0.4.0+cu92-cp37-cp37m-win_amd64.whl"
>
> 等待安装(安装的速度、安装能否成功均与网络快慢密切相关)。
>
> 待安装成功后，就只剩下一步了，即将我们创建的虚拟环境pytorch_gpu关联到当前项目中（file->settings->点击右上方小齿轮，点击add local，选择conda environment,选择existing environment->interpreter，选择这个虚拟环境所在的文件夹,如C:\user\Anaconda3\envs\pytorch_gpu\python.exe）
>
> 可能pycharm会报错：pycharm please specify a different SDK name，[原因与解决办法](https://blog.csdn.net/wu_l_v/article/details/79049718)是有两个*现有*虚拟环境具有相同的名称，删除其中一个之后，就可以创建新的虚拟环境，具体操作是：（1）在setting里面的解释器选择里面，打开show all；（2）在以下弹出窗口里边，对于重名环境用右边“-”进行删除，问题就解决啦。
