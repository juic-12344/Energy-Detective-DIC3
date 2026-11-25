# Energy Detective — DIC4 工作規劃與完成證據

## 作業目標（2026-11-28 截止）

1. Overleaf draft for IEEE conference：IEEE Conference 英文雙欄 LaTeX 研究草稿。
2. OpenSpec on GitHub：延續 DIC3 並建立 `draft-conference-paper` change。
3. MCP：本輪使用 GitHub MCP 讀取來源及進行 GitHub 版本控制；Overleaf 帳號需登入後才能建立線上專案。

## 論文來源與映射

| DIC3 來源 | DIC4 論文章節 |
|---|---|
| `docs/11_dic3_abstract.md`、最新 Proposal A–F | Abstract、Introduction |
| `docs/02_literature_review.md`、`docs/04_deep_research.md` | Related Work、研究缺口與限制 |
| `DESIGN.md`、`docs/05_architecture_proposal.md` | System Design、Fig. 1、Table II |
| `docs/06_methods_and_evaluation.md` | Data/Analytics、Forecasting、Evaluation Plan |
| `docs/07_proposed_scheme.md`、`docs/08_domain_knowledge.md` | Evidence & Response Verification、Algorithm 1 |
| `openspec/changes/implement-energy-detective/` | 原設計規格；本次不修改 |

## 技術參數核對

- UCI Individual Household Electric Power Consumption；固定回放時點 h；timestamp < h。
- kW / 60 與 Wh / 1000 換算 kWh；60 筆不同且有效分鐘值才是完整小時。
- MAD：過去 56 天相同時刻及日型、至少 14 筆、|score| > 3.5。
- RF：200 棵、max_depth=12、min_samples_leaf=5、random_state=42；lag 1/2/24/168；3/24 小時窗口；基準上一小時與前一天同時刻。
- 預測切分 70/15/15；MAE/RMSE、方法可用率與共同評估樣本。
- Agent 最多 8 次工具嘗試，最多 1 次修正，失敗亦計數。
- 10 題試測 + 50 題正式題（5 類各 10 題；6 一般、4 邊界），2 條件各 3 次，共規劃 300 次任務。
- 目前仍未取得模型及實驗成績；不可宣稱已節電、可診斷個別設備故障或已完成系統實作。

## 檔案與驗證流程

- `paper/main.tex`：IEEEtran conference 主檔，Fig. 1 使用 TikZ，Algorithm 1、表格及方程式可編輯。
- `paper/references.tex`：IEEE 編號式書目。
- `paper/IEEEtran.cls`：IEEEtran v1.8b (LPPL)。
- `openspec/changes/draft-conference-paper/`：proposal、design、spec、tasks。

```bash
openspec status --change draft-conference-paper
openspec validate draft-conference-paper --strict
cd paper
latexmk -pdf main.tex
```

Overleaf：將提供的 ZIP 直接上傳至 [Overleaf](https://www.overleaf.com/project)，New Project → Upload Project，使用 pdfLaTeX 及 `main.tex`；Recompile 後查看 PDF。暫用 Group 20 + National Chung Hsing University，英文姓名由組員確認後填入。

## 後續

- 完成 Overleaf 登入／線上匯入後，保存專案網址供課程提交。
- 確認作者英文姓名；若教授要匿名稿，維持指定匿名格式。
- 待期末實作完成後，再以實際已驗證的結果更新論文。

## 本輪本機驗證

- OpenSpec CLI 2.2.0：`openspec validate draft-conference-paper --strict` 通過，proposal/specs/design/tasks 四項 planning artifact 完成。
- pdfLaTeX 編譯兩次：4 頁 US letter IEEE conference 雙欄稿；無 unresolved citation/reference 或 overfull boxes，逐頁檢查版面。
- ZIP：三個根目錄檔案已檢查可正常解壓；登入後可直接匯入 Overleaf。
- 實驗尚未執行，Overleaf 線上編譯、作者確認仍列為未完成。
