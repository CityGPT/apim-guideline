# 用量限制

1. **請求速率限制（Request Rate Limiting）:**
    - 確定每個使用者或應用程式每分鐘/小時可以發送的請求數量。
    - 考慮不同使用者類型（例如免費、付費、內部用戶）的不同限制。
2. **配額（Quotas）:**
    - 考慮每個使用者或應用程式的每日、每週或每月請求配額。
    - 區分不同使用者類型的配額，以鼓勵付費用戶。
3. **並發請求限制（Concurrent Request Limiting）:**
    - 考慮限制同一使用者或應用程式同時進行的請求數量。
    - 確保伺服器資源不被單一使用者過多請求佔用。
4. **數據量限制（Data Volume Limiting）:**
    - 確定單一請求中允許的最大數據量。
    - 防止單一請求過大占用過多帶寬和伺服器資源。
5. **特定端點的限制（Endpoint-Specific Limitations）:**
    - 考慮根據不同端點或資源設定不同的用量限制。
    - 針對常被使用的端點提供更高的限制。
6. **API 金鑰的使用限制（API Key Usage Limitations）:**
    - 確保 API 金鑰的使用是受限的，以防止濫用。
    - 監控金鑰的使用情況，並及時撤銷或更新被濫用的金鑰。
7. **報價和支付方案（Quoting and Billing Plans）:**
    - 如果提供付費方案，制定不同的配額和限制，供內部或外部計價。
    - 提供透明計費方式。
8. **錯誤限制（Error Limitations）:**
    - 考慮限制由於錯誤而引起的重複請求或錯誤請求。
    - 防止過多的錯誤請求對伺服器造成負擔。
9. **通知和監控（Notification and Monitoring）:**
    - 提供使用者監控或訂閱其用量的工具和通知機制。
    - 警告使用者當前用量接近限制。

![Monitoring_Indicators](https://github.com/CityGPT/apim-guideline/blob/main/images/Monitoring_Indicators.png?raw=true)