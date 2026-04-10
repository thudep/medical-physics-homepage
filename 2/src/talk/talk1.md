# 第一次赛事培训：赛事宣讲 ＆ python 与神经网络基础

## 前言
在医学影像智能分析迅速发展的今天，如何从复杂的CT与MRI数据中精准提取关键信息，正成为医学物理与人工智能交叉领域的重要挑战。本次医学物理挑战赛聚焦“医学图像器官分割”这一核心问题，引导参赛者从实际临床需求出发，探索高效、可靠的智能算法解决方案。  

为帮助参赛选手顺利入门、快速上手，我们安排了第一次赛事宣讲与基础培训。本次培训将系统介绍赛题背景与技术难点，解析比赛评分机制，并结合实际案例，讲解医学图像处理与神经网络的基础知识。同时，还将提供Python与NumPy相关的必要技能培训，帮助大家打好实践基础，为后续建模与算法设计做好充分准备。  

无论你是初次接触医学影像处理，还是已有一定机器学习基础，本次培训都将为你搭建清晰的入门路径。我们期待与你一起，从基础知识出发，逐步解决医学影像难题。

## 基本信息

- **主讲人:** 唐裕胜
- **时间:** 2026年4月11日 14:30-16:30
- **活动形式:** 线下+线上会议
  - **地点:** 三教3200
  - **线上会议:** 腾讯会议: 831-332-040
- **会议议程:**
  1. 14:30-14:50: 赛事宣讲
    - 赛题内容
    - 评分方式
  2. 14:50-15:30: python 基础
    - python 基本语法
    - python 数组与计算
    - numpy 的基本用法
  3. 15:30-16:10: 神经网络入门与代码示例
    - 神经网络基础知识
    - MNIST代码示例
  4. 16:10-16:30: 答疑与自由交流

## 预习材料

在本次培训前, 需要选手自行准备 linux 环境, 如果你用的是 Windows 系统, 那么可以在管理员模式下打开 `PowerShell` , 使用如下命令安装 WSL2:

```powershell
wsl --install -d Debian
```

完成安装后, 可以自行完成用户名与密码的配置 (注意输入密码时, 在终端中不会显示).

如果遇到问题, 可以参考以下材料或自行查找视频资料, 也可以在培训会正式开始前半个小时线下向组委会寻求帮助:
- [官方文档: 如何使用 WSL 在 Windows 上安装 Linux](https://learn.microsoft.com/zh-cn/windows/wsl/install)
- [实验物理的大数据方法课程文档: WSL2 安装教程](https://physics-data.meow.plus/faq/env/windows/)
- [实验物理的大数据方法课程文档: macOS 环境配置](https://physics-data.meow.plus/faq/env/mac/)
- [实验物理的大数据方法课程视频资料: 在 macOS 上使用 UTM 安装 debian](https://hep.tsinghua.edu.cn/~orv/teaching/physics-data/UTM_Debian-12_arm64.webm)

如有需要, 可以自行完成软件源的更改配置, 以下给出清华大学 TUNA 镜像源的配置参考文档:
- [TUNA 官方文档: Debian 软件源](https://mirrors.tuna.tsinghua.edu.cn/help/debian/)
- [TUNA 官方文档: Ubuntu 软件仓库](https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/)
- [实验物理的大数据方法课程文档: Linux 环境配置](https://physics-data.meow.plus/faq/env/linux/)

## 培训材料
