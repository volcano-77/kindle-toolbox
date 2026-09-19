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
- 使用第三方 [SimpleUI](https://github.com/doctorhetfield-cmd/simpleui.koplugin) 改善主页体验。

SimpleUI 已在当前设备成功加载并用作 KOReader 主页 UI，但它不是 KOReader 官方内置功能。

## Safety Notes

- 不随意修改或删除 `system`、`libkh` 或越狱相关文件。
- 不混用来源不明的修复文件或教程。
- 系统级故障处理前先核对当前型号、固件和最新恢复文档。
