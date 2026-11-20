# 業務一覧(棚卸し)

> 最終更新: 2026-11-20 / 状態: リポジトリ調査からの**推定**。ユーザー確認待ち
> リポジトリの詳細は `work/repositories.md`

## プロジェクト・案件業務

| # | 案件 | リポジトリ | 種別 | 推定フェーズ | 期限・マイルストーン | 備考 |
|---|---|---|---|---|---|---|
| P1 | 沖縄宿泊税 管理SaaS | okinawa-stay-manager-v2 | 自社SaaS | 開発中(課金・印刷) | **2027-02 までに稼働**(宿泊税施行 2/1) | 本人が直接実装。`projects/okinawa-stay-manager.md` |
| P2 | 漁業振興基金 システム再構築 | blue-shield(旧: promotionFund、設計書: gyogyogyo-pj) | 受託 | 納品前の仕上げ | **2026-11 末 納品** | フルスクラッチ再構築。詳細は `projects/blue-shield.md` |
| P3 | 鹿屋体育大学 教務システム(提供中)のセキュリティ対応 | DzkKnyKmWeb / DzkKnyKmDb | 保守 | 改修・手順書は完了、**本番移行が未実施** | 未確認 | 現行 PHP 5.2.17。`projects/kanoya.md` |
| P4 | 不動産システム(5社に提供)の保守・サーバー移行 | FudosanWeb / FudosanWebAPI / FudosanDB | 受託・保守 | 移行・運用 | 未確認 | CentOS 7→Ubuntu 26.04 |
| P5 | ライフコーポレーションの J-Rent データ移行 | fudosan-iko-life | 受託 | 仕様・見積 | 未確認 | 工数見積作成済(11/16) |
| P6 | otc-kk 見積システム:kintone 版を運用中、スクラッチ版を提案 | otc-kk-kintone / otc-kk-apps | 保守 + 提案 | 提案用に開発中(開発サーバーでデモ可) | 未確認 | `projects/otc-kk.md` |
| P7 | 大学病院 施設予約 | facility-booking | 受託 | **見積の最終段階** | **2027-02 末 最終納品** | `projects/facility-booking.md` |
| P8 | 店舗管理システム | new-accounting-system | 受託・保守 | バージョンアップ | 未確認 | |
| P9 | 具志堅商店 WordPress | gushiken-shoten.co.jp | 保守 | Git管理を導入済 | — | 週次ミラー |
| P10 | RYU'S Apps 勤怠 | ryus-apps | 自社SaaS | **開発中**(フェーズ1。11/10 以降停止) | 未確認 | `projects/ryus-apps.md` |
| P11 | WorkApp(社内業務アプリ)と製品サイト | work-app / webapp-product-site | 社内アプリ | **運用中**・継続開発(最も活発) | — | 製品サイトの料金・規約は仮 |
| P12 | 公共施設予約 ashibi | ashibi | 自社製品・**提案中** | 2団体に提案(お試しで継続の見込み) | 未確認 | 沖縄県スポーツ協会・沖縄県青年会館。`projects/ashibi.md` |
| P13 | SecuBase(情報セキュリティ管理SaaS) | secubase | 自社SaaS | **開発中**(Phase 1。11/06 以降停止) | 未確認 | `projects/secubase.md` |
| P14 | 保育園向け勤怠 tsumiki(喜名保育園) | tsumiki | 受託/自社 | 要件・プロトタイプ。**ryus-apps への統合を検討** | 未確認 | 変形労働時間制。`projects/tsumiki.md` |
| P15 | Windows デスクトップ基盤検証 | ryus-desktop-template | 技術検証 | フェーズ4完了 | — | |
| P16 | コーポレートサイト | homepage | 社内 | 運用 | — | |

## 定常業務(推定・要確認)
| 業務名 | 頻度 | 内容 | 備考 |
|---|---|---|---|
| Claude 作成 PR のレビュー・マージ | 毎日 | 各リポジトリの PR 確認とマージ | 業務の中心と推定 |
| 現行システムの保守・障害対応 | 随時 | hotfix(promotionFund 等)、不具合修正 | |
| サーバー運用・脆弱性対応 | 随時 | PHP 更新、OS 移行、デプロイ | |
| 見積・要件定義 | 案件ごと | 工数見積、要件定義書、チェックリスト | facility-booking、fudosan-iko-life |
