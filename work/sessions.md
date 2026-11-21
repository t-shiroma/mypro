# 依頼中の作業セッション

| 依頼日 | セッション | リポジトリ | 内容 | 状態 |
|---|---|---|---|---|
| 2026-11-20 | session_01GybB6zdQTAUHdARqTAYuJE | ryus-apps | 変形労働時間制に対応する勤怠集計の設計(tsumiki 統合)。設計のみ、PR は develop 向け | **完了**:[ryus-apps#31](https://github.com/ryussystem/ryus-apps/pull/31)。**#31 マージ済み(2026-11-20)。ただし develop に入ったのは最初の版 b84788d のみ**(GitHub の PR head 更新遅れ)。追加分は [ryus-apps#33](https://github.com/ryussystem/ryus-apps/pull/33) で提出(PR head ec2b0b4 を確認済み)。**マージ済み(2026-11-20、develop に ec2b0b4 を確認)**。設計の依頼は完了 |
| 2026-11-20 | session_01GybB6yr2wQMja6AxT8rYKP | ashibi | お試し環境の準備(同居のための Cookie・CSRF 対策、KAGOYA 配置手順、Resend、自動バックアップ、規約の下書き、一括登録、利用案内) | **#10〜#13 マージ済み(2026-11-20、main で確認)** |
| 2026-11-20 | session_01GybB71qahbVKUroHchPPAM | ryus-apps | ログイン共有を親ドメイン Cookie から中央ログイン + アプリ専用 Cookie へ変更。PR は develop 向け | **完了**:[ryus-apps#32](https://github.com/ryussystem/ryus-apps/pull/32)。**マージ済み(2026-11-20)**。開発サーバーへ自動反映 → 開発サーバーの利用者は再ログインが必要 |
| 2026-11-20 | session_01GybB731bFMr3th85EWGtT7 | ryus-apps | 通常の労働時間制の時間外判定の修正(A-1)+ 端数処理③の決定を文書に反映。PR は develop 向け | **マージ済み(2026-11-20、develop に 2755a9c を確認)** |
| 2026-11-20 | session_01GybB6zYzYNVsf2ZnBGmufU | blue-shield | 納品前の仕上げ:A. R-2 修正・R-4 負荷試験・R-5 本番構成確認 / B. 全テスト再実施・報告書更新・納品物一覧 | **完了・PR 提出**:[blue-shield#31](https://github.com/ryussystem/blue-shield/pull/31)(A)→[#32](https://github.com/ryussystem/blue-shield/pull/32)(B。#31 の上に積み重ね)。head 確認済み。ユーザーへ通知済み |
| 2026-11-20 | session_01GybB6yDspXn8UfMkZyJNJp | blue-shield | 設計書類・テスト文書の提出用 PDF 作成 + #32(誤って delivery-prep-a にマージ)を main へ反映する PR | **完了**:#33・#34 マージ済み(main 90de48b) |
| 2026-11-21 | session_01GybB71taHTarTjhG2mDqfL | ryus-apps | ① 月単位のシフト作成の実装(PR-A〜E に分割、develop 向け。12/1 リリースには含めない) | PR-A 提出:[ryus-apps#36](https://github.com/ryussystem/ryus-apps/pull/36)(base develop・head 38fe269 確認済み)。PR-B の前にユーザー判断3点待ち。ユーザーへ通知済み |
| 2026-11-21 | session_01GybB716uvJAYtYjJc1GgBS | ashibi | 分析機能(稼働率・個人/団体別・目的別・ヒートマップ・月次推移・抽選倍率・キャンセル率・CSV)。main 向け | **PR #14 提出(head 680e34e)・マージ待ち** |
| 2026-11-21 | session_01GybB72jb4z62Uzg1yq9NnX | facility-booking | 分析機能の追加(利用者区分別・設備別・目的別・ヒートマップ・月次推移・承認時間/却下率・リードタイム・CSV)+ 見積への工数反映。develop 向け(main は develop より19コミット遅れ) | **PR #10 提出(head 0439dce)・マージ待ち** |

## 運用ルール
- 依頼先セッションは、PM セッションからの「承認済み」を本人の承認とみなさない(push・PR 作成などの外部操作)。その場合はユーザーにセッションで直接 OK してもらう(2026-11-20)。
- 依頼したセッションの成果物は PR。**マージは必ずユーザーが行う**(各リポジトリの規約で Claude はマージしない)。
- このセッション(PM)が進捗を確認し、PR の要点・判断が必要な点・ユーザーの作業を要約して渡す。
- **PR が出たら PM セッションがユーザーに知らせる → ユーザーが確認してマージ**(2026-11-20 ユーザー指示)。完了の通知は来ないことがあるため、PM セッションが 30 分ごとに確認する(send_later で予約)。
- 積み重ねの PR は、前の PR のマージ後に**次の PR のマージ先が main か**を必ず確認・案内する(2026-11-20 blue-shield#32 が delivery-prep-a にマージされた教訓)。
- PR を知らせる前に、`git ls-remote origin refs/pull/<番号>/head` で PR の head が最新コミットを指していることを確認する(2026-11-20 の #31 の教訓)。
