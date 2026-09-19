# KOReader 与微信读书方案记录

## 1. Purpose

记录 KOReader 与 `finlater/weread.koplugin` 的已核实能力、联网行为、适用需求和当前限制。本文仅用于方案评估，不执行安装。

## 2. KOReader Reading Statistics

KOReader 自带阅读统计功能，包括：

- 当前书阅读统计
- 阅读时间
- 阅读页数
- 时间范围统计
- Calendar View
- Today's Timeline
- 平均阅读相关统计

## 3. WeRead Plugin Features

`finlater/weread.koplugin` 当前仍在维护，并支持：

- 微信读书书架
- 公众号文章
- 阅读进度同步
- 阅读时长同步和统计
- 书评
- 划线和想法
- 搜索
- 章节下载和本地缓存

插件当前建议使用 KOReader 2026.03 或更高版本。

插件登录方式：

1. 在微信读书 App 中启用微信读书 Skill
2. 获取个人 API Key
3. 在 KOReader 中扫码登录

## 4. Offline vs Online Behavior

- 本地 EPUB/PDF 可用于离线阅读。
- 官方 Skill 可用于书架、元数据、进度、笔记、书评和统计等账号数据。
- 完整章节正文仍需要通过微信读书 Web Reader 流程获取，并可在本地缓存。
- 章节下载并缓存后，可以减少持续联网需求。

## 5. How It Fits My Needs

该方案适合以下需求：

- 本地 EPUB/PDF 离线阅读
- 阅读时长统计
- 阅读日历
- 微信读书书评、划线和想法
- 尽量减少对会员和持续联网的依赖

## 6. Current Blocker

- 该方案依赖 KOReader。
- 在 Kindle 上使用 KOReader 通常需要越狱环境。
- KT6 + 5.19.6 的越狱支持状态尚未最终确认。
- 因此当前只做方案记录，不执行安装。

## 7. Sources

- KOReader statistics plugin source
- finlater/weread.koplugin README
- finlater/weread.koplugin API reference
