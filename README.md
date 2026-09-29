# 總務處小提醒｜新生訓練簡報

泰山高級中學新生訓練用的總務處業務互動簡報，霓虹科技／星空風格，單一 HTML 檔案、零建置、可直接部署到 GitHub Pages。

## 專案簡介

每年新生訓練時，總務處需要向新生說明冷氣卡儲值、報修分流、註冊繳費、蒸飯箱使用等幾件「開學前一定要知道」的事。這個專案把這些提醒做成一份「插播快報」形式的互動簡報，以霓虹綠／藍／紫配色搭配星空背景、流星、行星等動態效果呈現，讓原本枯燥的行政宣導變得有記憶點，同時也方便新生訓練結束後隨時用手機掃碼回顧。

適用對象：學校總務處人員（簡報維護者）、新生訓練現場播放（教師／主持人操作翻頁）、新生本人（會後掃碼複習）。

## 功能特色

- **霓虹星空視覺風格**：CSS 漸層、模糊光暈、流星動畫、行星漂浮動畫，純 CSS/JS 打造，無外部圖庫或框架依賴
- **共 7 頁投影片內容**：
  1. 封面（插播快報樣式，含跑馬燈 LIVE 快訊）
  2. 冷氣卡儲值時間（每週三上午下課時段，隔日領取）
  3. 報修分流（生活設施找總務處／教學設備找設備組）
  4. 註冊繳費與匯款（線上辦理、獎補助匯款、出納組諮詢）
  5. 蒸飯箱使用異動（不再隨班提供，需至總務處前使用）
  6. 自我檢核清單（可勾選、狀態存於瀏覽器 localStorage，全部勾完會顯示提示訊息）
  7. QR Code 頁（供新生掃碼存回手機隨時複習）
- **多種操作方式**：鍵盤 ← / → 或空白鍵翻頁；手機左右滑動翻頁，或點畫面左右側區域
- **全螢幕切換**：內建全螢幕按鈕（`toggleFullscreen()`），適合投影時使用
- **檢核清單狀態記憶**：使用者勾選過的項目透過 `localStorage` 保存，重新整理頁面不會消失
- **零依賴、零建置**：整份簡報只有一個 `index.html`（內含所有 CSS／JS），沒有任何 npm 套件或建置流程

## 環境需求

- 純前端靜態網頁，不需要任何後端、資料庫或 API 金鑰
- 瀏覽器即可開啟（Chrome／Safari／Edge 等現代瀏覽器皆可，支援桌機與手機）
- 部署使用 GitHub Pages，不需要額外的建置工具或執行環境

## 安裝方式 / 快速開始

本機預覽：

```bash
git clone https://github.com/unique487/tssh-ga-freshman.git
cd tssh-ga-freshman
# 直接用瀏覽器開啟 index.html 即可，或啟動簡易伺服器
python -m http.server 8000
# 瀏覽器開啟 http://localhost:8000
```

線上瀏覽（已部署於 GitHub Pages）：
https://unique487.github.io/tssh-ga-freshman/

## 使用方法

- **播放簡報**：開啟 `index.html`，用鍵盤 ← / → 或空白鍵翻頁；觸控裝置可左右滑動，或點擊畫面左右側
- **全螢幕播放**：點擊簡報上的全螢幕按鈕（適合投影機播放）
- **內容更新**：直接編輯 `index.html` 裡對應的 `<section class="slide">` 區塊，修改文字或資料後 commit、push 到預設分支 `main`，GitHub Pages 約 1 分鐘後自動生效
- **更換圖片素材**：把新的圖檔放進 `assets/`，並在 `index.html` 中更新對應的 `<img src="assets/...">` 路徑
- **QR Code**：`assets/qr.png` 對應到第 7 頁，掃描後會開啟本簡報網址（頁面中的 `deck-url` / `deck-open` 由 JS 動態帶入目前網址）

## 資料夾結構

```
tssh-ga-freshman/
├── index.html          # 簡報主體，內含全部 CSS 樣式與 JS 邏輯（翻頁、全螢幕、檢核清單）
├── .nojekyll            # 停用 GitHub Pages 的 Jekyll 處理，確保靜態檔案原樣發布
└── assets/
    ├── tssh_logo.png     # 校徽
    ├── awen_bust.png     # 代言角色 A-WEN 半身圖
    ├── awen_neon.png     # 代言角色 A-WEN 霓虹版（封面使用）
    ├── anchor_desk.png   # 主播台背景圖
    └── qr.png            # 簡報網址 QR Code（第 7 頁使用）
```

## 技術棧

- 純 HTML / CSS / JavaScript（vanilla，無任何前端框架）
- CSS 自訂屬性（CSS variables）管理配色主題
- CSS `@keyframes` 動畫（星空漂移、流星、行星、跑馬燈等視覺效果）
- 瀏覽器原生 `localStorage`（記錄自我檢核清單勾選狀態）
- 瀏覽器原生 Fullscreen API（全螢幕播放）
- GitHub Pages 靜態網站託管
