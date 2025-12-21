# 🌏 台灣空氣品質 3D 視覺化地圖 (Taiwan AQI 3D Map)

這是一個基於 Web 的 3D 互動地圖，用於即時視覺化台灣各地的空氣品質指標 (AQI)。透過 3D 柱狀圖的高度與顏色，讓使用者能直觀地感受目前的空氣污染程度。

[👉 點擊這裡查看 Demo ](https://nono0325.github.io/taiwan-aqi-3d/)

## ✨ 特色 (Features)

  * **即時資料更新**：直接串接台灣環境部 (MOENV) 開放資料 API，獲取最新每小時數據。
  * **3D 互動體驗**：
      * **高度 (Elevation)**：柱狀體高度對應 AQI 數值，數值越高柱子越高。
      * **顏色 (Color)**：依照標準 AQI 顏色分級（綠、黃、橘、紅、紫、褐）。
  * **地圖控制**：支援旋轉 (Pitch/Bearing)、縮放與平移，使用深色地圖風格 (Dark Mode) 以突顯數據。
  * **互動資訊框**：滑鼠懸停 (Hover) 於測站上方時，顯示詳細數據（測站名稱、AQI、PM2.5）。

## 🛠️ 使用技術 (Tech Stack)

  * **HTML5 / CSS3 / Vanilla JavaScript**：純原生語法，無需編譯打包。
  * **[Deck.gl](https://deck.gl/)**：由 Uber 開源的高效能 WebGL 資料視覺化框架，用於繪製 3D Column Layer。
  * **[MapLibre GL JS](https://maplibre.org/)**：開源的地圖渲染引擎，用於載入底圖。
  * **Open Data API**：[環境部環境資源資料開放平臺](https://data.moenv.gov.tw/)。

## 🚀 如何執行 (How to Run)

### 方法 1：直接開啟 (最簡單)

由於這是一個靜態網頁專案，您只需要：

1.  下載本專案的 `index.html`。
2.  直接用瀏覽器 (Chrome, Edge, Firefox) 開啟該檔案即可。

### 方法 2：GitHub Pages (推薦)

1.  將本專案上傳至 GitHub Repository。
2.  進入 **Settings** -\> **Pages**。
3.  將 Branch 設定為 `main` 並儲存。
4.  獲得專屬網址，分享給朋友。

### 方法 3：使用 Docker (給開發者的進階選項)

如果您想在本地端模擬 Web Server 環境（避免某些瀏覽器的 CORS 限制），可以使用 Nginx：

```bash
# 在專案目錄下執行
docker run --rm -d -p 8080:80 -v $(pwd):/usr/share/nginx/html nginx
```

接著打開瀏覽器訪問 `http://localhost:8080` 即可。

## 📂 資料結構說明

本專案使用 API 回傳的 JSON 格式進行解析，主要使用以下欄位：

| 欄位名稱 | 說明 | 用途 |
| :--- | :--- | :--- |
| `sitename` | 測站名稱 | Tooltip 顯示 |
| `aqi` | 空氣品質指標 | 決定 3D 柱狀體的高度與顏色 |
| `longitude` | 經度 | 定位座標 |
| `latitude` | 緯度 | 定位座標 |
| `pm2.5` | 細懸浮微粒 | Tooltip 顯示 |

## ⚠️ 注意事項

  * **API Key**：目前的程式碼內含環境部公開 API 範例 Key，若用於高流量正式產品，建議至環境部平台申請專屬 API Key。
  * **CORS**：此 API 支援跨網域存取 (CORS)，因此可以直接在純前端網頁中呼叫。

## 📜 授權 (License)

MIT License.

-----

**資料來源**：行政院環境部 (Ministry of Environment)
