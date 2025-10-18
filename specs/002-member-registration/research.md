# 研究與決策記錄

## 技術選型

- **決策**：ASP.NET Core 8.0 Web API
  - **理由**：現代化、高效能、社群活躍，支援 RESTful 設計，與 SQL Server 整合佳。
  - **替代方案**：Node.js、Spring Boot、Django（但團隊現有 .NET 經驗最佳）

- **決策**：SQL Server
  - **理由**：企業級資料庫，與 .NET/EF Core 整合完善，支援交易與高可用性。
  - **替代方案**：PostgreSQL、MySQL

- **決策**：EF Core Code First
  - **理由**：可直接以 C# 類別設計資料結構，方便維護與遷移。
  - **替代方案**：Database First、Dapper

- **決策**：POCO DTO（不使用 AutoMapper）
  - **理由**：減少額外依賴，提升可讀性與除錯效率。
  - **替代方案**：AutoMapper

- **決策**：不使用 Redis
  - **理由**：本功能不需快取跨請求狀態，避免不必要的複雜度。

- **決策**：不使用 Minimal APIs
  - **理由**：維持傳統 Controller 架構，利於分層與測試。

## 測試策略
- 單元測試：xUnit + FluentAssertions
- 合約測試：OpenAPI 驗證
- 整合測試：TestServer 模擬 API

## 其他
- 所有規格、計畫、文件、錯誤訊息皆以繁體中文撰寫
- 不含前端實作
