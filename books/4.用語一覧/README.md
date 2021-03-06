## Gitでよく使われる用語一覧
ここではGitでよく使われる用語の一覧について説明します。
イメージが少し掴みにくいと思いますが、少しずつ慣れていきましょう！

初めてGitを使う方はProgateのGit講座を一度やってみましょう！

## repository（リポジトリ）

ファイルのバージョンを管理するためには、変更内容を保存しておく必要があるでしょう。
変更内容を保存しておくための保存先（倉庫のようなもの）のことをリポジトリといいます。
開発を行う時はリポジトリにファイルをアップロードすることで、ファイルの内容をメンバー全員に共有することが出来ます。

また、リポジトリには2種類あり、ローカルリポジトリとリモートリポジトリがあります。

![リポジトリ](../.vuepress/images/image4.png)

### ローカルリポジトリ

ローカルリポジトリとは、実際に自分のPC上で変更を行うリポジトリのことを言います。
自分がPC上で変更を加えると、変更前からどのファイルのどの部分を変更したかを確認することが出来ます。



### リモートリポジトリ

リモートリポジトリはチーム開発でのファイルのバージョン管理や、バックアップを目的としてネットワーク上に作られるリポジトリのことです。

もしかすると、これだけの説明では2つの違いは分かりにくいかもしれません。
なので、とりあえずの理解は以下の2点だけ踏まえておいてください！

:::tip
`ローカルリポジトリ`
自分のPC上で実際に変更するファイル

`リモートリポジトリ`
ネットワーク上に上がっている最新バージョンのファイル
:::

## init（初期化）
コマンドの通り、初期化(initialize)をしています。git initによって、このディレクトリはGitで管理をするために色々下準備をしてくれます(.gitという隠しディレクトリができて、そこに色々情報が追加されていきます)。

## add（アド）
Gitにはインデックスという、「どのファイルを管理対象にするか」を記録するエリアがあります。そこにファイルやフォルダを追加(add)するためのコマンドです。いくらファイルを編集しても、git addをしなくては編集内容がインデックスに反映されず、git commitをしても編集されていないと怒られてしまいます。
git add .を使うのかgit add -uを使うのかgit add -Aを使うのかについてはこちらが参考になります。

:::warning
`git add -a` や `git add .`は関係のないファイルまで追加されてしまうことがあるので、注意が必要です。
:::

## commit（コミット）
ローカルリポジトリのファイルを変更し、リモートリポジトリに変更したファイルをアップロードすることをcommit（コミット）と言います。
また、それぞれのコミットには、以下の6個の情報が保存されます。
- リビジョン番号（1e010f4572625f3741a306b8e996cのような値）
- コミットした人（誰が）
- コミットした日時（いつ）
- コミットしたときのファイル内容の差分（どのファイルの、どの箇所を）
- コミットメッセージ（どんなメッセージを残して）
- 親コミット（1つ前のコミット）のリビジョン番号


