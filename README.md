## 　　Lesson30.　GitHubのHPを作ってみる 
#### 開発メモ
### 1.裏技サイトを探す
　LessonのタイトルがAlfredとは無関係になってしまいました。ネタ切れです。
<br>　経験上、alfred化する場合、検索サイトのラッパーとして使うか、まとまっているサイトからパースするかだと思います
<br>　https://creive.me/archives/154/　
<br>　というまとめサイトを見つけたのでパースことにしました
<br>　でも裏技が50個とちょっと少なめです。。
<br>　
<br>　このサイトの裏技は<li>タグでまとまっています。
<br>　<li>のあとに数字とピリオドがあって、1から50までの裏技が紹介されています
<br>　たまにbタグで強調しているので、これを除けばOKそうです
<br>　ここまであたりをつけたらコーディングしましょう
### 2.コーディングする
　お約束通りcurlでソースを取得
<br>　改行やスペース、bタグ、を取り除いて、<li>タグの集合を作ります
<br>　その後で<li>タグ、</li>タグ、先頭の番号を削除
<br>　裏技のなかみ（文字列）を配列liに格納します
<br>　
<br>　サイト上、裏技は50件で変わらなそうな感じではありますが
<br>　一応、配列liの件数（最大値）を求めて、その中からランダムで3件選択します
<br>　深い意味はなく、全体が50件なので3件にしてみたという程度です
<br>
<br>　後はJSONフォーマットを作成して、はい、できあがり
### 3.最後の一工夫
<br>　テストをしてみると、裏技がalfred出力に全て書かれてしまうので、
<br>　ちょっと工夫してみました。それは、先頭の語句だけ出力するというものです
<br>　下記のパターンにマッチした部分だけをtitleとして表示させています
<br>　『〜、』『〜：』『〜に』『〜を』『〜は』『〜の』
<br>　argには裏技の文言全体をセットしていますので
<br>　alfred出力を選択すると、裏技の文言全体でサーチします

#### 背景
　webサーフィン中にいろいろなターミナルに関する裏技を見ていたのですが、
<br>　たまたま生活の裏技に飛び火して、alfred化してみました
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

