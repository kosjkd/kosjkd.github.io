# 極驗設備指紋測試頁面 說明文檔

## 專案概述

這是一個用於測試極驗（GeeTest）設備指紋 SDK 的網頁工具，可透過瀏覽器產生設備指紋 `geeToken`，並組裝成風控 API 請求所需的 JSON 格式。

## 功能特性

- 輸入 Geetest App ID 與使用者 IP，呼叫官方 SDK 產生設備指紋
- 支援三種業務場景：登錄 (`login`)、註冊 (`sign_up`)、活動 (`activity`)
- 可選輸入 User ID 與 User ID Type（手機號、MD5手機號、QQ OpenID、Wechat OpenID）
- 以語法高亮顯示產生的 JSON 結果（Prism.js）
- 一鍵複製 JSON 到剪貼簿

## 檔案結構

| 檔案 | 說明 |
|------|------|
| `index.html` | 主要頁面，含表單、SDK 呼叫、結果顯示 |
| `README.md` | 專案簡介 |
| `DOCUMENTATION.md` | 本說明文檔 |

## 使用方式

### 本地開啟

直接以瀏覽器開啟 `index.html` 即可，無需任何建置步驟。

```bash
open index.html
```

### 操作流程

1. 填入 **Geetest App ID**（預設已帶入測試值）
2. 填入 **使用者 IP**（IPv4 格式）
3. 選擇 **業務場景**
4. 若需要帶入使用者資訊，勾選「提供用戶 ID 和標識類型」並填入
5. 點擊「生成設備指紋」
6. 右上角「複製 JSON」可將結果複製使用

### 輸出 JSON 範例

```json
{
  "geeToken": "xxxxxxxxxxxxxxxxxx",
  "userIp": "117.136.52.227",
  "opTimestamp": 1727942400,
  "scene": "activity",
  "userId": "11500066894",
  "userIdType": 2
}
```

## 技術組成

| 技術 | 用途 |
|------|------|
| Tailwind CSS (CDN) | UI 樣式 |
| Prism.js | JSON 語法高亮 |
| Geetest `gd.js` | 設備指紋 SDK（`https://static.geetest.com/g5/gd.js`） |

## 外部相依

需要可連外的網路才能載入：
- `https://cdn.tailwindcss.com`
- `https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/*`
- `https://static.geetest.com/g5/gd.js`

## 欄位說明

| 欄位 | 類型 | 說明 |
|------|------|------|
| `appId` | string | 商戶在極驗後台申請的 App ID |
| `userIp` | string | 使用者端 IPv4 |
| `opTimestamp` | number | 操作時間戳（秒） |
| `scene` | string | 業務場景：`login` / `sign_up` / `activity` |
| `userId` | string | （選填）使用者識別碼 |
| `userIdType` | number | （選填）識別碼類型：`2`=手機號、`102`=MD5手機號、`3`=QQ OpenID、`4`=Wechat OpenID |

## 注意事項

- `appId` 需向極驗官方申請，公開頁面不應洩漏生產環境金鑰
- `networkTimeout` 預設 10 秒，若 SDK 載入失敗請檢查網路或 CSP 設定
- 若 SDK 回傳 `status !== "success"`，結果區塊會顯示錯誤 `code` 與 `msg`
