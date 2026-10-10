# Midgard 官方安装分发

本仓库只存放 Midgard 的官方安装资产，**不包含源码**：每个 `vX.Y.Z` Release 提供 `install.sh`、三平台清单（macos-arm64 / linux-x86_64 / linux-arm64）、平台 wheelhouse 与 uv 归档。wheel/sdist 等源码产物不在本仓库发布。

## 安装

把 `X.Y.Z` 替换为 Releases 页面中的最新版本（macOS 仅 Apple 芯片；macOS Intel 不受支持）：

```sh
curl -fsSL https://github.com/injenium/Midgard-release/releases/latest/download/install.sh | sh -s -- --version X.Y.Z --release-url https://github.com/injenium/Midgard-release/releases/download
```

安装器强制显式 `--version`（不自动解析 latest），只从官方 HTTPS `--release-url` 下载并按平台清单逐项校验 SHA256；默认安装到 `~/.local/share/midgard`，入口 `~/.local/bin/midgard`，不会修改系统 Python 或 shell 配置。安装完成后按提示运行 `midgard onboard` 完成实例配置。

## 升级

```sh
midgard update          # 联网解析本仓库最新正式版本；高于当前版本时执行加密快照升级
midgard update --check  # 只查询，不改动本地状态
```

## 校验与授权

- 平台清单与归档摘要随 Release 提供，安装过程逐项校验 SHA256；安装器拒绝非官方 HTTPS 基地址。
- 安装器与平台资产随 Midgard 以 [Apache-2.0](LICENSE) 授权发布。
