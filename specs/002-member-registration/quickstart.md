# 快速開始指南

## 專案需求
- .NET 8.0 SDK
- SQL Server 2019 以上

## 建置步驟
1. 下載原始碼並切換至 `002-member-registration` 分支
2. 設定 `appsettings.json` 連線字串
3. 執行 `dotnet ef database update` 建立資料庫
4. 執行 `dotnet test` 驗證測試通過
5. 執行 `dotnet run` 啟動 API 服務

## 測試說明
- 所有 API 測試皆可用 Postman 或 Swagger UI 驗證
- 測試帳號請參考測試資料腳本

## 注意事項
- 不支援 Minimal APIs、Redis、AutoMapper
- 所有錯誤訊息與 API 回應皆為繁體中文
