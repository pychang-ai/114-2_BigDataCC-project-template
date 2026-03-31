# 小組協作指南：組長與組員的 Git 協作流程

## 為什麼需要學這個？

專題和每週作業不同。每週作業是「一個人在自己的 Fork 裡寫」，但專題是「多個人在同一個 Repo 裡一起寫」。

如果不懂協作流程，你會遇到：
- 兩個人同時改同一個檔案 → 衝突
- 忘記拉最新版本就開始寫 → push 被拒絕
- 不知道誰在做什麼 → 重複工作或漏掉工作
- commit 訊息寫「update」→ 沒人知道改了什麼

這份指南教你怎麼避免這些問題。

---

## 第一部分：角色與分工

### 組長的工作

| 工作 | 什麼時候做 | 怎麼做 |
|------|----------|--------|
| 建立專題 Repo | W3 | 從模板 "Use this template" 建立 |
| 邀請組員和老師 | W3 | Settings > Collaborators > Add people |
| 建立 Issue 分配工作 | 每週 | 在 GitHub 上開 Issue，指派給負責的人 |
| 確認大家都有 push | 每週 | 在 GitHub 看 commit 紀錄 |
| 處理衝突 | 有衝突時 | 和相關組員一起解決 |

### 組員的工作

| 工作 | 什麼時候做 | 怎麼做 |
|------|----------|--------|
| 接受邀請 | 收到通知時 | GitHub 通知點 "Accept invitation" |
| Clone Repo | 第一次 | `git clone` |
| 每次工作前拉最新版 | 每次開始前 | `git pull origin main` |
| 完成後推送 | 每次完成後 | `git add` → `git commit` → `git push` |
| 關閉完成的 Issue | 做完時 | 在 GitHub 上 Close Issue |

---

## 第二部分：基本協作流程

### 2.1 組員第一次：Clone 專題 Repo

```bash
# 在你想放專案的目錄中執行
git clone https://github.com/組長帳號/114-2_BigDataCC-G01.git
cd 114-2_BigDataCC-G01
```

注意：專題 Repo 不需要 Fork，你直接 Clone 即可（因為組長已經把你加為 Collaborator）。

### 2.2 每次工作的標準流程

**黃金三步驟：Pull → 工作 → Push**

```bash
# ① 開始前：拉最新版本（最重要！）
git pull origin main

# ② 工作：編輯檔案、寫程式

# ③ 完成後：推送你的成果
git add .
git commit -m "[analysis] 完成海溫資料缺失值處理"
git push origin main
```

#### 為什麼一定要先 Pull？

```
你的電腦           GitHub（最新版）
  v1.0               v1.2（組員 A 推了新版本）
    │                  │
    └── 如果不 pull ──→ push 會被拒絕！
```

如果你不 pull 就直接開始寫，你的版本是舊的。等你寫完要 push 時，Git 會說：

```
! [rejected] main -> main (fetch first)
error: failed to push some refs
hint: Updates were rejected because the remote contains work that you do not have locally.
```

解法：

```bash
# 先拉最新版本，合併你的修改
git pull origin main

# 如果沒有衝突，直接推送
git push origin main
```

### 2.3 Commit 訊息格式

好的 commit 訊息讓所有人知道你做了什麼。

#### 格式

```
[分類] 簡短說明（做了什麼）
```

#### 分類標籤

| 標籤 | 用途 | 範例 |
|------|------|------|
| `[data]` | 資料相關 | `[data] 新增高雄港 2020-2025 船舶進出 CSV` |
| `[analysis]` | 分析程式 | `[analysis] 完成海溫缺失值處理與月均值計算` |
| `[model]` | 模型相關 | `[model] 加入 ResNet50 船舶分類模型` |
| `[notebook]` | Jupyter | `[notebook] 新增資料探索筆記含 5 張圖表` |
| `[docker]` | Docker | `[docker] 建立 Dockerfile，Python 3.10 基底` |
| `[docs]` | 文件 | `[docs] 更新期末報告第四章` |
| `[fix]` | 修正錯誤 | `[fix] 修正 CSV 讀取編碼問題` |
| `[proposal]` | 提案 | `[proposal] 提交專題提案初稿` |

#### 壞的 commit 訊息

```
update
修改
test
aaa
123
```

這種訊息完全看不出改了什麼，老師和組員都無法理解。

---

## 第三部分：用 Issue 管理工作分配

### 3.1 什麼是 Issue？

Issue 是 GitHub 的工作追蹤工具。把每個任務建成一個 Issue，就像一張待辦便條紙：
- 標題寫任務是什麼
- 內容寫具體要做什麼
- 指派給負責的人
- 做完後關閉

### 3.2 組長建立 Issue

在 GitHub 上：
1. 點選 Repo 頁面的「**Issues**」分頁
2. 點選「**New issue**」
3. 填寫標題和內容
4. 右側「**Assignees**」指派負責人
5. 點選「**Submit new issue**」

#### Issue 範例

```
標題：[W8] 收集高雄港船舶進出資料

內容：
負責人：@王小明
截止日：W8 結束前（4/16）

任務：
- [ ] 到航港局網站下載 2020-2025 年的船舶進出統計
- [ ] 資料存到 data/raw/ 目錄
- [ ] 在 data/README.md 記錄資料來源和欄位定義
- [ ] 完成後 push，並在此 Issue 回報
```

