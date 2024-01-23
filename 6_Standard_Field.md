# 6.標準欄位

本節描述了一組標準訊息欄位定義，當需要類似概念時應使用這些定義。 這將確保相同的概念在不同的 API 中具有相同的名稱和語義。

## 名稱

### Header

| Header Key                | Applies to | Example                                                                                                                                         |
| ------------------------- | ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Authorization             | Request    | Bearer eyJ0...Xd6j (Support Azure Active Directory)                                                                                             |
| Ocp-Apim-Subscription-Key | Request    | d3cafz8z4xr289d0v4dv22x2dddx6z26                                                                                                                |
| X-Content-Type-Options    | Response   | 預設值: nosniff                                                                                                                                 |
| X-Frame-Options           | Response   | 預設值: SAMEORIGIN                                                                                                                              |
| X-Content-Security-Policy | Response   | 預設值為空白，如果 Host name 不是 localhost 開頭，則為"default-src https:; script-src https: 'unsafe-inline'; style-src https: 'unsafe-inline'” |
| Content-Security-Policy   | Response   | 預設值為空白，如果 Host name 不是 localhost 開頭，則為"default-src https:; script-src https: 'unsafe-inline'; style-src https: 'unsafe-inline'” |
| Referrer-Policy           | Response   | 預設值: no-referrer                                                                                                                             |

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

## Json:API
