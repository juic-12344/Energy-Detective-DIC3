# Energy Detective 期中提案解析

本檔依 [期中 Proposal Word 與 PPT](https://github.com/lun-09-15/AIoT_Final_Proj/tree/55f87d45d9afab7258f817053610902cc185383b/deliverables)、[課程規範對照](Energy-Detective-期末專題規範對照.md) 和 [DIC3 作業說明](Energy-Detective-DIC3-plan.md) 整理，對照原有設計與本次改版。解析以 Energy Detective 的期中原稿和公開專案檔案為來源，由 Codex 整理。資料、模型和實驗狀態均依提案階段呈現。

## 01. 領域 Agent 的四項要素

| 要素 | 原提案設計 | DIC3 對應 |
|---|---|---|
| AI Agent | 以自然語言解析住戶需求與日期，協調資料、分析和知識工具，遇到必要資訊缺漏時澄清。 | R01 定義五類任務，R06 設定每任務 8 次工具呼叫及 1 次回答修正上限。 |
| Domain Knowledge | 區分 kW 與 kWh、用電與電費、全屋與設備群，以及觀測與待查原因。 | R02 規範換算，R07 約束設備群歸因與異常描述。 |
| Data Analytics | 回放 UCI 法國單戶歷史資料，計算小時電量、以 MAD 篩選異常候選、以 Random Forest 預測下一小時。 | R03 規範缺值與涵蓋率，R04 定義回放時間與模型截止，R08 規範評估。 |
| Real-World Application | 讓住戶查詢用電變化、時段和設備群，取得可追溯的檢查方向。 | R05 保留結果 ID、單位、日期、資料品質與來源，供回答與圖表核對。 |

## 02. 摘要 A–F 與緒論

| 段落 | 提案內容 |
|---|---|
| A. Attention Getter | IEA 報告指出住宅約占全球建築能源需求七成。住戶需要把電表紀錄轉成可理解的用電變化。 |
| B. But | 紀錄有缺值，設備群量測難以歸因到單台電器。能源 Agent 也可能答錯日期、單位或結果。 |
| C. Cure | 提出 Energy Detective，讓住戶用日常語句查詢、比較、篩選異常候選、預測及取得檢查建議。 |
| D. Development | LLM 協調固定分析工具，工具記錄資料與結果，系統於回答送出前核對可查證的主張。 |
| E. Experiments | 預測使用時間順序 70／15／15 切分，對照上一小時與前一天同時段。Agent 先試測 10 題，再以 50 題比較有／無外部檢查，兩條件每題各重複 3 次。 |
| F. Findings | 預期交付可追溯的分析流程、任務題集和可重現的評估方案。節電成效需要住戶行為與介入資料。 |

緒論把研究問題收斂到「外部回答檢查與有界修正能改善哪些錯誤，會增加多少延遲、用量及拒答」。文獻比較可把家電排程可行性檢查與本案的數值、日期、單位和證據核對對應到各自的評估任務。

[完整摘要](../docs/11_dic3_abstract.md) · [緒論](../docs/03_introduction_draft.md) · [文獻比較與來源](../docs/02_literature_review.md)

## 03. 深度研究與提案章節對照

| 項目 | 本案內容 |
|---|---|
| 五項核心思維 | 先定義量測目標、檢查粒度和涵蓋率、將異常視為待查線索、依當時可取得資訊驗證預測、以行為資料驗證建議成效。 |
| 三項專業取捨 | 社會比較與行動提示、預測表現與可解釋性、Agent 自主與外部檢查。 |
| 十個深度問題 | 功率與電量、移時、缺值、設備粒度、異常與浪費、尖峰誤差、時間洩漏、證據衝突、節電成效、跨家庭泛化。 |
| 技術設計 | 八模組系統架構、工具與證據流程、四份帶行號的虛擬碼及 OpenSpec 驗收規格。 |
| 研究評估 | 比較預測誤差和可用率，另量測對話任務完成、證據一致性、邊界處理、延遲和用量。 |

[Deep Research](../docs/04_deep_research.md) · [系統架構](../docs/05_architecture_proposal.md) · [Proposed Scheme](../docs/07_proposed_scheme.md) · [分析方法與評估](../docs/06_methods_and_evaluation.md)

## 04. 規格驗收與資訊圖

- **資料涵蓋率。** 某小時只有 30 個不同且有效的分鐘時，回報 50% 涵蓋率及部分觀測量。
- **異常候選。** 目標與參考資料符合判定條件時，只有修正 MAD 分數絕對值大於 3.5 才加上候選標籤。等於 3.5 時回報分數與基準。
- **證據一致性。** 草稿方向與工具結果衝突時，外部檢查阻擋該草稿並在預算內修正。證據仍不足時，輸出已可確認的部分與限制。

提案資訊圖以 A4 橫式的六區呈現 A–F、八個模組、評估、五項核心、三項取捨及十個深度問題。

[OpenSpec 規格](../openspec/changes/implement-energy-detective/specs/) · [A4 PDF](../docs/diagrams/Energy_Detective_DIC3_A4.pdf) · [A4 PNG](../docs/diagrams/Energy_Detective_DIC3_A4.png)
