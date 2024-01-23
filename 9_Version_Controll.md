# 9.版本管理

## 測試/正式

正式環境和測試環境是兩種不同的環境，各有其特定的用途：

**測試環境**：這是一個模擬正式交易的環境，提供給開發者進行整合串接測試，所有的測試均可以在測試環境上完成，可以幫助開發者在不影響實際交易內容的前提下，做好相關的驗證。

**正式環境**：正式運行的環境，會使用到正式的交易流程，該環境的 API 是真實的，並且會影響到實際的數據和系統。

## Alpha/Beta

### **Alpha**

**Alpha**版本仍然需要測試，其功能亦未完善，因為它是整個軟體釋出周期中的第一個階段，所以它的名稱是「Alpha」，[希臘字母](https://zh.wikipedia.org/wiki/%E5%B8%8C%E8%87%98%E5%AD%97%E6%AF%8D)中的第一個字母「[α](https://zh.wikipedia.org/wiki/%CE%91)」。

Alpha 版本通常會送到開發軟體的組織或某群體中的軟體測試者作[內部測試](https://zh.wikipedia.org/wiki/%E5%B0%81%E6%B8%AC)。在市場上，越來越多公司會邀請外部客戶或合作夥伴參與其測試。這令軟體在此階段有更大的可用性測試。

在測試的第一個階段中，開發者通常會進行[白盒測試](https://zh.wikipedia.org/wiki/%E7%99%BD%E7%9B%92%E6%B5%8B%E8%AF%95)。其他測試會在稍後時間由其他測試團體以[黑盒](https://zh.wikipedia.org/wiki/%E9%BB%91%E7%9B%92%E6%B8%AC%E8%A9%A6)或[灰盒](https://zh.wikipedia.org/wiki/%E7%81%B0%E7%9B%92%E6%B8%AC%E8%A9%A6)技術進行，不過有時會同時進行。

### **Beta**

**Beta**版本是軟體最早對外公開的軟體版本，由公司外的第三方開發者和業餘玩家等參與[公眾測試](https://zh.wikipedia.org/wiki/%E5%85%AC%E6%B8%AC)。 因為是 Alpha 的下一個階段，所以為希臘字母的第二個字 Beta (β)。 一般來說，Beta 包含所有功能，但可能有一些已知問題和較輕微的[程式錯誤](https://zh.wikipedia.org/wiki/%E7%A8%8B%E5%BA%8F%E9%94%99%E8%AF%AF)（BUG），要進行除錯（debug）。Beta 版本的測試者通常是開發軟體的組織的客戶，他們會以免費或優惠價錢得到軟體。Beta 版本亦作為測試產品的支援和市場反應等。

其他情況不同企業有不同的稱法，例如[微軟](https://zh.wikipedia.org/wiki/%E5%BE%AE%E8%BB%9F)曾以**Community Technology Preview**（簡稱**CTP**，中文稱為「社群技術預覽」）為發佈軟體的測試版本之一，微軟將這個階段的軟體散佈給有需要先行試用的使用者或廠商，並收集這些人的使用經驗，以便作為進一步修正軟體的參考。

## 升版原則

API 升版原則是指在開發和維護 API 時，如何進行版本控制以確保向後兼容性和系統的穩定性。

以下是一些主要的原則：

1. **向後兼容性**：當對 API 進行升級或修改時，應確保新版本的 API 能夠與舊版本的客戶端應用程式正常工作，這意味著你不能移除或更改舊版本 API 的任何功能，除非已經發布了一個新版本的 API 並給出了足夠的升級通知。
2. **版本控制**：你應該在 API 的 URL 或頭部信息中包含版本號，以便客戶端可以選擇使用哪個版本的 API。例如，你可以使用 URL 中的路徑參數（如 **`/v1/users`**）或接受頭部參數（如 **`Accept: application/vnd.company.myapp-v1+json`**）來指定 API 的版本。
3. **廢止政策**：如果打算移除舊版本的 API，應該提前通知用戶，並給他們足夠的時間來升級他們的應用程式以使用新版本的 API，也應該在 API 的文檔中清楚地標記出哪些 API 已經被廢止或即將被廢止。
4. **文檔和測試**：每當發布一個新版本的 API 時，都應該更新 API 文檔以反映任何新的或已更改的功能，提供足夠的測試工具和資源，以便開發人員可以測試他們的應用程式是否與新版本的 API 正常工作。

請注意，在進行 API 升級時，最重要的是要確保變更不會對你的用戶造成不必要的困擾或中斷。

## 廢止

API 廢止機制，也稱為 API 退役或 API 版本控制，是一種策略，用於管理 API 的生命週期。以下是一些關於 API 廢止機制的重要觀念：

1. **版本控制**：當 API 進行重大更新或改變時，通常會發布新的版本，舊版本的 API 可能會在一段時間後被廢止，但在此期間，開發者有時間適應新版本的 API。
2. **廢止通知**：當決定廢止某個 API 版本時，應提前通知開發者，這可以透過 API 的官方文檔、電子郵件通知或開發者門戶來完成。
3. **過渡期**：在 API 正式被廢止之前，應該有一段過渡期，在此期間，舊版本的 API 仍可使用，但可能不再接受新的功能更新。
4. **廢止策略**：API 的廢止策略應該在 API 的文檔中清楚地說明，這包括 API 何時會被廢止，以及開發者應如何遷移到新版本。

## Change log

Change log，也被稱為變更日誌，是一種記錄 API 版本變更的文件，它記錄了每個版本的變更，並指出哪些變更適用於當前版本，以及哪些變更適用於其他版本。

以下是一些 API 變更日誌的範例：

- [Meta Graph API](https://developers.facebook.com/docs/graph-api/changelog/)
- [Microsoft Graph](https://developer.microsoft.com/en-us/graph/changelog)
- [Google Cloud APIs](https://cloud.google.com/apis/design/changelog)
- [Shopify Developers Platform](https://shopify.dev/docs/api/release-notes)
