# 🎯 Cursor 開発ルール自動化システム

## 📋 概要

このシステムは、**常に使うルール**と**プロジェクト固有ルール**を分離し、効率的な開発環境を提供します
。

## 🏗️ ルール構成

### **📁 グローバルルール（常に適用）**

場所: `~/.cursor/global-rules/`

- **`development-process.mdc`** - 高度な問題解決プロセス
- **`task-management.mdc`** - @todo.md による統一タスク管理

### **📁 プロジェクト固有ルール**

場所: `.cursor/rules/project-specific/`

- **`clerk.mdc`** - Clerk 認証実装ルール
- **`uiux.mdc`** - shadcn/ui ベース UI/UX ルール
- **`nextjs.mdc`** - Next.js 開発ルール
- **`db-blueprint.mdc`** - データベース設計ルール
- **`techstack.mdc`** - 技術スタック管理ルール

## 🚀 使用方法

### **新規プロジェクトでのセットアップ**

```bash
# 1. 新規プロジェクトディレクトリに移動
cd /path/to/new-project

# 2. プロジェクトタイプに応じてセットアップ
~/.cursor/scripts/setup-project.sh [TYPE]
```

### **利用可能なプロジェクトタイプ**

| タイプ       | 含まれるルール               | 用途                         |
| ------------ | ---------------------------- | ---------------------------- |
| `web`        | UI/UX + HTML/CSS 開発標準    | 基本的な Web サイト          |
| `nextjs`     | UI/UX + Next.js              | Next.js アプリケーション     |
| `auth`       | UI/UX + Next.js + Clerk 認証 | 認証機能付きアプリ           |
| `database`   | UI/UX + Next.js + DB         | データベース使用アプリ       |
| `full-stack` | 全てのルール                 | フルスタックアプリケーション |

### **使用例**

```bash
# Next.js認証アプリのセットアップ
~/.cursor/scripts/setup-project.sh auth

# フルスタックアプリのセットアップ
~/.cursor/scripts/setup-project.sh full-stack
```

## 📝 自動生成される要素

### **1. ディレクトリ構造**

```
your-project/
├── .cursor/
│   └── rules/
│       ├── development-process.mdc  # グローバル
│       ├── task-management.mdc      # グローバル
│       └── [プロジェクト固有ルール]
└── @todo.md                         # タスク管理ファイル
```

### **2. @todo.md の初期化**

- プロジェクトセットアップタスク
- 基本的なタスク管理テンプレート
- 進捗ステータス管理

## 🔄 グローバルルールの自動適用

### **Cursor での自動適用**

グローバルルール（`~/.cursor/global-rules/`）は、以下の設定により**全てのプロジェクトで自動適用**さ
れます：

```yaml
---
description: グローバル開発プロセスルール
globs:
alwaysApply: true # 🔥 常に適用
---
```

### **効果**

- 新しいプロジェクトを開く度に、自動的に高品質な開発プロセスが適用
- タスク管理の一貫性確保
- 開発効率の大幅向上

## 🛠️ カスタマイズ

### **グローバルルールの更新**

```bash
# グローバルルールを編集
code ~/.cursor/global-rules/development-process.mdc
code ~/.cursor/global-rules/task-management.mdc
```

### **プロジェクト固有ルールの追加**

```bash
# 新しいルールファイルを作成
code .cursor/rules/project-specific/my-custom-rule.mdc
```

## 🎉 メリット

### **開発者体験の向上**

- ✅ 一貫した開発プロセスの自動適用
- ✅ プロジェクトタイプに応じた最適なルール設定
- ✅ タスク管理の標準化

### **生産性の向上**

- ⚡ セットアップ時間の大幅短縮
- ⚡ ルール設定の自動化
- ⚡ 品質保証の組み込み

### **保守性の向上**

- 🔧 ルールの集中管理
- 🔧 バージョン管理による変更追跡
- 🔧 チーム間での設定共有

## 🚨 重要事項

1. **グローバルルールの変更は全プロジェクトに影響**します
2. **@todo.md の更新は自動実行**されます
3. **プロジェクト固有ルールは必要に応じて選択**してください

---

このシステムにより、**全てのプロジェクトで高品質・一貫性のある開発環境**が自動的に構築されます。
