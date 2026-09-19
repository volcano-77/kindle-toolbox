# Kindle 越狱兼容性记录

## 1. Device

- Device model: Kindle 11th Generation, 2024 Release
- KindleModding device code: KT6
- Firmware: 5.19.6

## 2. Current Compatibility Status

**KT6 + 5.19.6 已确认获得 Véra 支持**，并且已有 Kindle 11th Generation（2024 Release，KT6）成功使用 Véra 越狱并运行 KOReader 的实际案例。

这说明该组合已有明确支持和成功实践，但越狱仍然不是零风险。当前策略仍是暂不执行任何越狱操作，先完成风险与恢复能力评估。

## 3. What Is Confirmed

- Véra 已确认支持 KT6 + 5.19.6。
- 已存在 KT6 2024 成功使用 Véra 越狱并运行 KOReader 的实际案例。
- KindleModding 的 KPM 工具链包含针对 KT6 新固件环境的兼容处理。
- 未越狱 Kindle 不能通过先降级来获取旧版越狱。
- 越狱的作用是让 Kindle 能够运行外部代码，例如 KOReader；它不等于更换整个操作系统。
- 当前应继续保持飞行模式，避免设备自动升级。

## 4. What Is Not Yet Confirmed

- 越狱仍然不是零风险，个体设备上的实际执行结果不能仅凭支持状态或成功案例保证。
- 其他新 Kindle 型号曾出现触控异常、启动循环、KOReader 异常等问题。这些问题不能直接推断 KT6 必然出现，但应作为风险参考。
- 新 Kindle 的恢复能力不如老型号，不能简单依赖传统分区备份恢复；具体恢复与失败处理边界仍需评估。
- 真正执行前，仍需确认当时的 Véra 官方向导继续识别 KT6 + 5.19.6，并复核最新风险信息。

## 5. Current Action

- 继续保持飞行模式，避免自动升级。
- 阅读恢复和失败处理文档，明确出现问题时的处理边界。
- 真正执行前再次确认 Véra 官方向导仍识别 **KT6 + 5.19.6**。
- 当前暂不执行任何越狱操作。

## 6. Sources

- KindleModding Véra
- KindleModding Firmware Downloads
- KindleModding Jailbreak FAQ
- KindleModding Downgrading Guide
- KindleModding Jailbreaking Overview
