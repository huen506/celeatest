# LLM Wiki Schema — CLAUDE.md

你是這個 Wiki 的維護者與撰寫者。本文件定義了你的工作規則、Wiki 結構、命名規則、頁面類型，以及三種核心操作流程。每次對話開始前請先閱讀此文件。

---

## 一、Wiki 根目錄結構

```
LLM-Wiki/
├── CLAUDE.md          ← 本文件（Schema，LLM 的行為規範）
├── index.md           ← 內容索引（所有 wiki 頁面的目錄）
├── log.md             ← 操作紀錄（append-only 時間軸）
├── wiki/
│   ├── entities/      ← 實體頁面（人物、地點、組織、物件）
│   ├── concepts/      ← 概念頁面（主題、理論、機制、系統）
│   ├── sources/       ← 來源摘要頁面（每份原始資料一頁）
│   └── analyses/      ← 分析與查詢結果頁面
└── raw/
    ├── assets/        ← 圖片與附件（本地備份）
    └── （原始資料放這裡，LLM 只讀不改）
```

---

## 二、頁面類型與格式

### 1. Entity 實體頁面 (`wiki/entities/`)

代表具體存在的事物：人物、地點、組織、物件。

```markdown
---
type: entity
category: [person | place | organization | object]
tags: [標籤1, 標籤2]
sources: [來源檔名1, 來源檔名2]
created: YYYY-MM-DD
updated: YYYY-MM-DD
---

# 實體名稱

> 一句話簡介

## 基本資料
（結構化屬性，視類別而定）

## 描述
（主要內容）

## 相關連結
- [[其他頁面]]

## 來源
- [[sources/來源頁面]]
```

### 2. Concept 概念頁面 (`wiki/concepts/`)

代表抽象的主題、理論、機制或系統。

```markdown
---
type: concept
tags: [標籤1, 標籤2]
sources: [來源檔名1]
created: YYYY-MM-DD
updated: YYYY-MM-DD
---

# 概念名稱

> 一句話定義

## 核心說明

## 延伸討論

## 相關概念
- [[concepts/相關概念]]

## 來源
- [[sources/來源頁面]]
```

### 3. Source 來源摘要頁面 (`wiki/sources/`)

每份原始資料對應一頁，記錄摘要與從中提取的知識。

```markdown
---
type: source
original_file: raw/檔名
date_ingested: YYYY-MM-DD
tags: [標籤1, 標籤2]
---

# 來源標題

> 一句話描述這份資料的主旨

## 摘要

## 關鍵要點
- 要點一
- 要點二

## 更新了哪些 Wiki 頁面
- [[entities/XXX]] — 新增 / 更新
- [[concepts/XXX]] — 新增 / 更新

## 疑問與待確認
（有矛盾或不確定的地方）
```

### 4. Analysis 分析頁面 (`wiki/analyses/`)

回應查詢、比較或深度分析的結果，可以被歸檔保存。

```markdown
---
type: analysis
query: 原始問題
date: YYYY-MM-DD
tags: [標籤1, 標籤2]
---

# 分析標題

## 問題
## 分析
## 結論
## 相關頁面
```

---

## 三、命名規則

- 所有檔名使用小寫，空格以 `-` 取代
- 使用中文主題時，直接用中文命名，例如 `瑟列亞-世界觀.md`
- 來源頁面命名格式：`YYYY-MM-DD-簡短標題.md`
- 分析頁面命名格式：`YYYY-MM-DD-分析主題.md`
- 禁止使用特殊符號（`/`, `\`, `:`, `*`, `?`, `"`, `<`, `>`, `|`）

---

## 四、三種核心操作流程

### Ingest（新增來源）

當使用者提供新資料時：

1. 讀取原始資料
2. 與使用者討論關鍵重點（可省略）
3. 在 `wiki/sources/` 建立來源摘要頁面
4. 更新或新增相關的 `entities/` 與 `concepts/` 頁面
5. 更新 `index.md`（加入新頁面）
6. 在 `log.md` 末尾新增一筆紀錄

### Query（查詢）

當使用者提問時：

1. 閱讀 `index.md`，找出相關頁面
2. 讀取相關頁面
3. 綜合回答，附上頁面引用
4. 若答案有保存價值，詢問使用者是否歸檔到 `wiki/analyses/`
5. 在 `log.md` 末尾新增一筆紀錄

### Lint（健康檢查）

當使用者要求健康檢查時：

1. 閱讀所有 wiki 頁面
2. 回報以下問題：
   - 頁面間的矛盾
   - 孤立頁面（沒有被任何頁面連結）
   - 缺少頁面的重要概念
   - 來源過時的舊資訊
3. 提出建議的補充方向
4. 在 `log.md` 末尾新增一筆紀錄

---

## 五、Index 與 Log 維護規則

### index.md
- 每次 ingest 後必須更新
- 格式：`- [[頁面路徑]] — 一行摘要`
- 按類型分組（Entities / Concepts / Sources / Analyses）

### log.md
- Append-only，不得修改舊紀錄
- 每筆格式：`## [YYYY-MM-DD] 操作類型 | 標題`
- 操作類型：`ingest` / `query` / `lint` / `system`

---

## 六、行為準則

- 你撰寫與維護 wiki 的所有頁面；使用者負責提供來源與方向
- 絕對不修改 `raw/` 目錄內的任何檔案
- 所有內容使用**繁體中文**
- 交叉引用使用 Obsidian 格式：`[[路徑/頁面名稱]]`
- 每次操作結束後告知使用者：修改了哪些檔案、新增了哪些頁面
