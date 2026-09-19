# Kindle 后续改造路线图

本文是后续改造的阶段规划，不是当前执行教程。

## Device

- Device model: Kindle 11th Generation, 2024 Release
- KindleModding device code: KT6
- Firmware: 5.19.6
- 已确认 Véra 支持 KT6 + 5.19.6，并已有实际成功案例
- 当前不执行任何越狱操作

## Phase 0 - Current State

- 保持飞行模式
- 不升级固件
- 继续使用原生 Kindle
- 可以正常整理本地书籍

## Phase 1 - Verify Jailbreak Support

已基本确认：

- Véra 支持 KT6 + 5.19.6
- 已存在 KT6 2024 成功使用 Véra 越狱并运行 KOReader 的实际案例
- KindleModding 的 KPM 工具链包含针对 KT6 新固件环境的兼容处理

真正执行前仍需完成：

- 再次确认 Véra 官方向导仍识别 KT6 + 5.19.6
- 阅读恢复和失败处理文档
- 明确出现问题时的处理边界

越狱仍然不是零风险。其他新 Kindle 型号出现过触控异常、启动循环、KOReader 异常等问题，这些不能直接推断 KT6 必然出现，但应作为风险参考。新 Kindle 的恢复能力不如老型号，不能简单依赖传统分区备份恢复。

只有剩余事项确认完成后，才能进入下一阶段。

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
- [ ] Phase 1 - Verify Jailbreak Support：基本确认（当前阶段）
- [ ] Phase 2 - Prepare Before Jailbreak：未开始
- [ ] Phase 3 - Jailbreak：未开始
- [ ] Phase 4 - Install KOReader：未开始
- [ ] Phase 5 - Enable Reading Statistics：未开始
- [ ] Phase 6 - Install WeRead Plugin：未开始
- [ ] Phase 7 - Customization：未开始
- [ ] Phase 8 - Maintenance：未开始
