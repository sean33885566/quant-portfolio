# 林宇軒 — Quantitative Machine Learning Portfolio

**Machine Learning for Quantitative Research**

以金融資料與機器學習進行台股量化研究，研究範圍涵蓋橫截面選股、日內 Tick 模型與金融資料品質驗證。除了模型預測本身，也進一步檢查交易成本、流動性、成交條件與比較基準，確認預測結果是否能轉換成實際研究價值。

[作品集 PDF](./LIN_YU_HSUAN_QUANT_ML_PORTFOLIO.pdf)
·
[Technical Appendix](./LIN_YU_HSUAN_QUANT_ML_TECHNICAL_APPENDIX.pdf)
·
[公開程式碼](https://github.com/sean33885566/quant-ml-research)

## 研究專案

### 1. 台股機器學習選股研究

**研究問題：**  
機器學習能否排序未來表現較好的台股，並將預測轉換成具有相對投資價值的投資組合？

**我做了什麼：**  
整合價量、財務與籌碼資料，以 LightGBM 測試未來 5～126 個交易日共 7 個預測期間，並使用 rolling / walk-forward 方式持續進行樣本外驗證。

**主要結果：**  
2019/02–2024/12 的 RankIC（模型分數排序與後續報酬排序的相關係數）為正。h22（預測未來 22 個交易日）／10 億元固定切分研究在 2023/01–2026/03 的正式評估期呈現可重現的正向相對績效；將同一組固定投組權重改以 T+1 次一交易日調整後開盤價成交，結果仍為正。其他實務帳戶檢查顯示資金規模、交易單位與基準定義會明顯影響結論，因此不宣稱為可直接部署策略。

`LightGBM` · `RankIC` · `Walk-forward` · `SHAP` · `Portfolio Backtest`

[查看完整研究 →](projects/taiwan-equity-ml.md)

### 2. 台股日內 Tick 機器學習研究

**研究問題：**  
日內模型的預測訊號，在只使用決策當下可取得資料並納入實際成交條件後，是否具有經濟價值？

**我做了什麼：**  
使用 112 個交易日的逐筆成交與五檔資料，建立日內特徵工程、LightGBM 回歸與三分類模型，並以事件帳戶驗證訊號在時間、流動性、門檻與五檔成交限制下的表現。

**主要結果：**  
回歸與三分類模型呈現部分樣本外預測證據；高信心放空分支在事件帳戶中呈正向點估，但交易樣本仍少、Sharpe 信賴區間跨零，目前仍需要更多未參與既有研究設計的全新後續資料（fresh-forward）確認穩定性。

`Tick Data` · `Order Book` · `Feature Engineering` · `LightGBM` · `Execution Validation`

[查看完整研究 →](projects/intraday-tick-ml.md)

### 3. 金融資料品質案例｜FinLab

**研究問題：**  
當金融資料出現歷史缺漏、欄位錯位或不可能數值時，如何確認問題來自資料，而不是模型或特徵工程？

**我做了什麼：**  
使用公開資訊觀測站（MOPS）／XBRL、臺灣證券交易所（TWSE）原始資料與欄位邏輯進行交叉確認，建立可重現案例後回報資料平台。

**主要結果：**  
找到歷史財報缺漏、法人交易欄位錯位與不可能負值等案例，其中部分問題後續獲平台確認並修正。

`Data Validation` · `XBRL` · `TWSE` · `Cross-field Checks`

[查看完整案例 →](projects/financial-data-quality.md)

## 技術與研究工具

Python · pandas · NumPy · scikit-learn · LightGBM · PyTorch · SHAP · Git

**研究工程與離線監控：**  
訓練中斷續跑（checkpoint／resume） · 研究產物版本與來源追蹤 · JSON 格式檢查與自動化測試 · 資料與模型狀態檢查

研究主題包括：

- time-aware / point-in-time 資料處理
- rolling / walk-forward validation
- cross-sectional ranking
- transaction-cost-aware backtesting
- Tick / order-book research
- data-quality validation

## Public Code

公開程式碼另置於：

**[quant-ml-research](https://github.com/sean33885566/quant-ml-research)**

公開版本使用合成資料（synthetic data）示範時間驗證、資料處理與研究控制，不重新散布原始金融資料。公開可執行 demo 以 Ridge 最小可執行基準（baseline）說明流程；本作品集所述歷史研究主要使用 LightGBM。

## Documents

- [Recruiter Portfolio PDF](./LIN_YU_HSUAN_QUANT_ML_PORTFOLIO.pdf)
- [Technical Appendix](./LIN_YU_HSUAN_QUANT_ML_TECHNICAL_APPENDIX.pdf)

本作品集區分模型預測證據、投資組合結果與實際可交易性；未將未通過後續驗證的結果描述為可部署交易策略。
