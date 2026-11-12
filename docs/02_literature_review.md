# Energy Detective 相關研究

## 1. 領域知識｜從電表資訊到可採取的行動

IEA 的建築能源統計說明住宅能源管理的重要性 [1]。在使用者層次，Boomsma 等人的試驗顯示即時用電回饋可能影響用量 [2]，Paunov 等人則在學生住宅比較社會比較與能力提示，觀察到兩種介入的用電趨勢均有所改善，兩者差異未達統計顯著 [3]。因此，本專題將「答案和建議能否核對」訂為初版評估目標，實際節電留待住戶介入研究。UCI 單戶資料可支援時段和設備群分析，缺值及共用電表使涵蓋率和可歸因性成為必要的回答條件 [7]。

## 2. AI 技術｜從預測與工具調用到回答驗證

住宅負載預測研究已比較 boosting 集成在不同站點的效果 [6]。這支持在同一測試時段與簡單基準比較，並分別報告誤差與方法可用率。能源 Agent 研究顯示，自然語言介面能協調資料及工具，但能源分析、成本估計與設備任務的正確率有所不同 [4]。排程研究也指出，工具動作、限制遵守與模型說明需要各自檢查 [5]。本專題因此為歷史分析的回答和圖表保留共同結果 ID，並在相同資料、工具及模型條件下比較外部檢查的效果。

## 3. Article Summary Table

核心文獻含三項能源領域來源與三篇 AI 研究。UCI 另列資料來源。限制欄記錄來源或本專題適用性判斷。

| Ref. | Year | Problem | AI Method | Domain Knowledge | Dataset | Findings | Limitation |
|---|---|---|---|---|---|---|---|
| [1] IEA | 2025 | 住宅能源效率的需求與改善方向 | 不適用；官方能源統計與政策分析 | 住宅能源用途、設備效率、氣候與地區差異 | IEA 能源統計與跨國部門分析 | 住宅約占建築能源需求 70%；家庭能源結構因地區而異 | 本專案適用範圍：宏觀能源背景，不能證明家庭 Agent 效果，不能當作家庭用電占比 |
| [2] Boomsma et al. | 2025 | 即時能源資訊是否改變住宅能源使用？ | 不適用；RCT 與統計分析 | 智慧電表、能源資訊呈現、成本顯著性與行為改變 | 荷蘭七地區 802 戶分析樣本，電力／天然氣紀錄與問卷 | 研究報告電力減少 2.2%、天然氣減少 6.9% | 作者提及問卷自我選擇；本案判斷：自願申請、使用顯示器的研究情境，不等同對話 Agent |
| [3] Paunov et al. | 2026 | 社會比較資訊與能力提升提示的成效是否不同？ | 不適用；24 週隨機實地實驗 | 社會規範、節能能力、動機與參與程度 | 瑞典學生住宅，140 戶納入分析；電表與問卷；OSF 提供資料 | 兩種介入均改善相對控制趨勢；彼此差異未達顯著 | 作者指出學生樣本與自願參與、可能資訊分享、參與度衰退；不能推論兩策略完全等效 |
| [4] He & Jazizadeh | 2025 | 如何以自然語言支援具情境感知能力的能源管理？ | LLM Agent、工具調用、程式分析與知識檢索 | 建築設定、用電、費率、設備狀態與使用偏好 | Pecan Street 四戶案例，15 分鐘資料；120 個查詢 | 作者報告能源分析回答正確率 77%，成本管理 49% | 作者指出生成程式分析的穩定性／重複性問題；設備控制使用模擬 API。本案不以此百分比直接評分自有系統 |
| [5] Jonah et al., v2 | 2026 | 如何把自然語言需求轉為符合限制的家庭設備時程？ | ReAct、原生工具調用、知識庫；與 MILP 比較 | 動態電價、光電、設備時限、功率上限與可行性 | 英國 Octopus Agile、氣象／光電估計、家庭需求；歷史資料與模擬請求 | 原生工具介面較自由文字解析可靠；一般低成本表現不能保證衝突情境下遵守限制 | 作者指出單一家庭配置與市場、有限設備類型、歷史週期及模擬請求；未驗證長期真實家庭節省 |
| [6] Muqtadir et al. | 2025 | 如何改善下一小時住宅負載預測？ | LightGBM、XGBoost、CatBoost 集成 | 負載時間變化、氣象、站點差異、缺值與異常處理 | Building Data Genome Project 2 的住宅用途資料與氣象／metadata；13 站點評估 | 在原文比較中呈現集成預測效果，且站點表現有差異 | 本案比較判斷：資料不是 UCI 單戶；工作重點為負載預測，不是自然語言回答與證據鏈評估 |

## 4. 既有研究、限制、研究缺口與本專題

