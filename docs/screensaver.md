# Custom Screensaver

当前使用第三方项目 [chengandre/kindle-custom-screensaver](https://github.com/chengandre/kindle-custom-screensaver)。本仓库只记录当前设备上的配置和结果，不复制项目源码。

## Current Status

- **Status:** ✅ Verified
- **Installed Version:** Needs verification
- **Extension Install Path:** Needs verification
- **Image Path:** `/mnt/us/screensavers`
- **Windows MTP Path:** `Internal Storage/screensavers`

## Verified Features

- PNG 自定义屏保可以正常显示。
- 多张 PNG 可以轮播。
- 实际测试中，多张图片能够轮流出现。
- Custom Screensaver 可以通过 Kindle 中对应入口启用。
- 原生 Kindle 屏保可以被替换。

## Image Convention

- 使用 PNG 格式。
- 使用简单 ASCII 文件名。
- 建议按顺序命名：`01.png`、`02.png`、`03.png`、`04.png`。
- 将图片放入 `/mnt/us/screensavers`。

当前已经观察到：目录中的非 PNG 图片没有进入轮播。

## Enable

插件安装后，还需要在 Kindle 中打开对应的 Custom Screensaver 入口并启用该功能。仅把图片复制到目录中，不代表自定义屏保已经启用。

## Rotation Behavior

当前设备已验证多张 PNG 能够轮流显示。轮播只记录已观察到的结果，不推断具体顺序、切换算法或所有格式的兼容性。

## Upload with FileSync

计划使用 FileSync 将 PNG 上传到 `/mnt/us/screensavers`。

**Status:** 🟡 To Verify

FileSync 已验证可以上传 EPUB，但上传屏保 PNG 后是否能直接进入当前轮播尚未正式测试，因此不能标记为 `✅ Verified`。

## Troubleshooting

如果仍显示原生屏保或图片不参与轮播，请检查：

1. Custom Screensaver 是否已经在 Kindle 中启用。
2. 路径是否为 `/mnt/us/screensavers`。
3. 图片是否为 PNG。
4. 文件名是否使用简单 ASCII 名称。

更多记录见 [troubleshooting.md](troubleshooting.md)。
