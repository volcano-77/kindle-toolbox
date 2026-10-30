# Plugins and Third-party Projects

本页统一记录当前 Kindle 使用的第三方项目和 KOReader 插件。本仓库不复制这些项目的源码。

## Status Legend

- ✅ Verified — 已在当前 KT6 + 5.19.6 设备上实际测试
- 🟡 To Verify — 尚未完成实际测试或信息核对
- ⚪ Optional — 非当前核心配置
- ❌ Not Used — 当前未使用

## Inventory

| Project | Repository | Purpose | Installed Version | Install Path | Status |
| --- | --- | --- | --- | --- | --- |
| KOReader | [koreader/koreader](https://github.com/koreader/koreader) | 主要 EPUB/PDF 阅读器 | v2026.07.1 | `/mnt/us/koreader` | ✅ Verified |
| Reading Statistics | [koreader/koreader](https://github.com/koreader/koreader) | KOReader 内置阅读统计 | Bundled with KOReader v2026.07.1 | Bundled with KOReader; exact plugin path needs verification | ✅ Verified |
| WeRead plugin | [finlater/weread.koplugin](https://github.com/finlater/weread.koplugin) | 微信读书书架、下载与缓存阅读 | 1.5.2 | `/mnt/us/koreader/plugins/weread.koplugin` | ✅ Verified |
| FileSync | [abrahamnm/filesync.koplugin](https://github.com/abrahamnm/filesync.koplugin) | 手机无线文件传输 | Needs verification | `/mnt/us/koreader/plugins/filesync.koplugin` | ✅ Verified |
| Custom Screensaver | [chengandre/kindle-custom-screensaver](https://github.com/chengandre/kindle-custom-screensaver) | 替换原生屏保并轮播 PNG | Needs verification | Exact extension path needs verification; images use `/mnt/us/screensavers` | ✅ Verified |
| SimpleUI | [doctorhetfield-cmd/simpleui.koplugin](https://github.com/doctorhetfield-cmd/simpleui.koplugin) | 可选 KOReader 主页 | 2.7.1 | `/mnt/us/koreader/plugins/simpleui.koplugin` | ⚠️ Installed, disabled |
| Moon | [AnkioTomas/moon](https://github.com/AnkioTomas/moon) | 本地书库与在线书源 | v0.4.6 | `/mnt/us/koreader/plugins/book.koplugin` | ✅ Installed; local library tested |
| KPM | Source needs verification | Kindle 插件管理与兼容工具链 | Needs verification | Needs verification | ✅ Verified |

## KOReader

- **Repository:** [koreader/koreader](https://github.com/koreader/koreader)
- **Installed Version:** v2026.07.1
- **Purpose:** 主要阅读器和插件运行环境
- **Install Path:** `/mnt/us/koreader`
- **Installation Method:** Needs verification
- **Status:** ✅ Verified
- **Verified features:** EPUB/PDF、本地文件夹书库、阅读进度、Reading Statistics、Calendar View、插件、Collections
- **Notes:** 当前主要书库根目录为 `/mnt/us/KOReader_Library`。

## Reading Statistics

- **Repository:** [koreader/koreader](https://github.com/koreader/koreader)
- **Installed Version:** Bundled with KOReader v2026.07.1
- **Purpose:** KOReader 阅读时间和历史统计
- **Install Path:** Bundled with KOReader; exact plugin path needs verification
- **Installation Method:** 作为 KOReader 内置功能启用
- **Status:** ✅ Verified
- **Verified features:** 阅读时间、阅读历史、Calendar View、每日阅读记录
- **Notes:** 只统计通过 KOReader 阅读的内容，不包含原生 Kindle 阅读器中的阅读。

## WeRead Plugin

- **Repository:** [finlater/weread.koplugin](https://github.com/finlater/weread.koplugin)
- **Installed Version:** 1.5.2
- **Purpose:** 在 KOReader 中访问微信读书内容并缓存阅读
- **Install Path:** `/mnt/us/koreader/plugins/weread.koplugin`
- **Installation Method:** Needs verification
- **Status:** ✅ Verified
- **Verified features:** QR Code 登录、Bookshelf、打开书籍、下载完整章节、生成本地 EPUB、离线阅读缓存书籍
- **Notes:** 缓存位于 `/mnt/us/koreader/weread/cache/<book_id>/`。不得在仓库中保存 API Key、Cookie、Token、二维码内容或账号信息。

## FileSync

- **Repository:** [abrahamnm/filesync.koplugin](https://github.com/abrahamnm/filesync.koplugin)
- **Installed Version:** Needs verification
- **Purpose:** 通过同一 Wi-Fi 下的手机浏览器上传文件
- **Install Path:** `/mnt/us/koreader/plugins/filesync.koplugin`
- **Installation Method:** Needs verification
- **Status:** ✅ Verified
- **Verified features:** 启动服务器、显示二维码、手机浏览器访问 Kindle 文件系统、上传 EPUB 到 `KOReader_Library`、在 Kindle 中读取上传后的书
- **Notes:** 向 `/mnt/us/screensavers` 上传 PNG 后是否可直接进入屏保轮播仍为 `🟡 To Verify`。

## Custom Screensaver

- **Repository:** [chengandre/kindle-custom-screensaver](https://github.com/chengandre/kindle-custom-screensaver)
- **Installed Version:** Needs verification
- **Purpose:** 使用 PNG 替换原生 Kindle 屏保
- **Install Path:** Needs verification
- **Installation Method:** Needs verification
- **Image Path:** `/mnt/us/screensavers`
- **Status:** ✅ Verified
- **Verified features:** PNG 正常显示、多张 PNG 轮播、通过 Kindle 中对应入口启用、替换原生屏保
- **Notes:** 当前观察到非 PNG 图片不会进入轮播。详见 [screensaver.md](screensaver.md)。

## SimpleUI

- **Repository:** [doctorhetfield-cmd/simpleui.koplugin](https://github.com/doctorhetfield-cmd/simpleui.koplugin)
- **Installed Version:** 2.7.1
- **Purpose:** 改善 KOReader 默认文件浏览器式界面，提供主页体验
- **Install Path:** `/mnt/us/koreader/plugins/simpleui.koplugin`
- **Installation Method:** Needs verification
- **Status:** ⚠️ Installed, disabled after exit failure
- **Verified features:** 插件加载、首次初始化、设置 Home Screen、显示阅读相关信息、作为 KOReader 主页 UI
- **Notes:** 电源菜单曾记录 `plugin` 为 nil 的异常，表现为退出仅回到 SimpleUI 主页、重启按钮无效。停用后 KOReader 原生文件管理器和退出到 Kindle 主页均已实测恢复。详见 [troubleshooting.md](troubleshooting.md)。

## Moon

- **Repository:** [AnkioTomas/moon](https://github.com/AnkioTomas/moon)
- **Installed Version:** v0.4.6 正式版
- **Install Path:** `/mnt/us/koreader/plugins/book.koplugin`
- **Installation Method:** Windows MTP 直接复制正式目录；资源管理器和 WPD 属性更新均未能重命名先前的暂存目录。
- **Status:** ✅ 653 个文件、106 个子目录经 WPD `STGM_READ` 全量校验；用户在设备上确认识别 73 本本地书，并抽查原阅读进度。
- **Open item:** 本地书分类未从 KOReader Collections 导入。详见 [moon-classification.md](moon-classification.md)。
- **Staging copy:** `book.koplugin.installing` 仍在设备上，未删除；它不是正式插件目录。

## KPM

- **Repository:** Source needs verification
- **Installed Version:** Needs verification
- **Purpose:** Kindle 插件管理与 KT6 新固件环境兼容处理
- **Install Path:** Needs verification
- **Installation Method:** Needs verification
- **Status:** ✅ Verified — 已安装并可使用
- **Notes:** 在来源和版本得到确认前，不添加推测链接。