| 階段 | 本專題的歸納 |
|---|---|
| Existing Research | 能源回饋實驗研究用電行為，負載預測研究衡量數值誤差，工具型 Agent 研究分析對話、工具執行及任務成功。 |
| Limitations | 能源介入的成效受樣本與情境影響。預測誤差無法衡量回答引用是否正確。能源 Agent 在不同任務的可靠性有差異。 |
| Research Gap | 在單戶歷史回放的五類任務中，加入外部檢查與有界修正後，數字、時間、單位和證據一致性能改善多少？哪些錯誤仍需要人工複核？ |
| Our Project | Energy Detective 固定分析工具與證據欄位，以同一模型、資料、工具及知識比較有／無外部檢查與修正，另報告預測基準與可用率。 |

## 5. 參考文獻

[1] International Energy Agency. (2025). *Energy Efficiency 2025*. Published 20 November 2025. [官方報告](https://www.iea.org/reports/energy-efficiency-2025)；[住宅／建築章節](https://www.iea.org/reports/energy-efficiency-2025/buildings)。

[2] Boomsma, M., Vringer, K., & van Soest, D. (2025). The impact of real-time energy consumption feedback on residential gas and electricity usage. *Journal of Environmental Economics and Management, 132*, 103163. [DOI](https://doi.org/10.1016/j.jeem.2025.103163)。

[3] Paunov, Y., Grüne-Yanoff, T., Marchionni, C., & Schwirplies, C. (2026). A randomized field experiment comparing nudges and boosts for household electricity conservation in student housing. *Scientific Reports, 16*, 27689. [DOI](https://doi.org/10.1038/s41598-026-69386-6)。

[4] He, T., & Jazizadeh, F. (2025). Context-aware LLM-based AI Agents for Human-centered Energy Management Systems in Smart Buildings. *arXiv:2512.25055v1*. [固定版本](https://arxiv.org/abs/2512.25055v1)。

[5] Jonah, S., Moses, Q., Babatunde, A., Ajao-Olarinoye, M., & Bammeke, D. (2026). LLMs for Agentic Home Energy Management. *arXiv:2607.04569v2*. [固定版本](https://arxiv.org/abs/2607.04569v2)。

[6] Muqtadir, A., Li, B., Ying, Z., Songsong, C., & Kazmi, S. N. (2025). Nowcasting the next hour of residential load using boosting ensemble machines. *Scientific Reports, 15*, 7157. [DOI](https://doi.org/10.1038/s41598-025-91767-6)。

[7] Hebrail, G., & Berard, A. (2006). *Individual Household Electric Power Consumption* [Dataset]. UCI Machine Learning Repository. [DOI](https://doi.org/10.24432/C58K54)。

## 6. Deep Research 補充文獻

以下兩筆支援後續專業取捨討論；加計後為四筆能源領域來源、四篇 AI 技術研究，資料集說明另計。2024 年資料作方法背景，近期動機仍以 2025–2026 年證據為主。

| Ref. | Year | Problem | AI Method | Domain Knowledge | Dataset | Findings | Limitation |
|---|---|---|---|---|---|---|---|
| [8] IEA | 2025 | 需求彈性如何改善電力系統運作？ | 不適用；官方政策與系統分析 | 負載轉移、削峰、系統效率、成本與使用需求 | IEA 系統與案例分析 | 調整用電時點／數量可帶來系統效益；須與能源效率整合 | 本案適用範圍：系統效益不是單戶已量測成效，不能保證移時會降低該戶總電量或費用 |
| [9] Béraud et al. | 2024 | 家庭能源估計如何兼顧誤差、透明度及商業一致性？ | Gradient Boost、Random Forest、線性迴歸、自訂決策樹等比較 | 年用電估計、住房特徵、帳單預估及異常客群 | papernest 約 42,000 客戶；以至少 70 天讀值推估年用電 | 作者選用可解釋自訂樹，並指出異常客群的韌性問題；RF 在原文比較中表現較佳 | 年用電／新客戶估計，不是本案下一小時預測；資料來自 papernest 客戶紀錄，不能直接比較分數；arXiv v1 |

[8] International Energy Agency. (2025). *The Value of Demand Flexibility: Benefits beyond balancing*. Published 23 December 2025. [官方來源](https://www.iea.org/reports/the-value-of-demand-flexibility)。

[9] Béraud, P., Rioux, M., Babany, M., de La Chevasnerie, P., Theis, D., Teodori, G., Pinguet, C., Rigaud, R., & Leclerc, F. (2024). An explainable machine learning approach for energy forecasting at the household level. *arXiv:2410.14416v1*. [固定版本](https://arxiv.org/abs/2410.14416v1)。
