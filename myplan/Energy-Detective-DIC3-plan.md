# Energy Detective 家庭用電分析 Agent — DIC3 提案規劃

研究與技術底稿來自 [Energy Detective 正式專案](https://github.com/lun-09-15/AIoT_Final_Proj)。

## 01. 提案解析與 A4 資訊圖

本案用歷史電表紀錄驗證五類用電分析任務，並設計外部回答檢查的對照評估。[A4 橫式資訊圖與其他附件](README-attachments.md) 整理了研究重點、系統模組及實驗規劃。

## 02. 摘要 A–F、緒論與相關研究

[摘要](../docs/11_dic3_abstract.md) 依研究動機、挑戰、解法、方法、實驗及預期成果組織。預期貢獻聚焦於回答的證據追溯，以及檢查機制對品質與成本的影響。研究背景、研究缺口及文獻比較見 [緒論](../docs/03_introduction_draft.md) 與 [相關研究](../docs/02_literature_review.md)。[領域深度研究](../docs/04_deep_research.md) 整理五項核心思維、三項取捨與十個深度問題。

## 03. 中文摘要與 IEEE 風格英文摘要

約 300 字的中文摘要與 IEEE 風格的英文摘要、Index Terms 收在[摘要文件](../docs/11_dic3_abstract.md)。

## 04. DIC3 作業對照

| DIC3 項目 | 檔案 |
|---|---|
| 安裝 OpenSpec 與工作流程 | 見下方安裝、驗證與工作流程 |
| 摘要 A–F、約 300 字摘要、IEEE-style 摘要、預期貢獻 | [摘要](../docs/11_dic3_abstract.md) |
| 5 Cores、3 Trade-offs、10 Details | [Deep Research](../docs/04_deep_research.md) |
| DESIGN.md 轉 OpenSpec | [DESIGN.md](../DESIGN.md)、[Proposal](../openspec/changes/implement-energy-detective/proposal.md)、[Design](../openspec/changes/implement-energy-detective/design.md)、[Specs](../openspec/changes/implement-energy-detective/specs/)、[Tasks](../openspec/changes/implement-energy-detective/tasks.md) |
| Introduction Refactor | [緒論](../docs/03_introduction_draft.md) |
| Related Work Refactor | [文獻比較與 Article Summary Table](../docs/02_literature_review.md) |
| DIC3 提案 Word 與 PPT | [Word](../deliverables/Energy_Detective_DIC3_Proposal.docx) · [PPT](../deliverables/Energy_Detective_DIC3_Proposal.pptx) |
| A4 橫式編號資訊圖 | [PDF](../docs/diagrams/Energy_Detective_DIC3_A4.pdf) · [PNG](../docs/diagrams/Energy_Detective_DIC3_A4.png) |

## 05. 系統設計與評估

- [八模組架構](../docs/05_architecture_proposal.md)
- [流程圖與虛擬碼](../docs/07_proposed_scheme.md)
- [分析方法與評估](../docs/06_methods_and_evaluation.md)

## 安裝與驗證

初版使用 Node.js 24 和 OpenSpec 2.0.0 初始化。以下指令可在 Windows CMD 的專案根目錄執行，重跑本版規格驗證。本提案鎖定的 npm 版本 OpenSpec 2.0.0 需要 Node.js 22.12.0 或以上。

```cmd
node --version
npm install -g @fission-ai/openspec@2.0.0
openspec --version
openspec list
openspec status --change implement-energy-detective
openspec validate implement-energy-detective --strict --type change
```

全新專案可用 `openspec init --tools antigravity` 初始化。本專案已附 `openspec/config.yaml` 及變更資料夾，可直接列出、檢視與驗證。若要在 Antigravity 裝本專案的 OpenSpec 整合，可在本機專案根目錄執行相同 init 指令。

[OpenSpec 安裝說明](https://github.com/Fission-AI/OpenSpec/blob/v2.0.0/docs/installation.md) · [CLI 文件](https://github.com/Fission-AI/OpenSpec/blob/v2.0.0/docs/cli.md)

### 本版驗證紀錄

以 [提交 `bc3ac4b`](https://github.com/juic-12344/Energy-Detective-DIC3/commit/bc3ac4bc4011ba26a3c6267ef6d9d14242fcfc4d) 的公開快照執行上述版本查詢、狀態檢查及嚴格驗證。以下為關鍵輸出，嚴格驗證的結束碼為 `0`。

```text
v22.14.0
2.0.0
Progress: 4/4 artifacts complete
Change 'implement-energy-detective' is valid
```

## 這次如何使用 Spec-Driven Development

1. **Proposal** 說明為何要做，以及變更影響。
2. **Specs** 用 Requirement 與 Scenario 定義功能如何驗收。例如，某小時只有 30 個有效分鐘時，系統回報 50% 涵蓋率及部分觀測量。
3. **Design** 記錄資料契約、系統決策和 R01–R08 對應。
4. **Tasks** 列出實作與驗收順序。完成各項驗收後勾選，變更完成後才歸檔。

`openspec status` 的 4/4 代表規劃文件齊備。目前工作項目等待實作，應用程式、模型訓練及正式評估都在後續階段。
