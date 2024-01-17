# Foxconn API Guideline

# 1.引言

Foxconn Cloud API

![Developement](https://github.com/CityGPT/apim-guideline/blob/main/images/Developement.png?raw=true)

## RFC 2119

需求級別關鍵字「MUST」、「MUST NOT」、“REQUIRED”、“SHALL”、 “不應”、“應該”、“不應”、“推薦”、“可以”，以及 本文檔中使用的「可選」應按照 [RFC 2119](https://maas-apim-test.developer.azure-api.net/guideline#) 中的說明進行解釋。

在本文檔中，此類關鍵字使用粗體突出顯示。

## 用量限制

> API 用量限制是為了確保公平使用、防止濫用、維護服務穩定性而制定。
> 

[用量限制](https://github.com/CityGPT/apim-guideline/blob/main/Limitation.md)

## Http Header

> HTTP headers 是在 HTTP 請求和回應中用來傳遞附加資訊的元素。Header 設計規範能夠提高 API 的可讀性、安全性和可維護性。良好的 HTTP Header 設計能夠提高 API 的可用性、安全性和互通性。
> 

[Http Header規範參考](https://github.com/CityGPT/apim-guideline/blob/main/Http_Header_Specification_Reference.md)

---

# 2.資源導向設計 Resource-Oriented Architecture (ROA)

> 設計應用程式或服務時將其建模為一系列的資源，而這些資源可被唯一的識別並通過標準化的接口進行操作
> 

## 設計流程

![StageTasks](https://github.com/CityGPT/apim-guideline/blob/main/images/StageTasks.png?raw=true)

資源來源分為開發戶和第三方服務。以五個階段的設計流程完成任務，準備、啟動、審核、設定、產出完成。

確定 API 提供什麼類型的資源。

確定資源之間的關係。

根據類型和關係確定資源命名方案。

決定資源模式。

## 資源為主

> 資源為主的 API 設計，目的是為了提供了直覺性、一致性、可擴展性和易讀性，可為開發者提供更好的使用體驗和更高的生產效率。
> 

## 最少方法

> 以最少方法附加到資源上，而盡可能的使用標準方法堆疊
> 

## 視圖區隔

1. 功能區隔：將api模組化，確保每個功能都有清晰的界面，不與其他部分直接耦合。 
2. 端點區隔：不同端點(Endpoints)分別處理不同功能，確保每個端點負責特地操作，降低端點之間的相依性 
3. 資源區隔：每個資源都有獨立的API端點，不同資源之間的操作互不相影響。 
4. 版本區隔：API引入版本控制，確保新的API不會對舊版本造成影響，使用者可以自行規劃升級時程。 
5. 權限區隔：以不同權限層級區隔，確保每個使用者或應用程式僅能訪問擁有權限的部分。

---

# 3.命名原則

## 欄位命名慣例

> API 欄位的命名原則是設計一個一致、清晰且易於理解的 API 的重要部分。
> 

[普遍原則](https://github.com/CityGPT/apim-guideline/blob/main/General_Policy.md)

API名稱命名慣例：

1. API名稱，以帕斯卡命名法(大駝峰)，例 : FieldName。
2. 以s取代List。

欄位名稱命名慣例：

1. 欄位名稱以駝峰式命名法，例：fieldName。
2. 以s取代List。

## 路徑規則

正式環境：

WS/版本/View/資源/ID/子屬性

WS/版本/View/資源:自訂動作

測試環境：

WS/環境/版本/View/資源/ID/子屬性

WS/環境/版本/View/資源:自訂動作

## RFC1035

API服務名稱參照RFC1035建議，可以被拆成一個或多個網址ip，以服務名稱為前綴詞，例如：maas.foxconn.com

---

# 4.標準方法

標準方法可以減少複雜度並增加一致性。

## 與實體數據關聯API

### 標準視圖(ABC)

標準視圖為定義對於資源操作時的視角，可以由名稱推測出使用這個視圖進行資源操作時，預期中的行爲反應。您`應該`遵循以下的定義，來規劃資源存取的存取方法。標準視圖分為三大類，分別為：

- All (Entity)
    
    All 代表使用這個方法進行資源的存取時，進行操作的是這個資源主體的完整內容。同樣的，利用同樣的視圖進行查詢作業時，預期得到的也會是對應資源的完整內容。
    
- Basic
    
    All 代表使用這個方法進行資源的存取時，進行操作的是這個資源主體的部分內容。對於資源主體的外部關聯性，都將以 Key-Value 的形式進行表示。
    
- Custom (Extended)
    
    Custom 是客製化的視圖，當對於這個資源的存取，有客製化的邏輯或是資料結構產生時，可以使用 Custom 的視圖進行規劃。而當使用客製化的方式時，視圖的命名不限於使用 Custom 或是 Extended，可以依照實際的作用進行命名的規劃。但您`應該`使用一個易於理解意圖的名稱來作為命名的原則。
    

### QCRU

| 動詞 | 類型 | Memo |
| --- | --- | --- |
| Get | Basic | 列舉所有資料 |
| Get | Basic | 取得特定資料 |
| Post | Basic | 新增資料 |
| Patch | Basic | 局部更新現有資料 |
| Put | Basic | 完整更新現有資料 |
| Get | Entity | 取得資料完整內容 |
| Get | Entity | 取得特定資料完整內容 |
| Post | Entity | 新建完整資料 |
| Patch | Entity | 局部更新資料內容 |
| Put | Entity | 完整更新現有資料 |
| Delete | Entity | 刪除資料 |
| Get | Extended | 取得關聯資料 |
| Delete | Extended | 刪除關聯資料 |

操作API的基本方法，查詢、建立、讀取、更新。

### 多語言

API底層已實現對特定欄位的多語言結構支援。當需要處理某些欄位的多語言需求時，您**應該**在模型設計階段引入底層的多語言結構，這包括建立相應的多語言表格及相關的資料關聯。

### 多租戶

多個租戶（Tenant）可以使用並共享資源，而這些租戶之間相互獨立、彼此隔離。每個租戶通常是一個組織、一個公司、或一個使用者群體，他們擁有自己的資料、設定和定制。

API底層已實現對特定欄位的多租戶結構支援。當需要處理某些欄位的多租戶需求時，您**應該**在模型設計階段引入底層的多租戶結構，這包括建立相應的多租戶表格及相關的資料關聯。

### 基本查詢條件

API底層已經支援的基本查詢條件如下：

1. **分頁支援：**
    - **`pageIndex`** 屬性：指定查詢結果的頁碼，從1起算。
    - **`pageRows`** 屬性：指定每頁的筆數，控制每次查詢返回的資料量。
2. **排序支援：**
    - **`OrderBy`** 屬性：用於指定排序條件，支援多個欄位，並且可以指定升冪或降冪排序。
3. **多語言支援：**
    - **`LangCode`** 屬性：用於指定查詢結果的語系代碼，以確保返回的資料符合指定的語言。
4. **跨語言查詢：**
    - **`CheckIsCrossLanguage`** 方法：用於確認是否設定了 **`IsCrossLanguage`** 為 **`true`**，支援跨語言查詢。

### 子查詢支援

當API的查詢取得了某些主表格的實體數據時，另外也提供相對應子查詢的API。

例：

主查詢：取得某使用者的基礎內容，

GET /api/Basic/usr/{id}

子查詢：取得某使用者的對話訊息，

GET /api/Extended/usr/{id}/UserMessages

### 狀態變更

狀態變更 API 功能旨在允許用戶根據資源的可變狀態執行不同的操作，例如標記資料是否已刪除，或者設置自訂的狀態，如審核中、已審核、退件等。

API底層已實現對特定資料的狀態變更支援。當需要處理某些資料的多租戶需求時，您**應該**在模型設計階段引入底層的狀態變更結構，這包括建立相應的狀態變更表格及相關的資料關聯。

### D刪除

刪除功能的 API 允許用戶立即刪除特定資源並且無法恢復。

# 5.自訂方法

## 環境/版本/View/資源:自訂動作

Ex:

DELETE /api/order/12345 刪除指定資料。

當需要回復時，以下列自訂動作方式標示需要進行回復資料的作業。

POST /api/order/12345:cancel

---

# 6.標準欄位

本節描述了一組標準訊息欄位定義，當需要類似概念時應使用這些定義。 這將確保相同的概念在不同的 API 中具有相同的名稱和語義。

## 名稱

### Header

| Header Key | Applies to | Example |
| --- | --- | --- |
| Authorization | Request | Bearer eyJ0...Xd6j (Support Azure Active Directory) |
| Ocp-Apim-Subscription-Key | Request | d3cafz8z4xr289d0v4dv22x2dddx6z26 |
| X-Content-Type-Options | Response | 預設值: nosniff |
| X-Frame-Options | Response | 預設值: SAMEORIGIN |
| X-Content-Security-Policy | Response | 預設值為空白，如果Host name不是localhost開頭，則為"default-src https:; script-src https: 'unsafe-inline'; style-src https: 'unsafe-inline'” |
| Content-Security-Policy | Response | 預設值為空白，如果Host name不是localhost開頭，則為"default-src https:; script-src https: 'unsafe-inline'; style-src https: 'unsafe-inline'” |
| Referrer-Policy | Response | 預設值: no-referrer |

| Name | Type | Applies to | Description |
| --- | --- | --- | --- |
| id | long | Both | 唯一識別 |
| langCode | string | Both | 語言碼 |
| targetId | long | Both | 主對象編號 |
| name | string | Both | 名稱 |
| creatorId | long | Both | 創建人 |
| createdDate | timestamp | Both | 創建時間 |
| editorId | long | Both | 最後修改人 |
| modifiedDate | timestamp | Both | 最後修改時間 |
| pageIndex | int | Both | 第幾頁(從1起算) |
| pageRows | int | Both | 每頁筆數 |
| totalRows | int | Response | 目前查詢條件下，符合條件的資料總筆數 |
| orderBy | string | Both | 排序，如果需要反向排序時，最後面可以加上 desc |
| currentLangCode | string | Response | 當前語言 |
| specifiedLangCode | string | Response | 指定語言 |
| currentUser | string | Response | 當前用戶 |
| currentTenant | string | Response | 當前租戶 (若以高市府為主，應無租戶相關資訊?) |
| currentView | string | Response | 當前視角 |
| tenantId | long | Both | 租戶 (若以高市府為主，應無租戶相關資訊?) |
| isCrossTenant | bool | Both | 允許跨租戶 (若以高市府為主，應無租戶相關資訊?) |
| status | int | Response | 狀態 |

### 查詢響應 (待確認)

| Name | Type | Description |
| --- | --- | --- |
| isSuccess | bool | 是否成功 |
| errorCode | string | 錯誤碼 |
| message | string | 訊息 |
| details | List<ResponseDetail> | 細節描述 |

**ResponseDetail Object**

通用響應

| Name | Type | Description |
| --- | --- | --- |
| target | bool | 細節對象 |
| message | string | 訊息 |

## Odata

## Json:API

---

# 7.錯誤碼

## 成功類型

200-呼叫成功

201-成功建立

202-請求已被接受

204-呼叫成功。但此操作不需要資料回應，或者該操作為一個長時間等候的操作。

## 用戶端錯誤類型

400-呼叫參數錯誤

401-無權限、身分未驗證

403-token失效

404-資源不存在

406-業務邏輯不允許

409-遇到衝突

## 伺服器端錯誤類型

500-伺服器端錯誤

---

# 8.設計模式

## 狀態及刪除

刪除操作通常使用 HTTP 的 **`DELETE`** 方法。以下是一些可能的 HTTP 狀態碼回傳：

- **200 OK**：請求成功，並且伺服器成功處理了請求。通常在成功刪除資源後回傳。
- **202 Accepted**：請求已被接受，但尚未處理。這通常用於異步操作，其中刪除操作已排入隊列，但尚未完成。
- **204 No Content**：請求成功，但沒有要回傳的內容。這通常在成功刪除資源後回傳。

## 空響應

空響應表示請求已經成功處理，但是沒有需要回傳給客戶端的內容。這種情況下，伺服器通常會回傳 HTTP 狀態碼 **`204 No Content`**。

## Fire-And-Forget

請求已被接受，但尚未處理。這通常用於異步操作，但尚未完成。

HTTP狀態碼 **`202 Accepted`**。

## 資源視圖

## 負荷上限

呼叫週期(秒)

呼叫次數

計算基準：API訂閱、IP Address、客製方式(待研究如何客製)

增量條件：Successful response (Code: 2xx)、Any request、客製方式

---

# 9.版本管理

## 測試/正式

正式環境和測試環境是兩種不同的環境，各有其特定的用途：

**測試環境**：這是一個模擬正式交易的環境，提供給開發者進行整合串接測試，所有的測試均可以在測試環境上完成，可以幫助開發者在不影響實際交易內容的前提下，做好相關的驗證。

**正式環境**：正式運行的環境，會使用到正式的交易流程，該環境的API是真實的，並且會影響到實際的數據和系統。

## Alpha/Beta

### **Alpha**

**Alpha**版本仍然需要測試，其功能亦未完善，因為它是整個軟體釋出周期中的第一個階段，所以它的名稱是「Alpha」，[希臘字母](https://zh.wikipedia.org/wiki/%E5%B8%8C%E8%87%98%E5%AD%97%E6%AF%8D)中的第一個字母「[α](https://zh.wikipedia.org/wiki/%CE%91)」。

Alpha版本通常會送到開發軟體的組織或某群體中的軟體測試者作[內部測試](https://zh.wikipedia.org/wiki/%E5%B0%81%E6%B8%AC)。在市場上，越來越多公司會邀請外部客戶或合作夥伴參與其測試。這令軟體在此階段有更大的可用性測試。

在測試的第一個階段中，開發者通常會進行[白盒測試](https://zh.wikipedia.org/wiki/%E7%99%BD%E7%9B%92%E6%B5%8B%E8%AF%95)。其他測試會在稍後時間由其他測試團體以[黑盒](https://zh.wikipedia.org/wiki/%E9%BB%91%E7%9B%92%E6%B8%AC%E8%A9%A6)或[灰盒](https://zh.wikipedia.org/wiki/%E7%81%B0%E7%9B%92%E6%B8%AC%E8%A9%A6)技術進行，不過有時會同時進行。

### **Beta**

**Beta**版本是軟體最早對外公開的軟體版本，由公司外的第三方開發者和業餘玩家等參與[公眾測試](https://zh.wikipedia.org/wiki/%E5%85%AC%E6%B8%AC)。 因為是Alpha的下一個階段，所以為希臘字母的第二個字Beta (β)。 一般來說，Beta包含所有功能，但可能有一些已知問題和較輕微的[程式錯誤](https://zh.wikipedia.org/wiki/%E7%A8%8B%E5%BA%8F%E9%94%99%E8%AF%AF)（BUG），要進行除錯（debug）。Beta版本的測試者通常是開發軟體的組織的客戶，他們會以免費或優惠價錢得到軟體。Beta版本亦作為測試產品的支援和市場反應等。

其他情況不同企業有不同的稱法，例如[微軟](https://zh.wikipedia.org/wiki/%E5%BE%AE%E8%BB%9F)曾以**Community Technology Preview**（簡稱**CTP**，中文稱為「社群技術預覽」）為發佈軟體的測試版本之一，微軟將這個階段的軟體散佈給有需要先行試用的使用者或廠商，並收集這些人的使用經驗，以便作為進一步修正軟體的參考。

## 升版原則

API升版原則是指在開發和維護API時，如何進行版本控制以確保向後兼容性和系統的穩定性。

以下是一些主要的原則：

1. **向後兼容性**：當對API進行升級或修改時，應確保新版本的API能夠與舊版本的客戶端應用程式正常工作，這意味著你不能移除或更改舊版本API的任何功能，除非已經發布了一個新版本的API並給出了足夠的升級通知。
2. **版本控制**：你應該在API的URL或頭部信息中包含版本號，以便客戶端可以選擇使用哪個版本的API。例如，你可以使用URL中的路徑參數（如 **`/v1/users`**）或接受頭部參數（如 **`Accept: application/vnd.company.myapp-v1+json`**）來指定API的版本。
3. **廢止政策**：如果打算移除舊版本的API，應該提前通知用戶，並給他們足夠的時間來升級他們的應用程式以使用新版本的API，也應該在API的文檔中清楚地標記出哪些API已經被廢止或即將被廢止。
4. **文檔和測試**：每當發布一個新版本的API時，都應該更新API文檔以反映任何新的或已更改的功能，提供足夠的測試工具和資源，以便開發人員可以測試他們的應用程式是否與新版本的API正常工作。

請注意，在進行API升級時，最重要的是要確保變更不會對你的用戶造成不必要的困擾或中斷。

## 廢止

API廢止機制，也稱為API退役或API版本控制，是一種策略，用於管理API的生命週期。以下是一些關於API廢止機制的重要觀念：

1. **版本控制**：當API進行重大更新或改變時，通常會發布新的版本，舊版本的API可能會在一段時間後被廢止，但在此期間，開發者有時間適應新版本的API。
2. **廢止通知**：當決定廢止某個API版本時，應提前通知開發者，這可以透過API的官方文檔、電子郵件通知或開發者門戶來完成。
3. **過渡期**：在API正式被廢止之前，應該有一段過渡期，在此期間，舊版本的API仍可使用，但可能不再接受新的功能更新。
4. **廢止策略**：API的廢止策略應該在API的文檔中清楚地說明，這包括API何時會被廢止，以及開發者應如何遷移到新版本。

## Change log

Change log，也被稱為變更日誌，是一種記錄API版本變更的文件，它記錄了每個版本的變更，並指出哪些變更適用於當前版本，以及哪些變更適用於其他版本。

以下是一些API變更日誌的範例：

- [Meta Graph API](https://developers.facebook.com/docs/graph-api/changelog/)
- [Microsoft Graph](https://developer.microsoft.com/en-us/graph/changelog)
- [Google Cloud APIs](https://cloud.google.com/apis/design/changelog)
- [Shopify Developers Platform](https://shopify.dev/docs/api/release-notes)

---

# 10.詞彙

## 系統共用名稱定義