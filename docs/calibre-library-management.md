# Calibre + KOReader 书库管理方案

本文记录 Windows 端 Calibre 总书库、KOReader 阅读端、FileSync 临时传输通道之间的长期分工，以及 2026-09-23 在 KT6 上完成的端到端验证结果。

## 1. Calibre 的作用

Calibre 是电脑端总书库和后台管理工具，负责：

- 保存电子书副本
- 管理书名、作者、封面、出版社、简介和系列
- 维护多维分类与标签
- 批量编辑、搜索和筛选
- 向 Kindle 发送经过整理的书籍

KOReader 继续负责阅读进度、阅读统计、Calendar View、SimpleUI、Collections 和实际阅读体验。Calibre 不重复维护 KOReader 的 `Unread 未读`、`Reading 在读`、`On Hold 搁置`、`Finished 读完` 状态。

## 2. Calibre Library 路径

| Item | Current value |
| --- | --- |
| Calibre version | 9.15.0 |
| Installation method | Calibre 官方 Windows 64-bit MSI |
| Publisher / signer | Kovid Goyal |
| Installation path | `C:\Program Files\Calibre2` |
| Main library | `D:\Calibre Library` |
| Library database | `D:\Calibre Library\metadata.db` |

`D:\Calibre Library` 是唯一正式主书库。不要创建 `Calibre Library 2`、`Calibre Library New` 等平行正式目录。

Calibre 会把导入的电子书复制到主书库，并按作者和书名维护内部目录。不要在文件管理器中手工重命名或移动 Calibre 书库内部的作者、书名目录；应在 Calibre 中编辑元数据，让 Calibre 管理路径。

当前配置和设备信息：

| Item | Verified value |
| --- | --- |
| Kindle model code | KT6 |
| Kindle firmware | 5.19.6 |
| EPUB send target | `Internal Storage\KOReader_Library` |
| Current Kindle EPUB count | 73 |

Calibre 已配置 EPUB 路由到 `KOReader_Library`。该路径已经通过实际发送、设备端路径检查、文件哈希核对和重复文件检查验证。

## 3. 当前书库架构

```text
电脑端长期总书库
D:\Calibre Library
        │
        ├── 元数据、分类、搜索、批量管理
        │
        └── 整理完成后发送 EPUB
                        │
                        ▼
Kindle 阅读端
/mnt/us/KOReader_Library
        │
        ├── KOReader 阅读、进度、统计和 Calendar View
        ├── SimpleUI
        └── KOReader Collections

手机临时通道
手机 ──FileSync──> Kindle
```

FileSync 继续保留，但不作为长期正式书库入口。手机临时传入 Kindle 的书，如果以后需要正式管理，再补录进 Calibre。

Calibre 是长期母库，Kindle 是当前阅读库。Calibre 分类与 KOReader Collections 是两套独立数据，同名标签不会自动同步。

## 4. 分类命名规则

- 所有实际分类值统一使用 `English 中文`。
- 不使用 `Mystery = 悬疑` 作为值；实际值应为 `Mystery 悬疑`。
- 字段名可以使用英文。
- 不同维度分列维护，一本书可以在同一字段拥有多个值。
- 候选值只在真正有书需要时创建，不预先填满所有候选项。
- 网络元数据只作参考，不能自动成为最终分类。
- 不根据书名、作者国籍或简介自动写入分类；任何建议分类都必须人工确认。

## 5. 自定义字段设计

以下字段已经创建。全部采用 Calibre 的 `text` + `is_multiple`，即“逗号分隔、像 Tags 一样显示在 Tag Browser”的多值文本类型。

