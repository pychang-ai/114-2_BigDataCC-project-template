# 114-2 巨量資料與雲端運算 期末專題

## 專題資訊

| 項目 | 說明 |
|------|------|
| 課程 | 114-2 巨量資料與雲端運算 |
| 組別 | 第 __ 組（請填入） |
| 組長 | （請填入姓名與學號） |
| 組員 | （請填入所有組員姓名與學號） |
| 專題名稱 | （請填入） |

## 專題說明

本專題要求使用 Docker 容器部署一個包含資料分析或 AI 功能的完整應用。專題需涵蓋從資料處理到模型部署的完整流程，並以 Docker 容器化方式部署，展現本學期所學的技術整合能力。

## 專題要求

### 必要技術

專題必須包含以下技術要素：

1. **Python 資料分析**：使用 Pandas、NumPy 進行資料清洗、轉換與統計分析
2. **資料視覺化**：使用 Matplotlib 或 Seaborn 產出分析圖表
3. **Docker 容器化**：撰寫 Dockerfile，將應用打包為容器
4. **Git 版本控制**：所有程式碼透過 GitHub 管理，commit 紀錄完整

### 選擇性技術（至少包含一項）

- 使用 Keras 預訓練模型進行影像辨識或文字分類
- 使用 Gradio 建立 AI 互動介面
- 使用 Jupyter Notebook 進行探索式資料分析
- 使用 MySQL 資料庫儲存與查詢資料
- 使用 Apache + PHP 建立 Web 前端

## 專題時程與 Repo 內容檢查點

每週結束時，教師會檢查各組 Repo 是否包含該週應有的內容。

| 週次 | 階段 | Repo 應出現的內容 |
|------|------|------------------|
| W3 | 分組與建立 Repo | `README.md` 填寫組別、組長、組員資訊 |
| W4 | 個人題目探索 | `my-topics/` 每人 1-3 個 `.md` 檔（用 topic_template.md 格式） |
| W5 | 決定題目與提案 | `proposal/proposal.md` 完成填寫（動機+資料+技術+分工+時程） |
| W6 | 教師審查提案 | 教師在 Repo 開 Issue 回饋修改建議 |
| W7 | 確定題目 | `proposal/proposal.md` 依回饋修正完成；`data/README.md` 確認資料來源與欄位定義 |
| W8 | 前期研究 | `data/raw/` 放入原始資料（或 README 附下載連結）；`notebooks/` 初步資料探索筆記 |
| W9 | 期中考 | （暫停，不檢查） |
| W10 | 資料分析啟動 | `src/analysis/` 資料清洗程式；`data/processed/` 清洗後資料 |
| W11 | 資料清洗與轉換 | `src/analysis/` 完整分析程式碼；`notebooks/` 分析筆記含視覺化圖表 |
| W12 | 視覺化完成 | `notebooks/` 完整分析筆記含所有圖表；視覺化結果可重現 |
| W13 | Docker 初版 | `docker/Dockerfile` 初版；容器可以 build 成功 |
| W14 | Docker 完成 + 應用 | `docker/Dockerfile` 定版；`src/app/` 應用程式（Gradio 或 Flask）；`docker-compose.yml`（如需多容器） |
| W15 | 整合測試 | 全系統 Docker 部署可正常啟動；`requirements.txt` 完整 |
| W16 | 最終整合 | `src/model/`（如有 ML）；Docker 部署最終確認；所有程式碼有註解 |
| W17 | 繳交報告 | `docs/report.md` 完成（十章結構）；`docs/slides/` 投影片上傳 |
| W18 | 期末發表 | 口頭報告 + 實機 Demo |

### Repo 內容累積示意

```
W3  README.md ✓
W4  README.md ✓  my-topics/ ✓
W5  README.md ✓  my-topics/ ✓  proposal/ ✓
W7  README.md ✓  my-topics/ ✓  proposal/ ✓（修正版）  data/README.md ✓
W8  README.md ✓  my-topics/ ✓  proposal/ ✓  data/raw/ ✓  notebooks/ ✓
W10 ..............................  data/processed/ ✓  src/analysis/ ✓
W13 ..............................  docker/Dockerfile ✓
W14 ..............................  src/app/ ✓
W17 ..............................  docs/report.md ✓  docs/slides/ ✓
```

## 選題流程說明

專題題目的產生分為四個階段，從個人發想到小組共識：

### 第一階段：個人題目探索（W4）

每位同學在專題 Repo 中建立 `my-topics/` 資料夾，提出 1-3 個有興趣的題目。每個題目建立一個 markdown 檔案，格式如下：

