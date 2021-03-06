# HTML
HyperText Markup Languageの意味  
HyperText は画像やリンクを埋め込めるテキストという意味  
Markup は視覚表現や文章構造を表現するための言語
困ったらここを見る https://developer.mozilla.org/ja/
## ドキュメントタイプ宣言
`<!DOCTYPE ~>` のような形式でHTML文書ファイルの銭湯に記述することで、HTMLのバージョンを宣言する。  
HTML4.01 以前では必須だったらしいが、HTML5では`<!DOCTYPE html>`と記述されていればHTML5であることを示すものとされているとのこと。  
ブラウザにもよるが、多くの場合は`<!DOCTYPE html>`と書かれていればHTML5 モードで、`<!DOCTYPE ~>`が記述されていなければ過去互換モードで表示されるらしい。  
よく分からんけど、HTML4.01 Strictの場合は  
`<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org/TR/html4/strict.dtd">`  
と記述されるそうな。  
とりあえずIE8以前のブラウザ対応が必要な場合を除いてHTML5を使えばよろしいらしい。  
正確にはHTML5ではなくHTML Living standardなんだけど、この部分の書き方は変わらないのでmo mantai。

## タグ
属性は小文字で書くことが多いが、大文字でも問題は無い。  
全角で書いてはいけない。 
### `<html>`
HTML文書であることを宣言  
HTML文書は`<html>`, `<head>`, `<body>`の3種類のタグで構造を定義し、  
全ての要素は`<html>`の中に配置する必要があり、  
`<head>`と`<body>`はそれぞれ`<html>`内に一つだけらしい。

|属性名|属性の値|値の例|備考|
| ------- | ------- | ------- | ------- |
| lang | 言語コード | lang="ja"（日本語） | htmlタグ内の言語 自動翻訳などで言語情報を識別する際に見られていたりするらしい |


### `<head>`
文書のヘッダーを定義  

### `<meta>`
メタ情報を定義  

|属性名|属性の値|値の例|備考|
| ------- | ------- | ------- | ------- |
| charset | 文字コード | charset="utf-8" | ページ内の文字コード |
| name | メタデータの名前 | name="description" | content属性と関連づけられる |
| content | メタデータの値 | content="説明" | タグのname属性に対応する値 |

### `<link>`
外部リソースへのリンク要素  

|属性名|属性の値|値の例|備考|
| ------- | ------- | ------- | ------- |
| rel | リンク先のファイル/ページとの関係 | rel="stylesheet" |  |
| href | 参照先 | href="css/stylesheet.css" |  |


### `<body>`
文書の本文を定義

### `<h1>, <h2>`
見出し

### `<p>`
パラグラフ
-> 1つのトピックについて書かれた文のまとまり（1つの文の場合も複数の文の場合もある）

### `<img>`
画像を表示する

|属性名|属性の値|値の例|備考|
| ------- | ------- | ------- | ------- |
| src | 画像のパス | src="image.png" | どのパスの画像を表示するか設定する |
| width | 幅 | width="100" | pixel単位 |
| height | 高さ | height="100" | pixel単位 |
| alt | 説明 | | 音声読み上げなどで読み上げられる |

### `<strong>`
強調したいテキストを表す。  
あくまで文章構造として重要性の高い内容を表すタグの為、装飾のために使うべきものではない。

### `<blockquote>`
引用、転載文であることを表す。
こちらも装飾のために使うべきではない。

|属性名|属性の値|値の例|備考|
| ------- | ------- | ------- | ------- |
| cite | 引用元 | cite="https://~" | Webページの場合はURL, 書籍の場合はISBNコードを指定する。 |

### `<hr>`
テーマの区切りを表す。  
ページ上では水平線として表示されるが、これも文章構造としてのタグなので、水平線を引きたい場合はこのタグではない方法でやるべき。

### `<br>`
文章の改行を表す。  
改行以外のレイアウト調整などの為には使うべきではない。

### `<pre>`
整形済みテキストを表す。  
このタグ内の文章は全てインデントなどもそのままの形で表示される。  
AAとか表示するのに使えそう。

### `<code>`
コードを表す。  
markdownでいう<code>``</code>と同じ。

### `<ul>`
箇条書きリストを表す。  
unorderd listの略で、順番に意味がないリストに使用する。  
個々のアイテムを `<li>`タグで囲んで使用する。

### `<ol>`
順序付きリストを表す。  
orderd listの略で、順番に意味があるリストに使用する。
個々のアイテムを `<li>`タグで囲んで使用する。

### `<dl>`
説明リストを表す。  
description listの略。  
個々のアイテムを、項目を`<dt>`タグ（description term）で、説明を`<dd>`タグ（description detail）で囲んで使用する。

