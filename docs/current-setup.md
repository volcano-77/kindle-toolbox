# Current Kindle Setup

本页是当前设备状态的总览。详细操作、插件说明和故障排查分别链接到其他文档。

## Device

| Item | Current value |
| --- | --- |
| Model | Kindle 11th Generation, 2024 Release |
| KindleModding code | KT6 |
| Firmware | 5.19.6 |
| Storage | 16 GB |
| Jailbreak | ✅ Verified — Véra completed successfully |

## Verified Setup

| Component | Status | Current use |
| --- | --- | --- |
| Kindle native system | ✅ Verified | Starts and remains usable after jailbreak |
| KOReader | ✅ Verified | EPUB/PDF reading, local folders, progress, plugins, Collections |
| Reading Statistics | ✅ Verified | Reading time, history, Calendar View, daily records |
| WeRead plugin | ✅ Verified | Bookshelf, book opening, full download, local EPUB, cached offline reading |
| FileSync | ✅ Verified | Phone-to-Kindle wireless EPUB upload |
| Custom Screensaver | ✅ Verified | PNG display and multi-image rotation |
| SimpleUI | ✅ Verified | KOReader home screen and reading information |
| KPM | ✅ Verified | Installed and usable; exact version and source need verification |
| Calibre 9.15.0 | ✅ Verified | Windows master library, metadata, classification, and EPUB transfer |

## Important Paths

| Purpose | Kindle path | Windows MTP view |
| --- | --- | --- |
| Main local library | `/mnt/us/KOReader_Library` | `Internal Storage/KOReader_Library` |
| KOReader | `/mnt/us/koreader` | `Internal Storage/koreader` |
| KOReader plugins | `/mnt/us/koreader/plugins` | `Internal Storage/koreader/plugins` |
| WeRead cache | `/mnt/us/koreader/weread/cache/<book_id>/` | `Internal Storage/koreader/weread/cache/<book_id>/` |
| Screensaver images | `/mnt/us/screensavers` | `Internal Storage/screensavers` |

Windows 端 Calibre 正式主书库固定为 `D:\Calibre Library`。Calibre 已配置并实测将 EPUB 发送到 `Internal Storage\KOReader_Library`。

## Device Directory Overview

```text
/mnt/us/
├── KOReader_Library/
├── koreader/
│   ├── plugins/
│   │   ├── filesync.koplugin/
│   │   ├── weread.koplugin/
│   │   └── simpleui.koplugin/
│   └── weread/
│       └── cache/
├── screensavers/
├── documents/
├── extensions/
├── fonts/
├── system/
└── ...
```

`system`、`libkh` 和越狱相关目录或文件不属于日常书库管理范围，不应随意修改或删除。

## KOReader Library

- 主书库根目录：`/mnt/us/KOReader_Library`
- 支持当前已验证的 EPUB/PDF 阅读流程。
- KOReader 已将该目录设置为主要根目录。
- 手机通过 FileSync 上传的 EPUB 可直接放入该目录。
- Calibre 发送 EPUB 到该目录的路径已经实测验证。
- 当前 Kindle 本地书库共有 73 个 EPUB 文件。

## Reading Statistics

- 阅读时间、阅读历史、Calendar View 和每日阅读记录已验证。
- 统计只包含通过 KOReader 阅读的内容。
- 原生 Kindle 阅读器中的阅读不会计入 KOReader Reading Statistics。

## WeRead Cache

完整章节下载后可生成类似以下文件：

```text
/mnt/us/koreader/weread/cache/<book_id>/<book name> - full.epub
```

已缓存书籍可以离线阅读。本仓库不记录任何 API Key、Cookie、Token、二维码内容或账号信息。

## Collections

KOReader Collections 是逻辑分类，不是物理文件夹。当前最终使用的 8 个 Collections 为：

- `Literary Fiction 文学小说`
- `Mystery & Crime 悬疑 / 犯罪`
- `Sci-Fi & Fantasy 科幻 / 奇幻`
- `Infinite Flow & Game 无限流 / 游戏`
- `Apocalypse & Survival 末世 / 生存`
- `Women 女性`
- `Society & Family 社会 / 家庭`
- `Nonfiction 非虚构`

Collection 成员关系保存在 `koreader/settings/collection.lua`。Calibre 分类和 KOReader Collections 是两套独立数据；同名标签不会自动同步，新增成员必须经过路径核对、备份和增量更新。

## Long-term Library Workflow

少量新书：

```text
手机 / FileSync → Kindle → KOReader 手动加入 Collection
```

批量新书：

```text
EPUB → Calibre → 整理元数据与分类 → 发送到 KOReader_Library → 增量更新 KOReader Collections
```

Calibre 是长期母库，Kindle 是当前阅读库。`.sdr` 保存每本书的 KOReader 阅读状态，不属于 Calibre 分类或 Collection 数据。

设备备份统一保存在 `D:\Kindle Backup`。该目录是本地私密备份，不进入 Git。

## High-level Restore Order

1. 核对设备型号、固件和当时有效的兼容性文档。
2. 完成系统级准备后，先确认 Kindle 原生功能正常。
3. 安装 KOReader，并恢复 `KOReader_Library` 根目录设置。
4. 按 [plugins.md](plugins.md) 恢复已确认来源的插件。
5. 恢复屏保图片、阅读统计和重要笔记。
6. 分别验证本地阅读、无线传书、WeRead 缓存与原生系统返回流程。

系统级操作仍应以当时最新且明确兼容的官方或社区文档为准；本页不提供越狱命令。
