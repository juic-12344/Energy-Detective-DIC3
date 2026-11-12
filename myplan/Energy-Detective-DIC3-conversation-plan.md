# Energy Detective DIC3 改版決策紀錄

本紀錄依原專案設計決策、本次作業對話的重點及 GitHub 提交整理。原始提案為 [Energy Detective 期中版](https://github.com/lun-09-15/AIoT_Final_Proj/tree/55f87d45d9afab7258f817053610902cc185383b/deliverables)，本次交付為家庭用電分析 Agent 的 DIC3 提案改版。

## 01. 原始材料

- [期中提案文字擷取](Energy-Detective-期中Proposal-文字擷取.md)，保留原稿正文、表格與行號虛擬碼。
- [課程規範對照](Energy-Detective-期末專題規範對照.md)，用於核對摘要、緒論、相關研究、Deep Research、設計與交付要求。
- [Energy Detective 提案解析](Energy-Detective-提案解析.md)，把原稿內容對應到課程規範、OpenSpec 與 A4 資訊圖。
- [期中版設計決策](https://github.com/lun-09-15/AIoT_Final_Proj/tree/55f87d45d9afab7258f817053610902cc185383b/docs/00_decisions.md)，包含既定資料來源、分析方法、功能邊界與實驗規劃。

## 02. 三項核心亮點與研究定位

1. **自然語言用電查詢。** 依歷史回放日解讀「昨天」「前天」等語句，時間或範圍不明時澄清。
2. **分析工具與能源知識。** 固定工具換算電量、比較時段、篩選異常候選與預測，使用資料涵蓋率和設備粒度限制推論。
3. **證據追溯與回答檢查。** 用結果 ID 連結答案、圖表及資料來源，核對日期、單位、數值、方向與引用。

研究聚焦於固定模型、工具及資料時，加入外部檢查與有界修正後，回答品質、延遲、用量和拒答如何改變。三項系統亮點見 [專題摘要頁](test.md)，五項領域核心思維見 [Deep Research](../docs/04_deep_research.md)。

## 03. 改版重點與理由

| 決策 | 理由及結果 |
|---|---|
| 把八項系統需求轉成 OpenSpec | 讓日期解析、缺值、單位、工具上限及推論界線能以具體情境驗收。 |
| 緒論聚焦外部回答檢查 | 固定模型、工具及資料，讓研究問題能對應有／無檢查與一次修正的實驗。 |
| 在 Related Work 補足比較對象 | 明確比較既有家電排程可行性檢查與本案的用電回答證據檢查。 |
| 對齊 MAD 虛擬碼與規格 | 只有分數絕對值大於 3.5 才加上異常候選標籤，並新增等於門檻時的驗收情境。 |
| 同步 Word、PPT 與 Markdown | 用 Word 補中文和 IEEE 風格英文摘要、學術貢獻及 OpenSpec 工作流程，簡報保留原頁次並新增兩頁。 |
| 補齊 `myplan/` 的改版紀錄和來源附件 | 補上本組原稿文字、規範對照、提案解析和專題摘要頁，方便從改版成果回查原始材料。 |

## 04. 提交與驗證

| 提交 | 紀錄 |
|---|---|
| [`19947a7`](https://github.com/juic-12344/Energy-Detective-DIC3/commit/19947a7a411b6eccd64a41f9347aadd08caf3c15) | 加入提案重構、分析方法、A4 資訊圖與 OpenSpec。 |
| [`8fa1b91`](https://github.com/juic-12344/Energy-Detective-DIC3/commit/8fa1b910b4ed7b6a77b4d9da0515cef5d3bc1617) | 加入提案總覽和附件索引。 |
| [`bc3ac4b`](https://github.com/juic-12344/Energy-Detective-DIC3/commit/bc3ac4bc4011ba26a3c6267ef6d9d14242fcfc4d) | 更新安裝說明、MAD 邊界情境、研究差異及 Word／PPT。 |
| [`73813ac`](https://github.com/juic-12344/Energy-Detective-DIC3/commit/73813ace80c55d9d5c6410f95f9a9f90a0b0dd96) | 保存 OpenSpec 2.0.0 嚴格驗證通過的實際輸出。 |

## 05. 後續工作

依 OpenSpec 任務取得並核對 UCI 資料、實作分析與回答檢查、凍結題集及評分規則，再進行正式實驗。OpenSpec 的 4/4 是規劃文件完成狀態，原型與評估仍在後續階段。

[提案規劃](Energy-Detective-DIC3-plan.md) · [附件索引](README-attachments.md) · [OpenSpec 任務](../openspec/changes/implement-energy-detective/tasks.md)
