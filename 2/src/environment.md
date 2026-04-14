# 环境配置问题

## `pytorch` 安装的问题

### `pytorch` 版本过高导致只能使用 CPU 训练

在运行模型训练时, 若出现类似于如下报错, 请查看本节内容.
```bash
UserWarning: CUDA initialization: The NVIDIA driver on your system is too old (found version 12060). Please update your GPU driver by downloading and installing a new version from the URL: http://www.nvidia.com/Download/index.aspx Alternatively, go to: https://pytorch.org to install a PyTorch version that has been compiled with your version of the CUDA driver. (Triggered internally at /pytorch/c10/cuda/CUDAFunctions.cpp:119.)
  return torch._C._cuda_getDeviceCount() > 0
```

#### 最简单的解决方法

如果您仅想要快速解决问题, 可以直接阅读此小节内容; 如果想了解更多, 请阅读[详细的问题分析与解决](#详细的问题分析与解决)小节.

最简单的解决方法是降低 `pytorch` 版本, 首先需要卸载当前版本的 `pytorch` 及相关包:
```bash
pip uninstall torch torchvision torchaudio -y
```
然后使用如下命令安装指定版本的 `pytorch`:
```bash
pip install torch==2.10.0 torchvision==0.25.0 torchaudio==2.10.0
```
如果安装时遇到了空间不足的问题, 请参考[安装 `pytorch` 时缓存空间不足](#安装-pytorch-时缓存空间不足)一节.

#### 详细的问题分析与解决

如果您想要详细了解问题发生的原因, 以及各种解决方式, 可以阅读此小节内容; 如果仅想快速解决问题, 请阅读[最简单的解决方法](#最简单的解决方法)小节.

对于出现的报错信息, 其大致的含义是: 在 CUDA 初始化时, 发现您系统的 NVIDIA 驱动版本太旧了 (上述例子中是 CUDA 12.6), 解决方法是在 [http://www.nvidia.com/Download/index.aspx](http://www.nvidia.com/Download/index.aspx) 网站下载新版本的显卡驱动, 或者在 [https://pytorch.org](https://pytorch.org) 网站下载在与您的驱动版本匹配的 `pytorch`.

出现此问题的原因是, `pytorch` 官方在 2026-03-24 发布了 [PyTorch 2.11.0 Release](https://github.com/pytorch/pytorch/releases/tag/v2.11.0), 从该版本开始, CUDA 13.0 将成为 PyPI 上发布的 PyTorch 轮子的"稳定" CUDA 变体. 而对于 NVIDIA RTX 40 系显卡, 常见的 CUDA 版本是 12.x , 可以通过如下命令查看
```bash
nvidia-smi
```
在表格第一行最后可以看到 CUDA 版本.

更新显卡驱动是一种解决方案, 可以自行研究; 这里主要是从 `pytorch` 层面给出两种解决方案. 第一种是直接用 Pytorch 2.10.0 , 按照[最简单的解决方法](#最简单的解决方法)小节操作即可; 如果仍想使用 Pytorch 2.11.0 , 可以下载指定驱动的版本, 在卸载完之前不适配的 `pytorch` 版本之后, 根据上述查询到的 CUDA 版本, 如果是 CUDA 12.6 , 使用如下命令安装:
```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126
```
如果是 CUDA 12.8 , 使用如下命令安装:
```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128
```

### 下载 `pytorch` 时缓存空间不足

如果在下载 `pytorch` 时, 报错最后出现:
```bash
pip._vendor.urllib3.exceptions.ProtocolError: ("Connection broken: OSError(28, 'No space left on device')", OSError(28, 'No space left on device'))
```
表明设备的剩余空间不足, 无法完成 `pytorch` 的下载, **如果您确认 C 盘空间充足** ( WSL 默认安装在 C 盘), 可能是由于 WSL 分配的 `/tmp` 目录所在磁盘分区过小所致, 可以使用
```bash
df -h /tmp
```
查看 `/tmp` 目录所在磁盘分区的使用情况, 如果 `Filesystem` 是 `tmpfs` , 表明 `/tmp` 的数据放在内存中, 此时空间通常较小, 只有几 `GB` 大小, 有时可能不能满足 `pytorch` 下载的需要, 此时可以通过修改 `pip` 缓存目录来完成下载. 

首先新建一个缓存文件夹 (仅示例, 可修改文件夹名)
```bash
mkdir ~/pip-cache/
```
然后指定以该文件夹为缓存文件夹下载 (自行补全 `...` 下载项)
```bash
TMPDIR=~/pip-cache/ pip install ...
```
