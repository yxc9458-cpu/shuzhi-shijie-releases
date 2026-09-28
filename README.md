# 数智视界 Windows 更新

本仓库用于发布数智视界 Windows 安装包和应用内更新清单，不存放用户工程、API 密钥或登录凭据。

## 下载

前往 [Releases](https://github.com/yxc9458-cpu/shuzhi-shijie-releases/releases) 下载最新版本的 `SoulLens-Setup-<版本>.exe`。

## 应用内更新

保持现有 dev 更新通道。从 0.6.5-dev 起，软件启动后自动检查 GitHub 更新，运行期间每隔 6 小时检查；网络异常后 15 分钟重试。下载并校验完成后，保存工程并选择重启安装。

当前使用完整安装器更新，仍需下载完整 EXE。安装到原路径并保留用户配置，不强制关闭正在使用的软件。

每个 Release 包含 EXE、dev.yml、release.json 和 SHA256SUMS.txt。应用在安装前验证 SHA-512。
