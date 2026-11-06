<div align="center">

# 🍊 NCHU Orange Lab
### 中興大學橘子實驗室

歡迎來到 NCHU Orange Lab 的 GitHub。(NCHU MIS AIA Lab)

[探索專案](https://github.com/orgs/NCHU-Orange-Lab/repositories) · [聯絡我們](mailto:nchumisaia@gmail.com)

</div>

---

## 關於這裡

這裡是中興大學橘子實驗室的 GitHub 專案入口。你可以在這裡瀏覽公開的程式碼、教學實作與專案文件，並透過各專案的 README 了解內容與使用方式。

## 公開專案

| 類別 | 專案 |
|------|------|
| 🏆 [競賽成果](#-競賽成果) | AICUP 2025 金牌解決方案、AI CUP 2026 桌球戰術預測、AI CUP 2025 桌球智慧球拍分析、AI CUP 2024 太陽能發電量預測、AI CUP 心臟 CT 分割流程 |
| 🔬 [研究](#-研究) | 形式化證明搜尋的語意對齊、TrackNetV3 |
| 🧰 [工具與應用](#-工具與應用) | AIR、消費行為洞察平台、GemmaFit、Simple QA Generator、Soundcore Desk |
| 📚 [教學與範本](#-教學與範本) | 智慧點餐系統、中興大學 LaTeX 論文模板 |

### 🏆 競賽成果

#### 🥇 [AICUP 2025 桌球智慧球拍資料分析｜金牌解決方案](https://github.com/NCHU-Orange-Lab/AICUP2025-Gold-Medal-Solution)

AICUP 2025 春季賽「桌球智慧球拍資料的精準分析競賽」的金牌解決方案，Private leaderboard 第 1 名（Private score 0.840163）。

- **任務**：用球拍上的 6 軸感測資料（3 軸加速度、3 軸角速度），預測選手的性別、持拍手、球齡與等級。
- **方法**：結合 TSFEL、多尺度、進階訊號、揮拍動作與 CNN 特徵，再做特徵組合（交互項、比值、差值），經 SMOTE 與三階段特徵篩選後，以 XGBoost 訓練最終模型。
- **重現結果**：提供比賽時的特徵快取與模型，可直接重現當時的提交檔，也可從原始資料重新計算。

[閱讀使用說明](https://github.com/NCHU-Orange-Lab/AICUP2025-Gold-Medal-Solution#readme) · [詳細用法與參數](https://github.com/NCHU-Orange-Lab/AICUP2025-Gold-Medal-Solution/blob/main/USAGE.md)

#### 🏓 [AI CUP 2026 桌球戰術預測｜第 9 名 佳作](https://github.com/NCHU-Orange-Lab/AI-CUP-2026-TEAM_10434)

AI CUP 2026 春季賽「基於時序資料之桌球戰術與結果預測競賽」TEAM_10434 的程式碼。根據每個 rally（一回合來回）已公開的前 n-1 拍，預測第 n 拍的球種與落點，並估計這一回合由發球方得分的機率。

- **方法**：把每個 rally 拆成多筆前綴（prefix）樣本，三個預測任務各訓練一個 2 層雙向 GRU（bidirectional GRU），再和統計式 backoff 模型做機率加權融合。
- **成果**：最終版本 Public leaderboard 0.4464793、Private leaderboard 0.3774274。
- **使用環境**：Python 與 PyTorch，作者在 Ubuntu 22.04 搭配 NVIDIA RTX 3090 執行；加上 `--cpu` 參數也能只用 CPU 確認流程。

[閱讀使用說明](https://github.com/NCHU-Orange-Lab/AI-CUP-2026-TEAM_10434#readme)

#### 🏓 [AI CUP 2025 桌球智慧球拍資料分析｜第 8 名 佳作](https://github.com/NCHU-Orange-Lab/AI_CUP_2025-Table-Tennis-Racket-Analysis)

AI CUP 2025 春季賽「桌球智慧球拍資料的精準分析競賽」排名 8/633 的解法。用智慧球拍的三軸加速度與三軸角速度資料，預測選手的性別、持拍手、打球年資與球技等級。

- **方法**：萃取時域、頻域（FFT）與小波（Wavelet）特徵，以 CatBoost 為主要模型（可切換為 TabPFN），在依選手分組的交叉驗證（StratifiedGroupKFold）中做兩階段特徵篩選，並用 BorderlineSMOTE 處理類別不平衡。
- **成果**：交叉驗證（CV）的四項任務平均 AUC 為 0.8576，其中持拍手 0.9973、性別 0.9180。
- **使用環境**：Python 3.10，主要套件為 CatBoost、TabPFN、scikit-learn 與 imbalanced-learn。

[閱讀使用說明](https://github.com/NCHU-Orange-Lab/AI_CUP_2025-Table-Tennis-Racket-Analysis#readme)

#### ☀️ [AI CUP 2024 太陽能發電量預測｜第 8 名 佳作](https://github.com/NCHU-Orange-Lab/AI_CUP_2024-Predicting-Solar-Power-Generation)

AI CUP 2024「根據區域微氣候資料預測發電量競賽」排名 8/500 的解法。整合 17 個地點的資料，以時間特徵加上日射量、雷達功率、太陽仰角與方位角等外部資料，預測太陽能板的發電量。

- **方法**：資料重新取樣成每 10 分鐘一筆並處理缺值與極端值，用 OpenFE 自動產生特徵，再以 LightGBM、CatBoost 為基礎模型、XGBoost 為最終模型做堆疊集成（Stacking）。
- **一鍵執行**：執行 `main.py` 就能依序完成前處理、特徵工程、訓練，並產生提交檔。
- **使用環境**：Python 3.9，XGBoost 與 CuPy 需要 NVIDIA 顯示卡（CUDA）。

[閱讀使用說明](https://github.com/NCHU-Orange-Lab/AI_CUP_2024-Predicting-Solar-Power-Generation#readme)

#### 🫀 [AI CUP 心臟 CT 分割流程｜TEAM_8421](https://github.com/NCHU-Orange-Lab/AI_CUP_TEAM_8421)

以 nnU-Net v2 為基礎的三階段 3D 醫學影像分割流程：先分割整個心臟，再依預測結果逐步裁切出較小的區域交給專門模型細部分割，目的是提升對鈣化等細小病灶的辨識。

- **方法**：用整體模型的預測外接框（bounding box）加上邊界（margin）裁切出心肌、主動脈瓣與鈣化區域，以 ResEnc L 設定分別訓練專門模型。
- **工具**：提供裁切、標籤重新編號與還原，以及把局部預測貼回整體結果（paste-back）的腳本。
- **使用環境**：Python 3.12、PyTorch（CUDA 12.8）與 nnU-Net v2.6.2，需要 NVIDIA 顯示卡，可在 Windows 與 Linux 執行。

[閱讀使用說明](https://github.com/NCHU-Orange-Lab/AI_CUP_TEAM_8421#readme)

### 🔬 研究

#### 📐 [形式化證明搜尋的語意對齊｜Semantic Alignment for Formal Proof Search](https://github.com/NCHU-Orange-Lab/semantic-alignment-formal-proof-search)

研究自然語言數學推理能不能幫助 Lean 定理證明器的策略（tactic）層級證明搜尋，並指出「局部到全域落差」（local-to-global gap）：單步選對策略的比例提高了，但整題證明的完成率沒有跟著提高。

- **方法**：利用同一證明狀態下 Lean 驗證器的回饋挖掘困難負樣本（hard negatives），訓練語意對齊模型重新排序候選策略，並在最佳優先搜尋（best-first search）中加入結構化價值引導。
- **成果**：排第一的候選策略能通過 Lean 驗證的比例（Lean-valid Top-1）從 75.8% 提升到 86.8%；但在 Lean Workbook 500 題保留測試定理上，加不加語意重排序的完成率都是 39.6%。
- **使用環境**：Python 3.12、PyTorch、Lean 4.8.0-rc1 與對應版本的 Mathlib，建議使用支援 CUDA 的顯示卡。

[閱讀說明](https://github.com/NCHU-Orange-Lab/semantic-alignment-formal-proof-search#readme) · [重現指南](https://github.com/NCHU-Orange-Lab/semantic-alignment-formal-proof-search/blob/main/reproduction/README.md) · [論文預印本（PDF）](https://github.com/NCHU-Orange-Lab/semantic-alignment-formal-proof-search/blob/main/paper/semantic_alignment_for_formal_proof_search.pdf)

#### 🏸 [TrackNetV3｜加入注意力機制的羽球追蹤網路](https://github.com/NCHU-Orange-Lab/TrackNetV3)

以 TrackNetV2 為基礎改進的羽球軌跡追蹤網路，是第一個在 TrackNet 中使用注意力機制（Attention）的版本。

- **成果**：在相同的小樣本資料集上，準確率從 TrackNetV2 的 88.49% 提升到 90.53%。
- **完整流程**：從影片標註、資料集格式轉換、模型訓練與預測，到軌跡去雜訊、平滑化及擊球時刻偵測。
- **使用環境**：以 PyTorch 為主，需要 NVIDIA 顯示卡（CUDA）；支援 Windows 與 Linux。

[閱讀使用說明](https://github.com/NCHU-Orange-Lab/TrackNetV3#readme)

### 🧰 工具與應用

#### 🧩 [AIR｜AI 程式碼重構規範套件](https://github.com/NCHU-Orange-Lab/AIR)

協助 AI 將 Python 專案逐步重構成分層架構，透過架構規則、工具 hooks 與 Git commit 前檢查，讓後續開發持續遵守規範。

- **分階段重構**：從安裝、分析與計畫，到建立分層、逐批遷移及驗收，每個階段由使用者確認後推進。
- **架構檢查**：區分組裝、流程、純邏輯、第三方工具、資料讀寫與跨層介面，檢查違規並提供修正提示。
- **使用環境**：目前支援 Python 專案，需要 Python 3.11 以上與 Git；提供 Claude Code 與 Codex 的工具接點。

[閱讀使用說明](https://github.com/NCHU-Orange-Lab/AIR#readme) · [查看版本](https://github.com/NCHU-Orange-Lab/AIR/releases) · [回報問題](https://github.com/NCHU-Orange-Lab/AIR/issues)

#### 📊 [消費行為洞察與預測平台｜Consumer Insight App](https://github.com/NCHU-Orange-Lab/consumer-insight-app)

在本機執行的繁體中文分析工具，非技術背景的使用者只要上傳交易 CSV，就能完成顧客分析並得到商業洞察摘要。

- **功能**：資料健檢、RFM（Recency / Frequency / Monetary）分析、KMeans 顧客分群、流失與回購預測，以及消費趨勢預測。
- **AI 摘要**：可選擇接上 Gemini API 產生商業洞察摘要；沒有設定金鑰時會改用本地的規則式摘要，其他功能照常可用。
- **使用環境**：以 Python 與 Gradio 開發，建議用 Docker Compose 啟動，也可以安裝套件後執行 `python app.py`。

[閱讀使用說明](https://github.com/NCHU-Orange-Lab/consumer-insight-app#readme)

#### 🏋️ [GemmaFit｜在手機本機執行的運動動作教練](https://github.com/NCHU-Orange-Lab/GemmaFit)

Android App，以單鏡頭姿態辨識分析運動動作並給出回饋，再由手機上的 Gemma 4 模型撰寫訓練摘要；無法判斷的情況會明確說明，也不做醫療診斷。

- **方法**：用 MediaPipe Pose 分析鏡頭或影片中的動作，即時回饋由確定性（deterministic）規則產生，摘要則交給手機本機的 Gemma-4-E2B-it 模型（LiteRT-LM）撰寫。
- **可靠性**：App 會檢查模型輸出的格式與引用的證據，不符合時改用備援摘要；在受限解碼下連續 100 次測試，輸出的 JSON 都能成功解析。
- **使用環境**：Kotlin 與 Jetpack Compose 開發的 Android App，需自行用 Gradle 建置，並另外放入約 2.5 GB 的模型檔。

[閱讀使用說明](https://github.com/NCHU-Orange-Lab/GemmaFit#readme) · [效能與驗證結果](https://github.com/NCHU-Orange-Lab/GemmaFit/blob/main/docs/benchmark/README.md)

#### 📝 [Simple QA Generator｜自動產生微調用問答資料](https://github.com/NCHU-Orange-Lab/Simple-QA-Generator)

用大型語言模型（LLM）把文件自動轉成問答對（QA pairs）的網頁工具，用來準備 HuggingFace SFTTrainer 監督式微調（Supervised Fine-tuning）的訓練資料。

- **輸入**：支援 TXT、PDF、DOCX、CSV、HTML、Markdown 等格式，切成文字區塊（chunk）後由 LLM 產生問答。
- **輸出**：可即時預覽，並下載標準 JSON 或 SFTTrainer 使用的對話（messages）格式。
- **使用環境**：Python 3.11 以上、Streamlit 網頁介面，需要 OpenAI API 金鑰（或相容的 API 服務），可自訂模型與提示詞（prompt）。

[閱讀使用說明](https://github.com/NCHU-Orange-Lab/Simple-QA-Generator#readme) · [中文說明](https://github.com/NCHU-Orange-Lab/Simple-QA-Generator/blob/master/README_zh.md)

#### 🔊 [Soundcore Desk｜藍牙喇叭控制與 4 聲道環繞](https://github.com/NCHU-Orange-Lab/anker-soundcore-glow-mini-7.1-Surround-Sound)

控制 soundcore Glow Mini（型號 A3136）藍牙喇叭的 Windows 桌面程式，介面為繁體中文。這是獨立開發的工具，不是 Anker 官方程式。

- **喇叭控制**：每顆喇叭一張卡片，可各自調音量、靜音，查看電量、充電狀態、韌體與序號，並開關 PartyCast。
- **4 聲道環繞**：把兩組 TWS 喇叭組成前後 4 聲道，將電腦播放的 5.1／7.1 聲音拆成前左、前右、後左、後右；一般立體聲音樂也能用「擴展環繞」以短時傅立葉轉換（STFT）分離出環境聲送到後方。
- **使用環境**：Windows 10／11 與 .NET Framework 4.8，只用系統內建元件、不連網路；4 聲道環繞另外需要免費的虛擬音效驅動程式 VB-CABLE。

[閱讀使用說明](https://github.com/NCHU-Orange-Lab/anker-soundcore-glow-mini-7.1-Surround-Sound#readme) · [協定研究紀錄](https://github.com/NCHU-Orange-Lab/anker-soundcore-glow-mini-7.1-Surround-Sound/blob/main/research/README.md)

### 📚 教學與範本

#### 🛒 [智慧點餐系統｜Smart Ordering System](https://github.com/NCHU-Orange-Lab/smart-ordering-system)

供技職學校教學使用的本機智慧點餐系統專案，使用 React、Django、MySQL、Docker 與 Gemini CLI。

- **查看內容**：閱讀專案 README，了解功能與執行方式。
- **學習實作**：從專案程式碼與文件了解系統的組成。
- **回報問題**：透過專案的 [Issues](https://github.com/NCHU-Orange-Lab/smart-ordering-system/issues) 提出問題或建議。

#### 🎓 [中興大學 LaTeX 論文模板｜NCHU Thesis LaTeX Template](https://github.com/NCHU-Orange-Lab/NCHU-Thesis-LaTeX-Template)

國立中興大學非官方的碩博士論文 LaTeX 模板，格式參考圖書館的規範，可直接編譯，也方便用 Git 做版本控制。正式提交前，請再確認系所是否有額外的格式規定。

- **內容**：已排好封面、摘要、目次、圖表目次、符號列表、示範章節、參考書目與附錄，口試委員審定書可視需要開啟。
- **設定**：在 `nchusetup.tex` 填入個人與論文資料，在 `main.tex` 切換碩士／博士、中文／英文、字型與浮水印等選項。
- **使用環境**：需要含 XeLaTeX 與 BibTeX 的 TeX 發行版，也可以使用 Overleaf 等線上編輯器。

[閱讀使用說明](https://github.com/NCHU-Orange-Lab/NCHU-Thesis-LaTeX-Template#readme)

[查看所有公開儲存庫 →](https://github.com/orgs/NCHU-Orange-Lab/repositories)

## 參與專案

歡迎透過各專案的 Issues 交流使用經驗與改進建議。回報問題時，請盡量提供操作步驟、執行環境及錯誤訊息，方便釐清問題。

使用、修改或分享專案內容前，請先確認該儲存庫的授權條款與使用說明。

## 聯絡我們

- **Email**：[nchumisaia@gmail.com](mailto:nchumisaia@gmail.com)
- **GitHub**：[NCHU-Orange-Lab](https://github.com/NCHU-Orange-Lab)

<!-- 維護備註：確認資料後，可補充研究方向、指導老師、團隊成員、論文成果與官方網站。請勿填入尚未確認的資訊。 -->

