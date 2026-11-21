# 職缺體檢 官網

職缺體檢 App 的介紹網頁，預計用 GitHub Pages 公開，網址 https://jobcheck.pocketjoystudio.com/ （pocketjoystudio.com 是工作室共用網域，這裡只用 jobcheck 子網域；`CNAME` 檔不要刪）。這個 repo 只有網頁檔案（HTML、CSS、圖片），沒有 App 或伺服器的程式。

App 只有繁體中文，所以網站也只有繁體中文，不做語言轉址。

| 網址 | 內容 |
|---|---|
| `/` | 首頁：介紹、功能、方案、資料來源、隱私重點、下載 |
| `/privacy/` | 隱私權政策（取代 https://sonia6891.github.io/job-check-app/privacy/） |
| `/support/` | 支援與常見問題、資料來源與聲明（取代 https://sonia6891.github.io/job-check-app/support/） |

- 樣式都在 `assets/style.css`；沒有外部字型、沒有追蹤碼、不需要 build。配色照 App 的 `src/theme/colors.ts`：珊瑚橘 `#FF6B4A`、奶油米 `#FBF6EE`、白。
- **隱私權政策、支援頁的內文**是從 App repo `job-check-mobile/site/privacy/index.html`、`site/support/index.html` 原封不動搬過來的（只換了頂端列和頁尾）。要改內容先改 App repo 那份，再把 `<main class="doc">` 裡面整段貼過來，不要只改這裡。
- 使用條款用 Apple 標準 EULA（和 App Store 說明一致），沒有自己的條款頁。
- 圖片來源：`assets/shots/*.jpg`、`assets/img/hero.jpg` 是 App repo `store/app-store-screenshots/實際畫面/6.9吋/` 的實際畫面縮小；圖示是 `assets/generated/app-icon.png`；`assets/img/cat.svg` 是 `src/components/CatBriefcaseArt.tsx` 的公文包貓咪轉成 SVG；`og.jpg`（1200×630）用圖示和貓咪排的。

## 數字從哪裡來（App 改了，這裡要一起改）

| 網站上的數字 | 來源 |
|---|---|
| 免費版每月完整體檢 5 份 | `job-check-mobile/src/lib/usage.ts` `FREE_MONTHLY_LIMIT = 5` |
| Pro 每月最多體檢 300 份 | `src/lib/usage.ts` `PRO_MONTHLY_LIMIT = 300` |
| Pro NT$60／月、NT$590／年 | `app/plans.tsx` `FALLBACK_PRICES`、`store/listing-zh-Hant.json` |
| 並排比較 2～5 份職缺（Pro） | `app/plans.tsx` BENEFITS、`app/compare.tsx` |
| 每月 1 日重新計算、同一份職缺當月不重複計次 | `store/listing-zh-Hant.json` 說明 |
| 30 秒找出地雷 | `app/(tabs)/index.tsx`（首頁貼上職缺卡片的說明） |
| 截圖原圖約 24 小時內刪除 | `site/privacy/index.html`、`app/(tabs)/index.tsx` |
| 165、1955 專線 | `store/listing-zh-Hant.json`、App 工具頁 |

非政府機關聲明的文字取自 `store/listing-zh-Hant.json` 的【非政府機關聲明】；資料來源清單照同一份說明的【官方政府資訊來源】。

## 上架狀態

- **iPhone**：已在台灣 App Store 上架（id 6823847793），按鈕可點。
- **Android**：還沒公開。上架後把兩個 `index.html` 區塊裡 Google Play 按鈕的 `class="store soon"` 改成 `class="store"`、拿掉 `aria-disabled="true"` 和 `<span class="tag">即將上架</span>`，再改下載區那句「Android 版即將推出」。Android 開放 Pro 時，方案區的「Pro 目前在 iPhone 版訂閱」也要改。
- App Store Connect 的支援網址、行銷網址、隱私權政策網址，以及 App 內的 `EXPO_PUBLIC_PRIVACY_POLICY_URL`，網站公開後可以改指到這裡（舊的 github.io 網址先別刪，等都改完再說）。
