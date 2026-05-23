# Antigravity 懶人包 #02：連接 GitHub (Windows PowerShell 版)

本懶人包已針對 **Antigravity** 進行優化與轉化。Antigravity 可以自動辨識、讀取此檔案，並在您的授權下自動在 PowerShell 終端機中執行相關安裝與檢測指令。

---

## 這個懶人包會幫你做什麼？

讓 Antigravity 能夠直接操控 GitHub，協助您管理本專案代碼與發布網頁：
- 驗證 Git、GitHub CLI 等基礎工具狀態
- 驗證或登入 GitHub 帳號並完成授權
- 設定全域 Git 使用者資訊（姓名與 Email）
- 初始化本機專案 Git 儲存庫（`git init`）
- 建立遠端 GitHub 儲存庫（Repository）並推播本專案上線
- 設定並啟用 GitHub Pages，讓您的成品（如 HTML 互動教材）能直接產生公開網址與 QR Code

---

## 先備條件

- [x] **Git**: 已安裝
- [x] **GitHub CLI (gh)**: 已安裝
- [ ] **GitHub 帳號**: 如果尚未註冊，請至 [GitHub 官網](https://github.com/signup) 註冊
- [x] **網路連線**: 保持暢通

---

## 執行步驟說明

### 步驟零：工具與狀態檢查
1. 檢查 Git 版本。
2. 檢查 GitHub CLI 版本。
3. 檢查 GitHub 登入狀態。

### 步驟一：登入 GitHub (若未登入)
若 `gh auth status` 顯示未登入，請執行：
```powershell
gh auth login --web --git-protocol https
```
系統會顯示單次驗證碼，並自動開啟瀏覽器，請在網頁上輸入驗證碼並完成授權。

### 步驟二：設定 Git 使用者資訊 (若未設定)
設定全域 Git 使用者名稱與信箱，以便記錄 Commit 歷史：
```powershell
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### 步驟三：初始化本機 Git 並推送到 GitHub
若本專案資料夾尚未建立 Git 儲存庫，請依序執行：
1. **初始化儲存庫**:
   ```powershell
   git init
   ```
2. **加入所有檔案**:
   ```powershell
   git add .
   ```
3. **建立初始 Commit**:
   ```powershell
   git commit -m "initial commit: Antigravity 專案初始化"
   ```
4. **建立 GitHub 遠端儲存庫並推送**:
   ```powershell
   gh repo create 2026GV --public --source=. --push
   ```

### 步驟四：啟用 GitHub Pages (選用)
您可以啟用 GitHub Pages 以提供線上展示網址（例如 `https://<your-username>.github.io/2026GV/`）：
```powershell
gh api repos/{owner}/2026GV/pages -X POST -f build_type=workflow -f source.branch=main -f source.path=/
```
*(注意：需要等待 1-2 分鐘讓 GitHub Actions 完成部署)*

---

## 常見問題與異常排除

| 狀況 | 原因 | 解法 |
| :--- | :--- | :--- |
| `gh: 找不到指令` | 系統環境變數 PATH 未包含 gh.exe 路徑 | 重開終端機或重新安裝 GitHub CLI |
| `Permission denied` | 權限不足，或是 SSH 金鑰/ Token 設定錯誤 | 執行 `gh auth login` 重新以 HTTPS 模式授權 |
| `Pages 顯示 404` | 部署中或分支路徑設定不正確 | 等待約 2 分鐘，或至 GitHub Repo 設定頁面 (Settings > Pages) 確認狀態 |

---

## 相關連結與下一步
- **[[00-環境建置|懶人包 #00：環境建置]]**
- **[[01-連接 NotebookLM|懶人包 #01：連接 Google NotebookLM]]**
- **[[03-建立第二大腦-Obsidian|懶人包 #03：連接 Obsidian 第二大腦]]**
- **[[README|Antigravity 懶人包索引]]**
