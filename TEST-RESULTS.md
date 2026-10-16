# 驗證結果

日期：2026-10-16。環境：Linux / Google Chrome headless / Playwright，直接以 file:// 載入。

- JavaScript 以 Node vm.Script 語法解析通過。
- 1440、1024、810、768、390、320 px 六種寬度 × 四區，共 24 組導覽及 document scrollWidth 檢查通過，無水平溢出。
- 1440 與 390 px 四區皆產生全頁截圖（screenshots/）。人工目視桌機總覽、手機總覽與個人資料；調整手機頁首以避免標題被日期擠壓。
- 男性 30 歲 / 175 cm / 70 kg：BMR 1648.75，畫面 1,649；久坐 TDEE 1978.5，畫面 1,979。相同女性資料 BMR 1482.75，通過。
- 未成年年齡、空白餐名、負熱量拒絕；合法資料儲存與 reload 恢復通過。
- PNG 上傳預覽解碼、儲存後清除預覽通過。
- 餐點新增、600+200=800 合計、跨日期 300 kcal、重整、刪除取消/確認通過。
- HTML 注入字串以純文字呈現，未生成 img 元素。
- 手動位置與餐飲種類正確 URL encode 到 Google Maps Search URL。
- 定位以測試替身確認按鈕前不呼叫、按下才呼叫、成功座標連結、手動輸入取代定位、定位失敗提示。
- 清除全部取消/確認、localStorage 移除、損壞 JSON 提示、模擬 quota exception 後保留暫存與警告，皆通過。
- 測試全程無 pageerror，無外部網路請求（只有 file/blob）。

## 未驗證
真實 GPS、手機相機與系統權限對話框、外部 Google 地圖結果、Safari/Firefox、聊天 App 預覽器、實體手機與安全區域。本次定位成功/拒絕為模擬，並未取得或傳送真實位置。照片大檔/格式錯誤分支與 localStorage.removeItem 失敗分支有實作，未在自動測試逐項觸發。非全面 WCAG 稽核。
