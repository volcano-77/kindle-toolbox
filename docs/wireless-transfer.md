# Wireless Transfer with FileSync

使用第三方 [FileSync KOReader plugin](https://github.com/abrahamnm/filesync.koplugin) 从手机向 Kindle 无线上传 EPUB。

- **Install Path:** `/mnt/us/koreader/plugins/filesync.koplugin`
- **Status:** ✅ Verified
- **Installed Version:** Needs verification

验证范围仅限当前 KT6 设备。

## Transfer EPUB

1. 让 Kindle 与手机连接同一个 Wi-Fi。
2. 在 Kindle 上打开 KOReader。
3. 打开 `Network`。
4. 打开 `FileSync`。
5. 选择 `Start file server`。
6. 选择 `Show QR code`。
7. 使用手机浏览器扫码。
8. 在手机页面中进入 `KOReader_Library`。
9. 上传 EPUB。
10. 在 Kindle 中刷新 KOReader 文件列表，确认并打开上传后的书籍。

## Connection Behavior

- 二维码页面关闭后，只要 FileSync Server 仍在运行，手机连接通常仍然有效。
- FileSync Server 停止、KOReader 退出或 Wi-Fi 断开后，连接结束。
- FileSync 暴露的是 Kindle 文件系统访问入口，只在需要传输时启动，完成后应停止服务器。

## Verified Result

当前已经实际验证：

- KOReader 中可以启动 FileSync Server。
- Kindle 可以显示二维码。
- 手机浏览器可以访问 Kindle 文件系统。
- EPUB 可以上传到 `KOReader_Library`。
- Kindle 可以看到并读取上传后的书籍。

## Screensaver Upload

理论目标是通过 FileSync 将 PNG 上传到 `/mnt/us/screensavers`，但“上传后是否可直接进入当前屏保轮播”尚未正式测试，状态为 `🟡 To Verify`。