### 3.3 組員完成後關閉 Issue

做完任務後：
1. push 程式碼到 Repo
2. 在 Issue 留言說明完成情況
3. 點選「**Close issue**」

或者在 commit 訊息中自動關閉：

```bash
git commit -m "[data] 新增高雄港船舶進出資料 closes #1"
```

`closes #1` 會在 push 後自動關閉第 1 號 Issue。

### 3.4 建議的 Issue 規劃

以下是各週建議開的 Issue（組長參考）：

| 週次 | Issue 標題範例 |
|------|--------------|
| W7 | 依教師回饋修正提案 |
| W7 | 確認資料來源並填寫 data/README.md |
| W8 | 收集原始資料到 data/raw/ |
| W8 | 建立資料探索 Notebook |
| W10 | 撰寫資料清洗程式 |
| W10 | 處理缺失值和異常值 |
| W11 | 完成統計分析程式 |
| W11 | 製作視覺化圖表 |
| W13 | 撰寫 Dockerfile |
| W14 | 開發 Gradio/Flask 介面 |
| W17 | 撰寫期末報告 |
| W17 | 製作投影片 |

---

## 第四部分：處理衝突

### 4.1 什麼時候會發生衝突？

兩個人同時修改**同一個檔案的同一行**，就會衝突。

```
時間線：
  組員 A：pull → 改 analysis.py 第 10 行 → push ✓
  組員 B：pull（舊版）→ 改 analysis.py 第 10 行 → push ✗ 衝突！
```

### 4.2 如何解決衝突？

```bash
# 1. push 被拒絕，先 pull
git pull origin main

# 2. Git 會提示衝突的檔案
# Auto-merging src/analysis/clean.py
# CONFLICT (content): Merge conflict in src/analysis/clean.py
```

打開衝突的檔案，你會看到：

```python
<<<<<<< HEAD
# 你的版本
df = df.dropna(subset=['temperature'])
=======
# GitHub 上的版本（組員 A 的修改）
df = df.fillna(df.mean())
>>>>>>> abc1234
```

三個步驟解決：
1. **看懂兩邊的差異**：你用 `dropna` 刪除空值，組員 A 用 `fillna` 填補空值
2. **跟組員討論**決定用哪個版本（或合併兩者）
3. **刪除衝突標記**，只留最終版本：

```python
# 討論後決定先填補再標記
df = df.fillna(df.mean())
```

然後：

```bash
git add src/analysis/clean.py
git commit -m "[fix] 解決 clean.py 衝突，採用 fillna 方案"
git push origin main
```

### 4.3 如何避免衝突？

| 方法 | 說明 |
|------|------|
| **分工時分檔案** | 不同人負責不同檔案，最少衝突 |
| **每次工作前先 pull** | 確保在最新版本上修改 |
| **小步快推** | 不要寫很久才 push，頻繁推送減少衝突 |
| **用 Issue 溝通** | 知道誰在改什麼檔案，避免同時修改 |

#### 最佳分工方式（以檔案為單位）

```
組員 A：負責 src/analysis/（資料清洗與分析）
組員 B：負責 src/model/（模型訓練）
組員 C：負責 src/app/（Gradio 介面）
組員 D：負責 data/ 和 notebooks/（資料管理與探索）
組員 E：負責 docker/ 和 docs/（部署與文件）
```

每人負責不同資料夾，幾乎不會衝突。

---

## 第五部分：查看團隊進度

### 5.1 在 GitHub 上看 commit 紀錄

進入 Repo 頁面，點選「**commits**」或「**Insights > Contributors**」，可以看到：
- 誰推了什麼 commit
- 每個人 commit 了幾次
- 最近一次 push 是什麼時候

### 5.2 用 Git 指令查看

```bash
# 看最近 10 筆 commit
git log --oneline -10

# 看每個人的 commit 次數
git shortlog -sn

# 看某個人的 commit
git log --author="王小明" --oneline
```

### 5.3 查看 Issue 進度

在 GitHub 的 Issues 頁面：
- **Open**：還沒做完的任務
- **Closed**：已完成的任務
- 可以用 **Milestones** 設定週次目標

---

## 常見問題

**Q：push 時出現 "rejected" 怎麼辦？**
先執行 `git pull origin main`，如果有衝突就照第四部分的步驟解決，沒衝突就直接 `git push origin main`。

**Q：我不小心把別人的檔案刪了怎麼辦？**
不要慌。Git 有版本紀錄，可以救回來：
```bash
# 查看檔案的歷史版本
git log -- 被刪除的檔案路徑

# 從上一個版本救回
git checkout HEAD~1 -- 被刪除的檔案路徑
git add .
git commit -m "[fix] 救回被誤刪的檔案"
git push origin main
```

**Q：我的 commit 寫錯訊息了可以改嗎？**
如果還沒 push，可以修改最後一次的 commit 訊息：
```bash
git commit --amend -m "[data] 正確的訊息"
```
如果已經 push 了，就不要改，下次注意就好。

**Q：要怎麼知道組員有沒有在做？**
在 GitHub 上看 commit 紀錄和 Issue 進度。如果某位組員長時間沒有 commit，組長應該主動詢問。

**Q：可以直接在 GitHub 網頁上編輯檔案嗎？**
可以，但只適合改小東西（如修 typo、更新 README）。寫程式請在本機用 VS Code。
