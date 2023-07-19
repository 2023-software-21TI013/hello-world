以下にgitの機能やコマンドについて書く。

# --変更の作成--
## 変更をレビューしコミット操作ログを作成する
- `$ git status`<br>
コミット可能なすべての新規または変更のあるファイルを一覧で表示する
- `$ git add [file]`<br>
バージョン管理のためにファイルのスナップショットを作成する
- `$ git reset [file]`<br>
ファイルをステージングから外すが、その内容は保持する
- `$ git diff`<br>
まだステージされていないファイルの差分を表示する
- `$ git diff --staged`<br>
ステージングと最後のファイルバージョンとの差分を表示する
- `$ git commit -m "[descriptive message]"`<br>
ファイルのスナップショットをバージョン履歴内に恒久的に記録する

# --ツールの設定--
## すべてのローカルリポジトリ用の、ユーザー情報設定方法
- `$ git config --global user.name "[name]"`<br>
コミット操作に付加される名前を設定する
- `$ git config --global user.email "[email address]"`<br>
コミット操作に付加されるメールアドレスを設定する
- `$ git config --global color.ui auto`<br>
コマンドラインの出力を見やすくするため色を設定する

# --リポジトリの作成--
## リポジトリを新規作成するもしくは既存のURLから取得する
- `$ git init [project-name]`<br>
指定した名前のローカルリポジトリを作成する
- `$ git clone [url]`<br>
プロジェクトとすべてのバージョン履歴をダウンロードする

# --変更の整理-- 
## 一連のコミットに名前をつけ、完了した成果を結合する
- `$ git branch`<br>
現在のリポジトリ上のすべてのローカルブランチを一覧で表示する
- `$ git branch [branch-name]`<br>
新規ブランチを作成する
- `$ git checkout [branch-name]`<br>
指定されたブランチに切り替え、作業ディレクトリを更新する
- `$ git merge [branch]`<br>
指定されたブランチの履歴を現在のブランチに統合する
- `$ git branch -d [branch-name]`<br>
指定されたブランチを削除する

# --ファイル名の整理--
## バージョン管理されているファイルの移動、または削除を行う
- `$ git rm [file]`<br>
作業ディレクトリからファイルを削除し、削除をステージする
- `$ git rm --cached [file]`<br>
バージョン管理からファイルを削除して、ローカルのファイルは保持する
- `$ git mv [file-original] [file-renamed]`<br>
ファイル名を変更し、コミットする

# --断片の保存--
## 未完成の変更を一時的に退避し、復旧させる
- `$ git stash`<br>
すべての変更のあるトラックされているファイルを一時的に保存する
- `$ git stash list`<br>
すべての一時保存された変更セットを一覧で表示する
- `$ git stash pop`<br>
直近に一時保存されたファイルを復旧する
- `$ git stash drop`<br>
直近に一時保存された変更セットを破棄する

# --コミットの修正--
## ミスの削除と履歴の置き換え
- `$ git reset [commit]`<br>
[commit] 以降すべてのコミットを取り消し、ローカルでは変更を保持する
- `$ git reset --hard [commit]`<br>
指定されたコミットに戻り、それ以降のすべての変更を破棄する

# --履歴の確認--
## プロジェクトファイルの進展を確認する
- `$ git log`<br>
現在のブランチのバージョン履歴を一覧で表示する
- `$ git log --follow [file]`<br>
名前の変更を含む指定したファイルのバージョン履歴の一覧を表示する
- `$ git diff [first-branch]...[second-branch]`<br>
２つのブランチ間の差分を表示する
- `$ git show [commit]`<br>
指定されたコミットのメタ情報と変更内容を出力する
 
# --トラッキングの制限--
## 一時ファイルやパスを除外する
- `*.log`<br>
  `build/`<br>
  `temp-*`<br>
  .gitignoreという名前のテキストファイルで、指定されたパターンに該当
  するファイルやパスを誤ってバージョン管理してしまうことを防ぐ
- `$ git ls-files --other --ignored --exclude-standard`<br>
プロジェクト内のすべての除外されたファイルを一覧で表示する<br>

# githubフロー
 数あるGitのブランチ戦略のひとつであり、mainブランチと自らのfeatureブランチの二つのブランチで開発を進める手法である。すべての変更をmainブランチにマーこまめにデプロイすることで、デプロイ待ちのコードを最小限にする。<br>ほぼ全フローの中で最速の超高速リリースが可能であり、SaaSのような常に機能アップし続けるようなプロジェクトに最適である。コードを修正してから適用までが早いためコンフリクト（修正箇所の衝突）が少なくなり、管理者の負担が比較的少ない。<br>
## githubフローは以下のような流れで開発が行われる。
 1. 分岐を作成する<br>
 自らのfeatureブランチを作成する。
 2. 変更を加える<br>
 作成したブランチ上でリポジトリに必要な変更を加える。その後変更をブランチにコミットしてプッシュする。各コミットにはどこを変更したか、分かりやすいメッセージをつけると良い。
 3. pull requestを作成する<br>
 変更に関するフィードバックを共同開発者に依頼するpull requestを作成する。
 4. レビューコメントに対応する。<br>
 レビュー担当者がpull request全体にコメントしたり、特定の行、ファイルにコメントを追加できる。レビューに応じて引き続き変更をコミットしプッシュすることができる。
 5. pull requestをマージする<br>
 pull requeseが承認されたら、pull requestをマージする。これによりブランチが自動的にマージされ、変更が既定のブランチに表示される。この履歴は全て記録される。
 6. ブランチを削除する<br>
 pull requestをマージした後、ブランチを削除する。これは、ブランチでの作業が完了したことを示し、ユーザや他のユーザが誤って古いブランチを使用することを防ぐ。
 
# 参考
[GITチートシート](https://training.github.com/downloads/ja/github-git-cheat-sheet.pdf) <br>
[┣ GitHub-flow | リポジトリ(GitLab)入門](https://zenn.dev/ryo_4947123/books/497459787cb294/viewer/branchstrategy_githubflow) <br>
[GitHub Flowとは](https://zenn.dev/ryo_4947123/books/497459787cb294/viewer/branchstrategy_githubflow) <br>
[GitHubフロー](https://docs.github.com/ja/get-started/quickstart/github-flow) <br>
