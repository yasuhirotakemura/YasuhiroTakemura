# SQL Server コーディング・命名規則

---

## 命名規則

### 1. オブジェクト命名規則

| オブジェクト         | 表記法     | プレフィックス | サフィックス | 最大長 | 例                   |
| -------------------- | ---------- | -------------- | ------------ | ------ | -------------------- |
| データベース         | UPPERCASE  | なし           | なし         | 30     | `MYDATABASE`         |
| スキーマ             | lowercase  | なし           | なし         | 30     | `myschema`           |
| テーブル             | PascalCase | なし           | なし         | 128    | `Customer`           |
| カラム               | PascalCase | なし           | なし         | 128    | `CustomerId`         |
| 主キー               | PascalCase | `PK_`          | なし         | 128    | `PK_Customer`        |
| 外部キー             | PascalCase | `FK_`          | なし         | 128    | `FK_Order_Customer`  |
| 一意キー             | PascalCase | `UQ_`          | なし         | 128    | `UQ_Customer_Email`  |
| インデックス         | PascalCase | `IX_`          | なし         | 128    | `IX_Customer_Email`  |
| ビュー               | PascalCase | `VI_`          | なし         | 128    | `VI_CustomerSummary` |
| ストアドプロシージャ | PascalCase | `usp_`         | なし         | 128    | `usp_GetCustomer`    |
| 関数                 | PascalCase | `udf_`         | なし         | 128    | `udf_CalculateTotal` |
| トリガー             | PascalCase | `TR_`          | なし         | 128    | `TR_Customer_DML`    |

---

### 2. テーブル・カラム命名ルール

#### テーブル名

- **単数形**を使用する
  - 例: `Customer`, `Order`
- **PascalCase** を使用する
  - 例: `OrderDetail`
- テーブル特性を示す場合のみプレフィックスを使用する
  - 例: `MT_CacheData`（メモリ最適化テーブル）

#### カラム名

- **PascalCase** を使用する
  - 例: `OrderDate`, `CustomerId`
- **データ型・テーブル名を含めない**
  - × `CustomerName`（テーブル内で明確な場合）
  - 〇 `Name`

---

### 3. 制約・インデックス命名ルール

- 主キー
  - `PK_<TableName>`
- 外部キー
  - `FK_<TableName>_<ReferencedTable>`
- 一意キー
  - `UQ_<TableName>_<ColumnName>`
- インデックス
  - `IX_<TableName>_<ColumnName>`

---

## T-SQL コーディングスタイル

### 1. 一般ルール

#### スキーマ修飾

- オブジェクトは必ず **スキーマ修飾** する

```sql
SELECT * FROM dbo.Customer;
```

- サーバー名・データベース名の **ハードコーディングは禁止**

#### キーワード・データ型

- SQL キーワードは **大文字**
- データ型は **小文字**

```sql
SELECT
    CustomerId
FROM
    dbo.Customer
WHERE
    IsActive = 1;
```

---

#### 区切り・改行

- 文末は必ず **セミコロン（;）**
- カンマは **次行に配置**

---

#### エイリアス

- 可読性の高いエイリアスを使用
- `AS` を明示的に記述

```sql
FROM
    dbo.Customer AS c
```

---

#### 括弧の使用

- 論理条件は **括弧で明示**

```sql
WHERE
    (A = 1 OR B = 2)
    AND C = 3;
```

---

### 2. ストアドプロシージャ・関数

#### 定義ルール

- 定義には **`ALTER PROCEDURE` / `ALTER FUNCTION`** を使用
- 必要に応じて存在チェックを行う

---

#### エラー処理

- `BEGIN TRY` / `BEGIN CATCH` を使用
- `RAISERROR` でエラー内容を明確化

---

#### パラメータ

- **camelCase** を使用

```sql
@customerId
@orderDate
```

---

#### NOCOUNT

- すべてのプロシージャで `SET NOCOUNT ON` を使用

---

### 3. 禁止事項

- `SELECT *` の使用禁止
- 予約語をオブジェクト名に使用しない
- トランザクションの **ネスト禁止**
- 曖昧な日付リテラルを使用しない

```sql
-- OK
'2023-01-01'
```

---

### 4. クエリフォーマット例

```sql
SELECT
    CustomerId,
    CustomerName,
    OrderDate
FROM
    dbo.Orders AS o
WHERE
    o.OrderDate > '2023-01-01'
ORDER BY
    o.CustomerName;
```

---

## その他ルール

- 基本方針として
  **「SQL Server Name Convention and T-SQL Programming Style」** に準拠する
- 日本固有要件や特別な事情がある場合は、**チーム内で合意の上例外を認める**

---

## 参考文献

- [https://github.com/ktaranov/sqlserver-kit/blob/master/SQL%20Server%20Name%20Convention%20and%20T-SQL%20Programming%20Style.md](https://github.com/ktaranov/sqlserver-kit/blob/master/SQL%20Server%20Name%20Convention%20and%20T-SQL%20Programming%20Style.md)
- [https://qiita.com/Masayuki_Ozawa/items/288c18907cfe36e66a86](https://qiita.com/Masayuki_Ozawa/items/288c18907cfe36e66a86)
- [https://avinton.com/academy/database-naming-conventions/](https://avinton.com/academy/database-naming-conventions/)
- [https://qiita.com/genzouw/items/35022fa96c120e67c637](https://qiita.com/genzouw/items/35022fa96c120e67c637)
