---
title: "Airsim"
---

# AirSim Quick Start
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## [环境配置](https://microsoft.github.io/AirSim/build_windows/)

- windows11
- 下载 Epic Games Launcher
- 安装 Visual Studio 2022 Community
  - 选择 C++桌面开发
  - Windows 10 SDK 10.0.19041
  - 选择“独立组件”板块中最新的.NET Framework SDK
- 安装 Unreal Engine 4.27
- 配置虚幻引擎
  - 编辑 —— 编辑器首选项 —— 源代码 —— 源代码编辑器 — Visual Studio 2022
  - 编辑 —— 编辑器首选项 —— 搜索“CPU” —— 关闭“Use Less CPU when in Background”
- 安装 AirSim
  - 打开 Developer Command Prompt for VS 2022
  - 在 D 盘中 `git clone https://github.com/Microsoft/AirSim.git`
  - `cd AirSim`
  - `build.cmd`
- [配置 anaconda 中的虚拟环境](https://microsoft.github.io/AirSim/apis/#python-quickstart)
  - `conda create -n AirSim`，注意 python 版本大于 3.6
  - `conda activate AirSim`
  - `pip install msgpack-rpc-python`
  - `pip install airsim`

## 配置测试

- 虚幻地图
  - 可利用已有地图 D:\AirSim\Unreal\Environments\Blocks
    - 双击 Blocks.sln
    - 在 DebugGame Editor —— Win64 模式下运行
  - [下载 AirSim 官方提供的地图](https://github.com/microsoft/AirSim/releases/tag/v1.8.1-windows)
    - 双击虚幻.exe 文件运行
  - [自行创建地图](https://microsoft.github.io/AirSim/unreal_custenv/)
- 激活 python 环境`conda activate AirSim`
- 运行 test.py 文件

```python
"""
 test python environment
 """
import airsim
# connect to the AirSim simulator
client = airsim.MultirotorClient()
client.confirmConnection()

# get control
client.enableApiControl(True)

# unlock
client.armDisarm(True)

# Async methods returns Future. Call join() to wait for task to complete.
client.takeoffAsync().join()
client.landAsync().join()

# lock
client.armDisarm(False)

# release control
client.enableApiControl(False)
```