```
my-topics/
├── topic1_船舶影像辨識.md
├── topic2_海溫趨勢分析.md
└── topic3_港口壅塞預測.md
```

每個題目檔案需包含：
- 題目名稱
- 為什麼對這個題目有興趣（50 字以上）
- 可能使用的資料來源
- 預計使用的技術

#### 如何找到好題目？

1. **從日常觀察出發**：想想海事或海洋領域中，有什麼問題是你好奇的？
2. **瀏覽資料來源**：先看看有什麼資料可以用，有資料才做得出來
3. **參考本文件的題目清單**：從建議題目中找靈感，也可以延伸或組合
4. **關注新聞時事**：近期有什麼海事相關的議題或事件？
5. **思考實用性**：這個題目做出來，對誰有幫助？能解決什麼問題？

#### 好題目的標準

- 資料取得可行（有公開資料或可自行收集）
- 範圍適中（一學期內 4-5 人可完成）
- 與海事海洋相關
- 能運用課程所學的技術
- 有明確的分析目標或應用場景

### 第二階段：組內討論與投票（W5）

1. 各組成員分享自己提出的 1-3 個題目構想
2. 組內討論每個題目的可行性、有趣程度、技術難度
3. 透過投票或共識決定一個小組題目
4. 可以選擇某位成員的題目，也可以組合多個題目的元素
5. 組長繳交正式的 `proposal/proposal.md`

### 第三階段：教師審查與修正（W6–W7）

1. W6：教師審查提案，在 Repo 開 Issue 提供回饋
2. W7：各組依回饋修正 `proposal/proposal.md`，確定最終題目
3. W7：確認資料來源可取得，填寫 `data/README.md`

### 第四階段：前期研究（W8）

1. 開始收集原始資料，放入 `data/raw/`
2. 建立 Jupyter Notebook，進行初步資料探索
3. 確認資料品質與可用性

## 評分標準

| 項目 | 配分 | 說明 |
|------|------|------|
| 專題提案 | 10 分 | 題目合理性、可行性、創新性 |
| 資料分析品質 | 20 分 | 資料清洗完整、分析有洞察、圖表清楚 |
| 程式碼品質 | 20 分 | 結構清楚、有註解、可讀性高 |
| Docker 部署 | 20 分 | Dockerfile 正確、容器可正常執行 |
| GitHub 管理 | 10 分 | commit 紀錄完整、分工明確、PR 使用得當 |
| 口頭報告與 Demo | 15 分 | 表達清楚、Demo 順暢、回答提問 |
| 文件完整度 | 5 分 | README、報告、投影片齊全 |

## 專題題目參考

以下為建議方向，專題須與海事或海洋領域相關。也可自行提案，但需經教師同意。

### 海洋資料分析類

- 台灣近海海溫變化趨勢分析：利用中央氣象署海洋觀測資料，分析近年海溫變化與季節趨勢
- 港口船舶進出資料分析：分析高雄港或其他國際港口的船舶進出頻率、貨運量趨勢
- AIS 船舶軌跡資料視覺化：利用自動識別系統資料，繪製船舶航行路徑與密度熱力圖
- 海洋廢棄物分布分析：整合淨灘資料或海洋廢棄物監測資料，分析分布熱點與種類比例
- 漁獲量與海洋環境關聯分析：結合漁業統計與海溫、洋流資料，探索漁獲量變化因素
- 全球航運碳排放資料分析：分析國際航運碳排放趨勢與減碳政策影響
- 潮汐與海流資料視覺化：利用觀測資料繪製潮汐預報與海流分布圖

### 海事 AI 應用類

- 船舶影像辨識：利用預訓練模型辨識船舶類型（貨輪、油輪、漁船、軍艦等）
- 海洋生物影像辨識：辨識魚類、珊瑚、海洋哺乳類等海洋生物
- 海事新聞自動分類：爬取海事相關新聞，利用 NLP 模型進行主題分類與情感分析
- 海上天氣預警文字分析：分析氣象預報文字，自動判斷航行風險等級
- 港口壅塞預測：利用歷史資料預測港口船舶等待時間

### 海事整合應用類

- 航運資料儀表板：用 Gradio 建立互動式航運資料分析與視覺化儀表板
- 船舶監控系統：結合 AIS 資料與地圖，建立即時船舶位置追蹤介面
- 海洋環境監測平台：整合海溫、鹽度、浪高等資料，建立多指標監測儀表板
- 漁船作業分析系統：利用 VMS 漁船監控資料，分析漁場分布與作業模式
- 港口智慧管理原型：整合船舶進出、貨物、天氣等資料的多容器管理系統