| Lookup name | Heading | Type | Multiple values | Purpose |
| --- | --- | --- | --- | --- |
| `#origin` | Origin | Text, tag-like | Yes | 文学来源、国家、地区或文学语境 |
| `#genre` | Genre | Text, tag-like | Yes | 传统小说、类型小说、文学小说及网络文学总入口 |
| `#webgenre` | Web Genre | Text, tag-like | Yes | 网络文学细分类 |
| `#nonfiction` | Nonfiction | Text, tag-like | Yes | 非虚构学科和主题分类 |
| `#theme` | Theme | Text, tag-like | Yes | 跨类型主题 |
| `#form` | Form | Text, tag-like | Yes | 文本形式 |
| `#readinguse` | Reading Use | Text, tag-like | Yes | 阅读用途，不是阅读状态 |

Calibre 自带 `Series` 和 `Rating` 继续保留，不创建重复自定义列。

## 6. Origin

来源明确时优先使用具体地区，不只使用宽泛的 `World Lit 世界文学`。

- `Chinese Lit 中国文学`
- `Japanese Lit 日本文学`
- `Korean Lit 韩国文学`
- `British Lit 英国文学`
- `American Lit 美国文学`
- `French Lit 法国文学`
- `German Lit 德语文学`
- `Russian Lit 俄罗斯文学`
- `European Lit 欧洲文学`
- `Latin American Lit 拉丁美洲文学`
- `African Lit 非洲文学`
- `Southeast Asian Lit 东南亚文学`
- `Other World Lit 其他世界文学`
- `World Lit 世界文学`

## 7. Genre

- `Literary Fiction 文学小说`
- `Mystery 悬疑`
- `Detective 推理`
- `Crime 犯罪`
- `Thriller 惊悚`
- `Horror 恐怖`
- `Sci-Fi 科幻`
- `Fantasy 奇幻`
- `Romance 爱情小说`
- `Historical Fiction 历史小说`
- `Coming-of-Age 成长小说`
- `Family Saga 家族小说`
- `Social Fiction 社会题材小说`
- `Campus 校园小说`
- `Workplace 职场小说`
- `Domestic Fiction 家庭小说`
- `Speculative Fiction 思辨小说`
- `Dystopian 反乌托邦`
- `Magical Realism 魔幻现实主义`
- `Adventure 冒险小说`
- `Satire 讽刺小说`
- `Web Fiction 网络文学`

`Web Fiction 网络文学` 是网络文学总入口；具体细类放在 `#webgenre`，不全部塞进 Genre。

## 8. Web Genre

- `Infinite Flow 无限流`
- `Quick Transmigration 快穿`
- `Transmigration 穿越`
- `Rebirth 重生`
- `System 系统文`
- `Apocalypse 末世`
- `Survival 生存`
- `Farming 种田文`
- `Cultivation 修仙`
- `Xianxia 仙侠`
- `Xuanhuan 玄幻`
- `Wuxia 武侠`
- `Urban 都市`
- `Modern Romance 现言`
- `Historical Romance 古言`
- `Fantasy Romance 幻言`
- `Palace 宫廷`
- `Court Politics 朝堂`
- `Suspense Web Fiction 悬疑网文`
- `Unlimited Horror 无限恐怖`
- `Game 游戏`
- `Esports 电竞`
- `Entertainment 娱乐圈`
- `Workplace Web Fiction 职场网文`
- `Slice of Life 生活流`
- `Sweet Romance 甜文`
- `Angst 虐文`
- `Strong Female Lead 大女主`
- `Female Protagonist 女主视角`
- `Male Protagonist 男主视角`
- `Multiple Protagonists 群像`
- `Interstellar 星际`
- `Mecha 机甲`
- `Dungeon 副本流`
- `Livestream 直播文`
- `Food 美食文`
- `Business 经商文`
- `Infrastructure 基建文`
- `Era Fiction 年代文`
- `Rural Fiction 乡村文`
- `Supernatural 灵异`
- `Rules Horror 规则怪谈`

## 9. Nonfiction

