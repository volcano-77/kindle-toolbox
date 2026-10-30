# Troubleshooting

本页记录当前设备实际遇到或当前配置中已确认的故障处理方式。除非特别说明，不代表所有 Kindle 都会出现同样问题。

## 1. KOReader 运行时 Windows 看不到 USB / MTP 存储

**Status:** ✅ Verified

当前设备实际遇到。

**Observed behavior:** KOReader 正在运行时，Windows 有时无法正常显示 Kindle 的 `Internal Storage`。

**Working resolution:**

1. 退出 KOReader。
2. 回到 Kindle 原生系统。
3. 重新连接 USB。
4. 在 Windows 中重新查看 Kindle `Internal Storage`。

这是当前设备上的实际解决方式，不应表述为所有设备都会发生。

## 2. Custom Screensaver 仍显示原生屏保

**Status:** ✅ Verified

**Cause:** 插件安装完成后，还需要在 Kindle 中启用对应的 Custom Screensaver 入口。

**Resolution:**

1. 打开 Kindle 中对应的 Custom Screensaver 入口。
2. 启用自定义屏保。
3. 确认图片位于 `/mnt/us/screensavers`。

## 3. Screensaver 图片不参与轮播

**Status:** ✅ Verified

检查：

- 图片是否为 PNG。
- 图片是否位于 `/mnt/us/screensavers`。
- 文件名是否使用简单 ASCII 名称，例如 `01.png`、`02.png`、`03.png`。

当前已经观察到：目录中的非 PNG 图片没有进入轮播。

## 4. WeRead 书籍不能直接阅读

**Status:** ✅ Verified

如果插件显示类似 `Cached 0/x chapters`，说明完整章节还没有下载到本地。

**Resolution:**

1. 在 WeRead 插件中选择 `Download full`。
2. 等待完整章节下载完成。
3. 使用生成的本地 EPUB 阅读。

缓存目录结构类似：

```text
/mnt/us/koreader/weread/cache/<book_id>/<book name> - full.epub
```

## 5. KOReader 默认首页像文件浏览器

**Status:** ✅ Verified

可采用：

- 将 `/mnt/us/KOReader_Library` 设置为主要根目录。
- 使用 KOReader 原生文件管理器；当前设备已停用 SimpleUI。

SimpleUI 曾在当前设备加载并用作主页，但现因退出故障停用。它不是 KOReader 官方内置功能。

## 6. SimpleUI 退出与重启按钮无效

**Status:** ✅ 已通过隔离测试定位到 SimpleUI 路径

在 SimpleUI 2.7.1 启用时，KOReader 与 SimpleUI 的退出操作只回到 SimpleUI 主页，SimpleUI 的重启按钮无效；相关电源菜单日志出现 `plugin` 为 nil 的报错。该现象与上游 [Issue #557](https://github.com/doctorhetfield-cmd/simpleui.koplugin/issues/557) 相似，但不能据此断言完全同因。

保留插件文件并停用 SimpleUI 后，KOReader v2026.07.1 正常进入原生文件管理器，也能退出到 Kindle 原生主页。此结果支持 SimpleUI 路径为当前故障的主要触发点；没有证据要求重装 KOReader 或更改 Kindle 系统分区。当前保持 SimpleUI 停用，修复或再次启用前先备份 KOReader 设置，并验证退出路径。

## 7. Moon 显示 73 本本地书，但分类为空

**Status:** ✅ 原因由 v0.4.6 源码和本地备份确认

Moon 扫描 EPUB 文件，但不导入 `koreader/settings/collection.lua`。默认“按文件夹分类”会将本地书库第一层目录视为分类；目前 73 本书按原路径保留，KOReader Collections 属于独立的逻辑多标签关系，所以 Moon 的分类页不会自动还原那 8 个集合。不要为恢复分类而移动 EPUB 或 `.sdr`。见 [Moon 分类迁移](moon-classification.md)。

## Safety Notes

- 不随意修改或删除 `system`、`libkh` 或越狱相关文件。
- 不混用来源不明的修复文件或教程。
- 系统级故障处理前先核对当前型号、固件和最新恢复文档。
