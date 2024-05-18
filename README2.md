# 講義8動画まとめの操作説明

ここでは、操作方法での解説説明を、後で復習して見返せるように画像と文章を通じて載せています。

## 目次<a id="anchor99"></a>
- [Spring Initializrでの登録操作とプロジェクトの起動操作](#anchor1)
- [.DS_Storeのコード表記追加](#anchor2)
- [プロジェクトの初期設定](#anchor3)
- [依存関係の追加に伴うライブラリーのダウンロードの操作](#anchor4)

<a id="anchor1"></a>
### Spring Initializrでの登録操作とプロジェクトの起動操作
#### Spring Initializrでの登録操作
まず依存関係の追加が必要です。 今回、InitializrからREST APIのプロジェクトを作る場合は
Spring Webに加えてMySQL DriverとMyBatis Frameworkが必要になります。

![スクリーンショット 2024-04-29 17 37 20](https://github.com/koikekatsumi/nameservice4-/assets/163390515/ddd90c27-57cf-406b-aa6f-e77eecac130c)

#### プロジェクトの起動操作
その後、ダウンロードファイルを解凍後、
メインメニュー＞＞FILE＞＞OPEN＞＞解凍したフォルダーを選び、OPENします。

<a id="anchor2"></a>
### .DS_Storeのコード表記追加
.DS_Storeファイルとは、Macでのみ使われる隠しファイルです。
Macに隠しファイル（不可視ファイル）があるのは重要なデータをユーザーが変更したりアクセスしてプログラムの大切なデータを誤って削除や変更してしまうことがないように、隠しファイルとしてユーザーが不用意に手を加えることなく、利用するために、MacBook内のデフォルトで隠しファイル/フォルダに設定されます。
尚、インテリジェイには、デフォルト設定されてない為、追加します。

.gitigone にて.DS_Storeのコードを追加

<img width="807" alt="スクリーンショット 2024-05-02 20 22 44" src="https://github.com/koikekatsumi/nameservice4-/assets/163390515/bbc47e5c-6e33-46a6-bfd5-0031d979a0b5">

<a id="anchor3"></a>
### プロジェクトの初期設定
ターミナルにて、下記のコマンドを入力
コマンドの各々の命令の意味あい

- リポジトリーの初期化
- ファイルの作成
- README.mdの表示の確認
- nameservice4（プロジェクト内にて）　表示を確認
- ステージングされたファイルの一覧を表示　ステージングしていないと、赤く表示されます。
- ステージング
- コミット

```
git init
echo "# nameservice4" >>README.md
ls
cat README.md
```

ここで、ターミナル上で、README.mdにプロジェクトの詳細を記載します。

＜記載例＞

＄　# このプロジェクトについて

このプロジェクトでは Spring Boot と MySQL を用いた簡単 Read 処理をする API を実装します。

```
git status
git add .
git commit -m "プロジェクトの初期設定"
```
その後、github上で、リポジトリを作成
下記のように、リポジトリーのpushコードをコピーして、ターミナルにて、コマンド実行します。

![スクリーンショット 2024-05-06 15 45 58](https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/88f95cee-8c94-448d-becb-6bbf4628fb37)

<a id="anchor4"></a>
### 依存関係の追加に伴うライブラリーのダウンロードの操作
インテリジェイ起動時、たとえばGradleを利用する場合、build.gradleには下記の画像の赤線のようにコードが追加されます。
依存関係を追加する際は記述を追加するだけでなく追加したライブラリをダウンロードする必要があります。

<img width="1180" alt="スクリーンショット 2024-05-04 9 00 51" src="https://github.com/koikekatsumi/nameservice4-/assets/163390515/dfd1070f-61fe-439d-98ec-58202c36ce12">

![2024-04-29_20 50 04のコピー](https://github.com/koikekatsumi/nameservice4-/assets/163390515/9b2f9760-cae0-4f7c-8f93-d222958937d7)

