# Alvin's CD Library

個人 CD 收藏展示頁，單一 HTML 檔案，無需後端或建置工具，直接用瀏覽器開啟即可使用。

---

## 功能

### 瀏覽與篩選
- **字母索引**：點擊 header 右上角的字母，快速跳至該字母開頭的藝人區塊
- **搜尋**：即時過濾藝人名稱或專輯名稱（支援中英文）
- **排序**：可依藝人名稱 A–Z、專輯名稱 A–Z、發行年份升冪／降冪排列

### 專輯卡片
- 自動從 iTunes Search API 抓取封面圖，有 Apple Music 連結的專輯優先以 `itunes/lookup` 取得
- 顯示藝人、專輯名稱、發行年份、曲風標籤、廠牌
- 點擊卡片上的 Apple Music 連結可直接開啟對應頁面

### 隨機挑選
- Header 排序選單右側有「挑選」按鈕
- 點擊後跳出 Modal，以**滾輪動畫**（slot machine）翻過多張封面後減速停在抽中的專輯
- 採用 **Shuffle Bag**（無放回抽樣）機制：
  - 每輪 64 張專輯各出現恰好一次，機率完全均等
  - 全部抽完才重新洗牌，進入下一輪
- Modal 內可點「再挑一張」繼續抽，或點「 Apple Music」直接開啟

---

## 資料結構

專輯資料定義在 `index.html` 底部的 `RAW` 陣列，每筆格式如下：

```js
["藝人", "專輯名稱", "年份", "曲風", "廠牌", "Apple Music URL"]
```

新增或修改專輯只需編輯這個陣列，其餘樣式與功能自動套用。

---

## 技術細節

| 項目 | 說明 |
|------|------|
| 架構 | 純 HTML / CSS / Vanilla JS，單檔案，無 framework |
| 字型 | Inter（Google Fonts） |
| 封面來源 | iTunes Search API（`itunes.apple.com/search` & `/lookup`） |
| 隨機演算法 | Fisher-Yates shuffle + pop（Shuffle Bag） |
| 滾輪動畫 | requestAnimationFrame + ease-out cubic 緩動 |
| 深色模式 | 跟隨系統（`@media (prefers-color-scheme: dark)`） |
| 響應式 | 支援手機版，Header 控制列自動折行，按鈕尺寸縮放 |

---

## 本地開啟

直接用瀏覽器開啟 `index.html` 即可，iTunes API 為跨域請求，現代瀏覽器不需額外設定。

```bash
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux
```

---

## 目前收藏數量

63 張，橫跨 Rock、Metal、Jazz、Alternative、Electronic、J-Pop、華語流行樂、獨立搖滾等曲風。
