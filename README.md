# DIC3｜Energy Detective 提案重構

本 repository 為物聯網數據分析與應用課程的 DIC3 提案重構交付。Energy Detective 使用自然語言支援家庭用電查詢、比較、異常候選、下一小時預測與檢查建議，重點是讓回答可追溯到資料與分析工具。研究與技術底稿來自 [Energy Detective 正式專案](https://github.com/lun-09-15/AIoT_Final_Proj)。

| DIC3 項目 | 檔案 |
|---|---|
| 安裝 OpenSpec 與工作流程 | 本頁 |
| 摘要 A–F、約 300 字摘要、IEEE-style 摘要、預期貢獻 | [摘要](docs/11_dic3_abstract.md) |
| 5 Cores、3 Trade-offs、10 Details | [Deep Research](docs/04_deep_research.md) |
| DESIGN.md 轉 OpenSpec | [DESIGN.md](DESIGN.md)、[Proposal](openspec/changes/implement-energy-detective/proposal.md)、[Design](openspec/changes/implement-energy-detective/design.md)、[Specs](openspec/changes/implement-energy-detective/specs/)、[Tasks](openspec/changes/implement-energy-detective/tasks.md) |
| Introduction Refactor | [緒論](docs/03_introduction_draft.md) |
| Related Work Refactor | [文獻比較與 Article Summary Table](docs/02_literature_review.md) |
| A4 橫式編號資訊圖 | [PDF](docs/diagrams/Energy_Detective_DIC3_A4.pdf) · [PNG](docs/diagrams/Energy_Detective_DIC3_A4.png) |

## 系統設計與評估

- [八模組架構](docs/05_architecture_proposal.md)
- [流程圖與虛擬碼](docs/07_proposed_scheme.md)
- [分析方法與評估](docs/06_methods_and_evaluation.md)

## 安裝與驗證

已在工作環境以 Node.js 24 和 OpenSpec 2.0.0 初始化，並執行嚴格驗證。Windows CMD 可以從專案根目錄執行以下指令。npm 安裝版需要 Node.js 20.19 或以上。

```cmd
node --version
npm install -g @fission-ai/openspec@2.0.0
openspec --version
openspec list
openspec status --change implement-energy-detective
openspec validate implement-energy-detective --strict --type change
```

全新專案可用 `openspec init --tools antigravity` 初始化。此包已附 `openspec/config.yaml` 及變更資料夾，可直接列出、檢視與驗證。若要在 Antigravity 裝本專案的 OpenSpec 整合，可在本機專案根目錄執行相同 init 指令。

[OpenSpec 安裝說明](https://openspec.dev/docs/installation) · [CLI 文件](https://openspec.dev/docs/cli)

## 這次如何使用 Spec-Driven Development

1. **Proposal** 說明為何要做，以及變更影響。
2. **Specs** 用 Requirement 與 Scenario 定義功能如何驗收。例如，某小時只有 30 個有效分鐘時，系統回報 50% 涵蓋率及部分觀測量。
3. **Design** 記錄資料契約、系統決策和 R01–R08 對應。
4. **Tasks** 列出實作與驗收順序。完成各項驗收後勾選，變更完成後才歸檔。

`openspec status` 的 4/4 代表規劃文件齊備。目前工作項目等待實作，應用程式、模型訓練及正式評估都在後續階段。
