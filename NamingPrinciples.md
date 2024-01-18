# 命名原則

API 及欄位的命名原則是設計一個一致、清晰且易於理解的 API 的重要部分。
API 名稱命名慣例：

1. API 名稱，以帕斯卡命名法(大駝峰)，例 : FieldName。
2. 以 s 取代 List。

欄位名稱命名慣例：

1. 欄位名稱以駝峰式命名法，例：fieldName。
2. 以 s 取代 List。

## 普遍原則

1. 採用清晰且易讀的名稱（Clear and Readable Names）:

- 使用具有描述性的名稱，讓開發者容易理解欄位的用途和內容。

- 避免使用過於簡略或不明確的縮寫。

2. 遵從標準命名慣例（Follow Standard Naming Conventions）:

- 遵從相應的命名慣例，例如使用 駝峰式大小寫 Camel Case（e.g., fieldName）或 蛇形命名法 Snake Case（e.g., field_name）、帕斯卡命名法 Pascal Case(e.g., FieldName)、串行 Kebab Case()。等。

- 在整個 API 中保持一致性。

3. 使用具體且一致的詞彙（Use Specific and Consistent Vocabulary）:

- 使用相同的詞彙來描述相似的概念，提高一致性。

- 避免在不同的地方使用不同的詞彙來描述相同的概念。

4. 避免過度縮寫（Avoid Excessive Abbreviations）:

- 避免使用過多或過度簡略的縮寫，以確保代碼易讀性。

- 只有在縮寫是行業標準或廣泛接受的情況下使用。

5. 保持一致的欄位命名風格（Maintain Consistent Field Naming Style）:

- 確保相同層次或相似用途的欄位使用相似的命名風格。

- 例如，如果使用 Camel Case 命名欄位，則在整個 API 中都應該保持這種風格。

6. 提供清晰的描述性註釋（Provide Clear Descriptive Comments）:

- 使用欄位的描述性註釋或文檔，以解釋欄位的用途和預期的值。

- 讓開發者了解如何使用該欄位以及該欄位的含義。

7. 適度的長度（Appropriate Length）

## RFC1035

API 服務名稱參照 RFC1035 建議，可以被拆成一個或多個網址 ip，以服務名稱為前綴詞，例如：maas.foxconn.com

## 路徑規則