コミットにはメッセージを入れることができ、以下の図のようなイメージが分かりやすいでしょう！
図に出てきているブランチという言葉は[次](/4.用語一覧/#branch（ブランチ）)に説明します！

![コミット](../.vuepress/images/image3.png)

## branch（ブランチ）
文字通り、木の枝と同じ意味です。
Gitでは木の枝のようにバージョン管理が行われています。
以下の図を見てみましょう。

![ブランチ](../.vuepress/images/image5.png)

下から順に上に行くほど新しいバージョンになっていることがわかると思います。
ブランチには名前をつけることができ、本筋（最新の内容 or 現行で動作している内容）のブランチの名前を「master」と名付けることが慣習となっています。

しかし、これだとなぜ枝のようになっているのか分かりにくいでしょう。

ここで、もう少し複雑な例を見てみましょう。

![複雑なコミット](../.vuepress/images/image8.png)

状況を説明します。

今、masterという名前のブランチがプロジェクトの本筋だったとしましょう。

じろうさんは、index.htmlというファイルに「あいうえお」という文字を追加したいのですが、本筋で作業を行った場合、もしかすると何らかのエラーが出てしますかもしれません。

そこで、topic-10という名前のブランチを新たに作成してあげることで、一旦、本筋のブランチとは切り離して作業することができます。（新しく作るブラント名は任意で決めることが出来ます！詳しくは[checkout（チェックアウト）](/4.用語一覧/#checkout（チェックアウト）)を参照してください。）

変更が終わった後、問題なく実装できていることが確認された時点で本筋のmasterブランチに反映してあげることが出来ます。

すると、どうでしょう！枝のように2つのブランチが作られていることが確認できると思います。


今はまだはっきりとイメージを掴むのは難しいかもしれませんが、少しずつ感覚を掴んでいきましょう！

:::tip

ここで抑えておきたいポイント

①masterが本筋（最新バージョンのブランチ）のブランチ

②ブランチは複数作ることができる

③ブランチを分けることで、本筋（master）にエラーが出ることを心配せずに作業することができる
:::

## checkout（チェックアウト）
ブランチを移動することをチェックアウトと言います。

先程の例を見てみましょう。

![チェックアウト](../.vuepress/images/image1.png)

masterブランチからtopic-10ブランチに切り替わっている場所、topic-10ブランチからmasterブランチに切り替わっている場所にそれぞれ「チェックアウト」と書いてあるのが分かるでしょう。

このように、ブランチを切り替える動作のことをチェックアウトと言います。

:::tip
新しくブランチを作った際、ブランチの名前は自由に決める事ができます。
:::

## push(プッシュ）
ローカルリポジトリのブランチ上で作成されたコミットを、リモートリポジトリにアップロードすることをプッシュと言います。

![プッシュ](../.vuepress/images/image9.png)

ローカルの履歴がリモートの履歴とコンフリクトする場合、エラーになりプッシュは失敗してしまいます。詳しくはコンフリクトを参照してください。

しかし、「- f 、-- force」オプションで強制的にプッシュすることで、上書きすることもできます。

:::danger
`-f`,  `--force` オプションについては推奨されていないやり方なので、解決方法は責任者などに一度確認を取りましょう！
:::

![プッシュエラー](../.vuepress/images/image7.png)

## pull （プル）
リモートリポジトリを共有して複数人で作業すると、みんながリモートリポジトリにプッシュしていきます。

そこで、自分のローカルリポジトリに、他の人がプッシュした変更内容を取り込むことをプルと言います。

プルすると、自分のPCの内容が変更されてしまいます。

変更を反映したくないけれど、変更の情報だけ取得したいときはfetch（フェッチ）を参照してください！

![プル](../.vuepress/images/image6.png)

## fork（フォーク）
GitHub上にある共同のリモートリポジトリを自分のリモートリポジトリにコピーすることをフォークと言います。

共同のリモートリポジトリに直接変更を加えてしまうと、それによってエラーが出てしまった場合、プロジェクト全体が滞ってしまいます。

そこで、一旦フォークして自分のリモートリポジトリに持ってきてから、それをローカルリポジトリに[クローン](/4.用語一覧/#clone（クローン）)して作業を行います。

そして、変更したところを共同のリモートリポジトリに反映することで、円滑にプロジェクトを進めることができます。

![フォーク](../.vuepress/images/image11.png)

## clone（クローン）
リモートリポジトリをローカルで扱うための操作。

ローカルにリモートリポジトリを丸々コピーすれば、本体プログラムとは別に作業できる。

## pull request（プルリクエスト）
コードレビューは、ソフトウェア開発工程で見過ごされた誤りを検出・修正することを目的としてソースコードの体系的な検査（査読）を行う作業のこと。

チーム開発の際にはこの作業を行うことをタスク化させるためにpull requestを使うことができる。

pull requestとは簡単に言うと、開発者のローカルリポジトリでの変更を他の開発者に通知する機能です。プルリクエストは次のような機能を提供します。

- 機能追加や改修など、作業内容をレビュー・マージ担当者やその他関係者に通知する。

- ソースコードの変更箇所をわかりやすく表示する。

- ソースコードに関するコミュニケーションの場を提供する。

 プルリクエストを使わない開発プロセス
 
![プルリク1](../.vuepress/images/image2.png)

プルリクエストを使う開発プロセス

![プルリク2](../.vuepress/images/image10.png)

Pull Request の手順
1. 対象のGitHubリポジトリをFork
1. ローカルへclone（クローン）
1. ローカルリポジトリで新規ブランチを作成
1. 修正を加えるadd（アド）、commit（コミット）
1. 作成したブランチをpush（プッシュ）する
1. Pull RequestをGitHub上で作成


