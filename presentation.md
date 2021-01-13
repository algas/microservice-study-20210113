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

1. なぜアンチパターンから学ぶのか？
1. アンチパターンと回避の実例
   - Data-Driven Migration AntiPattern
   - Reach-In Reporting AntiPattern
   - The Static Contract Pitfall
   - Grains of Sand Pitfall
1. その他のアンチパターン

---

## なぜアンチパターンから学ぶのか？

「他人の失敗から学べ。すべての失敗を為せるほどには人生は長くない。」

> "Learn from the mistakes of others. You can't live long enough to make them all yourself."
[Eleanor Roosevelt](https://www.goodreads.com/quotes/6521824-learn-from-the-mistakes-of-others-you-can-t-live-long)

---

## アンチパターンと回避の実例

今回紹介するアンチパターンは [Microservices antipatterns and pitfalls](https://www.oreilly.com/content/microservices-antipatterns-and-pitfalls/) から4つを引用
1. Data-Driven Migration AntiPattern
1. Reach-In Reporting AntiPattern
1. The Static Contract Pitfall
1. Grains of Sand Pitfall

マイクロサービスの話は他のメンバーが何度もしてるので「アンチパターン」という別の視点から見直してみる

---

## アンチパターン 1
### Data-Driven Migration AntiPattern

- Anti Pattern: データを先に移行するな
- Solution: 機能を先にデータは後に

---

## アンチパターンの回避 1
### Data-Driven Migration AntiPattern

具体例：モノリスからマイクロサービスへの移行
- フロントエンドから先に移行した

![width:400px](./images/microservice.png)

詳しくは次の資料で
- [Migrating to Microservices](https://speakerdeck.com/komukomo/migrating-to-microservices)
- [急速な成長を加速させるアーキテクチャ](https://tech.plaid.co.jp/cndt2020tokyo/)

---

## アンチパターン 2
### Reach-In Reporting AntiPattern

- Anti Pattern: レポート作成機能がサービスを跨っている
- Solution: 非同期イベントプッシュを使うべき

---

## アンチパターンの回避 2
### Reach-In Reporting AntiPattern

具体例：レポートデータ
- (一部の)レポートデータを BigQuery にまとめた
- リアルタイムレスポンスが必要なレポートにはキャッシュを使った

詳しくはエンジニアブログで
- [BigQueryの監査ログは役に立つ](https://tech.plaid.co.jp/bigquery_audit_log_useful/)
- [PLAID's Journey to Global Large-Scale Real-Time Analytics With Google BigQuery](https://tech.plaid.co.jp/google-cloud-next-19-in-sf/)

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

具体例：秘密情報の管理
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
- 逆コンウェイの法則(アーキテクチャのための組織を作る)
- まだ発展途上で永遠の課題

詳しくはエンジニアブログで
- [プレイド開発チームにおけるチーム・ジャーニー](https://speakerdeck.com/kadoppe/pureidokai-fa-timuniokerutimuziyani)
- [Self Contained Systemsの紹介](https://tech.plaid.co.jp/self-contained-systems/)

---

### その他のアンチパターン

- The “I Was Taught to Share” AntiPattern
- The Timeout AntiPattern
- Are We There Yet Pitfall
- Give It a Rest Pitfall

ここでは詳しくは紹介しません

---

## まとめ

- アンチパターンはマイクロサービスの構築に役立つ
- 既知のアンチパターンを全部回避できたわけではない
- これから新しいパターンやアンチパターンを確立していきたい

---

## 参考文献

- [Microservices antipatterns and pitfalls](https://www.oreilly.com/content/microservices-antipatterns-and-pitfalls/) 
- [Microservices Anti-Patterns: A Taxonomy](https://arxiv.org/pdf/1908.04101.pdf)
