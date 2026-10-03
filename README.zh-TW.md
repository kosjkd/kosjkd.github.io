# 極驗設備指紋測試工具

一個單頁的網頁工具，用來測試極驗（Geetest）設備指紋 SDK（`gd.js`）。於瀏覽器端產生 `geeToken`，並組出模擬後端呼叫極驗風控 API 時會送出的 JSON payload。

English version: [README.md](./README.md)

## 功能

- 以可自訂的 App ID 初始化極驗設備指紋 SDK
- 透過表單輸入常用請求欄位：User IP、業務場景（scene）、可選的 User ID / User ID Type
- 呼叫 `initGeeGuard`，顯示回傳的 `gee_token` 或錯誤資訊
- 以 JSON 語法高亮預覽組好的請求內容
- 一鍵複製生成的 JSON，方便貼到 API 工具中使用

## 支援的業務場景（scene）

`login`（登錄）、`sign_up`（註冊）、`activity`（活動）

## 支援的用戶標識類型（userIdType）

手機號（`2`）、MD5 手機號（`102`）、QQ OpenID（`3`）、Wechat OpenID（`4`）
