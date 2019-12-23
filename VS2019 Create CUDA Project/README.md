# VS2019 Create CUDA Project
## Create "控制台应用"
新建项目，选择"控制台应用"  
![控制台应用](https://github.com/fengyu10/CUDA-Programming/blob/master/VS2019%20Create%20CUDA%20Project/%E6%8E%A7%E5%88%B6%E5%8F%B0%E5%BA%94%E7%94%A8.png?raw=true)  
## 配置管理器
右键项目->属性->配置管理器->Debug 修改成x64  
![配置管理器](https://github.com/fengyu10/CUDA-Programming/blob/master/VS2019%20Create%20CUDA%20Project/%E9%85%8D%E7%BD%AE%E7%AE%A1%E7%90%86%E5%99%A8.png?raw=true)  
## 自定义依赖项
右键项目->生成依赖项->生成自定义->勾选"CUDA 10.1"  
![自定义依赖项](https://raw.githubusercontent.com/fengyu10/CUDA-Programming/master/VS2019%20Create%20CUDA%20Project/%E8%87%AA%E5%AE%9A%E4%B9%89%E4%BE%9D%E8%B5%96%E9%A1%B9.png)  

![勾选CUDA10.1](https://raw.githubusercontent.com/fengyu10/CUDA-Programming/master/VS2019%20Create%20CUDA%20Project/%E5%8B%BE%E9%80%89CUDA%2010.1.png)   
## 附加依赖项增加
右键项目->属性->链接器->输入->附加依赖项增加，添加以下文件名：  
cublas.lib  
curand.lib  
cudart.lib  
![附加依赖项](https://raw.githubusercontent.com/fengyu10/CUDA-Programming/master/VS2019%20Create%20CUDA%20Project/%E9%99%84%E5%8A%A0%E4%BE%9D%E8%B5%96%E9%A1%B9.png)   

![附加依赖项增加](https://raw.githubusercontent.com/fengyu10/CUDA-Programming/master/VS2019%20Create%20CUDA%20Project/%E9%99%84%E5%8A%A0%E4%BE%9D%E8%B5%96%E9%A1%B9%E5%A2%9E%E5%8A%A0.png)   
## 验证配置
运行以下代码
```
#include "cuda_runtime.h"
#include "device_launch_parameters.h"
#include <stdio.h>

int main() {
	int deviceCount;
	cudaGetDeviceCount(&deviceCount);

	int dev;
	for (dev = 0; dev < deviceCount; dev++)
	{
		int driver_version(0), runtime_version(0);
		cudaDeviceProp deviceProp;
		cudaGetDeviceProperties(&deviceProp, dev);
		if (dev == 0)
			if (deviceProp.minor = 9999 && deviceProp.major == 9999)
				printf("\n");
		printf("\nDevice%d:\"%s\"\n", dev, deviceProp.name);
		cudaDriverGetVersion(&driver_version);
		printf("CUDA驱动版本:                                   %d.%d\n", driver_version / 1000, (driver_version % 1000) / 10);
		cudaRuntimeGetVersion(&runtime_version);
		printf("CUDA运行时版本:                                 %d.%d\n", runtime_version / 1000, (runtime_version % 1000) / 10);
		printf("设备计算能力:                                   %d.%d\n", deviceProp.major, deviceProp.minor);
		printf("Total amount of Global Memory:                  %u bytes\n", deviceProp.totalGlobalMem);
		printf("Number of SMs:                                  %d\n", deviceProp.multiProcessorCount);
		printf("Total amount of Constant Memory:                %u bytes\n", deviceProp.totalConstMem);
		printf("Total amount of Shared Memory per block:        %u bytes\n", deviceProp.sharedMemPerBlock);
		printf("Total number of registers available per block:  %d\n", deviceProp.regsPerBlock);
		printf("Warp size:                                      %d\n", deviceProp.warpSize);
		printf("Maximum number of threads per SM:               %d\n", deviceProp.maxThreadsPerMultiProcessor);
		printf("Maximum number of threads per block:            %d\n", deviceProp.maxThreadsPerBlock);
		printf("Maximum size of each dimension of a block:      %d x %d x %d\n", deviceProp.maxThreadsDim[0],
			deviceProp.maxThreadsDim[1],
			deviceProp.maxThreadsDim[2]);
		printf("Maximum size of each dimension of a grid:       %d x %d x %d\n", deviceProp.maxGridSize[0], deviceProp.maxGridSize[1], deviceProp.maxGridSize[2]);
		printf("Maximum memory pitch:                           %u bytes\n", deviceProp.memPitch);
		printf("Texture alignmemt:                              %u bytes\n", deviceProp.texturePitchAlignment);
		printf("Clock rate:                                     %.2f GHz\n", deviceProp.clockRate * 1e-6f);
		printf("Memory Clock rate:                              %.0f MHz\n", deviceProp.memoryClockRate * 1e-3f);
		printf("Memory Bus Width:                               %d-bit\n", deviceProp.memoryBusWidth);
	}
	return 0;
}
```
![测试代码运行截图](https://github.com/fengyu10/CUDA-Programming/blob/master/VS2019%20Create%20CUDA%20Project/%E6%B5%8B%E8%AF%95%E4%BB%A3%E7%A0%81%E6%88%AA%E5%9B%BE.png?raw=true)
