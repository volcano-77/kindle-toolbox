# KOReader 与微信读书实际配置

## 1. Purpose

记录当前设备上已经实际运行的 KOReader 与第三方插件 `finlater/weread.koplugin`。插件源码不复制进本仓库。

- KOReader: ✅ Verified
- WeRead plugin: ✅ Verified
- Installed versions: Needs verification

## 2. KOReader Reading Statistics

KOReader Reading Statistics 已启用并实际验证：

- 阅读时间
- 阅读历史
- Calendar View
- 每日阅读记录

原生 Kindle 阅读器中的阅读不会计入 KOReader Reading Statistics。这里只统计通过 KOReader 阅读的内容。

## 3. WeRead Plugin Features

项目来源：[finlater/weread.koplugin](https://github.com/finlater/weread.koplugin)

安装目录：`/mnt/us/koreader/plugins/weread.koplugin`

当前已经实际验证：

- 微信读书书架
- QR Code 登录
- 打开微信读书中的书
- 下载完整章节
- 保存为本地 EPUB
- 离线阅读已经缓存的书籍

项目文档当前建议使用 KOReader 2026.03 或更高版本，但本机已安装的 KOReader 与插件精确版本仍是 `Needs verification`。

登录流程包括在微信读书 App 中启用微信读书 Skill，并在 KOReader 中按插件流程扫码登录。本仓库不记录 API Key、Cookie、Token、二维码内容、登录凭证或账号信息。

## 4. Offline vs Online Behavior

- KOReader 可以离线阅读本地 EPUB/PDF。
- 根据此前整理的插件/API 资料，官方 Skill 可用于书架、元数据、进度、笔记、书评和统计等账号数据；这些项目并未在本次记录中全部逐项验证。
- 完整章节正文通过微信读书 Web Reader 流程获取，下载后生成本地 EPUB。
- 已缓存的书籍可以离线阅读。

已验证的缓存目录结构类似：

```text
/mnt/us/koreader/weread/cache/<book_id>/
└── <book name> - full.epub
```

## 5. How It Fits My Needs

当前配置已经满足：

- 本地 EPUB/PDF 离线阅读
- 阅读时长统计
- 阅读日历
- 访问微信读书书架与书籍
- 下载完整章节并保存为本地 EPUB
- 离线阅读已缓存内容
- 尽量减少对会员和持续联网的依赖

## 6. Notes

- WeRead 是第三方 KOReader 插件，不是 KOReader 官方内置功能。
- 插件运行依赖 KOReader；当前设备已经完成越狱并成功运行 KOReader。
- 插件或 Web Reader 流程未来可能发生变化，升级前应查看项目 README 和变更说明。
- 当前已验证功能不代表所有微信读书功能都已测试。

## 7. Sources

- KOReader statistics plugin source
- [finlater/weread.koplugin README](https://github.com/finlater/weread.koplugin)
- finlater/weread.koplugin API reference
