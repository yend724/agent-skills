---
name: frontend-architecture
description: Frontend architecture conventions based on Feature-Sliced Design (simplified). Auto-triggers when creating new files, directories, or organizing project structure. Defines rules for feature-based code organization, module boundaries, dependency direction, and public API design.
paths: "src/**/*"
---

# Frontend Architecture

FSD（Feature-Sliced Design）を参考にしたフロントエンドアーキテクチャ規約集。最低限の 3 層を基本構成とする。

```
app/（ルーティング層） → features/（機能層） → shared/（共通層）
```

依存方向は常に上から下への単方向。shared が features に依存してはならない。

プロジェクトの規模や要件に応じて `entities/`、`widgets/` 等のレイヤーを追加してよい。ただし依存方向の単方向性は常に守る。

## When to Apply

以下の作業時に自動で参照する：

- 新しいファイル・ディレクトリの作成
- 既存コードのディレクトリ移動・リファクタリング
- feature 間の依存関係の設計
- 共通コードの配置判断

## Rule Categories

| Category | Prefix |
|----------|--------|
| ディレクトリ構成 | `structure-` |
| モジュール境界 | `boundary-` |

## Quick Reference

### ディレクトリ構成

- [structure-feature-based](rules/structure-feature-based.md) - コードは機能単位で features/ に整理する
- [structure-app-routing-only](rules/structure-app-routing-only.md) - app/ はルーティングとレイアウト構成のみに使う

### モジュール境界

- [boundary-public-api](rules/boundary-public-api.md) - モジュール単位で public API を export する
- [boundary-dependency-direction](rules/boundary-dependency-direction.md) - 依存方向は app → features → shared の単方向にする
- [boundary-shared-code](rules/boundary-shared-code.md) - 2つ以上の feature で使うコードは shared に置く
- [boundary-import-path](rules/boundary-import-path.md) - モジュール内は相対パス、モジュール外は絶対パスでインポートする

## How to Use

個別ルールの詳細は `rules/` ディレクトリ内のファイルを参照。上記 Quick Reference のリンクから各ルールにアクセスできる。
