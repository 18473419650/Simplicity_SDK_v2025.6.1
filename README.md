# MG24 SigMesh 模组 — SDK 与工具链

配合 [mg24-sigmesh-module](https://github.com/18473419650/mg24-sigmesh-module) 使用的
完整编译环境，作为该仓库的 **git submodule** 引入。

## 内容

| 目录 | 内容 | 版本 | 大小 |
|---|---|---|---|
| `sdk/` | Simplicity SDK | **2025.6.1** | ~1.6 GB |
| `toolchain/` | GNU ARM Toolchain | **12.2.rel1 (2023.7)** | ~967 MB |
| `msys/` | MSYS 1.0 make / sed / bash（Windows 构建用）| 1.0 | ~21 MB |

## 为什么单独一个仓库

- 源码仓库保持轻量（约 1 MB），clone 秒下
- SDK + 工具链共 2.6 GB，独立版本化，升级时不影响源码历史
- GitHub 单仓库建议控制在 5 GB 以内

## 用法

主仓库已经在 `.gitmodules` 里配置好，正常克隆即可：

```bash
git clone --recursive https://github.com/18473419650/mg24-sigmesh-module.git
cd btmesh_soc_empty_2
```

然后按主仓库的 `readme.md` 构建。

如果克隆时忘了 `--recursive`，补拉：

```bash
git submodule update --init --recursive
```

## 注意

- `toolchain/` **不包含** `arm-none-eabi-gdb.exe`（227 MB，超过 GitHub 单文件 100 MB 限制）。
  需要 GDB 单步调试请用 Simplicity Studio 自带的工具链，**编译不受影响**。
- `sdk/.git` 已剔除（SDK 本身是 git 仓库，避免嵌套子仓库）。
- `sdk/.gitattributes` 已剔除（否则 `*.a` 会走 Git LFS，耗尽免费配额）。
- `msys/` 必须保持 `msys/bin/` 布局（MSYS 运行时按 `<root>/bin` 定位根目录）。
- SDK 与工具链版权归 Silicon Laboratories / Arm Limited 所有，仅内部研发使用。
