# Energy Detective 摘要與預期貢獻

**題名**　Energy Detective：具證據追溯與回答驗證的家庭用電分析 Agent

## 摘要 A–F

| 段落 | 內容 |
|---|---|
| A. Attention Getter | IEA 估計住宅約占全球建築能源需求七成。住戶如何從電表紀錄辨識用電變化，影響他們能否進一步採取行動。見 [1–3]。 |
| B. But | 用電分析涉及時間、單位、資料涵蓋率及設備量測粒度。能源 Agent 即使能操作工具，回答也可能和工具輸出或限制條件不一致。見 [4–7]。 |
| C. Cure | 本專題提出 Energy Detective。使用者用自然語言查詢、比較用電，辨識異常候選、取得短期預測及檢查建議，並能查閱每項回答的分析依據。 |
| D. Development | 使用 UCI 法國單戶分鐘級歷史紀錄。LLM 協調固定工具，整合小時電量、MAD、Random Forest 與能源知識。系統記錄資料來源、時間、單位及結果，輸出前核對回答。 |
| E. Experiments | 預測按時間切分 70／15／15，比較 RF、上一小時及前日同時段的 MAE、RMSE 與可用率。Agent 先試測 10 題，再以 50 題比較有／無外部檢查，兩條件各重複 3 次，評估正確性、證據一致性、限制處理與成本。 |
| F. Findings | 預期交付可追溯的分析流程、案例及分層評估。實作後量測外部檢查的效果與代價。節電成效需另外透過住戶行為追蹤與對照驗證。 |

## 中文摘要｜約 300 字

住宅約占全球建築能源需求七成。住戶雖可取得電表紀錄，仍難以判斷用電何時增加、資料是否完整，以及哪個時段值得檢查。本專題提出 Energy Detective，以自然語言支援用電查詢、時段比較、異常候選、下一小時預測與檢查建議。系統使用 UCI 法國單戶歷史資料，由大型語言模型協調固定工具，整合小時電量換算、MAD、Random Forest 與能源知識，保留時間、單位、資料涵蓋率及來源，並於輸出前核對回答。預測評估以兩種簡單方法為基準，比較隨機森林的 MAE、RMSE 與可用率。Agent 先試測十題，再以五十題比較有無外部檢查，兩條件各重複三次，衡量數值正確性、證據一致性、限制處理與執行成本。預期成果為可追溯的家庭用電分析流程、任務題集與可重現的對照評估。

## English abstract｜IEEE-style

**Title—** Energy Detective: A Traceable Conversational Agent for Residential Electricity Analysis

**Abstract—** Household electricity records can show when consumption changes, yet interpreting those changes requires consistent time windows, units, and data coverage. We propose Energy Detective, a conversational agent that supports usage queries, interval comparisons, anomaly screening, one-hour-ahead forecasting, and evidence-backed inspection guidance. The proposed system replays minute-level records from one French household in the UCI repository. A large language model selects domain tools for energy aggregation, anomaly screening using median absolute deviation, and forecasting. Each tool records its inputs, result, unit, and provenance. An external checker verifies numerical claims, time windows, and references before presentation. Forecast evaluation will compare a random forest with persistence and a daily seasonal baseline on a chronological split using mean absolute error, root mean squared error, and forecast availability. Agent evaluation will compare matched configurations with and without external answer checking and correction on 50 held-out tasks, with three runs per task per configuration. The planned evaluation will examine numerical correctness, evidence consistency, handling of insufficient data, latency, and resource use. The expected deliverables are a traceable analysis workflow, task cases, and an evaluation protocol for studying the reliability and cost of answer verification.

**Index Terms—** Residential energy management, conversational agents, evidence traceability, load forecasting, answer verification.

## 預期貢獻與學術價值

| 預期貢獻 | 學術價值與驗證 |
|---|---|
| 家庭用電 Agent 的證據紀錄 | 把資料版本、查詢區間、欄位、單位、品質和工具結果對應到回答及圖表，使錯誤能回查到取數、計算或表述環節。以同一結果 ID 核對文字、圖表與數值。 |
| 外部回答檢查的對照設計 | 固定 LLM、資料、工具、知識和工具上限，量測加入外部檢查與一次修正後，證據一致性、錯誤、拒答、延遲及成本如何改變。 |
| 結合預測與對話品質的評估 | 以時間序列基準衡量預測品質，另用缺值、零基準、設備群歸因等題目檢查 Agent 如何回應。可觀察預測表現與回答可靠性各自的限制。 |
| 有條件的住戶檢查建議 | 住戶能看到用電何時改變、該先檢查何處、還需要補什麼資訊。初版的資料代表單一歷史家庭，跨家庭表現與實際節電是後續研究問題。 |

研究焦點是 **外部回答檢查能改善哪些用電分析錯誤，以及需要付出多少額外成本**。評估尚待執行，效果大小以實測報告為準。

[1–7] 見 [Related Work 與 Article Summary Table](02_literature_review.md)。
