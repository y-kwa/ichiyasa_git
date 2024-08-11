# Git練習用MD
## １番やさしいGit&GitHubの教科書使用

## ローカル環境でのgit
### gitの構成
ローカルのgitは作業を行うワークツリー、変更などを保存するローカルリポジトリ、ローカルリポジトリとワークツリーを繋ぐステージングエリアで構成される  

<img src="figs/git_image(component).png" width="300">

### gitの初期設定
- 1.ディレクトリを作成
- 2.`git init`でローカルリポジトリを作成  
最初の状態は以下の通り(現在の状態はgit statusで確認可能)  
<img src="figs/first_stat.png" width="300">

### gitへファイルやディレクトリの追加
- 1.`git add`でステージングエリアにファイルを追加  
追加されたファイルが緑で、未追加が赤で表示されている  
<img src="figs/git_add.png" width="300">  
git add ディレクトリ名でディレクトリ以下のファイルを全て指定可能  
<img src="figs/git_add_all_files.png" width="300">  

<img src="figs/git_image(git_add).png" width="300">  


### ファイル差分の確認
`git diff`コマンドでワークツリー-ステージングエリア間の差分を、--cachedオプションをつけることでステージングエリア-ローカルリポジトリ間の差分を確認することができる  
<img src="figs/git_diff.png" width="900">  

<img src="figs/git_diff_cached.png" width="300">  

<img src="figs/git_image(git_diff).png" width="300">  

### ローカルリポジトリへの追加(commmit)
`git commit`でステージングエリアにあるファイルをローカルリポジトリに追加  
コマンドを実行するとコミットメッセージを書くためのエディタが開くのでコミットの内容を記述する  
<img src="figs/commit_message.png" width="400">  

<img src="figs/git_commit.png" width="300">  

-mオプションをつけると1行でコミットメッセージまで完了できる  
<img src="figs/git_commit_m.png" width="500">  

コミット後の状態  
<img src="figs/commit_result.png" width="300">  

<img src="figs/git_image(git_commit).png" width="300">  

### 変更の取り消し
`git checkout`や`git reset`を使うことで変更前の状態に戻すことができる  

`git checkout -- ファイル名`でワークツリーの変更を取り消す
- git checkout前  
<img src="figs/git_checkout_bef.png" width="400">  
- git checkout後  
<img src="figs/git_checkout_aft.png" width="400">  

`git reset HEAD ファイル名`でステージングエリアを最新コミットの状態にする(ワーキングエリアの状態はそのまま、ステージングが取り消されるイメージ)  
<img src="figs/git_reset.png" width="400">  
- git reset実行前のファイル(最新のコミット状態)  
<img src="figs/git_reset_org_and_bef.png" width="400">  
- 変更したファイル(この状態でadd→resetをするとファイル状態はそのままにステージングエリアの状態は上の図に戻る)
<img src="figs/git_reset_aft.png" width="400">  

<img src="figs/git_image(git_checkout,reset).png" width="300">  

### git管理のファイルの削除
`git rm`でファイル削除とステージングエリアへの登録を同時に行う  
<img src="figs/git_remove.png" width="900">  
なぜかgit rm -r removeでディレクトリが消えなかった(ファイル名がremove_test.txtと一部被ってたのが原因？)  
<img src="figs/git_remove_error.png" width="300">  

### gitで管理しないファイルの作成
.gitignoreファイルを作成することでgitで管理しないファイルを指定することができる  
<img src="figs/gitignore_bef.png" width="900">  
.gitignoreに何も登録していない状態

.gitnoreに以下の内容を記述  
<img src="figs/gitignore_files.png" width="100">  

<img src="figs/gitignore_aft.png" width="400"> 
gitnore_test.txtが消えていることがわかる(gitの管理下から外れた)(pngが追加されているのはご愛嬌)  

### gitの履歴の確認
`git log`でコミット履歴を確認できる  
<img src="figs/git_log.png" width="300">  
表示内容は上から順にコミットハッシュ(コミットを識別するタグのようなもの)、コミットの実行者、コミット日時、コミットメッセージ  
-pオプションでファイル差分などより詳細な内容を確認できる  

## githubとの連携
### リモートリポジトリのフォークとクローン
リモートリポジトリをフォークすることで元のリポジトリに影響を与えることなく変更することができる
<img src="figs/fork_bef.png" width="900">

<img src="figs/fork_aft.png" width="900">

`git remote`でリモートリポジトリの情報を確認することができる(-vオプションでURLを表示)  
<img src="figs/git_remote.png" width="300">

### ブランチの作成
`git branch ブランチ名`でブランチを作成することができる  
`git branch`で今あるブランチを確認することができる(`git status`でも確認可能)  
`git checkout ブランチ名`で指定ブランチに移動する  
<img src="figs/git_branch.png" width="300">  

### ブランチで使うコマンド類
`git diff 比較したいブランチ名`で今あるブランチとの比較が行える  
<img src="figs/git_diff_master.png" width="300">  

`git push`でリモートリポジトリへ変更を反映させる  
`git push プッシュ先のリモートリポジトリ名 プッシュしたいブランチ名`  
※ このときリモートリポジトリの管理者がmasterブランチへマージしていいかを判断する(プルリクエストとレビュー)  

- 1.リモートリポジトリへプッシュする
<img src="figs/git_push.png" width="300">  
- 2.プッシュ後はGitHub上にプルリクエストのためのボタンが表示される  
<img src="figs/github_push.png" width="300">  
- 3.プルリクエストのためにコメントを書く  
<img src="figs/github_pullrequest.png" width="300">  
- 4.プルリクエストが実行される  
<img src="figs/github_pullrequest_result.png" width="300">  

### 作成したブランチ内での作業(この見出しに意味はない)
ブランチに関係するコマンドとか雑多なメモ  
- `git checkout -b ブランチ名`でブランチ作成&そのブランチにチェックアウト  
- ブランチ内でブランチを作成するとそのブランチからの派生となるので注意  
<img src="figs/git_branch_note.png" width="300">  

### ここはbranch_test2で書いてる内容です
ちなみに上の見出し部分のブランチ名はbranch_test  
あんま考えてないからこんなわかりにくい名前になるんです  
ということでここの内容をmainブランチに反映します  
<img src="figs/git_checkout_b.png" width="300">  
<img src="figs/git_add_a.png" width="300">  
note:`git add -A` (または`git add -all`)で変更を加えたファイル全てをステージングエリアに追加  
`git merge マージしたいブランチ名`でブランチの内容をマージできる(ちなみにここからのコメントはmainブランチで書いてます)  
<img src="figs/git_merge_test.png" width="300">  
`git merge main`とすると派生ブランチにメインブランチの内容を取り込める  
<img src="figs/git_merge_branchside.png" width="900">  
全体の作業内容はこんな感じ  
<img src="figs/merge_image.png" width="300">  

### ブランチの削除
ローカルリポジトリのブランチの削除方法は2通り  
- マージ済みのブランチを削除するには`git branch -d 削除したいブランチ名`  
- マージ状況に関わらずブランチを削除するには`git branch -D 削除したいブランチ名`  
<img src="figs/git_branch_d.png" width="300">  
-Dオプション使わなくても消えてますね  

### コンフリクトの解消
コンフリクト発生用のブランチを作ってメインブランチとコンフリクトさせてみる  
- 2*2=7841787859817  
メインブランチの記述内容
<img src="figs/discribe_main.png" width="300">  
コンフリクトブランチの記述内容
<img src="figs/discribe_branch.png" width="300">  