# Git練習用MD
## (１番やさしいGit&GitHubの教科書使用)

### gitの構成
ローカルなgitは作業を行うワークツリー、変更などを保存するローカルリポジトリ、ローカルリポジトリとワークツリーを繋ぐステージングエリアで構成される  

<img src="figs/git_image(component).png" width="300">

### gitの初期設定
- 1.ディレクトリを作成
- 2.git initでローカルリポジトリを作成  
最初の状態は以下の通り(現在の状態はgit statusで確認可能)  
<img src="figs/first_stat.png" width="300">

### gitへファイルやディレクトリの追加
- 1.git addでステージングエリアにファイルを追加  
追加されたファイルが緑で、未追加が赤で表示されている  
<img src="figs/git_add.png" width="300">  
git add ディレクトリ名でディレクトリ以下のファイルを全て指定可能  
<img src="figs/git_add_all_files.png" width="300">  

<img src="figs/git_image(git_add).png" width="300">  


### ファイル差分の確認
git diffコマンドでワークツリー-ステージングエリア間の差分を、--cachedオプションをつけることでステージングエリア-ローカルリポジトリ間の差分を確認することができる  
<img src="figs/git_diff.png" width="600">  

<img src="figs/git_diff_cached.png" width="300">  

<img src="figs/git_image(git_diff).png" width="300">  

### ローカルリポジトリへの追加(commmit)
git commitでステージングエリアにあるファイルをローカルリポジトリに追加  
コマンドを実行するとコミットメッセージを書くためのエディタが開くのでコミットの内容を記述する  
<img src="figs/commit_message.png" width="300">  

<img src="figs/git_commit.png" width="300">  

-mオプションをつけると1行でコミットメッセージまで完了できる  
<img src="figs/git_commit_m.png" width="300">  

コミット後の状態  
<img src="figs/commit_result.png" width="300">  

<img src="figs/git_image(git_commit).png" width="300">  

### 変更の取り消し
git checkoutやgit resetを使うことで変更前の状態に戻すことができる  

git checkout -- ファイル名でワークツリーの変更を取り消す
- git checkout前  
<img src="figs/git_checkout_bef.png" width="300">  
- git checkout後  
<img src="figs/git_checkout_aft.png" width="300">  

git reset HEAD ファイル名でステージングエリアを最新コミットの状態にする(ワーキングエリアの状態はそのまま、ステージングが取り消されるイメージ)  
<img src="figs/git_reset.png" width="300">  
- git reset実行前のファイル(最新のコミット状態)
<img src="figs/git_reset_org_and_bef.png" width="300">  
- 変更したファイル(この状態でadd→resetをするとファイル状態はそのままにステージングエリアの状態は上の図に戻る)
<img src="figs/git_reset_aft.png" width="300">  

<img src="figs/git_image(git_checkout,reset).png" width="300">  

### git管理のファイルの削除
git rmでファイル削除とステージングエリアへの登録を同時に行う  
<img src="figs/git_remove.png" width="900">  
なぜかgit rm -r removeでディレクトリが消えなかった(ファイル名がremove_test.txtと一部被ってたのが原因？)  
<img src="figs/git_remove_error.png" width="300">  

### gitで管理しないファイルの作成
.gitignoreファイルを作成することでgitで管理しないファイルを指定することができる  
<img src="figs/gitignore_bef.png" width="900">  
.gitignoreに何も登録していない状態

.gitnoreに以下の内容を記述  
<img src="figs/gitignore_files.png" width="100">  

<img src="figs/gitignore_aft.png" width="900"> 
gitnore_test.txtが消えていることがわかる(gitの管理下から外れた)(pngが追加されているのはご愛嬌)  

### gitの履歴の確認
git logでコミット履歴を確認できる  
<img src="figs/git_log.png" width="300">  
表示内容は上から順にコミットハッシュ(コミットを識別するタグのようなもの)、コミットの実行者、コミット日時、コミットメッセージ  
-pオプションでファイル差分などより詳細な内容を確認できる  