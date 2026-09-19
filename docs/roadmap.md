# Kindle 后续改造路线图

本文是后续改造的阶段规划，不是当前执行教程。

## Device

- Device model: Kindle 11th Generation, 2024 Release
- KindleModding device code: KT6
- Firmware: 5.19.6
- 当前仍未最终确认 KT6 + 5.19.6 的稳定越狱支持
- 当前不执行任何越狱操作

## Phase 0 - Current State

- 保持飞行模式
- 不升级固件
- 继续使用原生 Kindle
- 可以正常整理本地书籍

## Phase 1 - Verify Jailbreak Support

需要确认：

- KT6 + 5.19.6 是否有官方或社区明确支持
- 使用哪一种越狱方案
- 成功案例是否足够
- 已知失败风险
- 是否存在恢复方案

只有以上事项全部确认后，才能进入下一阶段。在此之前，不假设 KT6 + 5.19.6 已经支持越狱。

## Phase 2 - Prepare Before Jailbreak

未来确认支持后再进行：

- 备份重要书籍和笔记
- 记录当前设备状态
- 准备所需文件
- 阅读完整安装与恢复文档
- 确认设备电量、USB 连接和电脑环境

## Phase 3 - Jailbreak

- 按已确认兼容的官方或社区文档执行
- 不混用不同教程
- 不使用未知来源文件
- 执行前再次核对型号和固件
- 完成后先验证 Kindle 原生功能是否正常

本阶段不提供当前可直接执行的命令。

## Phase 4 - Install KOReader

未来越狱成功后：

- 安装适配当前 Kindle 的 KOReader
- 第一次仅验证：
  - 能否正常启动
  - EPUB/PDF 是否可打开
  - 字体与排版是否正常
  - 退出后能否正常回到 Kindle 原生界面
- 暂时不安装其他插件

## Phase 5 - Enable Reading Statistics

验证 KOReader 自带统计功能：

- 阅读时间
- 阅读页数
- Calendar View
- Today's Timeline
- 当前书统计

## Phase 6 - Install WeRead Plugin

在 KOReader 稳定后再考虑：

- 安装 `finlater/weread.koplugin`
- 配置微信读书 Skill
- 获取 API Key
- 扫码登录
- 测试书架、书评、划线、进度同步
- 测试章节下载和本地缓存

## Phase 7 - Customization

最后才考虑：

- 字体
- 页面排版
- 手势
- 状态栏
- 屏保
- 其他 UI 美化

## Phase 8 - Maintenance

- 固件升级前先检查越狱兼容性
- KOReader 升级前查看 release notes
- 微信读书插件升级前查看 changelog
- 定期备份阅读统计与重要笔记

## Checklist

- [x] Phase 0 - Current State：完成
- [ ] Phase 1 - Verify Jailbreak Support：进行中（当前阶段）
- [ ] Phase 2 - Prepare Before Jailbreak：未开始
- [ ] Phase 3 - Jailbreak：未开始
- [ ] Phase 4 - Install KOReader：未开始
- [ ] Phase 5 - Enable Reading Statistics：未开始
- [ ] Phase 6 - Install WeRead Plugin：未开始
- [ ] Phase 7 - Customization：未开始
- [ ] Phase 8 - Maintenance：未开始
