# 操作紀錄

> Append-only。不得修改舊紀錄。
> 格式：`## [YYYY-MM-DD] 操作類型 | 標題`

---

## [2026-04-11] system | Wiki 系統初始化

- 建立資料夾結構：`wiki/entities/`, `wiki/concepts/`, `wiki/sources/`, `wiki/analyses/`, `raw/assets/`
- 建立 `CLAUDE.md`（Schema）
- 建立 `index.md`（內容索引）
- 建立 `log.md`（本文件）
- Wiki 系統就緒，等待第一次 ingest

## [2026-04-11] ingest | Celēa 專案共同原則文件 v1.0

- 來源：`raw/Celēa_專案共同原則.docx`
- 新增 source 頁面：`wiki/sources/2026-04-11-Celēa專案共同原則.md`
- 新增 entity 頁面：`wiki/entities/德拉文・沃恩.md`
- 新增 entity 頁面：`wiki/entities/希洛葳.md`
- 新增 concept 頁面：`wiki/concepts/能量體系.md`
- 新增 concept 頁面：`wiki/concepts/兩大勢力.md`
- 更新 `index.md`

## [2026-04-11] ingest | 批量 ingest — 剩餘 8 份文件

來源：
- `raw/Celēa_demo前傳_世界觀.docx`
- `raw/Celēa_demo前傳_劇情骨架.docx`
- `raw/城鎮_希洛葳_設定文件.docx`
- `raw/角色_德拉文・沃恩角色資料卡.docx`
- `raw/角色_米蕾爾・艾許沃恩角色資料卡.docx`
- `raw/角色_莉歐拉・哈爾特角色資料卡.docx`
- `raw/角色_西芙角色資料卡.docx`
- `raw/角色_維若妮卡・海耶_角色資料卡.docx`

新增 source 頁面（8）：
- `wiki/sources/2026-04-11-Celēa_demo前傳_世界觀.md`
- `wiki/sources/2026-04-11-Celēa_demo前傳_劇情骨架.md`
- `wiki/sources/2026-04-11-城鎮_希洛葳_設定文件.md`
- `wiki/sources/2026-04-11-角色_德拉文・沃恩.md`
- `wiki/sources/2026-04-11-角色_米蕾爾・艾許沃恩.md`
- `wiki/sources/2026-04-11-角色_莉歐拉・哈爾特.md`
- `wiki/sources/2026-04-11-角色_西芙.md`
- `wiki/sources/2026-04-11-角色_維若妮卡・海耶.md`

新增 entity 頁面（5）：
- `wiki/entities/米蕾爾・艾許沃恩.md`
- `wiki/entities/莉歐拉・哈爾特.md`
- `wiki/entities/西芙.md`
- `wiki/entities/維若妮卡・海耶.md`
- `wiki/entities/蕾姆娜・貝拉.md`
- `wiki/entities/眠角樹.md`

新增 concept 頁面（2）：
- `wiki/concepts/核刻技術體系.md`
- `wiki/concepts/三條主線.md`

更新既有頁面（4）：
- `wiki/entities/德拉文・沃恩.md` — 補充性格、行動邏輯、底線
- `wiki/entities/希洛葳.md` — 補充空間結構、腐敗細節、關鍵地點
- `index.md` — 全面更新
