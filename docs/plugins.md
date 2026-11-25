# Plugins and Third-party Projects

本页统一记录当前 Kindle 使用的第三方项目和 KOReader 插件。本仓库不复制这些项目的源码。

## Status Legend

- ✅ Verified — 已在这台 KT6 上实际测试，具体版本以各项记录为准
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
| Moon | [AnkioTomas/moon](https://github.com/AnkioTomas/moon) | 本地书库与在线书源 | v0.7.2 | `/mnt/us/koreader/plugins/book.koplugin` | ✅ Installed |
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
- **Installed Version:** v0.7.2（2026-11-25）
- **Install Path:** `/mnt/us/koreader/plugins/book.koplugin`
- **Installation Method:** Windows MTP 直接复制正式目录；资源管理器和 WPD 属性更新均未能重命名先前的暂存目录。
- **Historical verification:** v0.4.6 的文件校验和本地书库实测见 [Moon 分类迁移](moon-classification.md)。
- **Open item:** 本地书分类未从 KOReader Collections 导入。详见 [moon-classification.md](moon-classification.md)。
- **Staging copy:** `book.koplugin.installing` 仍在设备上，未删除；它不是正式插件目录。

## Moon Third-Party Sources

记录日期 2026-11-25。实测环境为 Kindle KT6、固件 5.20.1.0.2、KOReader v2026.07.1、月读 v0.7.2。

| 书源 | 版本 | 设备实测 |
| --- | --- | --- |
| 微信读书 | v0.2.0 | 正常阅读、阅读进度同步、阅读时长同步均通过 |
| 番茄小说 | v0.2.0 | 在线阅读通过 |

两个书源的离线阅读均待验证。原有独立 WeRead 插件保留在 `weread.koplugin`，其缓存阅读实测属于独立插件。

- 月读自 v0.6.0 起将原内置平台书源拆出，第三方插件由 GarfieldTony 维护。 [月读数据源手册](https://moon.ankio.net/manual/library/sources) · [第三方书源安装说明](https://moon.ankio.net/manual/library/sources/plugins)
- 从维护者的发布页获取对应 ZIP 和同一版本的 `SHA256SUMS`。 [moon-source Releases](https://codeberg.org/GarfieldTony/moon-source/releases) · [本次使用的 v0.2.0](https://codeberg.org/GarfieldTony/moon-source/releases/tag/v0.2.0)

### 安装与迁移

1. 退出 KOReader 后连接 USB。在 Windows 的 MTP 设备中打开 `Internal Storage/koreader/plugins`，对应 Kindle 上的 `/mnt/us/koreader/plugins`。本设备通过 MTP 访问，无盘符。
2. 首次迁移前，将月读数据备份到本机私有位置。至少保存 `koreader/.moon/book.sqlite3`（如有 SQLite 边车文件则一并保存）、微信书源与公共书源设置，以及旧的 `.moon/cache/wechat`。本次在安装微信书源前核对了备份的路径和文件大小，并对数据库执行了 SQLite 完整性检查。备份、账号数据和插件 ZIP 只留在本地。
3. 下载 `moonsource-weread.koplugin-0.2.0.zip` 和 `moonsource-fanqie.koplugin-0.2.0.zip`，按发布者提供的校验表核对 SHA-256。解压后将两个 `moonsource-*.koplugin` 目录分别放在 `book.koplugin` 同级。检查 `main.lua`、`_meta.lua` 和 `moon_source.lua` 直接位于各插件根目录。本次从设备回读并逐文件校验，微信 36 个文件、番茄 24 个文件全部匹配。
4. 微信书源首次加载时会尝试把月读旧源 ID 从 `wechat` 迁移到 `weread`，涉及设置、数据库记录和缓存路径。迁移会清空已处理的旧设置项，同步时还会清理旧版归入书库的公众号条目及其关联记录。确认备份和迁移范围后再首次启动月读。
5. 断开 USB，重启 KOReader，进入月读 **设置 → 书库 → 启用的书源** 勾选对应书源。到 **账号** 查看登录状态，按提示用微信或番茄小说 App 扫码，然后到月读图书馆切换书源并刷新。

### 更新与兼容性

- 月读本体 `book.koplugin` 单独发布。月读内的入口为 **设置 → 我的设备 → 版本**。 [月读本体 Releases](https://github.com/AnkioTomas/moon/releases)
- 第三方书源有独立的 Codeberg 版本和安装包。初装走手动复制。v0.2.0 自带 **设置 → 书库 → 更新**，可手动检查，也可启用自动检查。发现新版后会提示确认，确认安装时会一并更新已安装的该系列书源。也可从发布页手动下载并校验后更新。更新月读本体后，仍需单独检查书源版本。
- 更新前记录当前 KOReader、月读和书源版本，阅读双方发布说明，核对最低版本和迁移要求。此次最低要求为 KOReader 2026.07、月读 0.6.0，已验证组合见本节开头。先保留可用的插件版本和私有数据快照，再更新一个组件或一组同版本书源。重启后检查书源出现、账户状态和在线阅读，再分别用同一本书验证双向进度、适用书源的时长同步，以及断网后重开已缓存章节。

### 故障与回滚

1. 书源未出现时，检查目录层级、三个 Lua 入口和启用状态，再核对发布版本与 KOReader、月读兼容性。登录或同步异常时，先检查网络、账号状态和发布者已知问题。 [番茄书架新增书籍同步问题](https://github.com/AnkioTomas/moon/issues/152)
2. 若故障出现在更新后，先禁用受影响的书源并重启。若月读无法打开，退出 KOReader 后通过 MTP 将受影响的插件目录移出 `plugins/`。保留当前数据快照，按需要恢复相应的已验证插件版本，并复查其数据格式兼容性。
3. 插件文件回退不会逆转数据迁移。若确需回退数据，应先保存故障后的数据，评估恢复旧快照会丢失哪些新增进度或书架变更，再由用户确认。退出 KOReader 后成套恢复兼容版本的数据库、相关设置和缓存，而非单独覆盖数据库。不要为恢复单个书源而随意降级月读或清空数据。

## KPM

- **Repository:** Source needs verification
- **Installed Version:** Needs verification
- **Purpose:** Kindle 插件管理与 KT6 新固件环境兼容处理
- **Install Path:** Needs verification
- **Installation Method:** Needs verification
- **Status:** ✅ Verified — 已安装并可使用
- **Notes:** 在来源和版本得到确认前，不添加推测链接。
