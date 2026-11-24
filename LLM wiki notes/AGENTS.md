# LLM Wiki — 論文知識庫

> 這是一個由 LLM 維護的多領域論文知識庫。LLM 負責所有的摘要撰寫、交叉引用、索引維護和知識整合。使用者負責提供來源、參與討論、和引導方向。

## 語言規範

- 所有 Wiki 頁面以**繁體中文**撰寫
- **專有名詞保留英文**（如 Transformer、Attention、RLHF、fine-tuning）
- 論文標題保留原文（通常為英文），可附中文翻譯
- 人名保留英文原名

## 目錄結構

```
LLM wiki notes/
├── AGENTS.md              # 本檔案 — Wiki 規範與工作流程
├── wiki/
│   ├── index.md           # 全局索引（按主題分類列出所有頁面）
│   ├── papers/            # 論文摘要頁
│   │   └── <slug>.md      # 每篇論文一個檔案
│   ├── concepts/          # 概念頁
│   │   └── <concept>.md   # 每個核心概念一個檔案
│   ├── people/            # 人物頁
│   │   └── <person>.md    # 重要作者、實驗室、機構
│   ├── topics/            # 主題總覽頁
│   │   └── <topic>.md     # 子領域綜合整理
│   └── comparisons/       # 比較頁
│       └── <comparison>.md # 不同方法的對比分析
└── raw/                   # 原始來源（僅供參考，LLM 不修改）
    └── ...
```

### 檔案命名規則

- 使用 **英文小寫 + 連字號** 命名：`attention-is-all-you-need.md`
- 論文摘要頁：取論文標題的關鍵詞縮寫，如 `attention-is-all-you-need.md`
- 概念頁：直接用概念名稱，如 `transformer.md`、`rlhf.md`
- 人物頁：用人名，如 `geoffrey-hinton.md`
- 主題總覽頁：用主題名稱，如 `large-language-models.md`
- 比較頁：用描述性名稱，如 `rlhf-vs-dpo.md`

## 頁面模板

### 論文摘要頁 (`wiki/papers/`)

```markdown
---
title: "論文原始標題"
title_zh: "中文翻譯標題"
authors:
  - Author Name 1
  - Author Name 2
year: 2024
venue: "NeurIPS 2024"       # 發表場所（期刊/會議），若為 preprint 則寫 "arXiv preprint"
url: "https://..."          # 原始連結
tags:
  - tag1
  - tag2
date_added: 2026-11-23      # 加入 Wiki 的日期
related_papers: []           # 相關論文的檔名（不含路徑），如 ["attention-is-all-you-need.md"]
related_concepts: []         # 相關概念的檔名，如 ["transformer.md"]
---

# 論文標題

> 一句話摘要：用一句話概括這篇論文的核心。

## 核心貢獻與新穎性

- 這篇論文解決了什麼問題？
- 主要的創新點是什麼？
- 為什麼重要？

## 方法論摘要

- 核心方法/架構描述
- 實驗設計
- 使用的數據集
- 評估指標與方法

## 主要結果與數據

- 關鍵實驗結果（可用表格呈現）
- 與 baseline 的比較
- 最重要的數字和發現

## 與其他論文的關聯

- 引用/建立在哪些前作之上
- 與哪些同期工作相關
- 後續有哪些延伸工作
- 是否反駁或挑戰了先前的結論

## 局限性與未來方向

- 作者自述的局限
- 我觀察到的潛在問題
- 論文提出的未來方向

## 實用性評估

- 這篇論文對實際工作有什麼用？
- 哪些想法可以直接應用？
- 適用場景與限制
```

### 概念頁 (`wiki/concepts/`)

```markdown
---
title: "Concept Name"
aliases: []                  # 別名或縮寫
tags:
  - concept
related_concepts: []
key_papers: []               # 定義或深入探討此概念的論文
---

# 概念名稱（English Name）

## 定義

簡明的概念定義。

## 核心原理

詳細解釋這個概念的運作原理。

## 重要變體與發展

按時間線列出重要的變體和演進。

## 相關論文

列出 Wiki 中探討此概念的論文，附簡短說明。

## 相關概念

列出相關的概念頁連結。
```

### 人物頁 (`wiki/people/`)

```markdown
---
title: "Person / Lab / Institution Name"
type: person | lab | institution
affiliation: "所屬機構"
tags:
  - people
---

# 名稱

## 簡介

一段簡介。

## 主要貢獻

在本 Wiki 涵蓋範圍內的主要貢獻。

## Wiki 中的相關論文

列出此人/機構在 Wiki 中的論文連結。
```

### 主題總覽頁 (`wiki/topics/`)

