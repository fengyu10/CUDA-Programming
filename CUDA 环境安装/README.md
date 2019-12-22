# CUDA环境安装
## 基础环境介绍
WIN10 X64 企业版LTSC，Nvidia GeForce 1070，VS2019
## 安装CUDA Toolkit
在保证NVIDIA显卡驱动成功安装的条件下，从下面链接下载并安装对应版本的CUDA Toolkit.（注意：最好已经安装好VS）
cuda下载链接，https://developer.nvidia.com/cuda-downloads  
![CUDA10 downloads](https://github.com/fengyu10/CUDA-Programming/blob/master/CUDA 环境安装/CUDA10 downloads.png)  
通过在命令窗中执行 nvcc -V初步判断是否安装成功
![nvcc -v](https://github.com/fengyu10/CUDA-Programming/blob/master/CUDA 环境安装/nvcc -v.png)  
安装成功后(默认安装)系统会增加如下环境变量：
```
CUDA_PATH：  C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1
CUDA_PATH_V10_1：  C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1
NUMBER_OF_PROCESSORS： 8
NVCUDASAMPLES_ROOT：  C:\ProgramData\NVIDIA Corporation\CUDA Samples\v10.1
NVCUDASAMPLES8_0_ROOT：  C:\ProgramData\NVIDIA Corporation\CUDA Samples\v10.1
NVTOOLSEXT_PATH：  C:\Program Files\NVIDIA Corporation\NvToolsExt\
```
