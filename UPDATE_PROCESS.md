# 后续版本发布流程

## 1. 确定版本号

开发版使用 `0.6.5-dev`、`0.6.6-dev` 递增；版本号必须高于已发布版本，不能重复使用旧版本号。

## 2. 完成代码和资源修改

确认导演台、画布、Electron 主进程、preload、后端和所有素材均已同步到发布载荷。不要放入用户数据目录、API Key、项目数据库、日志、缓存或旧备份。

## 3. 构建与测试

1. 更新 ASAR 内 `package.json` 的版本号。
2. 运行 `node --check electron/updater.js`。
3. 重新打包 `app.asar`，并保留 `app.asar.unpacked` 原生模块。
4. 编译 Inno Setup 安装器。
5. 使用独立测试配置启动安装后的程序，确认前端 4189、后端 8189、画布和导演台均可用。

## 4. 生成更新清单

运行本地 `生成更新清单.ps1`，得到：

- `dev.yml`
- `release.json`

`dev.yml` 中的安装器文件名、字节数和 SHA-512 必须与实际文件一致。

## 5. 创建 GitHub Release

1. Tag 使用 `v<版本号>`，例如 `v0.6.5-dev`。
2. 开发版必须勾选 **Set as a pre-release**。
3. 上传安装器、`dev.yml`、`release.json`。
4. 发布后分别打开三个文件的下载链接，确认可以访问。

## 6. 更新策略

在 `release.json` 中设置：

- `forceUpdate: false`：普通更新，下载后由用户决定安装时间。
- `forceUpdate: true`：强制更新，客户端下载并校验完成后自动启动安装。
- `minimumSupportedVersion`：低于该版本的客户端必须升级。

强制更新前必须先在测试电脑验证安装、项目恢复和导演台存档兼容性。

## 7. 回滚

发现严重问题时，不要删除旧 Release。修复后发布更高版本号；客户端不会自动降级到更低版本。
