# CSS
Cascading Style Sheetsの略で、HTMLの装飾を行うことができる。  
書き方としては、HTMLのheadタグ内にstyleタグを記述し、その中に書く方法と、  
.cssファイル内に書き、それをHTMLのheadタグ内に書いたlinkタグで参照する方法、  
HTMLのタグにstyle属性を書き、その中に記述する方法の3つがある。  
コメントは `/* */`。  
全角文字が含まれる場合は、ファイルの先頭に `@charset "utf-8"` と書く必要がある。

## セレクター
cssを適用する対象。

| セレクター | 対象 |
| ------- | ------- |
| (タグ名) | 指定したタグ |
| .(クラス名) | 指定したクラス |
| #(ID名) | 指定したID |
| \[(属性名)\] | 指定した属性が付いたタグ |
| * | 全ての要素 |

属性名に関しては、\[(属性名)="~"\] のような形式で値についても指定することができる。  
= で完全一致、^=で前方一致、$=で後方一致、\*=で部分一致で値を指定できる。

### 組み合わせ記法
|表記|意味|
| ------- | ------- |
| .a, .b | .a と .b両方にスタイルを適用する |
| h1.a | h1タグでかつ.aに対してスタイルを適用する |
| main > h1 | mainの直下の階層にあるh1に対してスタイルを適用する |
| main h1 | mainより下の階層にあるh1に対してスタイルを適用する |
| p + p | pタグの直後にあるpタグに対してスタイルを適用する |

\+ は隣接した要素の間に罫線を引くなどの用途で使える。

### 疑似要素
h1::before, h1::afterなどと書くことで指定したセレクタの前後にコンテンツを配置したり、そのコンテンツのスタイルを設定できる。例えば  
`h1::before {
  content: "@";
}
`  
のようにすると、h1タグのコンテンツの後に@が追加される。

### 疑似クラス
|表記|意味|
| ------- | ------- |
| h1:hover | h1タグの要素にホバーした際のスタイル |
| main > :nth-child\(3\) | mainタグの直下の要素の内、3番目の要素のスタイル |
| main > :nth-child\(4n\) | mainタグの直下の要素の内、4n番目の要素のスタイル |
| main > :first-child | mainタグの直下の要素の内、最初の要素のスタイル |
| main > :last-child | mainタグの直下の要素の内、最後の要素のスタイル |
| main > h2:nth-of-type\(3\) | mainタグの直下の要素の内、3番目のh2タグのスタイル |
| li:empty | liタグの内、コンテンツが空の要素のスタイル |
| li:not(:empty) | liタグの内、コンテンツが空ではない要素のスタイル(:not()の中にはセレクタが入れられる) |

### 詳細度
同じタグに複数のスタイルが適用される場合、詳細度の高いスタイルから優先される。  
詳細度は、セレクタにidが含まれる数を比較し、同じならclass/属性/疑似クラスが含まれる数を比較し、更に同じなら要素/疑似要素が含まれる数を比較することで判断される。  
詳細度が同じなら、後に記述されているスタイルが適用される。  
また、HTMLに直接Style属性で書かれたスタイルは詳細度に関わらずcssで書かれたスタイルより優先され、またcolor: red !important; のように値の後ろに!importantがかかれたスタイルは詳細度に関わらず最優先される。  
!importantを複数書いた場合は、より詳細度の高い方が優先される。

## 宣言
セレクターに対して適用する装飾。  
同じ属性を複数書いた場合、より後ろに書いたものが適用される。

## 属性
### color
文字色。

### font-size
文字サイズ。  
ピクセル単位で指定ができる。

### text-align
文字揃え。
centerで中央など。

### font-weight
文字の太さ。
normalで通常、boldで太字。

### text-decoration
文字に下線や取り消し線を引いたり消したりする。

### font-family
フォント。
コンマで区切ることで複数フォントを指定できる。
また、sans-serifでゴシック体、serifで明朝体、cursiveで筆記体、monospaceで等幅フォントから自動でフォントを選んでくれる。

### line-height
ページにテキストが表示されるとき、そのテキストには行ボックスという領域が割り振られる。  
その行ボックスの高さを指定することができる。 

### vertical-align
baselineとすると行ボックス内のベースライン（文字の表示の基準位置）を基準に位置が決定される。  
topとすると行ボックスの上、bottomで下となる。  
middleとすると英小文字の中央と画像の中央が合わせられる。  
長さで設定することもでき、2pxならベースラインから2px上、-2pxならベースラインから2px下となる。

### overflow
ボックスモデルから溢れたテキストの扱いを指定できる。

### border-width
枠線の太さ。

### border-style
枠線のスタイル。

### border-color
枠線の色。

### border
width, style, colorを一括指定できるプロパティ。

### border-radius
枠線の角を丸めるプロパティ。

### padding
ボックスモデルの内側の範囲を設定するプロパティ。

