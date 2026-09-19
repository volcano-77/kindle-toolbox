# Kindle Toolbox Roadmap

本路线图记录当前完成状态和后续维护方向，不是越狱执行教程。

## Completed

- [x] ✅ Verified — 在 Kindle 11th Generation（2024 Release，KT6）固件 5.19.6 上使用 Véra 完成越狱
- [x] ✅ Verified — 越狱后 Kindle 原生系统正常启动
- [x] ✅ Verified — 安装并运行 KOReader
- [x] ✅ Verified — 使用 `/mnt/us/KOReader_Library` 作为主要书库根目录
- [x] ✅ Verified — 阅读 EPUB/PDF，并保存阅读进度
- [x] ✅ Verified — 启用 Reading Statistics、阅读历史、Calendar View 和每日阅读记录
- [x] ✅ Verified — 安装 WeRead 插件，登录、打开书架与书籍、下载完整章节并生成本地 EPUB
- [x] ✅ Verified — 使用 FileSync 从手机无线上传 EPUB 到 `KOReader_Library`
- [x] ✅ Verified — 安装并使用 PNG 自定义屏保与多图轮播
- [x] ✅ Verified — 安装并使用 SimpleUI 作为 KOReader 主页 UI
- [x] ✅ Verified — 开始使用 KOReader Collections 进行逻辑分类

## Optional Improvements

- [ ] ⚪ Optional — 记录 KOReader、KPM 和各第三方插件的当前安装版本
- [ ] ⚪ Optional — 确认 KPM 的准确项目来源与设备安装目录
- [ ] ⚪ Optional — 制定阅读统计、重要笔记和关键配置的定期备份流程
- [ ] ⚪ Optional — 继续调整字体、排版、手势、状态栏和其他 UI 选项
- [ ] ⚪ Optional — 完善 Collections 分类与使用约定
- [ ] 🟡 To Verify — 使用 FileSync 向 `/mnt/us/screensavers` 上传 PNG 后，是否可直接进入屏保轮播

## Future Ideas

- [ ] ⚪ Optional — 编写从空白设备恢复当前配置的核对清单
- [ ] ⚪ Optional — 在任何固件升级前重新检查 Véra、KPM、KOReader 和插件兼容性
- [ ] ⚪ Optional — 在 KOReader 或插件升级前记录版本、阅读 release notes/changelog，并准备回退方案
- [ ] ⚪ Optional — 补充已验证的配置备份与恢复结果

## Maintenance Rules

- 只把当前设备上实际测试成功的结果标为 `✅ Verified`。
- 未测试内容使用 `🟡 To Verify`，非必需改进使用 `⚪ Optional`。
- 不在本仓库保存第三方项目源码、账号凭证或敏感设备标识。
- 不因为当前设备成功，就推断其他型号或固件同样兼容。
