# 依頼中の作業セッション

| 依頼日 | セッション | リポジトリ | 内容 | 状態 |
|---|---|---|---|---|
| 2026-11-20 | session_01GybB6zdQTAUHdARqTAYuJE | ryus-apps | 変形労働時間制に対応する勤怠集計の設計(tsumiki 統合)。設計のみ、PR は develop 向け | **完了**:[ryus-apps#31](https://github.com/ryussystem/ryus-apps/pull/31)。**#31 マージ済み(2026-11-20)。ただし develop に入ったのは最初の版 b84788d のみ**(GitHub の PR head 更新遅れ)。追加分は [ryus-apps#33](https://github.com/ryussystem/ryus-apps/pull/33) で提出(PR head ec2b0b4 を確認済み)。**マージ済み(2026-11-20、develop に ec2b0b4 を確認)**。設計の依頼は完了 |
| 2026-11-20 | session_01GybB6yr2wQMja6AxT8rYKP | ashibi | お試し環境の準備(同居のための Cookie・CSRF 対策、KAGOYA 配置手順、Resend、自動バックアップ、規約の下書き、一括登録、利用案内) | **#10〜#13 マージ済み(2026-11-20、main で確認)** |
| 2026-11-20 | session_01GybB71qahbVKUroHchPPAM | ryus-apps | ログイン共有を親ドメイン Cookie から中央ログイン + アプリ専用 Cookie へ変更。PR は develop 向け | **完了**:[ryus-apps#32](https://github.com/ryussystem/ryus-apps/pull/32)。**マージ済み(2026-11-20)**。開発サーバーへ自動反映 → 開発サーバーの利用者は再ログインが必要 |
| 2026-11-20 | session_01GybB731bFMr3th85EWGtT7 | ryus-apps | 通常の労働時間制の時間外判定の修正(A-1)+ 端数処理③の決定を文書に反映。PR は develop 向け | **マージ済み(2026-11-20、develop に 2755a9c を確認)** |
| 2026-11-20 | session_01GybB6zYzYNVsf2ZnBGmufU | blue-shield | 納品前の仕上げ:A. R-2 修正・R-4 負荷試験・R-5 本番構成確認 / B. 全テスト再実施・報告書更新・納品物一覧 | **完了・PR 提出**:[blue-shield#31](https://github.com/ryussystem/blue-shield/pull/31)(A)→[#32](https://github.com/ryussystem/blue-shield/pull/32)(B。#31 の上に積み重ね)。head 確認済み。ユーザーへ通知済み |
| 2026-11-20 | session_01GybB6yDspXn8UfMkZyJNJp | blue-shield | 設計書類・テスト文書の提出用 PDF 作成 + #32(誤って delivery-prep-a にマージ)を main へ反映する PR | **完了**:#33・#34 マージ済み(main 90de48b) |
| 2026-11-21 | session_01GybB71taHTarTjhG2mDqfL | ryus-apps | ① 月単位のシフト作成の実装(PR-A〜E に分割、develop 向け。12/1 リリースには含めない) | PR-A [ryus-apps#36](https://github.com/ryussystem/ryus-apps/pull/36) **マージ済み(2026-11-21、develop 5be3480)**。判断3点はおすすめどおりで確定(①社員ごとの日の種類の表 ②責任者が配下の組織も作成・公開 ③休憩1つ)。PR-B [ryus-apps#37](https://github.com/ryussystem/ryus-apps/pull/37) **マージ済み(2026-11-21、develop 4519ce2)**。PR-C [ryus-apps#38](https://github.com/ryussystem/ryus-apps/pull/38) **マージ済み(2026-11-21、develop 4e348d7)**。PR-D [ryus-apps#39](https://github.com/ryussystem/ryus-apps/pull/39) **マージ済み(2026-11-21、develop c5b5c87)**。PR-E [ryus-apps#40](https://github.com/ryussystem/ryus-apps/pull/40) **マージ済み(2026-11-21、develop ebc7b5d)。①完了。社内開発環境への反映を確認** |
| 2026-11-21 | session_01GybB716uvJAYtYjJc1GgBS | ashibi | 分析機能(稼働率・個人/団体別・目的別・ヒートマップ・月次推移・抽選倍率・キャンセル率・CSV)。main 向け | **#14 マージ済み(2026-11-21、main で確認)** |
| 2026-11-21 | session_01GybB72jb4z62Uzg1yq9NnX | facility-booking | 分析機能の追加(利用者区分別・設備別・目的別・ヒートマップ・月次推移・承認時間/却下率・リードタイム・CSV)+ 見積への工数反映。develop 向け(main は develop より19コミット遅れ) | **#10 マージ済み(2026-11-21、develop で確認)** |
| 2026-11-21 | session_01GybB72jb4z62Uzg1yq9NnX | facility-booking | 分析機能の積み残し(マニュアルの章・機能一覧xlsx・数値列の右寄せ)。develop 向け | **#11 マージ済み(2026-11-21、develop で確認)** |
| 2026-11-24 | session_01GybB6z57jnyZCj8ErQZJNV | okinawa-stay-manager-v2 | ryus-apps.jp 同居のための Cookie(__Host-)・CSRF(Origin なしを拒否)修正。develop 向け | **PR [#43](https://github.com/ryussystem/okinawa-stay-manager-v2/pull/43) マージ済み(2026-11-24、develop 76892e3)** |
| 2026-11-24 | session_01GybB6zfoK31VAKR169pWrF | secubase | ryus-apps.jp 同居のための Cookie(__Host-)修正。main 向け | **PR [#43](https://github.com/ryussystem/secubase/pull/43) マージ済み(2026-11-24、main)** |
| 2026-11-24 | session_01GybB6yW9MSds8CNpm6MpAK | work-app | 給与連携の内訳ポップアップ(日ごとの内訳・週40h超の週小計・月合計は一覧と一致)。main 向け | **#196 マージ済み(2026-11-24、main ec5ce78)** |
| 2026-11-24 | session_01GybB6zfoK31VAKR169pWrF | secubase | 手順書・設定例のドメインを secubase.ryus-apps.jp に書き換え(文書のみ)。main 向け | **#44 マージ済み(2026-11-24、main)** |
| 2026-11-24 | session_01GybB72sHRvJNhAKtXxtEQz | secubase | 運営者向けのテナント管理画面(admin.secubase.ryus-apps.jp 推奨・社内IPのみ)。main 向け・PR 分割 | **#45・#46 マージ済み(2026-11-25、main 316a04d)** |
| 2026-11-24 | session_01GybB6yeHzo4QBsJRccA9nX | DzkKnyKmWeb | PHP 8.5.13 の動作確認(構文・PHPUnit、8.5.12 と比較)、php.ini に暫定対策、手順書のサービス名 DzkKnyKmApache、11/26 当日のチェックリスト | ローカルコミット a85f2a9。単体(DBなし)45件・DB 4件は両版成功。PR [DzkKnyKmWeb#5](https://github.com/ryussystem/DzkKnyKmWeb/pull/5) **マージ済み(2026-11-25、develop)**。追補 PR [DzkKnyKmWeb#6](https://github.com/ryussystem/DzkKnyKmWeb/pull/6) **マージ済み(2026-11-25)**。Oracle XE(JA16SJISTILDE)で 8.5.12/8.5.13 とも単体54件・結合43シナリオ(264 OK・既知6・NG0)、結果一致 |
| 2026-11-25 | session_01GybB72CR6S7z6nqH3P8NWP | secubase | @eslint/js 10 対応(#38 の置き換え・4行修正)、dependabot.yml で TS7 を除外・グループの重なり解消。main 向け | **#48 マージ済み(2026-11-25)** |
| 2026-11-25 | session_01GybB71XLbWCLw17GMFHjhc | ashibi | 2団体の施設データをホームページから取得し一括登録用ファイルを作成、取れない項目の一覧。main 向け | PR [ashibi#15](https://github.com/ryussystem/ashibi/pull/15) **マージ済み(2026-11-25、main)** |
| 2026-11-25 | session_01GybB6yQoPvsTNu38sGgNL8 | secubase | 情報資産の CIA 評価・要対応の印・リスク対応計画の下書き(PR1、汎用の計算列と条件)。main 向け | **#47 マージ済み(2026-11-25)** |
| 2026-11-25 | session_01GybB6yASgsWe5GpfrzcaiL | ashibi | 部屋の組み合わせの同時貸出を防ぐ機能(汎用・スポ協の AB⇔A・B を登録)。main 向け | **#16 マージ済み(2026-11-25)** |

## 運用ルール
- 依頼先セッションは、PM セッションからの「承認済み」を本人の承認とみなさない(push・PR 作成などの外部操作)。その場合はユーザーにセッションで直接 OK してもらう(2026-11-20)。
- 依頼したセッションの成果物は PR。**マージは必ずユーザーが行う**(各リポジトリの規約で Claude はマージしない)。
- このセッション(PM)が進捗を確認し、PR の要点・判断が必要な点・ユーザーの作業を要約して渡す。
- **PR が出たら PM セッションがユーザーに知らせる → ユーザーが確認してマージ**(2026-11-20 ユーザー指示)。完了の通知は来ないことがあるため、PM セッションが 30 分ごとに確認する(send_later で予約)。
- 積み重ねの PR は、前の PR のマージ後に**次の PR のマージ先が main か**を必ず確認・案内する(2026-11-20 blue-shield#32 が delivery-prep-a にマージされた教訓)。
- PR を知らせる前に、`git ls-remote origin refs/pull/<番号>/head` で PR の head が最新コミットを指していることを確認する(2026-11-20 の #31 の教訓)。

- 依頼後20分ほどで get_session を見て、push 前の本人 OK 待ち(BLOCKED)で止まっていればすぐユーザーに知らせる(2026-11-24)
