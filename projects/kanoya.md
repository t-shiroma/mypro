# 鹿屋体育大学 教務システム(DzkKnyKmWeb / DzkKnyKmDb)

> 最終更新: 2026-11-20 / ユーザー提供情報 + リポジトリ調査

## 概要
| 項目 | 内容 |
|---|---|
| 顧客 | 鹿屋体育大学 |
| 種別 | 提供中システムの保守 |
| システム | 教務システム(Web:時間割・シラバス・成績・学年暦・掲示板・履修・受講者名簿 など)。URL `esv.nifs-k.ac.jp` |
| リポジトリ | [DzkKnyKmWeb](https://github.com/ryussystem/DzkKnyKmWeb)(PHP)、[DzkKnyKmDb](https://github.com/ryussystem/DzkKnyKmDb)(Oracle DDL・PL/SQL) |
| 現在の課題 | **PHP などのセキュリティ対応** |

## 本番環境の現状(2026-10-23 調査)と移行後
| 項目 | 現行 | 移行後 |
|---|---|---|
| OS | Windows Server 2019 | 同じ |
| PHP | 5.2.17(32bit)※移行前 | **8.5.12(64bit)で稼働中** |
| Apache | 2.4.46 Win32 | 2.4 最新(64bit) |
| Oracle クライアント | 11.2(32bit) | Instant Client 19.32 |
| DB | **Oracle 12c 12.1.0.2**(サポート終了済み) | 同じ(今回は対象外) |

## 進み具合
| 工程 | 状態 |
|---|---|
| PHP 8 対応の改修(Web) | 完了(2026-10-22〜23 に集中対応、11/18 マージ) |
| DB 側の DDL 整備 | 完了(11/18 マージ) |
| テスト | 単体・結合テストの仕様書兼成績書あり(`docs/test/`) |
| 本番移行の手順 | 方式 B(現行サーバーに並べて構築し、8443 番で確認してから 443 番に切替)。チェックリスト・切り戻し手順あり |
| **本番移行の実施** | **完了**(本番は PHP 8.5.12 で稼働中。2026-11-20 ユーザー確認。リポジトリのチェックリストは未記入のまま) |

## PM 観点の気づき
- PHP 8.5 への移行は完了。今後は **PHP のセキュリティ更新(パッチ版)を継続的に当てる運用**が課題。
- 2026-11-19 の PHP セキュリティリリース(8.5.13)への対応要否を確認中(`log/2026-11-20.md`)。
- 更新作業は、履修登録・成績入力の期間を避ける必要がある。
- 本番 DB の Oracle 12.1 もサポート終了済み。次の課題として、DB のバージョンアップ(またはサポート方針)を大学に提案するか検討。
- PHP 8.5 は今後も定期的な更新が必要 → 運用(四半期ごとの PHP 更新など)を保守契約の中で決めておきたい。

## 確認事項(ユーザーへ)
- [ ] 履修登録・成績入力などの繁忙期と、作業できる期間
- [ ] 当日の作業は現地?リモート?(作業者は誰か)
- [ ] 保守契約の範囲(PHP 定期更新、DB のバージョンアップは含む?)

## 2026-11-19 PHP セキュリティリリース(8.5.13)への対応判断(2026-11-20)

**結論:対応が必要(8.5.12 → 8.5.13 へ更新)。緊急度は「高・数日以内」。** 悪用の報告は 11/20 時点で無い(CISA KEV 未掲載、IPA も悪用確認なし)。
※判断材料は二次情報(piyolog、Lilting、Rescana、watchtowr、Cycode)。php.net の告知・GHSA の一次資料は未確認。

### 本番の構成
Windows Server 2019 / Apache 2.4 + **mod_php(php8apache2_4.dll、Thread Safe 版)** / PHP 8.5.12 / セッションは files(既定)・`use_strict_mode=1`。
本番の php.ini は**最小限の記述**(php.ini-production を元にしていない)ため、書いていない項目は PHP の組み込みの既定値になる → `session.upload_progress.enabled=1`、`zend.exception_ignore_args=0`、`fatal_error_backtraces` 有効(8.5 の既定)。

### 該当判定
| CVE | 内容 | 判定 | 理由 |
|---|---|---|---|
| CVE-2026-126714(Critical) | セッション files ハンドラーの部分上書き → RCE の可能性 | **該当** | files ハンドラー(既定)、upload progress 有効(既定)、ZTS。悪用には読み込み側のガジェットチェーンが必要(Smarty・TCPDF・PEAR を同梱) |
| CVE-2026-129474(Critical) | 8.5 のみ。`__call` 中の致命的エラーのバックトレースで UAF | **該当の可能性** | `zend.exception_ignore_args` 未設定(=0)、`fatal_error_backtraces` 有効。Smarty が `__call` を使う |
| CVE-2026-115560(Critical) | upload progress と serializer の不一致 → RCE | 低い | 条件の「serializer の異なる書き手と読み手でセッション保存先を共有」に当たらない(アプリ1つ・既定の serializer)。ただし upload progress は有効 |
| CVE-2026-129481(Critical) | セッション終了時のコールバックの UAF | 低い | 独自のストリームラッパー・セッションハンドラーなし |
| CVE-2026-129182(Critical) | 8.5 のみ。ディレクトリ別設定でのバックトレース UAF | 低い | httpd.conf・.htaccess に `php_value` なし |
| CVE-2026-129496(Critical) | タイムゾーンキャッシュの UAF | 非該当 | 非 ZTS のみが条件。本番は TS 版 |
| CVE-2026-129289 / 129291 / 129292 | PHP-FPM | 非該当 | FPM 不使用 |
| CVE-2026-129538 | php-cgi | 非該当 | CGI 不使用(Apache モジュールは対象外と明記) |
| CVE-2026-128090 / 129501 / 15353 / 129506 / 129438 | Phar・新 DOM API・SOAP・URI | 非該当 | 使っていない(soap 拡張は未読み込み) |
| CVE-2026-127960 / 128064 | HTTP ストリーム(DoS・大文字スキームの平文送信) | 低い | 外部 URL の file_get_contents 等なし |

### 対応案
1. **すぐできる暫定対策(php.ini に追記 → Apache 再起動のみ)**
   - `session.upload_progress.enabled = 0`(アプリはアップロード進捗を使っていないことを確認済み)
   - `zend.exception_ignore_args = 1`
   - (任意)`fatal_error_backtraces = 0`
2. **本対策:PHP 8.5.13 へ更新**(手順は `DzkKnyKmWeb/docs/WINDOWS_WEBSERVER.md` §8.2。ジャンクションの切替なので数分の停止・切り戻し容易。oci8 の DLL はそのまま使える)
   - 注意:手順書 §8.2 のサービス名は `Apache2.4` だが、本番(方式 B)のサービス名は **`DzkKnyKmApache`**。
   - 検証用サーバーで先に 8.5.13 を確認 → 本番は利用者の少ない時間帯に実施。
3. 暫定対策の php.ini 変更は、8.5.13 適用後も残す(リポジトリの `docs/windows/prod/php.ini` にも反映する)。
