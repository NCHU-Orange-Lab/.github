<div align="center">

# 🍊 NCHU Orange Lab
### 中興大學橘子實驗室

歡迎來到 NCHU Orange Lab 的 GitHub。

[探索專案](https://github.com/orgs/NCHU-Orange-Lab/repositories) · [聯絡我們](mailto:nchumisaia@gmail.com)

</div>

---

## 關於這裡

這裡是中興大學橘子實驗室的 GitHub 專案入口。你可以在這裡瀏覽公開的程式碼、教學實作與專案文件，並透過各專案的 README 了解內容與使用方式。

## 公開專案

### 🧩 [AIR｜AI 程式碼重構規範套件](https://github.com/NCHU-Orange-Lab/AIR)

協助 AI 將 Python 專案逐步重構成分層架構，透過架構規則、工具 hooks 與 Git commit 前檢查，讓後續開發持續遵守規範。

- **分階段重構**：從安裝、分析與計畫，到建立分層、逐批遷移及驗收，每個階段由使用者確認後推進。
- **架構檢查**：區分組裝、流程、純邏輯、第三方工具、資料讀寫與跨層介面，檢查違規並提供修正提示。
- **使用環境**：目前支援 Python 專案，需要 Python 3.11 以上與 Git；提供 Claude Code 與 Codex 的工具接點。

[閱讀使用說明](https://github.com/NCHU-Orange-Lab/AIR#readme) · [查看版本](https://github.com/NCHU-Orange-Lab/AIR/releases) · [回報問題](https://github.com/NCHU-Orange-Lab/AIR/issues)

### 🛒 [智慧點餐系統｜Smart Ordering System](https://github.com/NCHU-Orange-Lab/smart-ordering-system)

供技職學校教學使用的本機智慧點餐系統專案，使用 React、Django、MySQL、Docker 與 Gemini CLI。

- **查看內容**：閱讀專案 README，了解功能與執行方式。
- **學習實作**：從專案程式碼與文件了解系統的組成。
- **回報問題**：透過專案的 [Issues](https://github.com/NCHU-Orange-Lab/smart-ordering-system/issues) 提出問題或建議。

### 🏓 [AICUP 2025 桌球智慧球拍資料分析｜金牌解決方案](https://github.com/NCHU-Orange-Lab/AICUP2025-Gold-Medal-Solution)

AICUP 2025 春季賽「桌球智慧球拍資料的精準分析競賽」的金牌解決方案，Private leaderboard 第 1 名（Private score 0.840163）。

- **任務**：用球拍上的 6 軸感測資料（3 軸加速度、3 軸角速度），預測選手的性別、持拍手、球齡與等級。
- **方法**：結合 TSFEL、多尺度、進階訊號、揮拍動作與 CNN 特徵，再做特徵組合（交互項、比值、差值），經 SMOTE 與三階段特徵篩選後，以 XGBoost 訓練最終模型。
- **重現結果**：提供比賽時的特徵快取與模型，可直接重現當時的提交檔，也可從原始資料重新計算。

[閱讀使用說明](https://github.com/NCHU-Orange-Lab/AICUP2025-Gold-Medal-Solution#readme) · [詳細用法與參數](https://github.com/NCHU-Orange-Lab/AICUP2025-Gold-Medal-Solution/blob/main/USAGE.md)

### 🏸 [TrackNetV3｜加入注意力機制的羽球追蹤網路](https://github.com/NCHU-Orange-Lab/TrackNetV3)

以 TrackNetV2 為基礎改進的羽球軌跡追蹤網路，是第一個在 TrackNet 中使用注意力機制（Attention）的版本。

- **成果**：在相同的小樣本資料集上，準確率從 TrackNetV2 的 88.49% 提升到 90.53%。
- **完整流程**：從影片標註、資料集格式轉換、模型訓練與預測，到軌跡去雜訊、平滑化及擊球時刻偵測。
- **使用環境**：以 PyTorch 為主，需要 NVIDIA 顯示卡（CUDA）；支援 Windows 與 Linux。

[閱讀使用說明](https://github.com/NCHU-Orange-Lab/TrackNetV3#readme)

[查看所有公開儲存庫 →](https://github.com/orgs/NCHU-Orange-Lab/repositories)

## 參與專案

歡迎透過各專案的 Issues 交流使用經驗與改進建議。回報問題時，請盡量提供操作步驟、執行環境及錯誤訊息，方便釐清問題。

使用、修改或分享專案內容前，請先確認該儲存庫的授權條款與使用說明。

## 聯絡我們

- **Email**：[nchumisaia@gmail.com](mailto:nchumisaia@gmail.com)
- **GitHub**：[NCHU-Orange-Lab](https://github.com/NCHU-Orange-Lab)

<!-- 維護備註：確認資料後，可補充研究方向、指導老師、團隊成員、論文成果與官方網站。請勿填入尚未確認的資訊。 -->

