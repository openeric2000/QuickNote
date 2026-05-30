# QuickNote

QuickNote 是一個以單一 HTML 檔運作的客戶備忘錄工具，適合用來快速記錄客戶名稱、送貨日期、商品內容、送貨方式與備註。資料直接保存在瀏覽器 localStorage，不需要資料庫，也不需要額外後端。

## 功能

- 新增、編輯、刪除客戶紀錄
- 依客戶名、日期、貨品、行政區、送貨方式或備註搜尋
- 多選刪除目前列表中的紀錄
- 維護送貨方式選項
- 直接開啟、儲存、匯入與匯出 JSON 資料
- 以 GitHub Pages 部署靜態網站

## 技術組成

- 單頁應用：index.html
- 前端框架：Vue 3（CDN 載入）
- 資料儲存：瀏覽器 localStorage
- 部署方式：GitHub Actions + GitHub Pages

## 本機使用

1. 直接用瀏覽器開啟 index.html。
2. 開始新增與管理客戶備忘錄。
3. 所有資料會保存在目前瀏覽器的 localStorage。

如果需要更接近正式站的使用方式，也可以在專案根目錄啟動簡單靜態伺服器，例如：

```powershell
python -m http.server 8080
```

啟動後開啟 http://localhost:8080。

## GitHub Pages 部署

repo 內已加入 GitHub Actions workflow：.github/workflows/deploy-pages.yml。

建議設定如下：

1. 到 GitHub Repository Settings -> Pages。
2. Build and deployment 的 Source 改成 GitHub Actions。
3. push 到 main 後，Actions 會自動部署目前專案內容。

這樣可以避開 GitHub 內建 pages-build-deployment 流程目前出現的 Node.js 20 deprecation warning，並改由 repo 自己控制部署版本。

## 資料注意事項

- localStorage 只存在目前瀏覽器與裝置。
- 清除瀏覽器資料後，備忘錄內容也會一起消失。
- 若要跨裝置使用，建議先透過畫面中的 JSON 開啟 / 儲存 / 下載副本流程備份資料。
- 若要使用直接開啟與儲存 JSON，建議使用支援 File System Access API 的現代瀏覽器。

## 專案結構

```text
QuickNote/
|-- .github/
|   `-- workflows/
|       `-- deploy-pages.yml
|-- index.html
`-- README.md
```
