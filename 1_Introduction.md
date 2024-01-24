[目錄](README.md "目錄")

# 引言

> 這是 Web API 的一般設計指南，也是本平台在創建資源(Resource)時遵循的指南。使用共用相同的設計指南，方便開發人員在發現以及查找時，可以因為一致性而更加的直覺，也讓我們更容易地一起工作。

在開發人員用於構建其他軟體的軟體元件時，提供易於使用、適合用途、可擴展、可維護且在整個產品中保持一致的 API 可以決定軟體的成敗。我們強烈建議開發人員使用這些設計原則，但不強制要求，本指南適用於 REST API 。

這份指南是一個及時的文件，隨著時間推移，隨著新的風格和設計模式被採用和認可，我們將陸續添加新內容。正因如此，它永遠不會是完整的，並永遠為 API 設計的藝術和技巧留有充裕的空間。

設計具有強預設值、跨相關專案一致的行為以及開發人員易用性的強大 API，需要設身處地為使用您的介面的人著想，並將他們的擔憂放在心上。您提供的 API 會對軟體產品的運行狀況產生巨大的長期影響，這就是 REST API 管理委員會隨時為您提供説明的原因！我們發佈了一系列最佳實踐、REST 指南和 OpenAPI 風格指南，以説明您打造出色的開發人員體驗。

## 開發生態

![Developement](images/Developement.png?raw=true)

## RFC 2119

> 需求級別關鍵字「應該(Must, Required, Shall)」、「不該(Must Not, Shall not)」、「建議(Should, Recommended)」、「不建議(Should Not, Not Recommended)」，以及本文中使用的「可選(Optional)」應按照 [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt) 中的說明進行解釋。

## 用量限制

> API 用量限制是為了確保公平使用、防止濫用、維護服務穩定性而制定。

[用量限制](Limitation.md)

## Http Header

> HTTP headers 是在 HTTP 請求和回應中用來傳遞附加資訊的元素。Header 設計規範能夠提高 API 的可讀性、安全性和可維護性。良好的 HTTP Header 設計能夠提高 API 的可用性、安全性和互通性。

[Http Header 規範參考](Http_Header_Specification_Reference.md)

[目錄](README.md "目錄")
