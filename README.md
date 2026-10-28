# TVBoxOSC

![Build](https://shields.io/github/actions/workflow/status/mojiyu/TVBoxOSC/test.yml?branch=master&logo=github&label=Build)
[![Channel](https://img.shields.io/badge/Follow-Telegram-blue.svg?logo=telegram)](https://t.me/TVBoxOSC)
[![Download](https://img.shields.io/github/v/release/mojiyu/TVBoxOSC?color=orange&logoColor=orange&label=Download&logo=DocuSign)](https://github.com/mojiyu/TVBoxOSC/releases/latest)
[![Total](https://shields.io/github/downloads/mojiyu/TVBoxOSC/total?logo=Bookmeter&label=Counts&logoColor=yellow&color=yellow)](https://github.com/mojiyu/TVBoxOSC/releases)

## 源码与构建

本仓库负责自动打包和发布，不直接保存 Android 应用源码。GitHub Actions 会分别拉取以下两个 fork 的 `main` 分支，各自构建 APK：

- [mojiyu/TVBoxOS](https://github.com/mojiyu/TVBoxOS) (Updated: ab11d289e09963a9daf65ca7f6b7a9a8cbe184e1)
- [mojiyu/Box](https://github.com/mojiyu/Box) (Updated: 258a5fef61578869ae905ca230bdde9e99fc19a8)

`Updated` 是沿用的构建记录，成功发布后由工作流更新。修改应用功能时，请在对应源码 fork 中修改并推送到 `main`；需要上游更新时，先在源码 fork 中同步上游。打包仓库不会自动同步源码 fork。

### 手动打包

1. 打开本仓库的 **Actions → Test → Run workflow**（若 Actions 尚未启用，先启用）。
2. 首次运行建议勾选 `rebuild`，忽略已有构建记录。
3. 仅验证打包时勾选 `donotpublish`；产物仍会上传到该次运行的 Artifacts。不勾选则会发布 Release 并更新上述构建记录，要求工作流具备仓库内容写权限。
4. 成功后下载 `mojiyu-TVBoxOS` 或 `mojiyu-Box` Artifact，或从本仓库 Releases 下载发布产物。

构建流程位于 [test.yml](.github/workflows/test.yml)：拉取源码 → 修改版本与构建配置 → 配置签名 → 执行 `./gradlew assemblerelease --build-cache --parallel --daemon --warning-mode all` → 上传 APK 和源码压缩包。APK 文件名和 Release 标签包含项目名，以区分两个版本。

## Credits
This repo relies on the following third-party projects:
- [CatVodTVOfficial/TVBoxOSC](https://github.com/CatVodTVOfficial/TVBoxOSC)
- [q215613905/TVBoxOS](https://github.com/q215613905/TVBoxOS)
- [takagen99/Box](https://github.com/takagen99/Box)
