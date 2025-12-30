## 命名規則

### 基本ルール

- コメントや要約以外では **日本語を使用しない**
- **ローマ字つづりは使用しない**（翻訳困難な場合は要相談）
- **二文字の名前**でも先頭のみ大文字（× `ID` → 〇 `Id`）
- ドキュメントに記載のない **省略形は使用しない**
- 名前空間は以下の構成とする

```bash
Company.Project.UiFramework.Folder
```

---

### 要素別命名規則

| 要素                      | ルール             | 例                  |
| ------------------------- | ------------------ | ------------------- |
| インターフェース          | `I` + PascalCase   | `IRepository`       |
| クラス                    | PascalCase         | `UserService`       |
| 抽象クラス                | `Base` を付与      | `ViewModelBase`     |
| 派生クラス                | 元クラス名を含める | `MainViewModel`     |
| 属性クラス                | `Attribute` を付与 | `RequiredAttribute` |
| 構造体 / 列挙体           | PascalCase         | `UserType`          |
| メソッド                  | PascalCase         | `GetUser()`         |
| 定数                      | PascalCase         | `MaxRetryCount`     |
| ローカル変数 / 引数       | camelCase          | `userName`          |
| private フィールド        | `_` + camelCase    | `_userId`           |
| private static フィールド | `s_` + camelCase   | `s_cache`           |

---

### インターフェース・クラス命名ルール

- インターフェースには `I` を付ける
- **機能を表すインターフェース**には `able` を付ける
  - 例: `Readable`, `Writable`
- **処理主体のクラス**には `er` を付ける
  - 例: `Handler`, `Converter`

---

### メソッド命名ルール

- **非同期メソッド**には `Async` を付ける
- **イベントハンドラ**は `OnXxx` または `ControlName_OnXxx`
- **型パラメータ**は `T` または `T-` で始める
- **自然な英文として読めること**
- **必ず動詞を含める**

```csharp
GetUser()
LoadDataAsync()
CanExecute()
```

---

### 論理値・コレクションの命名

- 論理値は `is`, `has`, `can` を使用
- **二重否定は禁止**

  - × `isNotNull`
  - 〇 `isNull`

- コレクションは **複数形**

  - × `UserList`
  - 〇 `Users`

---

## コーディングスタイル

### 基本ルール

- `this.` を省略しない
- static メンバは **クラス名付きで呼び出す**
- 定義済み型は使用しない

  - × `string.IsNullOrEmpty`
  - 〇 `String.IsNullOrEmpty`

- 名前空間とクラス名の重複は禁止

---

### 定数・メンバ管理

- 定数は `const` ではなく **`static readonly`**
- ローカル定数は **グローバル定数化を検討**
- record のプライマリコンストラクタ引数は **大文字開始**

---

## UI 要素の命名

- コントロール名は **大文字開始**
- 語尾にコントロール種別を付ける
- **ハンガリアン記法は UI のみ許可**

```text
btnSave
txtUserName
lblErrorMessage
```

- ボタン名には **動詞または役割が明確な名前**を付ける

---

## デバッグ技法

---

## 参考サイト

- [C# CODING GUIDELINES 2024 - Qiita](https://qiita.com/Ted-HM/items/1d4ecdc2a252fe745871)