- `Philosophy 哲学`
- `Psychology 心理学`
- `Sociology 社会学`
- `History 历史`
- `Politics 政治`
- `Economics 经济`
- `Anthropology 人类学`
- `Biography 传记`
- `Memoir 回忆录`
- `Essays 随笔`
- `Narrative Nonfiction 叙事非虚构`
- `Science 科普`
- `Technology 科技`
- `Education 教育`
- `Career 职业`
- `Self Development 自我成长`
- `Media 媒体研究`
- `Cultural Studies 文化研究`
- `Literary Criticism 文学评论`
- `Social Issues 社会议题`
- `Gender Studies 性别研究`
- `Feminist Theory 女性主义理论`
- `True Crime 真实犯罪`
- `Travel 旅行`
- `Art 艺术`
- `Film 电影`
- `Writing 写作`

## 10. Theme

- `Women 女性`
- `Feminism 女性主义`
- `Gender 性别议题`
- `Family 家庭`
- `Relationships 关系`
- `Love 爱情`
- `Friendship 友情`
- `Motherhood 母职`
- `Fatherhood 父职`
- `Growing Up 成长`
- `Identity 身份认同`
- `Trauma 创伤`
- `Mental Health 心理健康`
- `Society 社会`
- `Class 阶层`
- `Work 工作`
- `Education 教育`
- `Death 死亡`
- `Loneliness 孤独`
- `Youth 青春`
- `Marriage 婚姻`
- `Crime 犯罪议题`
- `Power 权力`
- `Freedom 自由`
- `Body 身体`
- `Memory 记忆`
- `Grief 哀伤`
- `Violence 暴力`
- `War 战争`
- `Poverty 贫困`
- `Family Conflict 家庭冲突`
- `Female Friendship 女性友谊`

## 11. Form

- `Novel 小说`
- `Novella 中篇小说`
- `Short Stories 短篇小说集`
- `Essays 随笔集`
- `Nonfiction 非虚构`
- `Biography 传记`
- `Memoir 回忆录`
- `Poetry 诗歌`
- `Comics 漫画`
- `Manga 日漫`
- `Web Novel 网络小说`
- `Reference 工具书`
- `Academic 学术`
- `Anthology 选集`
- `Diary 日记`
- `Letters 书信`

## 12. Reading Use

这些值只描述阅读用途，不复制 KOReader 阅读状态。

- `Easy Read 轻松读`
- `Deep Read 深度读`
- `Reread 重读`
- `Reference 参考`
- `Study 学习`
- `Casual 随便看看`
- `Research 研究`
- `Comfort Read 治愈阅读`
- `Challenge 挑战阅读`

## 13. Series

系列名使用 Calibre 自带 `Series` 字段，例如“哈利·波特”“那不勒斯四部曲”“三体”。不要把系列名混进 Genre、Theme 或 Tags。

## 14. Rating

保留 Calibre 自带 `Rating`。不自动评分，后续由用户手工填写。

## 15. Calibre → KOReader Collections 工作流

### 已验证的 EPUB 发送路径

- Kindle：KT6，Firmware 5.19.6。
- Calibre：9.15.0。
- Calibre Library：`D:\Calibre Library`。
- Calibre 已配置 EPUB 路由到 `KOReader_Library`。
- 实际发送目标：`Internal Storage\KOReader_Library`，对应 Kindle 路径 `/mnt/us/KOReader_Library`。
- 发送后以设备端真实路径和文件哈希为准，不只依赖 Calibre 设置推测结果。

### 当前 8 个 KOReader Collections

- `Literary Fiction 文学小说`
- `Mystery & Crime 悬疑 / 犯罪`
- `Sci-Fi & Fantasy 科幻 / 奇幻`
- `Infinite Flow & Game 无限流 / 游戏`
- `Apocalypse & Survival 末世 / 生存`
- `Women 女性`
- `Society & Family 社会 / 家庭`
- `Nonfiction 非虚构`

### 数据边界

- Calibre 分类保存在 Calibre 主书库数据库中。
- KOReader Collection 成员关系保存在 `koreader/settings/collection.lua`。
- `.sdr` 保存书籍阅读状态和 sidecar 数据。
- Calibre 分类和 KOReader Collections 是两套独立数据；即使名称相同，也不会自动同步。
- 当前没有安装自动 Collections patch 或 Calibre 插件。

