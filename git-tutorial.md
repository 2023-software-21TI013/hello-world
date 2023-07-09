以下にgitの機能やコマンドについて書く。

--変更の作成--<br>
変更をレビューしコミット操作ログを作成する<br>
$ git status<br>
コミット可能なすべての新規または変更のあるファイルを一覧で表示する<br>
$ git add [file]<br>
バージョン管理のためにファイルのスナップショットを作成する<br>
$ git reset [file]<br>
ファイルをステージングから外すが、その内容は保持する<br>
$ git diff<br>
まだステージされていないファイルの差分を表示する<br>
$ git diff --staged<br>
ステージングと最後のファイルバージョンとの差分を表示する<br>
$ git commit -m "[descriptive message]"<br>
ファイルのスナップショットをバージョン履歴内に恒久的に記録する<br>

--ツールの設定--<br>
すべてのローカルリポジトリ用の、ユーザー情報設定方法<br>
$ git config --global user.name "[name]"<br>
コミット操作に付加される名前を設定する<br>
$ git config --global user.email "[email address]"<br>
コミット操作に付加されるメールアドレスを設定する<br>
$ git config --global color.ui auto<br>
コマンドラインの出力を見やすくするため色を設定する<br>
リポジトリの作成<br>
リポジトリを新規作成するもしくは既存のURLから取得する<br>
$ git init [project-name]<br>
指定した名前のローカルリポジトリを作成する<br>
$ git clone [url]<br>
プロジェクトとすべてのバージョン履歴をダウンロードする<br>

--変更の整理-- <br>
一連のコミットに名前をつけ、完了した成果を結合する<br>
$ git branch<br>
現在のリポジトリ上のすべてのローカルブランチを一覧で表示する<br>
$ git branch [branch-name]<br>
新規ブランチを作成する<br>
$ git checkout [branch-name]<br>
指定されたブランチに切り替え、作業ディレクトリを更新する<br>
$ git merge [branch]<br>
指定されたブランチの履歴を現在のブランチに統合する<br>
$ git branch -d [branch-name]<br>
指定されたブランチを削除する<br>

--ファイル名の整理--<br>
バージョン管理されているファイルの移動、または削除を行う<br>
$ git rm [file]<br>
作業ディレクトリからファイルを削除し、削除をステージする<br>
$ git rm --cached [file]<br>
バージョン管理からファイルを削除して、ローカルのファイルは保持する<br>
$ git mv [file-original] [file-renamed]<br>
ファイル名を変更し、コミットする<br>

--断片の保存--<br>
未完成の変更を一時的に退避し、復旧させる<br>
$ git stash<br>
すべての変更のあるトラックされているファイルを一時的に保存する<br>
$ git stash list<br>
すべての一時保存された変更セットを一覧で表示する<br>
$ git stash pop<br>
直近に一時保存されたファイルを復旧する<br>
$ git stash drop<br>
直近に一時保存された変更セットを破棄する<br>

--コミットの修正--<br>
ミスの削除と履歴の置き換え<br>
$ git reset [commit]<br>
[commit] 以降すべてのコミットを取り消し、ローカルでは変更を保持する<br>
$ git reset --hard [commit]<br>
指定されたコミットに戻り、それ以降のすべての変更を破棄する<br>

--履歴の確認--<br>
プロジェクトファイルの進展を確認する<br>
$ git log<br>
現在のブランチのバージョン履歴を一覧で表示する<br>
$ git log --follow [file]<br>
名前の変更を含む指定したファイルのバージョン履歴の一覧を表示する<br>
$ git diff [first-branch]...[second-branch]<br>
２つのブランチ間の差分を表示する<br>
$ git show [commit]<br>
指定されたコミットのメタ情報と変更内容を出力する<br>

--トラッキングの制限--<br>
*.log<br>
build/<br>
temp-*<br>
.gitignoreという名前のテキストファイルで、指定されたパターンに該当<br>
するファイルやパスを誤ってバージョン管理してしまうことを防ぐ<br>
$ git ls-files --other --ignored --exclude-standard<br>
プロジェクト内のすべての除外されたファイルを一覧で表示する<br>

参考<br>
GITチートシート
https://training.github.com/downloads/ja/github-git-cheat-sheet.pdf