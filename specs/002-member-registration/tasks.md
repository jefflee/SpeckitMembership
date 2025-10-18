# 會員註冊流程 - 任務清單

## Phase 1: 專案初始化
- [ ] T001 建立 ASP.NET Core 8.0 Web API 專案結構於 src/
- [ ] T002 設定 SQL Server 連線於 src/appsettings.json
- [ ] T003 建立 EF Core Code First 初始遷移於 src/
- [ ] T004 建立測試專案結構於 tests/
- [ ] T005 建立 contracts/openapi.yaml 並驗證 OpenAPI 合約

## Phase 2: 基礎資料模型與服務
- [ ] T006 建立 UserAccount 實體於 src/models/UserAccount.cs
- [ ] T007 建立 EmailVerification 實體於 src/models/EmailVerification.cs
- [ ] T008 建立資料庫關聯與驗證狀態流轉於 src/models/
- [ ] T009 建立 UserAccountService 於 src/services/UserAccountService.cs
- [ ] T010 建立 EmailVerificationService 於 src/services/EmailVerificationService.cs

## Phase 3: 使用者故事 1 - 基本資料註冊 (P1)
- [ ] T011 [US1] 建立註冊 API Controller 於 src/controllers/RegisterController.cs
- [ ] T012 [US1] 實作註冊流程（資料驗證、密碼規則、身分證字號唯一）於 src/services/UserAccountService.cs
- [ ] T013 [US1] 單元測試註冊流程於 tests/unit/RegisterTests.cs
- [ ] T014 [US1] 合約測試註冊 API 於 tests/contract/RegisterContractTests.cs

## Phase 4: 使用者故事 2 - Email 驗證碼確認 (P2)
- [ ] T015 [US2] 建立 Email 驗證 API Controller 於 src/controllers/EmailVerificationController.cs
- [ ] T016 [US2] 實作驗證碼發送、重發、鎖定邏輯於 src/services/EmailVerificationService.cs
- [ ] T017 [US2] 單元測試 Email 驗證流程於 tests/unit/EmailVerificationTests.cs
- [ ] T018 [US2] 合約測試 Email 驗證 API 於 tests/contract/EmailVerificationContractTests.cs

## Phase 5: 使用者故事 3 - 未驗證帳號功能限制 (P3)
- [ ] T019 [US3] 實作未驗證帳號登入與功能限制於 src/services/UserAccountService.cs
- [ ] T020 [US3] 建立登入 API Controller 於 src/controllers/LoginController.cs
- [ ] T021 [US3] 單元測試未驗證帳號登入與受限功能於 tests/unit/LoginTests.cs
- [ ] T022 [US3] 合約測試登入 API 於 tests/contract/LoginContractTests.cs

## Phase 6: Polish & Cross-Cutting Concerns
- [ ] T023 實作所有錯誤訊息繁體中文化於 src/
- [ ] T024 完善 API 文件於 contracts/openapi.yaml
- [ ] T025 完成 quickstart.md 撰寫與驗證
- [ ] T026 完成 code review 與合併

## 依賴關係
- Phase 1、2 為所有故事基礎，必須先完成
- Phase 3、4、5 可依優先順序獨立進行
- Phase 6 為收尾與品質提升

## 平行執行建議
- 註冊、Email 驗證、登入 API 及其測試可分工平行開發
- 錯誤訊息繁體中文化與 API 文件可於主流程外同步進行

## MVP 建議範圍
- 完成 Phase 1~3（註冊流程與測試）即可交付最小可用產品
