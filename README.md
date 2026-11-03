# MG24 SigMesh 模组 — SDK 与工具链

配合 [mg24-sigmesh-module](https://github.com/18473419650/mg24-sigmesh-module) 使用的
完整编译环境。作为该仓库的 **git submodule** 引入。

## 内容

| 目录 | 内容 | 版本 | 大小 |
|---|---|---|---|
| \sdk/\ | Simplicity SDK | **2025.6.1** | ~1.6 GB |
| \	oolchain/\ | GNU ARM Toolchain | **12.2.rel1 (2023.7)** | ~967 MB |
| \msys/\ | MSYS1.0 make / sed / bash（Windows 构建用）| 1.0 | ~21 MB |

## 为什么单独一个仓库

- 源码仓库保持轻量（~1 MB），clone 秒下
- SDK/工具链体积 2.6 GB，独立版本化，升级时不影响源码历史
- GitHub 单仓库建议 < 5 GB

## 用法

\\\ash
git clone --recursive https://github.com/18473419650/mg24-sigmesh-module.git
cd mg24-sigmesh-module
./build.sh        # Windows: .\\build.ps1
\\\

## 注意

- \	oolchain/\ **不包含** \rm-none-eabi-gdb.exe\（227 MB，超过 GitHub 单文件 100 MB 限制）。
  需要 GDB 调试请用 Simplicity Studio 自带的工具链。
- \sdk/.git\ 已剔除（SDK 本身是 git 仓库，避免嵌套）。
- SDK 与工具链版权归 Silicon Laboratories，仅内部研发使用。
