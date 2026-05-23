# Antigravity 專案設定檔 (AGENTS.md)

本設定檔提供給 **Antigravity AI 助理** 用於記錄專案相關之全域變數與操作規則。

## 🧠 Obsidian 第二大腦固定路徑

* **主要 Obsidian Vault**: `C:\Users\User\OneDrive\Obsidian\win-ob`

當使用者提到以下關鍵字時，預設指此資料夾：
- 「Obsidian」、「Secondbrain」、「我的筆記本」、「第二大腦」

### 檔案系統讀寫規則

1. **讀取筆記**：
   - 搜尋或讀取筆記時，直接在 `C:\Users\User\OneDrive\Obsidian\win-ob` 目錄下檢索 `.md` 檔案。
2. **寫入筆記**：
   - 新建或修改筆記時，優先寫入 `00 inbox/` 或使用者指定的子資料夾。
   - 所有筆記檔案副檔名需為 `.md`，並使用 `UTF-8` 編碼寫入。
3. **格式規範**：
   - 保留 Obsidian 的雙向連結語法 `[[連結文字]]`。
   - 新增正式筆記時，請加上標準的 Frontmatter YAML 區塊，例如：
     ```yaml
     ---
     title: '筆記標題'
     date: 'YYYY-MM-DD'
     tags:
       - 標籤1
       - 標籤2
     ---
     ```
   - 回應與寫入內容一律使用**繁體中文 (zh-TW)**。
