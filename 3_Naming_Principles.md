[目錄](README.md "目錄")

# 3.命名原則

## 欄位命名慣例

> API 欄位的命名原則是設計一個一致、清晰且易於理解的 API 的重要部分。

[普遍原則](./General_Policy.md)

API 名稱命名慣例：

1. API 名稱，以帕斯卡命名法(大駝峰)，例 : FieldName。
2. 以 s 取代 List。

欄位名稱命名慣例：

1. 欄位名稱以駝峰式命名法，例：fieldName。
2. 以 s 取代 List。

## 路徑規則

正式環境：

​ WS/版本/View/資源/ID/子屬性

​ WS/版本/View/資源:自訂動作

測試環境：

​ WS/環境/版本/View/資源/ID/子屬性

​ WS/環境/版本/View/資源:自訂動作

## RFC1035

API 服務名稱參照 RFC1035 建議，可以被拆成一個或多個網址 ip，以服務名稱為前綴詞，例如：maas.foxconn.com

[目錄](README.md "目錄")
