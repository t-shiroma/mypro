# 不動産システム(賃貸管理)

> 最終更新: 2026-11-20 / ユーザー提供情報 + リポジトリ調査(推定は「推定」と明記)

## 構成
| リポジトリ | 役割 | 技術 | 備考 |
|---|---|---|---|
| FudosanSystem(未接続) | 本体(賃貸管理システム)と推定 | PHP 5.3 / Oracle、Docker(`release-container`) | ユーザーの一覧で FudosanWeb が2回書かれていたので、片方はこれの可能性(要確認) |
| [FudosanDB](https://github.com/ryussystem/FudosanDB) | 本体の DB(テーブル・PL/SQL・帳票ビュー) | Oracle | 顧客別のチケットが最も多い |
| [FudosanWeb](https://github.com/ryussystem/FudosanWeb) | 不動産WEB連携システム(`entry.life-okinawa.jp`=入居申込の受付と推定)→ 本体へ転送 | Laravel 13 / PHP 8.5 / MySQL | 現状は**ライフ向け**のみと推定 |
| [FudosanWebAPI](https://github.com/ryussystem/FudosanWebAPI) | 顧客のWebサイト・SalesForce から本体(Oracle)を参照する API | Laravel 13 / PHP 8.5 | 接続先は顧客ドメインで識別 |
| [fudosan-iko-life](https://github.com/ryussystem/fudosan-iko-life) | **ライフの J-Rent へのデータ移行** | PHP | 11/16 移行仕様・工数見積を作成 |

## 顧客
| 顧客 | チケット接頭辞(推定) | ドメイン(API 設定より) | 備考 |
|---|---|---|---|
| ライフコーポレーション | `LIFE-` | life-okinawa.jp、lifecorp.ryussystem.co.jp | チケット最多(主要顧客)。FudosanWeb も利用。**J-Rent へ移行予定** |
| 日研住宅 | `NIKKEN-` | nikkenjutaku.jp | FudosanDB で 2026-04 に帳票追加(定借関連) |
| とみや不動産 | `TOM-` | — | FudosanDB に TOM チケット多数 |
| アシストホーム | `AST-` | assist-home.com | |
| クリアス不動開発 | `CRE-`(推定) | — | 要確認 |
| (sunsun-okinawa.com) | `SUN-` | sunsun-okinawa.com | **ユーザーの一覧にない**。過去の顧客?(cybozu.sunsun-okinawa.com は利用終了の記載あり) |
| (共通) | `REMS-` | — | 製品共通の改修と推定(REMS = 不動産管理システムの製品名?) |

## 進行中の作業
- サーバー移行:CentOS 7 → Ubuntu 26.04(FudosanWeb / FudosanWebAPI。手順書・スクリプト整備済み)
- PHP の脆弱性対応の手順化(11/19)
- ライフの J-Rent 移行(fudosan-iko-life):**工数見積を顧客へ提出済み(2026-11-20 ユーザー確認)**。見積 26.5 人日(18〜40)+業務部門 3〜5 人日。見積外:残りのマスタ 3〜5・取引データ 6〜10 人日。回答待ち

## PM 観点の気づき
- **ライフコーポレーションが J-Rent へ移行する=最大顧客の離脱**の可能性。売上・保守体制・他4社への影響(共通部分の保守費の按分など)を確認したい。
- FudosanWeb がライフ専用なら、移行後に FudosanWeb をどうするか(廃止?他社展開?)の判断が必要。
- 本体(FudosanSystem)が PHP 5.3 / CentOS 6 系のコンテナで稼働しており、セキュリティ面で最もリスクが高い。

## 確認事項(ユーザーへ)
- [ ] 一覧の「FudosanWeb」重複は FudosanSystem のこと?(なら接続して調査します)
- [ ] ライフの J-Rent 移行の時期と、移行後のライフとの契約(保守は終了?)
- [ ] sunsun-okinawa.com(SUN)は現在も顧客?
- [ ] クリアス不動開発のチケット接頭辞は CRE?
- [ ] 各社の保守契約の内容(定額保守/スポット改修)と、saki-nagamine さん・k-sesoko さんとの分担
