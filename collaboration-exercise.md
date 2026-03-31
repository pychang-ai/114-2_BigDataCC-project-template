# 小組協作練習

> 本練習讓每組實際演練 Git 協作流程。請全組一起在課堂上完成。

## 練習資訊

| 項目 | 說明 |
|------|------|
| 前置條件 | 組長已建立專題 Repo 並邀請所有組員 |
| 所需時間 | 約 30-40 分鐘 |
| 繳交方式 | 練習結果直接留在專題 Repo 中（不需另外發 PR） |

---

## 練習 1：全員 Clone 與首次 Push（每人都做）

每位組員在自己的電腦上操作：

```bash
# 1. Clone 專題 Repo（替換為你們的 Repo 網址）
git clone https://github.com/組長帳號/114-2_BigDataCC-G01.git
cd 114-2_BigDataCC-G01

# 2. 確認可以看到所有檔案
ls

# 3. 建立你的個人資料夾（用你的學號命名）
mkdir members/你的學號
```

在 `members/你的學號/` 中建立 `profile.md`：

```markdown
# 組員資料

| 項目 | 內容 |
|------|------|
| 姓名 | （填入） |
| 學號 | （填入） |
| 負責項目 | （填入，例如：資料收集與清洗） |
| GitHub 帳號 | （填入） |
| 一句話自我介紹 | （填入） |
```

推送到 GitHub：

```bash
git add members/
git commit -m "[members] 新增組員資料 — 你的姓名"
git push origin main
```

### 檢查點

在 GitHub 上確認：每位組員的資料夾都出現在 `members/` 下。

---

## 練習 2：模擬工作流程 — Pull → 工作 → Push

由組長先推一個檔案，組員再拉取。

### 組長操作

```bash
# 組長建立一個共用的工作紀錄檔
echo "# 專題工作紀錄" > work-log.md
echo "" >> work-log.md
echo "| 日期 | 組員 | 工作內容 |" >> work-log.md
echo "|------|------|---------|" >> work-log.md

git add work-log.md
git commit -m "[docs] 建立專題工作紀錄"
git push origin main
```

### 全體組員操作（含組長）

```bash
# 1. 拉取最新版本
git pull origin main

# 2. 確認 work-log.md 已出現
cat work-log.md

# 3. 每人輪流在 work-log.md 最後加一行（一次一個人操作，避免衝突）
```

**按座位順序，每人依序做以下操作：**

```bash
# 拉最新版本
git pull origin main

# 加入你的紀錄（替換為你的資訊）
echo "| $(date +%Y/%m/%d) | 你的姓名 | 完成協作練習 |" >> work-log.md

# 推送
git add work-log.md
git commit -m "[docs] 新增工作紀錄 — 你的姓名"
git push origin main
```

**重要：一個人 push 完，下一個人才能開始。每個人開始前一定要先 `git pull`。**

### 檢查點

在 GitHub 上確認：`work-log.md` 包含所有組員的紀錄，每人一行。

---

## 練習 3：製造衝突並解決（兩人一組練習）

這個練習故意製造衝突，讓你學會怎麼處理。

### 準備：組長建立測試檔案

```bash
git pull origin main

cat > conflict-test.md << 'EOF'
# 衝突測試

## 我們的專題

主題：（待填寫）

## 使用的技術

技術：（待填寫）
EOF

git add conflict-test.md
git commit -m "[test] 建立衝突測試檔案"
git push origin main
```

### 步驟 1：兩位組員同時拉取

組員 A 和組員 B **同時**執行：

```bash
git pull origin main
cat conflict-test.md
```

現在兩人的版本一樣。

### 步驟 2：兩人各自修改同一行

**組員 A** 修改 `conflict-test.md`：

```markdown
## 我們的專題

主題：高雄港船舶進出分析
```

```bash
git add conflict-test.md
git commit -m "[test] 組員A填寫專題主題"
git push origin main
```

**組員 B** 也修改同一行（不要先 pull）：

```markdown
## 我們的專題

主題：台灣近海海溫趨勢
```

```bash
git add conflict-test.md
git commit -m "[test] 組員B填寫專題主題"
git push origin main
# 這裡會失敗！出現 rejected 錯誤
```

### 步驟 3：組員 B 解決衝突

```bash
# 拉取最新版本（會提示衝突）
git pull origin main
```

打開 `conflict-test.md`，會看到：

```
## 我們的專題

<<<<<<< HEAD
主題：台灣近海海溫趨勢
=======
主題：高雄港船舶進出分析
>>>>>>> abc1234
```

**兩人討論後，修改為最終版本**（例如合併兩者）：

```markdown
## 我們的專題

主題：高雄港船舶進出與海溫關聯分析
```

刪除所有 `<<<<<<<`、`=======`、`>>>>>>>` 標記，只留最終內容。

```bash
git add conflict-test.md
git commit -m "[fix] 解決衝突，合併兩人的主題構想"
git push origin main
```

### 檢查點

在 GitHub 上確認：`conflict-test.md` 包含合併後的最終內容，commit 紀錄可以看到衝突解決的過程。

---

## 練習 4：使用 Issue 分配工作（組長操作，全員觀看）

### 組長操作

在 GitHub 上建立 3 個 Issue：

**Issue #1**

```
標題：[練習] 更新 README.md 組別資訊
內容：請在 README.md 填寫組別、組長、組員等基本資訊。
指派：組長自己
```

**Issue #2**

```
標題：[練習] 確認資料來源
內容：在 data/README.md 填寫至少一個可能使用的資料來源。
指派：任一組員
```

**Issue #3**

```
標題：[練習] 更新 proposal 時程表
內容：在 proposal/proposal.md 填寫各週預計完成項目。
指派：任一組員
```

### 被指派的組員操作

```bash
git pull origin main

# 完成指派的工作（編輯對應的檔案）

git add .
git commit -m "[proposal] 更新時程規劃 closes #3"
git push origin main
```

`closes #3` 會在 push 後自動關閉 Issue #3。

### 檢查點

在 GitHub Issues 頁面確認：至少 1 個 Issue 被自動關閉（顯示 Closed）。

---

## 練習完成後的清理

衝突測試檔案可以刪除：

```bash
git pull origin main
rm conflict-test.md
git add conflict-test.md
git commit -m "[cleanup] 刪除協作練習的衝突測試檔案"
git push origin main
```

`members/` 資料夾和 `work-log.md` 可以保留，作為組員名冊和後續工作紀錄使用。

---

## 練習摘要

完成這四個練習後，你應該會：

| 技能 | 對應練習 |
|------|---------|
| Clone 共用 Repo 並 push | 練習 1 |
| Pull → 工作 → Push 標準流程 | 練習 2 |
| 遇到衝突時不慌張，能解決 | 練習 3 |
| 用 Issue 分配和追蹤工作 | 練習 4 |
