# 依頼中の作業セッション

| 依頼日 | セッション | リポジトリ | 内容 | 状態 |
|---|---|---|---|---|
| 2026-11-20 | session_01GybB6zdQTAUHdARqTAYuJE | ryus-apps | 変形労働時間制に対応する勤怠集計の設計(tsumiki 統合)。設計のみ、PR は develop 向け | **完了**:[ryus-apps#31](https://github.com/ryussystem/ryus-apps/pull/31)。**#31 マージ済み(2026-11-20)。ただし develop に入ったのは最初の版 b84788d のみ**(GitHub の PR head 更新遅れ)。追加分は [ryus-apps#33](https://github.com/ryussystem/ryus-apps/pull/33) で提出(PR head ec2b0b4 を確認済み)。**マージ済み(2026-11-20、develop に ec2b0b4 を確認)**。設計の依頼は完了 |
| 2026-11-20 | session_01GybB6yr2wQMja6AxT8rYKP | ashibi | お試し環境の準備(同居のための Cookie・CSRF 対策、KAGOYA 配置手順、Resend、自動バックアップ、規約の下書き、一括登録、利用案内) | **PR 提出**:[ashibi#10](https://github.com/ryussystem/ashibi/pull/10)→[#11](https://github.com/ryussystem/ashibi/pull/11)→[#12](https://github.com/ryussystem/ashibi/pull/12)→[#13](https://github.com/ryussystem/ashibi/pull/13)(積み重ね。順にマージ)。head 確認済み。ユーザーへ通知済み |
| 2026-11-20 | session_01GybB71qahbVKUroHchPPAM | ryus-apps | ログイン共有を親ドメイン Cookie から中央ログイン + アプリ専用 Cookie へ変更。PR は develop 向け | **完了**:[ryus-apps#32](https://github.com/ryussystem/ryus-apps/pull/32)。**マージ済み(2026-11-20)**。開発サーバーへ自動反映 → 開発サーバーの利用者は再ログインが必要 |
| 2026-11-20 | session_01GybB731bFMr3th85EWGtT7 | ryus-apps | 通常の労働時間制の時間外判定の修正(A-1)+ 端数処理③の決定を文書に反映。PR は develop 向け | **PR 提出**:[ryus-apps#34](https://github.com/ryussystem/ryus-apps/pull/34)(head 2755a9c 確認済み)。マージ前に開発サーバーで確認スクリプトの実行が必要。ユーザーへ通知済み |
| 2026-11-20 | session_01GybB6zYzYNVsf2ZnBGmufU | blue-shield | 納品前の仕上げ:A. R-2 修正・R-4 負荷試験・R-5 本番構成確認 / B. 全テスト再実施・報告書更新・納品物一覧 | 作業中 |

## 運用ルール
- 依頼したセッションの成果物は PR。**マージは必ずユーザーが行う**(各リポジトリの規約で Claude はマージしない)。
- このセッション(PM)が進捗を確認し、PR の要点・判断が必要な点・ユーザーの作業を要約して渡す。
- **PR が出たら PM セッションがユーザーに知らせる → ユーザーが確認してマージ**(2026-11-20 ユーザー指示)。完了の通知は来ないことがあるため、PM セッションが 30 分ごとに確認する(send_later で予約)。
- PR を知らせる前に、`git ls-remote origin refs/pull/<番号>/head` で PR の head が最新コミットを指していることを確認する(2026-11-20 の #31 の教訓)。
