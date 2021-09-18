## 　　Lesson30.　GitHubのHPを作ってみる 
#### 開発メモ
ワークフロー
<br>　<img width="600" src="https://user-images.githubusercontent.com/40127279/127757986-ab910290-6835-4ddf-bc12-3cbb324bb8d3.png">

ワークフローの解説は後にして、GitHubページのカスタマイズ方法です

### 1.GitHubのHP
　GitHubは公開用のHPのデザインが準備されています。このページがまさにそれです
<br>　試してみましが、特に便利かどうかわかりません
<br>　せっかく作ったのでポイントをメモしておきます
### 2.ページの設定
　多分リポジトリ1つについて1ページだと思います
<br>　リポジトリを作成後、そのリポジトリページのメニューからSettingsメニューを選択
<br>　GitHub Pagesという項目があるので、Click iy out here!をクリック
<br>　Sourceは、Branch:main /(root) を選択してSave
<br>　Change Theme ボタンから好きなテーマを選択
<br>　ちなみに私の場合は『Leap Day』
<br>　たぶん設定はこのくらい
### 3.作成が必要なファイルは3つ
<br>　リポジトリページに戻って下記の3つのファイルを作成
<br>　1.style.scss
<br>　2. _ config.yml 
<br>　3.README.md
<br>　mainに置いていますが、ブランチを作りたい場合はsettingsも変更要です
<br>　以下3ファイルの説明です
<br>　
<br>　1.style.scss
<br>　add fileからCreate new fileを選択し
<br>　name your file...に『assets/css/style.scss』と入力
<br>　（『/』でリポジトリの下層フォルダが作成されます）
<br>　テキスト編集エリアに下記を入力
<br>　なお、h2以下はこのサイトのスタイルシートになります
```
---
---
@import 'jekyll-theme-leap-day';

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
<br>　
<br>　3.README.md
<br>　リポジトリ直下に作成します
<br>　このファイルには、HTMLタグの一部を記号で書くことができます
<br>　詳細は各テーマのサンプルを確認してみてください
<br>　ただ、改行はbrタグを書く必要があるので、それほど便利ではないかな
<br>　preタグは置き換えの記号があるのですが、コードを書く想定なので
<br>　そのままでは使いにくいかな。スタイルシートでカスタマイズすれば
<br>　ほぼプレーンテキストで書けると思います。
<br>　ある程度HTMLを意識しないと書けないですし、横の文字数は少ないですし、
<br>　これだったら自分でHTMLを作成した方あ楽で自由と思うかも。
<br>　
<br>　なお、2と3のファイルは、リポジトリ直下なので、ローカルに作成したものを
<br>　upload　filesでまとめてアップロードする方が楽です
<br>　
<br>　README.mdを更新したり、アップロードしたりすると
<br>　設定した場所にHPのindex.htmlを生成しましす
### 4.裏技サイトを探す
　ここからはワークフローの解説
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
### 5.コーディング
　お約束通りcurlでソースを取得
<br>　改行やスペース、bタグ、を取り除いて、liタグの集合を作ります
<br>　その後でliタグ、先頭の番号を削除して、裏技の中身を配列liに格納します
<br>　
<br>　サイト上、裏技は50件で不変な感じではありますが
<br>　一応、配列liの件数（最大値）を求めて、その中からランダムで3件選択します
<br>　深い意味はなく、全体が50件なので3件にしてみたという程度です
<br>　後はJSONフォーマットを作成して、はい、できあがり
### 6.最後の一工夫
<br>　テストをしてみると、裏技がalfred出力に全て書かれてしまうので
<br>　ちょっと工夫してみました。それは、先頭の語句だけを出力するというものです
<br>　下記のパターンにマッチした部分だけをtitleとして表示させています
<br>　『〜、』『〜：』『〜に』『〜を』『〜は』『〜の』
<br>　なお、argには裏技の文言全体をセットしています
<br>　そのため、alfred出力を選択すると、裏技の文言全体でサーチします
<br>　<img width="600" src="https://user-images.githubusercontent.com/40127279/127758004-c7bf4579-4235-4f23-9136-2814f41174b4.png">

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

