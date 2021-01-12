---
marp: true
---

# アンチパターンから学ぶマイクロサービス

2021-01-13
Microservices Study

Plaid, Inc.
山内 雅浩

---

## 自己紹介

- 所属: 株式会社プレイド
- 氏名: 山内 雅浩 
- github: [@algas](https://github.com/algas)
![width:200px](./images/myavatar.png)
- 趣味: 狩猟、料理、筋トレ
- 最近勉強してること: 秘密計算、耐量子計算機暗号

---

## 発表概要

1. アンチパターンから学ぶべき3つの理由
1. アンチパターンと回避の実例
   - Data-Driven Migration AntiPattern
   - Reach-In Reporting AntiPattern
   - アンチパターン3
1. その他のアンチパターン

---

## アンチパターンから学ぶべき3つの理由

1. 失敗は成功の母
1. まだパターンが十分に確立してないから
1. (もう1つ何かある？)

---

## アンチパターンと回避の実例

[Microservices antipatterns and pitfalls](https://www.oreilly.com/content/microservices-antipatterns-and-pitfalls/) より引用

1. Data-Driven Migration AntiPattern
1. Reach-In Reporting AntiPattern
1. The Timeout AntiPattern
1. The "I was taught to share" AntiPattern
1. Grains of Sand Pitfall
1. The Static Contract Pitfall

---

## アンチパターン 1
### Data-Driven Migration AntiPattern

- Anti Pattern: データを先に移行するな
- Solution: 機能を先にデータは後に

---

## アンチパターンの回避 1
### Data-Driven Migration AntiPattern

モノリスからマイクロサービスへ
- フロントエンドから先に移行した
- バックエンドは後で移行した

---

## アンチパターン 2
### Reach-In Reporting

- Anti Pattern: レポート作成機能がサービスを跨っている
- Solution: 非同期イベントプッシュを使うべき

---

## アンチパターンの回避 2
### Reach-In Reporting

レポートデータ
- (一部の)レポートデータを BigQuery にまとめた
- リアルタイムレスポンスが必要なレポートにはキャッシュを使った

詳しくはエンジニアブログで
- [BigQueryの監査ログは役に立つ](https://tech.plaid.co.jp/bigquery_audit_log_useful/)
- [プレイドのCTOが登壇しました！ 〜Google Cloud Next '19 in SFレポート〜](https://tech.plaid.co.jp/google-cloud-next-19-in-sf/)
- [6,000スロットを使うBigQueryのリソース配分最適化への挑戦](https://tech.plaid.co.jp/bigquery-slot-resource-optmization/)

---

## アンチパターン 3
### The Static Contract Pitfall

- Anti Pattern: コントラクトのバージョン管理をしてない
- Solution: 2つの解決パターン
   - Header Versioning: バージョン番号をリクエストヘッダーに入れる
   - Schema Versioning: バージョン番号をリクエストスキーマに入れる

---

## アンチパターンの回避 3
### The Static Contract Pitfall

秘密情報の管理
- Schema Versioning
- 秘密情報の管理に Secret Manager を使った
- k8s では External Secret で秘密情報を管理している

詳しくはエンジニアブログで
- [悩みに悩んだ Kubernetes Secrets の管理方法、External Secrets を選んだ理由](https://tech.plaid.co.jp/nayanda-kubernetes-secret-management/)

---

## アンチパターン 4
### Grains of Sand Pitfall

- Anti Pattern: マイクロサービスの粒度が細かすぎ
- Solution: 3つの解決パターン
   - サービスのスコープと機能を分析する
   - データベーストランザクションを分析する
   - サービスのコレオグラフィーを分析する

---

## アンチパターンの回避 4
### Grains of Sand Pitfall

- チームの境界とサービスの境界を合わせる
- 逆コンウェイの法則
- まだ発展途上で永遠の課題

詳しくはエンジニアブログで
- [Self Contained Systemsの紹介](https://tech.plaid.co.jp/self-contained-systems/)
- [Kubernetes to Metaparticle. 分散プログラミングへの新しいアプローチ](https://tech.plaid.co.jp/metaparticle/)

---

### The Timeout

- Anti Pattern: 共通のタイムアウト値を設定するな
- Solution: サーキットブレーカーを使え

---

### The "I was taught to share"

- Anti Pattern: 何も考えずに共有するな
- Solutions: 4つの解決パターン
   - Shared Project: 共有プロジェクト
   - Shared Library: 共有ライブラリ
   - Replication: 複製
   - Consolidation: 共有しない
---

### その他のアンチパターン

- 文献1
- 文献2
- 文献3

---

## まとめ

- アンチパターンから学んでマイクロサービスを構築した
- 全部のアンチパターンを回避できたわけではない

---

## 参考文献


