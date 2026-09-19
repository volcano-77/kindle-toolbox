# Kindle 越狱验证与兼容性记录

## 1. Device

- Device model: Kindle 11th Generation, 2024 Release
- KindleModding device code: KT6
- Firmware: 5.19.6

## 2. Current Compatibility Status

**✅ Verified：当前这台 KT6 + 5.19.6 已使用 Véra 成功完成越狱。**

越狱后 Kindle 原生系统仍可正常启动，KOReader、KPM、自定义屏保和第三方 KOReader 插件均可运行。该结果只适用于当前实测设备，不扩大为对所有 KT6 或其他设备的兼容性保证。

## 3. What Is Confirmed

- Véra 已确认支持 KT6 + 5.19.6。
- 当前 KT6 2024 设备已经实际使用 Véra 越狱成功。
- KindleModding 的 KPM 工具链包含针对 KT6 新固件环境的兼容处理。
- Kindle 原生系统在越狱后可正常启动。
- KOReader 可正常启动并阅读 EPUB/PDF。
- KPM 插件、自定义屏保和第三方 KOReader 插件可正常使用。
- 未越狱 Kindle 不能通过先降级来获取旧版越狱。
- 越狱的作用是让 Kindle 能够运行外部代码，例如 KOReader；它不等于更换整个操作系统。

## 4. Risk Boundary

- 越狱仍然不是零风险，单台设备上的成功不能保证其他设备获得相同结果。
- 其他新 Kindle 型号曾出现触控异常、启动循环、KOReader 异常等问题。这些问题不能直接推断 KT6 必然出现，但应作为风险参考。
- 新 Kindle 的恢复能力不如老型号，不能简单依赖传统分区备份恢复。
- 未来重新部署、恢复或升级前，仍需重新核对当时的兼容性、恢复文档和失败处理边界。

## 5. Maintenance Notes

- 不在本文重复完整越狱教程或提供可直接执行的命令。
- 固件升级前先检查 Véra、KPM、KOReader 和已安装插件的兼容性。
- 重新部署前再次确认官方或社区向导仍明确识别 **KT6 + 5.19.6**。
- 先阅读最新恢复和失败处理文档，再决定是否进行系统级操作。
- 不把未知来源文件复制到 Kindle。

## 6. Sources

- Current KT6 device verification record
- KindleModding Véra
- KindleModding Firmware Downloads
- KindleModding Jailbreak FAQ
- KindleModding Downgrading Guide
- KindleModding Jailbreaking Overview
