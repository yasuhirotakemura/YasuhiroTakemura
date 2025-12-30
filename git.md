
# Git 運用ルール

## Git の基礎を学習する

- [Git でのバージョン コントロールの概要 - Microsoft Learn](https://learn.microsoft.com/ja-jp/training/paths/intro-to-vc-git/)
- [GitHub の基礎 - 管理の基本と製品の機能 - Microsoft Learn](https://learn.microsoft.com/ja-jp/training/paths/github-administration-products/)

---

## コミットメッセージ規則

### 基本フォーマット

```
<type>: <変更内容の要約>
```

例
```
feat: ログイン機能を追加
````

---

### コミットタイプ一覧

| タイプ | 用途 |
|------|------|
| `feat:` | 新機能の追加・機能改善 |
| `fix:` | バグ修正 |
| `docs:` | ドキュメント（README・仕様書など）の変更 |
| `style:` | コードスタイル変更（インデント、フォーマットなど） |
| `refactor:` | リファクタリング（動作変更なし） |
| `test:` | テストコードの追加・修正 |
| `chore:` | 細かな作業、設定ファイル変更、ツール関連 |
| `ci:` | CI/CD 設定ファイルの変更 |
| `perf:` | パフォーマンス改善 |
| `build:` | ビルドシステム・依存関係の変更 |

---

### コミットメッセージ例

```bash
git commit -m "feat: ログイン機能を追加"
git commit -m "fix: ユーザーログイン時のバグを修正"
git commit -m "docs: READMEにインストール手順を追加"
git commit -m "style: インデントを修正"
git commit -m "refactor: ユーザー登録処理を整理"
git commit -m "test: ユーザー登録の単体テストを追加"
git commit -m "chore: 開発用設定ファイルを更新"
git commit -m "ci: GitHub Actions の設定を更新"
git commit -m "perf: APIレスポンスを高速化"
git commit -m "build: 依存ライブラリを更新"
````

---

## ブランチ命名規則

### 基本フォーマット

```
<type>/issue-<番号>-<概要>
```

例:

```
feature/issue-11-user-authentication
```

---

### ブランチタイプ一覧

| タイプ         | 用途          |
| ----------- | ----------- |
| `feature/`  | 新機能の追加・機能改善 |
| `bugfix/`   | バグ修正        |
| `docs/`     | ドキュメント変更    |
| `style/`    | コードスタイル変更   |
| `refactor/` | リファクタリング    |
| `test/`     | テストコード追加・修正 |
| `chore/`    | 設定変更・ツール関連  |
| `ci/`       | CI/CD 関連    |
| `perf/`     | パフォーマンス改善   |
| `build/`    | ビルド・依存関係変更  |
| `hotfix/`   | 緊急修正        |
| `release/`  | リリース準備      |

---

### ブランチ作成例

```bash
git checkout -b feature/issue-11-user-authentication
git checkout -b bugfix/issue-12-login-page-error
git checkout -b docs/issue-13-update-readme
git checkout -b style/issue-14-fix-indentation
git checkout -b refactor/issue-15-user-registration-cleanup
git checkout -b test/issue-16-add-user-registration-tests
git checkout -b chore/issue-17-update-config
git checkout -b ci/issue-18-update-github-actions
git checkout -b perf/issue-19-improve-api-performance
git checkout -b build/issue-20-update-dependencies
git checkout -b hotfix/issue-21-critical-payment-error
git checkout -b release/issue-22-v1.0.0
```

---

## 補足ルール

* コミットは **1コミット = 1目的**
* 可能な限り **Issue 番号を含める**
* `hotfix/` は最小修正・即マージを前提
* `release/` ブランチでは新機能を追加しない

---
