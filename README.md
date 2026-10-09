# printer-resetter-releases

Release downloads and update feed for Printer Resetter for EPSON.

## Printer Resetter for EPSON 0.9.9 — personal-test 预发布

此版本用于完整 App 更新链路测试，面向 Apple Silicon（arm64），最低 macOS 13。不是正式生产版本。App 使用本地 ad-hoc 代码签名，更新包和 feed 使用专用 EdDSA 身份签名；未经过 Apple Developer ID 签名或公证。系统首次启动提示须由用户自行处理，不建议绕过系统保护。

## 测试包

- build 1：引导版本，用于发现 build 2。
- build 2：整包更新目标。两个版本的程序代码及原生后端一致，仅构建号和嵌入代码签名不同；不代表新增设备功能。
- `appcast.xml`：已签名的 build 2 更新 feed。仓库 main 根目录的同名文件是 App 配置的 feed 地址。
- `release-manifest.json` 与 `.ed25519`：签名前发布清单快照及分离签名；其中 published=false、installed=false 是生成清单时的状态。
- `SHA256SUMS.txt`、两个 `.zip.ed25519`：归档哈希与签名。

## 已完成验证

原生 arm64 编译；解压后严格代码签名验证；两个 ZIP、最终 feed、发布清单的 EdDSA 验证；四类篡改副本均被拒绝。更新策略、维护锁、安装中断日志、路径拒绝、设备操作门控与启动发现使用模拟测试验证。未连接或操作打印机。

## 当前限制

尚未完成 App 内在线发现、下载、安装和重启的端到端测试。当前两个包正常启动会自动发现设备，未提供运行时完全禁用硬件访问的测试开关，因此不能将其当作“零设备访问”测试包运行。本次未安装或启动这些包。请勿将预发布标记理解为已验证所有机型、支持无人值守维护或可用于生产。

已从 GitHub 固定 Release URL 匿名下载全部十项资产，逐字节与本地原件一致；两个 ZIP、最终 feed 和发布清单的 EdDSA 验证均通过。这不等于 App 内安装及重启测试通过。上游 EWR 版本 1.4.1，固定提交 cd4c4984f151d3aed4f8a00cebcd63a59acc8d69。第三方许可见 `THIRD-PARTY-NOTICES.txt` 及 App 内许可证页面。本项目独立开发，并非 Epson 官方产品。

[预发布下载](https://github.com/BLACKCATRECORDS/printer-resetter-releases/releases/tag/personal-test-0.9.9-b2)
