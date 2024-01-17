# Http Header規範參考

### **1. 命名規範（Naming Convention）:**

- 使用大寫字母，並使用破折號（hyphen）分隔單詞，例如：**`Content-type`**。
- 遵從 RFC 2616 中的標準命名規範。

### **2. Content-Type 和 Accept:**

- 正確設定 **`Content-Type`**，指定發送請求的內容類型。
- 正確設定 **`Accept`**，指定期望接收的回應的內容類型。

### **3. 認證和授權（Authentication and Authorization）:**

- 使用標準的 **`Authorization`** header 來傳遞身份驗證資訊。
- 避免在 URL 中明文傳遞認證資訊。

### **4. 緩存控制（Cache Control）:**

- 使用 **`Cache-Control`** header 控制緩存行為。
- 避免不必要的緩存，特別是對於包含敏感資訊的請求或回應。

### **5. 跨域資源共用（CORS）:**

- 如果涉及跨域請求，使用 **`Access-Control-Allow-Origin`** 和相關的 CORS headers 進行設定。

### **6. 安全性（Security）:**

- 使用 **`Strict-Transport-Security`** header 促使使用者端使用 HTTPS。
- 使用 **`Content-Security-Policy`** header 以限制內容來源，提高安全性。

### **7. 重定向（Redirection）:**

- 使用 **`Location`** header 正確處理重定向。
- 避免無限重定向迴圈。

### **8. 日期和時間（Date and Time）:**

- 使用 **`Date`** header 提供正確的日期和時間信息。
- 避免使用過期的 **`Expires`** header。

### **9. 壓縮（Compression）:**

- 使用 **`Accept-Encoding`** header 表明客戶端是否支援壓縮。
- 使用 **`Content-Encoding`** header 表明回應內容是否被壓縮。

### **10. 自訂 Headers:**

- 避免使用非標準的自訂 headers，除非有足夠的理由。
- 如果使用自訂 headers，應該遵從慣例和文檔。

### **11. 版本控制（Versioning）:**

- 如果支援多個 API 版本，可以考慮使用自訂 header 或 URI 中的版本號。

### **12. 請求和回應大小（Request and Response Size）:**

- 考慮使用 **`Content-Length`** 或 **`Transfer-Encoding`** header 正確報告請求和回應的大小。

### **13. 追蹤和日誌（Tracking and Logging）:**

- 使用適當的 headers 或其他機制來方便追蹤和日誌。

### **14. 適用標準（Applicable Standards）:**

- 遵守相關的 HTTP 標準和相關的 RFC 文件。