### `<table>`
表を表す。
`<caption>`タグでキャプションを付けることができる。
`<thead>`タグtable headerが表のヘッダーを、`<tbody>`タグtable bodyが表の本体を表す。  
また、各行を`<tr>`タグtable rowで囲み、  
ヘッダーの各セルを`<th>`タグtable header cellで、  
本体の各セルを`<td>`タグtable data cellで囲む。

### `<a>`
リンクを表す。anchor

|属性名|属性の値|値の例|備考|
| ------- | ------- | ------- | ------- |
| href | リンク先URL | `href="https://~"` | href="#id"のようにすると、指定したidのタグがある位置へのページ内リンクとして機能する。  href="#"のようにすると、ページの先頭へのリンクとして機能する。 |
| target | リンク先の文書の開き方 | `target="_blank"` | 別タグで開かせたりできる |

### `<time>`
時間を表すタグ。

### `<div>`
スタイルを設定するためのタグで、ブロック単位で設定を行う際に使用する。

### `<span>`
スタイルを設定するためのタグで、文字単位で設定を行う際に使用する。

### `<input>`
入力フォームを設定するタグ。
チェックボックスはchecked属性を設定することで最初からチェック状態にできる。  
ラジオボタンは同じname属性を持つinputフォーム間では同時に一つしか選択できないチェックボタンとして機能する。

|属性名|属性の値|値の例|備考|
| ------- | ------- | ------- | ------- |
| type | 入力フォームの種類| type="text" | textは文字列, passwordはパスワード, checkboxはチェックボックス, radioはラジオボタン, colorはカラーピッカー, dateは日付入力, numberは数値入力, rangeはスライダー |
| value | 初期値 | value="hello" |  |
| placeholder | プレースホルダー | placeholder="test" |  |

### `<textarea>`
複数行入力できるフォームタグ。
inputと違い、タグと閉じタグの間に初期値を入力する。

|属性名|属性の値|値の例|備考|
| ------- | ------- | ------- | ------- |
| placeholder | プレースホルダー | placeholder="test" | HTML5から追加された |

### `<label>`
入力フォームにラベルを設定するタグ。  
入力フォームのidをこのタグのfor属性に指定するか、このタグの中に入力フォームのタグを入れてしまうことでこのタグを入力フォームを対応させることができる。

### `<select>`
セレクトボックスを設定するタグ。  
`<option>`タグでセレクトボックス内の要素を定義する。

|属性名|属性の値|値の例|備考|
| ------- | ------- | ------- | ------- |
| size | 一度に表示される要素の数 | size="2" |  |
| multiple | 複数選択可能にする | multiple | Ctrlキーを押しながらクリックすることで複数選択できるようにする |

### `<fieldset>`
フォームをグループ化するタグ。
`<legend>`タグでキャプションを付けることができる。

### `<button>`
ボタンを設定するタグ。

|属性名|属性の値|値の例|備考|
| ------- | ------- | ------- | ------- |
| disabled | ボタンを向こうにする | disabled |  |

### `<form>`
入力した値をプログラムに送信するために使用するタグ。  
form内の入力フォームにname属性を付けることで、プログラムでどの入力フォームから送信された値なのかを識別することができる。  
form内のボタンをクリックすることで、form内の入力フォームに入力された値が送信される。

|属性名|属性の値|値の例|備考|
| ------- | ------- | ------- | ------- |
| action | 送信したデータを処理するプログラムのURL | action="sample.php" |  |
| method | HTTPメソッド | method="post" | post, get, dialogが指定可能 |


### 区切りを表すタグ
#### `<header>`
文書のヘッダーを表すタグ。

#### `<footer>`
文書のフッターを表すタグ。

#### `<nav>`
ページ内のナビゲーション（メニューのリンクなど）に使われるタグ。

#### `<aside>`
ページ内容と関連の薄いコンテンツ（サイドバーの広告など）に使われるタグ。

#### `<article>`
ページ内の独立したコンテンツを表すタグ。  

#### `<main>`
ページ内の主要なコンテンツで、ページ内に1つしか使えないタグ。

#### `<section>`
以上のどれにも当てはまらない区切りに使用するタグ。

### `<!-- -->`
コメント  
この中に書いた文章はコメントアウトされる

## 実体参照
|表記|表示される文字|
| ------- | ------- |
| `&lt;` | < |
| `&gt;` | > |


## 疑似要素
タグ内にdata- から始まる任意の属性と値を設定することができる。  
cssで attr\(data-~\)のように設定した属性を指定することでこの値を参照することができる。  
これを疑似要素という。