```markdown
---
title: "Topic Name"
tags:
  - topic
---

# 主題名稱

## 概述

這個子領域的整體介紹。

## 核心概念

列出此主題下的核心概念連結。

## 重要論文

按時間或重要性列出相關論文。

## 發展脈絡

此領域的演進時間線。

## 開放問題

目前尚未解決的問題和研究方向。
```

### 比較頁 (`wiki/comparisons/`)

```markdown
---
title: "Method A vs Method B"
tags:
  - comparison
compared_items: []           # 被比較的論文或概念檔名
---

# 比較標題

## 比較摘要

一段簡要說明為什麼要做這個比較。

## 對比表

| 維度 | Method A | Method B |
|------|----------|----------|
| ...  | ...      | ...      |

## 詳細分析

逐項深入分析。

## 結論

什麼情況下用哪個方法。
```

## 連結與交叉引用規範

- 使用**標準 Markdown 連結**：`[顯示文字](../相對路徑/檔名.md)`
- 所有連結使用**相對路徑**（以當前檔案位置為基準）
- 在頁面末尾或相關段落中加入交叉連結
- 連結文字應具描述性，不要用「點此」之類的文字

### 連結範例

從 `wiki/papers/some-paper.md` 連結到概念頁：
```markdown
本文提出的架構基於 [Transformer](../concepts/transformer.md) 的改進。
```

從 `wiki/concepts/transformer.md` 連結回論文：
```markdown
- [Attention Is All You Need](../papers/attention-is-all-you-need.md) — 提出 Transformer 架構的原始論文
```

## 工作流程

### 1. 論文消化（Ingest）

當使用者提供一個網頁連結時：

1. **讀取**：訪問連結，讀取論文全文內容
2. **討論**：向使用者報告關鍵發現，討論重點與感想
3. **等待確認**：使用者確認後再進行歸檔
4. **建立摘要頁**：在 `wiki/papers/` 建立論文摘要頁，依照模板填寫所有欄位
5. **更新相關頁面**：
   - 檢查是否需要**新建**概念頁、人物頁、主題頁
   - **更新**已存在的相關頁面（新增論文連結、補充資訊）
   - 如果新論文與已有論文存在對比關係，考慮建立比較頁
6. **更新索引**：在 `wiki/index.md` 中新增條目
7. **報告**：向使用者總結所有的變更（新建了哪些頁面、更新了哪些頁面）

### 2. 查詢（Query）

當使用者提出問題時：

1. 先讀取 `wiki/index.md` 找到相關頁面
2. 深入閱讀相關頁面
3. 綜合回答，附上頁面引用
4. 如果回答產生了有價值的分析，建議使用者是否要將其歸檔為新的 Wiki 頁面（比較頁、主題頁等）

### 3. 健康檢查（Lint）

當使用者要求或定期建議進行：

- 檢查頁面之間的交叉引用是否完整
- 找出孤立頁面（沒有任何連結指向它）
- 找出提到但尚未建立的概念
- 檢查是否有矛盾的資訊
- 建議可以深入的方向或缺少的來源

## 索引維護（index.md）

`wiki/index.md` 是全局索引，結構如下：

```markdown
# 📚 LLM Wiki 索引

> 最後更新：YYYY-MM-DD

## 論文 (Papers)

### [主題分類名稱]
- [論文標題](papers/slug.md) — 一句話摘要 (Author, Year)

## 概念 (Concepts)
- [概念名稱](concepts/name.md) — 簡要說明

## 人物與機構 (People & Institutions)
- [人名](people/name.md) — 所屬機構，主要貢獻領域

## 主題總覽 (Topics)
- [主題名稱](topics/name.md) — 簡要說明

## 比較分析 (Comparisons)
- [比較標題](comparisons/name.md) — 簡要說明
```

每次 ingest 完成後必須更新索引。論文在索引中按主題分類排列；當某個分類累積超過 10 篇論文時，考慮建立對應的主題總覽頁。

## 漸進式成長規則

Wiki 從簡單開始，隨著內容增長自動演化：

1. **< 10 篇論文**：只需論文摘要頁 + index.md，概念頁和人物頁按需建立
2. **10-30 篇論文**：開始建立主題總覽頁，整理各子領域的論文群
3. **30+ 篇論文**：主動建議比較頁、尋找跨領域連結、提出知識缺口
4. 當同一概念在 3 篇以上論文中被提及但尚無概念頁時，主動建議建立
5. 當同一作者有 2 篇以上論文在 Wiki 中時，建議建立人物頁

## 重要注意事項

- **不要修改 `raw/` 目錄**中的任何檔案，那是原始來源
- **不要修改本檔案（AGENTS.md）**，除非使用者明確要求
- 每次修改 Wiki 頁面後，列出所有修改的檔案讓使用者確認
- 如果對某個資訊不確定，標註 `[待確認]` 而非猜測
- 保持頁面簡潔，避免冗長的段落；善用列表和表格