### margin
ボックスモデルの外側の範囲を設定するプロパティ。  
autoを指定すると、余った領域が自動で割り当てられる。
例えばmargin-left: auto; とすると左側のマージンが余った領域分の大きさになるのでコンテンツは右寄せの状態になる。leftとright両方がautoになると左右に均等に割り当てられるので、中央寄せの状態になる。  
marginは隣り合うボックス両方に指定されていると、小さい方は無視して大きい方だけが反映される。これはmarginの相殺と呼ぶ。

### display
blockが指定されていると縦に、inlineが指定されていると横に（詰まると改行される）要素が追加されていく。  
inlineはサイズの変更が効かず、blockとinline-blockはサイズの変更が反映される。

### position
表示位置の起点を指定する。

### box-sizing
box-borderという値にすると、widthとheightにborderやpaddingを含むようにする。

|値|動き|
| ------- | ------- |
| static | 通常通り |
| relative | staticの位置から指定した値分移動させることができる |
| fixed | ウィンドウから指定した値の位置に固定表示（スクロールしても動かない）させる。また、他のコンテンツはこのコンテンツを無視して配置される。 |
| absolute | 親がstaticなら、ウィンドウから指定した値の位置に絶対位置で表示（スクロールすると通常通り流れていく）、それ以外なら親要素から指定した分移動した位置に表示させる。 |

### z-index
要素の重なり順を設定できる。  
positionがstatic以外の時にしか効果が無い。

### opacity
透明度を指定する。  
色のAlphaと違い、要素全体の透明度を指定することができる。また、画像の透明度なども変更することができる。

### box-shadow
要素に影を付けることができる。
box-shadow: 横の位置, 縦の位置, (ぼかし), (影の拡大), 色

### text-shadow
テキストに影を付けることができる。
text-shadow: 横の位置, 縦の位置, (ぼかし), 色

### background-color
背景色。

### background-image
背景に画像を設定することができる。

### background-size
背景画像をどのようにサイジングするかを設定できる。
coverとするとコンテンツの大きさに合わせて画像を拡大縮小するようにする。

### background-position
背景画像の拡大縮小を、画像のどこを基準にするか設定できる。
centerとすると画像の中心を基準にできる。

### background
background-color, image, size, positionを一括指定できる。
positionとsizeに関しては、center/cover のようにまとめて指定しなければならない。

### float
rightと設定すると、指定したコンテンツを右に回り込ませるように配置できる。
clear属性でfloatで指定した値と同じ値を設定すると、clear属性を指定したコンテンツはfloatを設定したコンテンツより下に配置することができる。

### list-style-type
リストの各要素につく丸や数字などの形式を指定できる。

### list-style-position
リストの各要素の記号を、リストの外側に置くか内側に置くか指定できる。

### list-style-image
リストの各要素に丸や数字などの代わりに画像をアイコンとして使用できる。

### list-style
list-style-type, list-style-position, list-style-imageを一括指定するプロパティ。  
list-style-imageの方が優先され、list-style-typeは画像が使えない場合の予備として扱われる。

### cursor
マウスポインタが要素の上にある場合のポインタの形状を設定するプロパティ。

## フレックスボックス
display: flex;を指定しているときのレイアウトルール。  
display: flexを指定しているタグをflex containerとして、その子タグであるflex itemをどう配置するか決める。
### Flex Container
#### flex-direction
flex containerに設定することで、主軸と交差軸の向きを決めることができる。要素は主軸の向きに並べられる。  
rowだと横に、columnだと縦にコンテンツを並べ、row-reverse, column-reverseとすると主軸の向きが逆になる。  

#### justify-content
flex itemをどのように並べるかを決める。  
flex-startなら主軸の始点から、flex-endなら主軸の終点を基準に、centerなら中央ぞろえ、space-betweenなら均等割り付け等。  

#### align-items
交差軸に余裕がある時に、交差軸に対してどのように要素を並べるかを決める。  
flex-start, flex-end, center等。

#### flex-wrap
flex itemsがflex containerをはみ出してしまう場合、デフォルトでは各itemを縮めて表示するが、縮める代わりに折り返したりすることができる。 
flex-wrap: wrap;とすることで折り返させることができ、wrap-reverseとすることで交差軸を反転させることもできる。

#### align-content
flex-wrapが設定されており、コンテンツが折り返されていて交差軸に余裕がある場合のみ効果がある。  
wrapされているflex items全体が交差軸に対してどのように並べられるかを決める。
flex-start, flex-end, center, space-between等。

#### flex-flow
flex-directionとflex-wrapを一括指定できる。

### Flex Item
#### align-self
指定したflex itemを交差軸上にどのように配置するかを設定する。

#### order
指定した値が小さい順に並べられるようになる。初期値は0

#### flex-basis
主軸方向にどのくらいのサイズになるかを指定する。初期値はauto  
widthより優先されるが、max-widthより大きくはならない。

#### flex-grow
主軸方向に余白がある場合、どれだけ伸ばすかを割合で指定する。

#### flex-shrink
主軸方向にはみ出てしまった場合、どれだけ縮めるかを割合で指定する。  
wrapより優先されるっぽい。