### 建議資料來源

| 資料集 | 來源 | 網址 |
|--------|------|------|
| 海洋觀測資料 | 中央氣象署 | https://ocean.cwa.gov.tw |
| 港口統計資料 | 交通部航港局 | https://www.motcmpb.gov.tw |
| AIS 船舶資料 | MarineTraffic | https://www.marinetraffic.com |
| 全球漁業資料 | Global Fishing Watch | https://globalfishingwatch.org |
| 海洋廢棄物監測 | 環境部 | https://ocean.epa.gov.tw |
| 國際航運統計 | UNCTAD | https://unctad.org/statistics |
| 海洋環境資料 | Copernicus Marine | https://marine.copernicus.eu |
| 台灣漁業統計 | 農業部漁業署 | https://www.fa.gov.tw |

---

## Repo 結構說明

```
114-2_BigDataCC-G01/
│
├── README.md              ← 本檔案：專題總覽與說明
│
├── proposal/              ← 專題提案
│   └── proposal.md        ← 提案內容（第 11 週繳交）
│
├── data/                  ← 資料集
│   ├── raw/               ← 原始資料
│   ├── processed/         ← 清洗後的資料
│   └── README.md          ← 資料來源說明
│
├── src/                   ← 程式碼
│   ├── analysis/          ← 資料分析程式
│   ├── model/             ← 模型相關程式
│   ├── app/               ← 應用程式（Gradio / Flask）
│   └── utils/             ← 共用工具函式
│
├── notebooks/             ← Jupyter Notebook
│   └── exploration.ipynb  ← 資料探索與分析
│
├── docker/                ← Docker 部署
│   ├── Dockerfile         ← 容器建置檔
│   └── docker-compose.yml ← 多容器編排（如需要）
│
├── docs/                  ← 文件
│   ├── report.md          ← 期末報告
│   └── slides/            ← 投影片
│
├── .gitignore             ← Git 忽略規則
└── requirements.txt       ← Python 套件需求
```

## 各資料夾使用說明

### proposal/

第 11 週前繳交專題提案，`proposal.md` 需包含：
- 專題名稱與動機
- 使用的資料集來源
- 預計使用的技術
- 分工規劃
- 預期成果

### data/

- `raw/`：放原始資料檔案（CSV、JSON 等）
- `processed/`：放清洗處理過的資料
- `README.md`：說明資料來源、欄位定義、授權方式
- 注意：大型檔案（超過 100MB）請使用 .gitignore 排除，改在 README 中提供下載連結

### src/

所有程式碼放在此處，依功能分子資料夾：
- `analysis/`：資料分析用的 Python 程式
- `model/`：機器學習模型訓練與推論
- `app/`：Gradio 或 Flask 應用程式
- `utils/`：共用的工具函式

### docker/

- `Dockerfile`：定義容器映像檔的建置步驟
- `docker-compose.yml`：如果使用多個容器（例如 Python + MySQL），用此檔案編排

### docs/

- `report.md`：期末報告，第 17 週前繳交
- `slides/`：發表用投影片

---

## 操作指南

### 組長建立 Repo

1. 到模板頁面點選「**Use this template**」>「**Create a new repository**」
2. Repository name 填入：`114-2_BigDataCC-G01`（替換為你的組別編號）
3. 設為 **Public**
4. 點選 **Create repository**

### 邀請組員和老師

1. 進入 Repo > **Settings** > **Collaborators**
2. 點選 **Add people**
3. 加入組員（權限：**Write**）
4. 加入老師 `pychang-ai` 和助教帳號（權限：**Write**）

### 組員日常操作

```bash
git clone https://github.com/組長帳號/114-2_BigDataCC-G01.git
cd 114-2_BigDataCC-G01

# 每次工作前先拉最新版本
git pull origin main

# 完成工作後
git add .
git commit -m "描述你做了什麼"
git push origin main
```

### 建議的 commit 訊息格式

```
[分類] 說明

範例：
[data] 新增台北市交通資料 CSV
[analysis] 完成資料清洗與缺失值處理
[model] 加入 ResNet50 影像辨識功能
[docker] 建立 Dockerfile 和 docker-compose
[docs] 更新期末報告初稿
[fix] 修正資料讀取路徑錯誤
```

---

## 注意事項

1. 每位組員都要有 commit 紀錄，不接受只有一人提交的專題
2. 資料集請注明來源與授權方式，不可使用未經授權的資料
3. 程式碼需有適當的註解，方便他人理解
4. Docker 部署必須能在乾淨的環境中正常啟動
5. 期末報告和投影片請在第 17 週前上傳