### 当前采用的增量方法

1. 在 Calibre 中完成元数据和双语分类。
2. 只发送已确认的新 EPUB，并检查目标路径和重复文件。
3. 完全退出 KOReader。
4. 备份当前 `collection.lua`。
5. 只向现有 Collection 追加新书的真实路径，不删除或重建旧成员。
6. 写入后重新读取并验证成员数量、路径存在性、重复项和 Lua 结构。
7. 同时确认 `.sdr`、Reading Statistics 和其他 KOReader 设置未变化。

稳定性优先，当前不使用未经设备验证的自动同步 patch。

## 16. 手机 FileSync 的定位

批量新书的正式整理流程：

```text
EPUB → Calibre → 整理元数据与分类 → 发送到 KOReader_Library → 增量更新 KOReader Collections
```

少量新书的临时快速阅读流程：

```text
手机 / FileSync → Kindle → KOReader 手动加入 Collection
```

FileSync 的价值是快速临时传输；Calibre 的价值是长期、可搜索、可恢复的总书库。临时传入的书以后需要正式管理时，再导入 Calibre。

## 17. 安全迁移流程

后续每批迁移继续遵守以下规则：

1. 先在 Calibre 中查重，避免向 Kindle 发送已有书或完全重复版本。
2. 发送前确认 EPUB 路由仍指向 `KOReader_Library`。
3. 不处理正在阅读的重要书，不覆盖对应 `.sdr`。
4. 发送后核对真实文件路径、文件数量和重复副本。
5. 更新 Collections 前完全退出 KOReader，并备份 `collection.lua`。
6. 只对本批新书追加成员关系，不重建全部 Collections。
7. 写入后确认 Reading Statistics、`.sdr`、WeRead、SimpleUI 和其他 EPUB 未变化。

## 18. 测试流程

2026-09-23 已完成以下验证：

1. 9 本新书成功导入 `D:\Calibre Library`。
2. 元数据和七个自定义分类字段可以正常维护，多值字段可以搜索和筛选。
3. 首本路径测试发现默认发送位置为 `Internal Storage\documents`。
4. Calibre EPUB 路由随后配置为 `KOReader_Library`。
5. 首本重新发送后确认位于 `Internal Storage\KOReader_Library`，错误路径测试副本已清理。
6. 剩余 8 本使用相同路由发送成功，最终 9 本均位于 `KOReader_Library`。
7. 所有设备副本均与 Calibre 源 EPUB 完成哈希核对。
8. 没有产生重复副本，当前 Kindle EPUB 总数为 73。
9. 9 本书共完成 21 条 KOReader Collection 成员关系增量更新。
10. 更新前已备份 `collection.lua`，更新后确认原有成员、`favorites`、`weread` 和 `To Be Read` 均保留。
11. Reading Statistics、`.sdr`、其他 EPUB 和其他 KOReader 设置均未修改。

示例分类：

| Example | Origin | Genre | Web Genre | Theme | Form |
| --- | --- | --- | --- | --- | --- |
| 普通文学书 | `Japanese Lit 日本文学` | `Literary Fiction 文学小说` | — | `Family 家庭, Women 女性` | `Novel 小说` |
| 悬疑小说 | `Chinese Lit 中国文学` | `Mystery 悬疑, Detective 推理` | — | `Women 女性` | `Novel 小说` |
| 网络文学 | — | `Web Fiction 网络文学` | `Infinite Flow 无限流, Survival 生存` | `Female Protagonist 女主视角` | `Web Novel 网络小说` |

## 19. 风险

- Calibre 自动获取的 Tags、Subjects、Genres 和 Metadata 可能不符合个人体系。
- 把已有 Kindle 书重新发送回设备可能产生路径变化或重复文件。
- Calibre 分类不会自动变成 KOReader Collections；跳过增量核对可能造成缺项或错误成员关系。
- 自动 Collections patch 会写 KOReader Collections，名称冲突可能影响现有书单。
- 任何涉及 sidecar 的同步工具都可能影响 `.sdr`、阅读进度或批注；本阶段不安装。
- Calibre 书库内部文件由 Calibre 管理，手工移动或重命名可能破坏数据库与文件的对应关系。
- 只备份 `metadata.db` 不足以恢复完整书库；应备份整个 `D:\Calibre Library`。