#### flex
flex-basis, grow, shrinkを一括指定できる。
flex: 1;のような場合、flex-growに1を指定する動作になっている。  
flex-growのみを設定した場合はflex-basisは0%となり、常にflex-growで指定したサイズ比でコンテンツが表示されることになる。

### ノウハウ
- 親要素の大きさが指定されていないと、flex itemのflex-growによる拡大は効かないため、親要素にheightを指定しておく必要がある。
- FlexBoxではマージンの相殺が発生しない。
- あるタグの中のコンテンツを中央配置したいときは、親タグにdisplay: flex; justify-content: center; align-content: center; を指定すると良い。

## アニメーション
### transition-property
CSSプロパティが変化する際に、変化の途中を補完するプロパティを選択する。  
ここで指定したプロパティは値が変化したときに、以下のtransition-durationプロパティで指定した時間かけて変化するようになる。  
コンマ区切りで複数指定できる。

### transition-duration
CSSプロパティが変化する際に、transition-propertyで指定したプロパティについてはこのプロパティで指定した時間かけて変化するようになる。  
0.3秒ぐらいがちょうどいいとされている。らしい。

### transition-delay
アニメーションするまでに指定した時間待機するようにできる。

### transition-timing-function
アニメーションの移動速度の制御を変更できる。
easeが通常、ease-outが小さな部品、ease-in-outが大きな部品、linearが回転する部品などに使われる。  
デベロッパーツールからStylesのこのプロパティについてるアイコンをクリックすることで、細かく調整が可能。

### transition
上四つを一括指定できる。複数プロパティに対しては、background .5s ease, transform .5s ease のように、それぞれのプロパティに対してすべての値を設定する必要がある。

### transform
図形を変形させることができる。  
translate(~px, ~px)でX, Y座標に指定した値だけ移動させる、rotate(~deg)で指定した値だけ回転させる、scale(x, y)で指定した値だけ拡大縮小させるなど。

### transform-origin
図形の移動中心を変更することができる。  
Hoverした時だけなどではなく、基本的には常に適用したいプロパティなので常に適用される方の宣言に書いておく。  

### @keyframe
時間毎にスタイルの状態を記述することで、アニメーションさせることができる。
`
@keyframe <アニメーション名> {  
  30% { ~ }  
  60% { ~ }  
  100% { ~ }  
}  
`
みたいな感じ。

### animation-name
@keyframe で設定したアニメーション名を指定するとそのアニメーションを実行させることができる。

### animation-duration
アニメーションにかかる時間を設定できる。

### animation-delay
アニメーションが始まるまでの時間を設定できる。

### animation-iteration-count
アニメーションを何回繰り返すかを指定できる。infiniteとすると無限に繰り返すことができる。

### animation
上四つのプロパティを一括指定できる。

### animation-fill-mode
アニメーション終了後の状態を設定できる。

### animation-direction
アニメーションの再生方向を指定できる。alternateとすると再生終了後に逆再生することもできる。

### animation-timing-function
アニメーションの再生速度の制御を指定できる。  
Keyframe内に記述することで、キーフレームごとに設定することもできる。

### pointer-events
クリックイベントに反応するかを設定できる。  
アニメーション後にクリックイベントに反応しないようにしたりできる。

## 単位
### em
1emが1文字分の高さ。
継承先には計算後の値が伝播するため、継承元の文字サイズが基準で計算される。

### (単位無し)
1文字分の高さ。
継承先には計算前の値が伝播するため、継承先の文字サイズが基準で計算される。

### 単位が違う値同士の計算
calc()を使用すると、単位が違う値同士を計算することができる。
calc((100% - 30px) / 4) のような感じ。  
注意点として、各演算子の前後には半角スペースが必要。
## 色指定
### 色の名前
MDNで調べれば色々定義されてるのが分かるのでそっちを見よう

### RGBA
rgba(255, 0, 0, 1.0)といった形式で設定できる。  
右から順にRed, Green, Blue, Alphaで、Alphaは不透明度を表している。  
Alphaが1.0の場合は rgb(255, 0, 0)といった感じで書くことができる。  
`#ff0000ff`と書くこともできる。
また、Red, Green, Blue, Alpha各要素の前と後が同じ値の場合は省略して `#f00f` のように書くこともでき、AlphaがFFの場合は省略できるので `#f00` と書ける。

### HSLA
Hue（色相 0~360）, Saturation（彩度 0%~100%）, Lightness（明度 0%~100%）, Alphaで指定する。  
LightnessやHueを少しずつずらしていくことでグラデーションが作れるので、今風のデザインを作るのに簡単そう。

## スタイルの継承
タグにスタイルを宣言すると、その子要素であるタグにもスタイルが継承されていく仕組み。  
すべてのタグが継承されるわけではない。そのスタイルが継承されるかどうかはMDNのサイトを参照すると良い。  
また、その属性にinheritという値を指定すると、本来継承されないスタイルも親要素からの値を継承することができる。