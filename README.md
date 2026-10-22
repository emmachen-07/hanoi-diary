# HANOI DIARY｜河內旅行手帳

旅行日期：2026/12/10–12/14，兩人同行；臺南飛河內、河內飛高雄。

## 免費部署
1. 在 Firebase Console 建立專案，選擇免費 Spark 方案。啟用 Authentication → Sign-in method → Google。
2. 建立 Cloud Firestore 資料庫。打開 `firestore.rules`，把 `REPLACE_WITH_ADMIN_GMAIL` 改成管理員 Gmail，再將規則貼進 Firestore → Rules 並發布。
3. 在 Firebase 專案設定新增 Web App，複製 `firebaseConfig` 物件到 `firebase-config.js`，並將 `adminEmail` 設成同一個管理員 Gmail。
4. 在 Authentication → Settings → Authorized domains 加入 GitHub Pages 的網域 `你的帳號.github.io`。若 Firebase 不允許該網域或 Google 登入彈窗被瀏覽器阻擋，須依 Firebase 官方文件排查。
5. 建立公開 GitHub Repository，將 `index.html`、`app.js`、`firebase-config.js` 上傳到根目錄。在 Settings → Pages 選 Deploy from branch → main / root。稍待 GitHub Pages 產生網址。
6. 管理員及旅伴分別用自己的 Google 帳號登入。只有管理員能編輯行程、景點、路線圖、共同行李項目；兩人可記錄花費，行李勾選各自獨立。

## 注意
- 這是初版 MVP。記帳目前按幣別統計、記錄付款者與分攤備註，**尚未自動計算債務淨額**；地鐵圖目前支援圖片網址，**尚未支援直接上傳圖片**。
- Firebase 設定檔是公開的前端識別資料，不是秘密；真正的存取權限依賴 Firestore 安全規則。請勿把服務帳號私鑰放到 GitHub。
- 初次連線前本機展示資料不會自動匯入 Firebase。雲端資料首次為空，請由管理員重新建立行程。
- 免費方案有配額限制，超出配額可能限制服務。Firebase 不要求為 Spark 方案綁定付費帳戶。
- 本版未限制旅伴名單，任何獲得網址且能以 Google 登入的人都可能讀取共用資料。正式分享前建議加上兩位使用者 UID 白名單。
