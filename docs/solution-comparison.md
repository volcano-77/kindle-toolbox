# Kindle 阅读方案历史决策记录

> 本文保留选型阶段的关键考虑。技术选型已经完成，当前实际配置请查看 [current-setup.md](current-setup.md)。

## 当时的目标

- 本地资源和离线阅读优先
- 需要阅读时间与日历统计
- 希望查看微信读书书架、书评、划线和想法
- 尽量减少对会员和持续联网的依赖
- 改善界面与文件管理体验

## 方案结果

| 方案 | 决策状态 | 当前结论 |
| --- | --- | --- |
| 原生 Kindle | ❌ Not Used | 未作为完整阅读方案采用；原生系统仍保留并可正常使用 |
| 原生 Kindle + Calibre | ⚪ Optional | 可继续作为书库整理或格式转换工具，但不是当前设备端核心方案 |
| Véra + KOReader | ✅ Verified | 已在 KT6 + 5.19.6 上完成越狱，KOReader 可正常运行 |
| KOReader + WeRead plugin | ✅ Verified | 已登录、打开书架和书籍、下载完整章节并生成本地 EPUB |
| 主要依赖微信读书 | ❌ Not Used | 当前采用本地书库与缓存离线阅读并行的方式 |

## 已验证的实际结果

- KOReader 可以阅读 EPUB/PDF，并使用 `/mnt/us/KOReader_Library` 作为主要书库根目录。
- KOReader Reading Statistics 可以记录阅读时间、阅读历史、Calendar View 和每日阅读记录。
- WeRead 插件可以下载完整章节、生成本地 EPUB，并离线阅读已缓存书籍。
- FileSync 可以从同一 Wi-Fi 下的手机浏览器向 Kindle 无线上传 EPUB。
- SimpleUI 可以替代默认文件浏览器式首页，提供 KOReader 主页体验。
- Custom Screensaver 可以显示并轮播 PNG 图片。

## 决策边界

- 上述 `✅ Verified` 只代表当前 Kindle 11th Generation（2024 Release，KT6）和固件 5.19.6 的实测结果。
- 越狱和第三方插件仍有维护与恢复风险，不能据此推断其他型号或固件同样可用。
- 第三方项目的实际版本仍需单独记录；无法从仓库确认的版本不作猜测。
