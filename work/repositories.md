# 担当リポジトリ一覧

> 最終更新: 2026-11-20(ユーザー提示の21件を調査。README・CLAUDE.md・直近40コミットから推定)
> 「推定」はコードから読み取った内容で、ユーザー未確認。

## A. 自社プロダクト・SaaS(株式会社リュウズシステム)

| リポジトリ | 概要 | 技術 | 状況(直近) |
|---|---|---|---|
| [ryus-apps](https://github.com/ryussystem/ryus-apps) | RYU'S Apps(SaaS群)。第1弾「勤怠」。ryus-apps.jp。portal / accounts / kintai / admin | React + Hono + Prisma + PostgreSQL(RLS) | 11/10 給与ソフト連携CSV、説明書の写真撮り直し。PRは `develop` 向け |
| [work-app](https://github.com/ryussystem/work-app) | 社内業務アプリ(内製)WorkApp。勤怠・経費精算・規程・イベント補助・アンケート 等 | React + Hono + Prisma + PostgreSQL | **最も活発**(PR #195)。11/19 チームアンケート追加 |
| [webapp-product-site](https://github.com/ryussystem/webapp-product-site) | WorkApp 製品紹介サイト(料金・規約は仮/雛形) | 静的HTML | 10/16 更新。料金・規約が未確定 |
| [okinawa-stay-manager-v2](https://github.com/ryussystem/okinawa-stay-manager-v2) | 沖縄県宿泊税(**2027-02-01施行**)の特別徴収義務者向け 宿泊実績・申告管理SaaS。Airbnb取込、Stripe課金 | React + Hono + PostgreSQL(RLS) | 11/18 Stripe確認ツール。**ユーザー本人が直接コミット** |
| [secubase](https://github.com/ryussystem/secubase) | SecuBase:情報セキュリティ管理SaaS。Phase1はiSSO対応の資料管理 | React + Mantine + Hono + Drizzle | 11/06 以降停止 |
| [tsumiki](https://github.com/ryussystem/tsumiki) | 保育園向け勤怠管理システム(要件定義+プロトタイプ) | — | 10/19 以降停止 |
| [ashibi](https://github.com/ryussystem/ashibi) | 公共施設予約システム(マルチ団体。沖縄県スポーツ協会の設定あり) | React + Hono + Caddy | 11/17 団体別設定 |
| [homepage](https://github.com/ryussystem/homepage) | 自社コーポレートサイト(新ロゴでリニューアル、お知らせCMS) | PHP + MySQL | 10/29 以降安定 |

## B. 顧客システム(受託・保守)

| リポジトリ | 顧客・領域(推定) | 概要 | 技術 | 状況(直近) |
|---|---|---|---|---|
| [FudosanWeb](https://github.com/ryussystem/FudosanWeb) | 不動産会社 | 不動産WEB連携システム。Laravel 5.5→13 / PHP 7→8.5、CentOS 7→Ubuntu 26.04 移行 | Laravel 13, MySQL, Docker | 11/19 PHP更新手順。10/27 申込転送の不具合修正 |
| [FudosanWebAPI](https://github.com/ryussystem/FudosanWebAPI) | 不動産会社 | 不動産API(SalesForce連携、Oracle参照) | Laravel 13, Oracle | 11/19 php-update.sh |
| [fudosan-iko-life](https://github.com/ryussystem/fudosan-iko-life) | 不動産会社 | 現行賃貸管理(FudosanSystem/DB)→ **J-Rent データ移行**。移行仕様・CSV作成・工数見積 | PHP 5.3(現行コンテナ内) | 11/16 工数見積作成 |
| [promotionFund](https://github.com/ryussystem/promotionFund) | 沖縄県漁業振興基金 | 外国漁船操業等調査・監視事業(kintone版・**現行運用**) | kintone + React | 10/07 hotfix 対応(#452〜474) |
| [blue-shield](https://github.com/ryussystem/blue-shield) | 沖縄県漁業振興基金 | promotionFund の**再構築**。利用者:基金・漁協・水産庁・沖縄県。PC専用 | React + Hono + Drizzle + PostgreSQL | 11/19 画面詳細設計書・ER図。設計書/テスト/マニュアル整備中 |
| [DzkKnyKmWeb](https://github.com/ryussystem/DzkKnyKmWeb) | 鹿屋体育大学 | 教務システム(Web)。PHP 8 移行・本番移行(方式B) | PHP 8.5, Oracle, Windows Server | 11/18 マージ。本番移行チェックリスト |
| [DzkKnyKmDb](https://github.com/ryussystem/DzkKnyKmDb) | 鹿屋体育大学 | 教務システムの DB(Oracle DDL・PL/SQL) | Oracle | 11/18 マージ |
| [otc-kk-apps](https://github.com/ryussystem/otc-kk-apps) | 製品メーカー(パイル・ポール等) | 見積システム新規(kintone版から移行)。依頼書・営業週報も | React + Hono + Drizzle | 11/06 自動デプロイ整備。PRは `develop` 向け |
| [otc-kk-kintone](https://github.com/ryussystem/otc-kk-kintone) | 同上 | 旧 kintone カスタマイズ(移行元) | kintone + Vite | 2024-06 以降停止(参照用) |
| [facility-booking](https://github.com/ryussystem/facility-booking) | 大学病院 | 院内施設予約。要件定義v2確定、機能/非機能チェックリスト、工数見積 | React 19 + Hono + PostgreSQL 18, ConoHa | 11/17 見取り図から部屋選択 |
| [new-accounting-system](https://github.com/ryussystem/new-accounting-system) | 店舗運営の顧客 | 店舗管理(日報・売上・仕入・タイムカード・給与) | Laravel 13 / PHP 8.4 | 11/19 Laravel 13 へ更新 |
| [gushiken-shoten.co.jp](https://github.com/ryussystem/gushiken-shoten.co.jp) | 具志堅商店 | WordPress サイトの Git 管理(ヘテムルからの週次ミラー・デプロイ) | WordPress, GitHub Actions | 11/19 構築 |

## C. 技術検証

| リポジトリ | 概要 | 状況 |
|---|---|---|
| [ryus-desktop-template](https://github.com/ryussystem/ryus-desktop-template) | Windows 業務アプリを Avalonia 12 + .NET 10 で作れるかの検証(Delphi 資産の後継候補?) | 11/19 フェーズ4まで完了 |

## 横断的な特徴(観察)

- **開発スタイル**:大半のリポジトリで Claude Code がブランチで実装し、ユーザーがレビューしてマージしている。ユーザーの役割は「設計・判断・レビュー・リリース」が中心。
- **標準スタック**:新規は React + Hono + PostgreSQL + Caddy + Docker に統一。共通部品・UI規約は work-app が源流で、ryus-apps / otc-kk-apps に移植。
- **レガシー刷新の流れ**:kintone → 自前Web(promotionFund→blue-shield、otc-kk-kintone→otc-kk-apps)、PHP/Laravel の大幅バージョンアップ(FudosanWeb、DzkKnyKm、会計)、OS移行(CentOS 7→Ubuntu)。
- **関係者(コミット履歴より)**:saki-nagamine、k-sesoko(不動産系)、miyukikoga(otc-kk-kintone)。

## ローカル clone(このセッション)

`/home/user/<リポジトリ名(小文字)>` に浅い clone(--depth 40)あり。セッション終了で消える。
