# 資料模型設計

## 使用者帳號（UserAccount）
- Id (int, PK)
- 身分證字號 (string, unique, required)
- 姓名 (string, required)
- 密碼雜湊值 (string, required)
- Email (string, required)
- Email 驗證狀態 (enum: Unverified, Verified, Locked)
- Email 驗證鎖定結束時間 (datetime, nullable)
- 建立時間 (datetime)
- 最後登入時間 (datetime, nullable)

## Email 驗證（EmailVerification）
- Id (int, PK)
- UserAccountId (int, FK)
- 驗證碼 (string, required)
- 發送時間 (datetime, required)
- 有效期限 (datetime, required)
- 驗證狀態 (enum: Unverified, Verified, Locked)
- 錯誤次數 (int, default 0)
- 鎖定結束時間 (datetime, nullable)

## 驗證狀態流轉
- 註冊完成 → Unverified
- 驗證碼正確 → Verified
- 驗證碼錯誤達 5 次 → Locked（10 分鐘後自動回復 Unverified）
