# Moon v0.4.6 分类迁移边界

截至 2026-10-30，Moon v0.4.6 已在 KT6 的 KOReader v2026.07.1 中识别 73 本本地 EPUB；用户在设备上抽查了原阅读进度。插件目录的 653 个文件、106 个子目录已通过 Windows WPD `STGM_READ` 全量 SHA-256 校验。**73 本书被识别不代表 KOReader Collections 已导入 Moon。**

## 原始数据核对

只读解析 MTP 备份里的 `koreader/settings/collection.lua`，并将 `KOReader_Library` 的 73 个 EPUB 与 Calibre `metadata.db` 的 EPUB 记录按文件 SHA-256 核对。Calibre 有 78 条 EPUB 记录；设备的 73 本都能唯一匹配到其中一条，没有同哈希歧义。73 本在 Calibre 中均有至少一个自定义分类值，但 Calibre 的七个多值字段与 KOReader Collections 是不同的数据源，不自动同步；同名或近义标签也不能直接当作已确认的集合成员关系。

| KOReader Collection | 备份成员数 | 对应 73 本设备书库 |
| --- | ---: | ---: |
| Literary Fiction 文学小说 | 29 | 29 |
| Mystery & Crime 悬疑 / 犯罪 | 15 | 15 |
| Sci-Fi & Fantasy 科幻 / 奇幻 | 9 | 9 |
| Infinite Flow & Game 无限流 / 游戏 | 16 | 16 |
| Apocalypse & Survival 末世 / 生存 | 8 | 8 |
| Women 女性 | 19 | 19 |
| Society & Family 社会 / 家庭 | 37 | 37 |
| Nonfiction 非虚构 | 6 | 6 |

八个集合合计 **139 条成员关系**，覆盖 66 本不同的书：19 本只属于一个集合，47 本属于多个集合，另有 7 本不在这八个集合中。备份文件还有 `To Be Read`、`favorites`、`weread`，它们未被当作这八个主题分类，也没有被修改。

逐书路径、书名、Calibre ID、哈希和分类映射仅保存在 Windows 本地私密分析目录，不纳入本仓库。

## 分类为何没有出现在 Moon

Moon v0.4.6 的本地扫描在默认“按文件夹分类”模式下，以书库根目录的第一层文件夹生成 `category`，第二层生成 `series`。备份里的 73 本 EPUB 全部直接位于 `KOReader_Library` 根目录；同级的 `.sdr` 边车目录被扫描器跳过。原八个 Collections 是 `collection.lua` 中的逻辑成员关系，Moon 不读取该文件。因此分类页没有自动还原原有集合。

Moon 的书库位于 KOReader 数据目录下的 `.moon/book.sqlite3`，`books` 表用一个 `category TEXT` 字段存放每本书的分类，界面按该字段的**完整值**分组。它没有与 KOReader Collections 等价的多对多成员表；把多个集合名拼成一个字符串只会形成一个新分类。源码依据：`source/local/common.lua` 的目录扫描、`source/local/setting.lua` 的开关、`source/local/scan.lua` 的编辑路径、`book/books_db.lua` 的表定义与 `countsBy` 查询。

## 可以保留什么，不能自动迁移什么

关闭 Moon 的“按文件夹分类”后，v0.4.6 的本地书编辑路径只更新 Moon 书库字段，不移动 EPUB，也不改 `.sdr`。但该开关会先清空 Moon 本地源现有 `category` 和 `series`；必须先备份当前 Moon 数据库并确认状态。此模式可以给**单分类**书设置一个分类，但不能让 47 本多集合书同时出现在各自原有的多个分类里。无法在不改 Moon 源码或不重新选择分类的前提下，把八个 KOReader Collections **无损迁移为 Moon 的分类页**。

因此本轮没有生成会写入 Moon 数据库的迁移脚本，也没有对 47 本重叠书自动指定“主分类”。既有 KOReader Collections、Calibre 多值分类与 EPUB 路径应继续作为完整分类基线；不要为了 Moon 分类移动 EPUB 或 `.sdr`。

## 下次连接设备时

1. 保持 KOReader 退出，通过 MTP 只读核对并单独备份最新的 `collection.lua`、Moon `.moon/book.sqlite3` 及相关设置；核对数据库实际路径和 SQLite 完整性。原始备份与正式 Calibre `metadata.db` 保持不变。
2. 在数据库副本上核对 Moon 本地源的 73 个 `stable_id` 是否仍对应原 EPUB 路径，并确认 `folder_category` 当前值。不要直接用旧备份覆盖新进度。
3. 保留八个多标签集合在 KOReader/Calibre 中。若以后愿意接受 Moon 每书仅显示一个分类，再由人工确定 47 本重叠书的取舍，先在数据库副本模拟、逐项核对，再考虑单独授权设备修改。

当前未从设备读取安装后的 Moon 数据库，因此尚未验证任何实际 Moon 数据库写入或分类恢复结果。
