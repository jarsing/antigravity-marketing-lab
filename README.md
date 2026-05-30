# Antigravity Marketing Lab

GDG Changhua Build with AI 2026 工作坊「跟著 Antigravity 邁向代理人開發時代」Hands-on Lab。

本練習使用 Google Cloud Shell、Antigravity CLI、一支預先準備好的 `local-marketing-agent` Skill，以及你自己填寫的 brief，完成一項最小但完整的 Agent 任務：

> 根據自己的活動或產品 brief，產生一句可以拿去討論或發布的主標題。

---

## 今天你會完成什麼？

今天不要求你安裝 Antigravity IDE，也不要求你修改網站程式。你會完成：

1. 在 Cloud Shell 安裝 Antigravity CLI。
2. 從 GitHub 取得這個專案。
3. 查看專案裡預先準備好的 Agent Skill。
4. 填寫自己的 brief。
5. 請 Agent 依照 Skill 產生一句主標題。
6. 查看並分享你的 AI 協作成果。

完整的 `local-marketing-agent` Skill 可以支援：

- Stage 1：活動／產品主標題
- Stage 2：LINE 推播短文案
- Stage 3：Facebook 貼文開頭

為了讓每位會眾都能在現場完成，今天只執行 Stage 1。

---

## Step 1：開啟 Google Cloud Shell

請使用瀏覽器登入你的個人 Google 帳號，並開啟 [Google Cloud Shell](https://shell.cloud.google.com/)。

建議使用個人 Gmail 帳號；公司或學校帳號可能會有權限限制。

今天不需要：

- 安裝 Antigravity Desktop App 或 Antigravity IDE
- 安裝 VS Code
- 建立後端
- 部署網站
- 串接 API
- 使用付費 Google Cloud 服務

---

## Step 2：安裝 Antigravity CLI

在 Google Cloud Shell 中貼入以下指令：

```bash
curl -fsSL https://antigravity.google/cli/install.sh | bash
export PATH="$HOME/.local/bin:$PATH"
```

---

## Step 3：確認 Antigravity CLI 安裝完成

執行：

```bash
agy --version
```

若畫面成功顯示版本編號，代表 Antigravity CLI 安裝完成。

> 看到版本編號後，請先停在這裡，等待講者確認全場進度。

---

## Step 4：下載本次 GitHub 專案

執行：

```bash
git clone https://github.com/jarsing/antigravity-marketing-lab.git
cd antigravity-marketing-lab
```

---

## Step 5：工程師暖身：確認自己在哪裡

執行：

```bash
pwd
ls -la
```

說明：

- `pwd`：顯示目前所在資料夾。
- `ls`：列出目前資料夾檔案。
- `ls -la`：包含隱藏資料夾一起顯示，例如 `.agents`。

---

## Step 6：確認專案中的 Agent Skill

本次 Hands-on 不需要另外安裝 Skill。

從 GitHub clone 本專案後，專案中已經包含一支由講者預先準備好的地方行銷 Agent Skill：

```text
.agents/skills/local-marketing-agent/SKILL.md
```

請執行：

```bash
find .agents -maxdepth 4 -type f
```

你應該會看到：

```text
.agents/skills/local-marketing-agent/SKILL.md
```

接著查看 Skill 內容：

```bash
cat .agents/skills/local-marketing-agent/SKILL.md
```

這支 Skill 已經定義了今日 Agent 任務需要遵守的工作方法，例如：

- 使用台灣慣用繁體中文。
- Stage 1 只產生一句活動／產品主標題。
- 主標題以 24 個中文字以內為原則。
- 不得捏造 brief 中未提供的折扣、贈品、日期、名額或成效。

今天你不需要修改這支 Skill。你只需要填寫自己的 brief，再請 Antigravity Agent 依照這支 Skill 完成任務。

---

## Step 7：填寫自己的 brief

請開啟並編輯：

```text
challenge/my-brief.md
```

內容格式如下：

```markdown
# Brief

- 宣傳主題：
- 目標對象：
- 最大特色或亮點：
- 希望對方採取的行動：
- 可以使用的地名或關鍵字：
- 不可以自行添加的資訊：
```

填寫完成後，可用以下指令檢查：

```bash
cat challenge/my-brief.md
```

---

## Step 8：啟動 Antigravity CLI

確認你目前仍在專案資料夾 `antigravity-marketing-lab` 中，接著執行：

```bash
agy
```

第一次啟動時，請依畫面指示完成 Google 帳號登入與授權。

完成後，請停留在 Antigravity CLI 介面，等待講者進行下一步。

---

## Step 9：將任務交給 Agent

在 Antigravity CLI 中貼入以下任務：

```text
請讀取 challenge/my-brief.md，
使用 local-marketing-agent Skill 執行「Stage 1：主標題產生」。

請自行檢查標題是否符合 Skill 規則；
若不符合，請修正後再交付。

最後只將通過檢查的最終主標題
儲存到 outputs/my-headline.md。
```

---

## Step 10：查看 Agent 交付的成果

完成後，請執行：

```bash
cat outputs/my-headline.md
```

你應該會看到類似以下格式：

```markdown
# 主標題

「你的活動或產品主標題」
```

請思考：

1. 這句標題是否符合你的 brief？
2. 它是否加入了 brief 中沒有提供的資訊？
3. 你會不會真的拿去使用？

---

## Step 11：分享你的作品

分享時只需要說：

> 我的 brief 是想宣傳＿＿＿＿。  
> Agent 交付的主標題是：「＿＿＿＿」。  
> 我覺得這句可以／不可以直接使用，因為＿＿＿＿。

現場會邀請數位會眾分享，並選出：

- 最想直接拿去用獎
- 最有在地感獎
- 現場上站獎

---

## 加碼：完成很快的人可以試試

### 查看整個專案有哪些檔案

```bash
find . -maxdepth 4 -type f | sort
```

### 查看網站原始碼前 80 行

```bash
sed -n '1,80p' website/index.html
```

### 只請 Agent 說明下一步，不實際修改檔案

若你的額度充足，可以在 `agy` 中詢問：

```text
根據 outputs/my-headline.md 與 website/ 現有程式，
請只說明如果要把這句主標題整合進首頁 Hero 區塊，
預計需要修改哪些檔案與原因。

請不要實際修改檔案。
```

---

## 若遇到問題

### 無法安裝或啟動 Antigravity CLI

請先確認：

```bash
export PATH="$HOME/.local/bin:$PATH"
agy --version
```

若仍無法啟動，請立即與身邊成功完成安裝的會眾兩人一組，不要停留在環境排錯。

### 帳號登入或額度不足

若你的帳號暫時無法執行 Agent 任務：

1. 仍請完成自己的 brief。
2. 與旁邊會眾共同使用一個可操作帳號。
3. 共同產生一份主標題成果。
4. 仍可參與現場作品分享。

---

## 回家後可以繼續做什麼？

完成 Stage 1 後，你可以繼續嘗試：

- 讓 Skill 產生 LINE 推播短文案。
- 讓 Skill 產生 Facebook 貼文開頭。
- 修改 Skill 的語氣與限制。
- 把它改成旅行、招生、個人品牌、客服或其他工作方法。
- 使用 Antigravity IDE 或 Antigravity 2.0 將成果接續放進網站或產品。

今天你完成的不只是一句標題，而是第一次把自己的 brief 交給 Agent，讓它依照 Skill 完成並交付一份 AI 協作成果。
