---
marp: true
---

# アンチパターンから学ぶマイクロサービス

2021-01-13
Microservices Study

Plaid, Inc.
山内 雅浩 [@algas](https://twitter.com/algas)

---

## 発表概要

- アンチパターンから学ぶべき3つの理由
- アンチパターン一覧
- アンチパターン対策の実践例

---

## アンチパターンから学ぶべき3つの理由

1. 失敗は成功の母
1. まだパターンが十分に確立してないから
1. (もう1つ何かある？)

---

## アンチパターン一覧

"Microservices antipatterns and pitfalls (O'REILLY)" より引用

1. Data-Driven Migration
1. The Timeout
1. The "I was taught to share"
1. Reach-In Reporting
1. Grains of Sand Pitfall
1. The Static Contract Pitfall

---

### Data-Driven Migration

- Anti Pattern: データを先に移行するべからず
- Solution: 機能を先にデータは後に移行すべき

---

### The Timeout

- Anti Pattern: 共通のタイムアウト値を設定するべからず
- Solution: サーキットブレーカーを使うべき

---

### The "I was taught to share"

- Anti Pattern: 依存するものが多すぎる
- Solution: 4つの解決パターン
   - Shared Project: 共有プロジェクト
   - Shared Library: 共有ライブラリ
   - Replication: 複製
   - Consolidation: 共有しない

---

### Reach-In Reporting

- Anti Pattern: レポート作成機能がサービスを跨っている
- Solution: 非同期イベントプッシュを使うべき

---

### Grains of Sand Pitfall

- Anti Pattern: マイクロサービスの粒度が細かすぎる
- Solution: 3つの解決パターン
   - サービスのスコープと機能を分析する
   - データベーストランザクションを分析する
   - サービスのコレオグラフィーを分析する

---

### The Static Contract Pitfall

- Anti Pattern: コントラクトのバージョン管理をしてない
- Solution: 2つの解決パターン
   - Header Versioning: バージョン番号をリクエストヘッダーに入れる
   - Schema Versioning: バージョン番号をリクエストスキーマに入れる

---

## アンチパターン対策の実践例 1

### Data-Driven Migration

フロントエンドから先に移行した
バックエンドは後で移行する

---

## 参考文献


