[目錄](README.md "目錄")

# 標準欄位

本節描述了一組標準訊息欄位定義，當需要類似概念時應使用這些定義。 這將確保相同的概念在不同的 API 中具有相同的名稱和語義。

## 名稱

### Header

| Header Key                | 應用於   | 說明                                                                                                                                            |
| ------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Authorization             | Request  | IDP 驗證訊息，例如 : Bearer eyJ0...Xd6j                                                                                                         |
| Ocp-Apim-Subscription-Key | Request  | APIM 驗證訊息，例如 : d3cafz8z4xr289d0v4dv22x2dddx6z26                                                                                          |
| Content-Language          | Request  | 指定語言 : en                                                                                                                                   |
| X-Api-Version             | Response | 指定版本編號
| X-Content-Type-Options    | Response | 預設值: nosniff                                                                                                                                 |
| X-Frame-Options           | Response | 預設值: SAMEORIGIN                                                                                                                              |
| X-Content-Security-Policy | Response | 預設值為空白，如果 Host name 不是 localhost 開頭，則為"default-src https:; script-src https: 'unsafe-inline'; style-src https: 'unsafe-inline'” |
| Content-Security-Policy   | Response | 預設值為空白，如果 Host name 不是 localhost 開頭，則為"default-src https:; script-src https: 'unsafe-inline'; style-src https: 'unsafe-inline'” |
| Referrer-Policy           | Response | 預設值: no-referrer                                                                                                                             |

| Name              | Type      | Applies to | Description                                    |
| ----------------- | --------- | ---------- | ---------------------------------------------- |
| id                | long      | Both       | 唯一識別                                       |
| langCode          | string    | Both       | 語言碼                                         |
| targetId          | long      | Both       | 主對象編號                                     |
| name              | string    | Both       | 名稱                                           |
| creatorId         | long      | Both       | 創建人                                         |
| createdDate       | timestamp | Both       | 創建時間                                       |
| editorId          | long      | Both       | 最後修改人                                     |
| modifiedDate      | timestamp | Both       | 最後修改時間                                   |
| pageIndex         | int       | Both       | 第幾頁(從 1 起算)                              |
| pageRows          | int       | Both       | 每頁筆數                                       |
| totalRows         | int       | Response   | 目前查詢條件下，符合條件的資料總筆數           |
| orderBy           | string    | Both       | 排序，如果需要反向排序時，最後面可以加上 desc  |
| currentLangCode   | string    | Response   | 當前語言                                       |
| specifiedLangCode | string    | Response   | 指定語言                                       |
| currentUser       | string    | Response   | 當前用戶                                       |
| currentTenant     | string    | Response   | 當前租戶 (若以高市府為主，應無租戶相關資訊?)   |
| currentView       | string    | Response   | 當前視角                                       |
| tenantId          | long      | Both       | 租戶 (若以高市府為主，應無租戶相關資訊?)       |
| isCrossTenant     | bool      | Both       | 允許跨租戶 (若以高市府為主，應無租戶相關資訊?) |
| status            | int       | Response   | 狀態                                           |

### 查詢響應 (待確認)

#### 成功

| Name      | Type     | Description                                 |
| --------- | -------- | ------------------------------------------- |
| pageIndex | int      | 目前指定的頁數                              |
| pageRows  | int      | 目前指定的每頁筆數                          |
| totalRows | int      | 目前查詢條件下，符合條件的資料總筆數        |
| Data      | [Object] | 物件清單，物件定義**必需**在 API 文件中定義 |

#### 失敗

| Name      | Type             | Description |
| --------- | ---------------- | ----------- |
| isSuccess | bool             | 是否成功    |
| errorCode | string           | 錯誤碼      |
| message   | string           | 訊息        |
| details   | [ResponseDetail] | 細節描述    |

**ResponseDetail Object**

| Name    | Type   | Description |
| ------- | ------ | ----------- |
| target  | bool   | 細節對象    |
| message | string | 訊息        |

## Odata

> Open Data Protocol (OData)是微軟支持且定義出來的網頁開放式資料協定，此協定支援 ATOM Publishing Protocol(AtomPub，XML)及 JSON 格式，在最新 OData 4.0 版本使用 REST 原則，近期被 OASIS 委員會所採納。

[OData]("https://www.odata.org") 支援資料模型的描述及根據資料模型的資料進行查詢與更新功能，協定的規則來自於 REST 規範，並透過既有的 HTTP 加上標準的 CRUD 方式所組成。而 OData 的設計原則依循以下幾個理念：

1. 傾向機器能儲存各種資料來源
2. 服務能支援拓展性的功能
3. 以 REST 設計原則為導向
4. 容易地建立兼容的服務
5. 保持簡單

OData 定義了查詢語言，在 URI 網址後附加可供選擇的查詢方法，包含以下幾種：

1. $top = n 表示回傳前 n 筆資料。
2. $skip = n 表示略過前 n 筆資料。
3. $format 決定資料回傳的格式是 JSON 或是 XML 的 AtomPub。
4. $orderby 決定資料的結果排序是升冪或降冪。
5. $filter 回傳符合特定表達式的資料。
6. $select 回傳資料的某些欄位。

[目錄](README.md "目錄")
