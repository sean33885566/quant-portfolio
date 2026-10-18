# 林宇軒 - Quantitative Machine Learning Portfolio

**Machine Learning for Quantitative Research**

以 Python、LightGBM 與金融資料進行個人量化研究，重點是橫截面排序、時序驗證、離線研究工程及資料品質。

[作品集 PDF](./LIN_YU_HSUAN_QUANT_ML_PORTFOLIO.pdf) · [技術附件](./LIN_YU_HSUAN_QUANT_ML_TECHNICAL_APPENDIX.pdf) · [合成資料示範程式](https://github.com/sean33885566/quant-ml-research)

## 1. 台股機器學習選股研究

整合價量、財務及籌碼資料，以 LightGBM 研究未來報酬排序，建立月頻 purged walk-forward 歷史驗證、RankIC 評估及含交易限制的投組回放。

分別評估模型排序能力、0050 基準比較與費後投組績效；部分歷史設定雖呈正向績效點估，但已檢查設定相對 0050 的 Sharpe 差異未達統計顯著，且 2025 年 4 月後部分市場期間的相對績效落後。研究結果尚不足以支持穩健超額報酬的宣稱。

[研究方法與適用邊界](projects/taiwan-equity-ml.md)

## 2. 金融資料品質案例

以 MOPS／XBRL、TWSE 原始資料及跨欄位邏輯核對財報缺漏、欄位錯位與不可能數值，建立可重現案例後回報資料平台。部分案例獲平台確認，平台後續回覆稱已修正／回補；未宣稱已獨立全量驗收所有修正。

[查看案例與來源截圖](projects/financial-data-quality.md)

## 3. 離線研究工程

建立離線模型訓練與歷史驗證流程，依 fold 保存完成狀態並跳過已完成項目續跑，使用模型及分數產物 manifest、版本追蹤與自動化檢查，管理多個預測期間的研究結果與實驗來源。這是研究工程實作，未宣稱 production MLOps 或實盤系統。

[研究流程與驗證邊界](projects/taiwan-equity-ml.md#研究與工程實作)

## 封存研究與更正

Tick V3／R1 曾將未來資訊誤納為模型輸入，相關預測與交易績效主張已正式撤回。保留原網址與[完整失效說明](projects/intraday-tick-ml.md)供追溯；本項不列為主要代表成果。

## 技術與公開程式

Python · pandas · NumPy · scikit-learn · LightGBM · PyTorch · SHAP · Git

公開 [quant-ml-research](https://github.com/sean33885566/quant-ml-research) 使用合成資料與 Ridge baseline 示範時間驗證及研究控制；不等同完整真實台股 LightGBM 回測、私有 Tick 模型或實盤交易系統。

## 2026-10-18 文件修訂

同步撤回已不適合對外引用的舊固定切分績效與受污染的 Tick V3／R1 結果，補充 PIT 代理規則，以及 fold 層級時序外測試與策略選擇後獨立驗證的差別。保留原始歷史研究紀錄，不改寫研究歷史。