## 20. 回滚方法

### Windows / Calibre

1. 在重大批量操作前关闭 Calibre。
2. 备份整个 `D:\Calibre Library`，包括所有子目录和 `metadata.db`。
3. 保留原始 EPUB，确认 Calibre 副本正常前不删除源文件。
4. 出现问题时停止继续导入，不自动清理；先检查差异，再决定是否恢复完整书库备份。

### Kindle / KOReader

1. 设备备份统一放在 `D:\Kindle Backup`。
2. 该目录只作为本地私密备份，不进入 Git。
3. 设备测试前备份书籍、`.sdr`、Reading Statistics 和 Collections。
4. 修改 Collections 前至少单独备份 `koreader/settings/collection.lua`。
5. 只操作当前批次，不触碰正在阅读的重要书。
6. 出现异常时停止同步，不批量覆盖或删除。
7. 经人工确认后，使用操作前备份恢复受影响数据。

2026-09-23 的 Collection 增量更新前备份保存在本地 Kindle Backup 目录中；仓库只记录策略和结果，不保存实际备份文件。

## 21. 后续正式迁移步骤

1. 扫描指定来源中的新 EPUB，并与 Calibre 主书库查重。
2. 只导入确认需要保留的新书或不同版本。
3. 在 Calibre 中整理元数据、封面和双语分类。
4. 保持 Reading Use 默认留空，除非人工明确指定。
5. 连接 Kindle 后确认 EPUB 路由仍为 `KOReader_Library`。
6. 分批发送并核对设备端路径、文件哈希、总数和重复副本。
7. 完全退出 KOReader，备份 `collection.lua`。
8. 只为本批新书增量追加 Collection 成员关系。
9. 验证原有成员、`.sdr`、Reading Statistics 和其他设置未变化。
10. 安全弹出 Kindle，进入 KOReader 检查显示结果。

## 22. 《漂亮炮灰[无限]（精排版）》分类修正

该书不属于：

- `Horror 恐怖`
- `Unlimited Horror 无限恐怖`

当前保留的 Calibre 分类：

- Genre：`Web Fiction 网络文学`
- Web Genre：`Infinite Flow 无限流`
- Web Genre：`Dungeon 副本流`

对应 Kindle Collection：

- `Infinite Flow & Game 无限流 / 游戏`

不要将该书加入 `Mystery & Crime 悬疑 / 犯罪` 或 `Sci-Fi & Fantasy 科幻 / 奇幻`。

## 23. 仓库安全边界

以下内容绝对不进入 Git：

- `D:\Kindle Backup`
- `D:\Calibre Library`
- EPUB 文件
- `.sdr` 目录或文件
- `collection.lua` 实际副本
- `statistics.sqlite3`
- `settings.reader.lua`
- `weread.lua`
- WeRead cache
- Cookie、Token、API Key 和账号信息

本仓库只保存公开安全的配置说明、验证结果、路径约定和恢复策略。

## References

- [Calibre Windows download](https://calibre-ebook.com/download_windows64)
- [Calibre custom columns CLI](https://manual.calibre-ebook.com/generated/en/calibredb.html)
- [Calibre library FAQ](https://manual.calibre-ebook.com/faq.html)
- [KOReader Calibre metadata module](https://github.com/koreader/koreader/blob/master/plugins/calibre.koplugin/metadata.lua)
- [KOReader Calibre metadata documentation](https://koreader.rocks/doc/modules/koplugin.calibre.metadata.html)
- [Community Calibre Collections user patch](https://github.com/SinTan1729/koreader-patches/blob/main/2-calibre-collections.lua)
- [KOReader Sync Calibre plugin](https://github.com/kyxap/koreader-calibre-plugin)
