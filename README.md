## 　　Lesson30.　GitHubのHPを作ってみる 
#### 開発メモ
### 0.GitHubのHP
　リポジトリを作成、そのリポジトリページのメニューからSettingsメニューを選択
<br>　GitHub Pagesという項目があるので、Click iy out here!をクリック
<br>　Sourceは、Branch:main /(root) を選択してSave
<br>　Change Theme ボタンから好きなテーマを選択
<br>　ちなみに私の場合は『Leap Day』
<br>　たぶん設定はこのくらい
<br>　リポジトリページに戻って下記の3つのファイルを作成
<br>　mainに置いていますが、ブランチを作りたい場合はsettingsも変更要です
<br>　
<br>　1.style.scss
<br>　add fileからCreate new fileを選択し
<br>　name your file...に『assets/css/style.scss』と入力
<br>　（『/』でリポジトリの下層フォルダが作成されます）
<br>　テキスト編集エリアに下記を入力
```
---
---
@import 'jekyll-theme-leap-day';

((以下スタイルシートを記述))

((ちなみに私の場合は下記))
h2 {
  font-size:12pt;   
  color:#ffffff;
  line-height:8;
  background-color: #4276b6;
}
h4 {
  margin-top:20px;
  font-size:11pt; 
  font-style: italic;
  color:#4276b6;
  border-bottom: solid 1px #4276b6;  
  }
h3 {
  font-size:10pt; 
  color:#ffcc00;
  text-shadow: 1px 1px 1px #888888;
  }

```
<br>　2. _ config.yml （アンダーバーの後のスペースは不要です）
<br>　リポジトリ直下に作成します
<br>　私の場合下記のように、タイトルとデスクリプションを設定しています
```
theme: jekyll-theme-leap-day
title: AlfredWorkflowで遊ぶページ
description: Lesson30.GitHubのHPを作ってみる 
```
<br>　『:』の後のスペースがなくてエラーとなったことがありましたのでご注意を
<br>　3.REAMME.md
<br>　リポジトリ直下に作成します
<br>　mdとはマークダウンファイルという意味で、HTMLタグの
<br>　リポジトリ直下に作成します。上記cssみたいにサブフォルダではないので、
<br>　2と3のファイルは、ローカルに作成したものを
<br>　upload　filesでまとめてアップロードする方が楽です


### 1.裏技サイトを探す
　LessonのタイトルがAlfredとは無関係になってしまいました。そう、ネタ切れです
<br>　経験上、alfred化する場合、検索サイトのラッパーとして使うか、
<br>　まとまっているサイトからパースするかだと思います
<br>　https://creive.me/archives/154/　
<br>　というまとめサイトを見つけたのでパースことにしました
<br>　でも裏技が50個とちょっと少なめです。。
<br>　
<br>　このサイトの裏技はliタグでまとまっています
<br>　liのあとに数字とピリオドがあって、1から50までの裏技が紹介されています
<br>　たまにbタグで強調しているので、これを除けばOKそうですね
<br>　ここまであたりをつけたらコーディングしましょう
### 2.コーディング
　お約束通りcurlでソースを取得
<br>　改行やスペース、bタグ、を取り除いて、liタグの集合を作ります
<br>　その後でliタグ、先頭の番号を削除して、裏技の中身を配列liに格納します
<br>　
<br>　サイト上、裏技は50件で不変な感じではありますが
<br>　一応、配列liの件数（最大値）を求めて、その中からランダムで3件選択します
<br>　深い意味はなく、全体が50件なので3件にしてみたという程度です
<br>　後はJSONフォーマットを作成して、はい、できあがり
### 3.最後の一工夫
<br>　テストをしてみると、裏技がalfred出力に全て書かれてしまうので
<br>　ちょっと工夫してみました。それは、先頭の語句だけを出力するというものです
<br>　下記のパターンにマッチした部分だけをtitleとして表示させています
<br>　『〜、』『〜：』『〜に』『〜を』『〜は』『〜の』
<br>　なお、argには裏技の文言全体をセットしています
<br>　そのため、alfred出力を選択すると、裏技の文言全体でサーチします

#### 背景
　webサーフィン中にいろいろなターミナルに関する裏技を見ていたのですが
<br>　たまたま生活の裏技に飛び火してしまい、alfred化することにしてみました
#### 取扱説明
### 機能:
　ランダムに裏技を表示させる
### インストール:
　1.[alfredworkflow](https://github.com/KitanoTamotsu/waza/releases/download/1.0/waza.alfredworkflow.zip)をダウンロード 
<br>　2.ファイルをダブルクリックしてワークフローに登録
### 使い方:
　Alfredからキーワード『waza』で起動
<br>
<br>
[トップページに戻る](https://kitanotamotsu.github.io/)

