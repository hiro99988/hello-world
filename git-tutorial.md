# gitの機能

　gitとは、分散管理型のバージョン管理システムであり、
元々はオープンソースソフトウェア管理のためのソフトウェアである。
ファイルの作成・変更・削除のファイル変更記録を残すことができ、いつ・誰が・なにを・どのような変更をしたか
を記録できる。
このような記録が残るため、変更した箇所に戻ることができ、多数のメンバーとも共同でコード開発ができる。
gitは、コミット(commit)によりファイルの変更を登録する。
commitは原則、変更・削除できず、commitの変更・削除も記録として残る。

# gitのコマンド

## ツールの設定
すべてのローカルリポジトリ用の、ユーザー情報設定
- git config
    - git config –global
    - git config –global user.name "[name]"
    - git config –global user.email "[email address]"

## 設定・確認系
- git init [project-name]
指定した名前のローカルリポジトリを作成
- git status
ワークツリーのステータスを表示
- git log
ログを表示
    - -- onelineでコミットメッセージの1行のみの一覧表示
- git diff
ファイルの差分を表示

## コミット系
- git add
ステージングエリアに追加
- git commit
コミットの実行
    - -m "[descriptive message]"
      コミットメッセージを追加

## 修正系
- git commit --amend --no-edit
コミットの修正
- git checkout
削除されたファイルを復旧や過去コミットの復元など（元に戻す変更がstaging area/index内にある場合）
- git reset
コミットのリセット
- git revert
「コミットの変更を打ち消す」コミット
- git rm
ファイルとindex情報の削除

## リモート系
- git clone
レポジトリをコピー
- git pull
リモートレポジトリの同期
- git push
変更をアップロードする
- git request-pull
プルリクエスト：変更依頼
- git remote
リモートレポジトリの設定

## ブランチ系
- git branch  [branch-name]
新規ブランチの作成
- git branch --set-upstream-to origin/main
リモートブランチ（origin/main）と紐付ける設定
- git checkout
ブランチの切り替え
- git merge
ブランチの統合
    - --ff-only 変更のない統合先ブランチにマージ

## gitによる共同編集（コンフリクト）
- git stash
一時退避
- git pull
originからプル（同期）
-  git stash pop
一時退避したものの変更を加える

## ブランチマージのコンフリクトの対処例
- git merge --abort
main ブランチをマージを試行する前の状態に復元
- git pull
マージ先の変更を取得、新しいブランチを作成し、変更を行って、そのブランチを main ブランチにマージ、変更をプッシュ
- git reset --hard
マージを開始する前の状態に戻す
影響を受けたファイルに Git によって挿入された情報を使用して、手動で解決

 # githubフロー
 - 2つのブランチで構成
 - mainブランチは常にデプロイできる状態にある
 - Pull Requestがあり、他の開発者がコードをレビューし承認されたらマージする
 - gitフローとは異なりブランチは新たに作られる