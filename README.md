# 🧱 pypi_autodl

一个用于 **离线环境** 安装 Python 包的自动化构建工具。
它可以在 **联网机器或 GitHub Actions** 上运行，自动分析并下载所有依赖（包括构建依赖如 `Cython`、`setuptools-scm`），生成完整的 **`wheelhouse/` 离线包目录**。

---

## ✨ 功能特性

✅ 自动解析 `packages.txt` 中列出的包
✅ 自动包含所有构建系统依赖（`setuptools`、`wheel`、`setuptools-scm`、`Cython`、`build` 等）
✅ 支持 ARM64
✅ 支持多 Python 版本（默认 3.10，可修改）
✅ 兼容 GitHub Actions，可自动上传离线包到 artifact

☑️使用QEMU实现x86模拟arm64平台

## 📦 使用方法

### 1️⃣ 编辑包列表

在 `packages.txt` 中写入需要的包（可包含版本号）：

```txt
abtem
ase
numpy
```

2️⃣ 下载软件包

提交改动到 github 后，运行github action `Build ARM64 Python Wheelhouse`

### 3️⃣ 在离线环境安装

将action的制品下载拷贝到目标主机后执行：

`pip install --no-index --find-links=wheelhouse -r packages.txt
`
