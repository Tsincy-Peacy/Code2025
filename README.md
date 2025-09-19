# Code2025

USTC CS1003.05 2025 Web



Made by [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)



### Environment

采用 Python 原生 venv 模块，快速开发，避免工具依赖。

这里假定使用 Windows 操作系统开发，其他操作系统请自行变更指令。

```powershell
cd Code2025
python -m venv .venv  # 创建虚拟环境
.venv/Scripts/Activate.ps1  # 激活虚拟环境
pip install mkdocs-material  # 使用 pip 安装 mkdocs-material 及其依赖包 mkdocs 等
```



### Develop

```powershell
cd Code2025
mkdocs serve  # 开发状态
```

在浏览器打开：http://127.0.0.1:8000/，可以实时查看修改。



页面设置在mkdocs.yml，详细介绍查看 MkDocs 或 [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) 官网。

页面 Markdown 源码在 docs 中。



### Build

```powershell
cd Code2025
git add .
git commit -m "comment"
git push  # 不需要 mkdocs build 操作，已包含在 Github Actions
```

