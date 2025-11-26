# Week 4 - Weather APP

- 使用 AI 工具生成一個天氣查詢應用程式
- 串接天氣 API 取得即時天氣資訊
- 部署至線上平台（如 GitHub Pages、Zeabur 等）

# 🎯規格需求

```
- 可輸入城市名稱查詢天氣
- 顯示目前溫度、天氣狀況
- 顯示天氣圖示
- 具備響應式設計（RWD）
- 錯誤處理（如城市名稱錯誤時顯示提示）
```

# 🔗 參考資源

- [OpenWeatherMap API](https://openweathermap.org/api) - 免費天氣 API
- [中央氣象署開放資料平台](https://opendata.cwa.gov.tw/) - 台灣氣象資料

# 🚀 步驟

## 取得 API KEY

- 前往 [中央氣象署開放資料平台](https://opendata.cwa.gov.tw/) 註冊帳號
- 註冊後前往 [登入](https://opendata.cwa.gov.tw/userLogin)
- 登入後前往取得授權碼

## 建置後端

- fork https://github.com/gonsakon/CwaWeather-backend
- clone repo
- create `.env`

```
CWA_API_KEY=your-api-key
PORT=3000
NODE_ENV=development
```

> [!WARNING]
> `.env` 不會加入版控，部署時候要自行設定

```sh
npm install
npm start
```

- test backend on http://localhost:3000

## 部署後端

- 前往 [Zeabur](https://zeabur.com/) 新增專案
- 部署服務，選擇 GitHub Repo (需事先驗證過 GitHub)
- 新增環境變數，設定 `CWA_API_KEY`
- 自訂網域，確認服務狀態正常
- 測試端點，例如

  https://hex-cwa.zeabur.app/api/weather/kaohsiung

> [!TIP]
> 如果異常可以嘗試重啟

## 修改區域

- 研究後端程式碼與 [氣象署 API](https://openweathermap.org/api)
- 替換為自己縣市，例如 "新北市"

```js
// 呼叫 CWA API - 一般天氣預報（36小時）
// API 文件: https://opendata.cwa.gov.tw/dist/opendata-swagger.html
const response = await axios.get(
  `${CWA_API_BASE_URL}/v1/rest/datastore/F-C0032-001`,
  {
    params: {
      Authorization: CWA_API_KEY,
      locationName: "新北市",
    },
  }
);
```

- 重新推送 `push`，到 Zeabur 觀察部署狀況
- 重新測試 API，確認資料是否變更

## 建置前端

- fork https://github.com/dpi627/CwaWeather-frontend
- clone repo
- 改為自己城市，替換 API

```html
<div class="location-pill">📍 新北市</div>
```
```js
const API_URL = "https://hex-cwa.zeabur.app/api/weather/kaohsiung";
```

- publish to GitHub Pages and test

# 📋完成作業

- [GitHub Repository (backend)](https://github.com/dpi627/CwaWeather-backend)
- [Zeabur Deployment](https://hex-cwa.zeabur.app/)
- [Zeabur Endpoint](https://hex-cwa.zeabur.app/api/weather/kaohsiung)
- [GitHub Repository (frontend)](https://github.com/dpi627/CwaWeather-frontend)
- [GitHub Pages (Live Demo)](https://dpi627.github.io/CwaWeather-frontend/)

# ✨自己加碼

- 使用 AI 工具輔助開發
- 加入更多天氣資訊（濕度、風速、體感溫度等）
- 加入天氣預報功能
- 優化 UI/UX 設計

## Backend

- 取得 API Schema 連結，預備提供給 AI 理解
- 使用 GitHub Copilot in vscode
- 模型 Claude Opus 4.5
- 產出 copilot-instructions.md
- Plan Mode 進行規劃，提出規格，包含
  - 理解 API 文件
  - 城市改為變數而非固定字串
  - 36 小時 API 改為支援臺灣六都城市天氣
  - 新增六都未來三天天氣 API 端點
- 依照 Plan Mode 建議補充 Further Conditions
- 儲存 Plan 到專案中 (Open on Editor & Save)
- 執行計畫 implement `#path-to-plan`
- 本地端測試
- 重新生成 copilot-instructions.md (更新規格)
- 推送修改、等待 Zeabur 自動部署
- 前往 Zeabur 測試