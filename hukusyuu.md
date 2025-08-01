# 期末に向けた復習

## テストについて
- マークダウン
- Git
- Dart入門
- Chapter1～4(主に2,3)
- 問題数は20問
- 問題の形式はプログラムを読んでどういった結果になるかという感じ

## Markdown
文章を簡単に構造的に表現できる。覚えておくと非常に便利。AIでの作成にも相性が良い。  
テストに向けてclassroomにあるチートシートを必ず復習。

・段落...空白行を挟む

・改行...改行の前に空白を二つ入れる

・引用...文の先頭に「>」を入れる。多重引用の場合は「>>」を入れる。

・コード…「`」(バッククォート)三つで囲みます。(上にcをつけると色がつくときあり)
```
    hakaka
```

・インラインコード…単語をバッククォートで囲む(`さとし`)

・水平線…アンダースコア、アスタリスク、ハイフンなどを三つ以上連続して記述
いえ
***
なら
___
こんな風に段落も作れるぞ
---

・リスト  

・箇条書き…ハイフン、プラス、アスタリスクのいずれかを先頭に記述。ネストはタブで表現  
- リスト1
  - リスト1＿1
  - リスト1＿2
- リスト2

・番号…番号を先頭に記述します。番号は自動で採番されるのですべて1.で大丈夫です。  
1. リスト1
 1. リスト1－1
 1. リスト1－2
1. リスト2

・リンク…[表示文字](URL)でリンクになります。
　　　[Google](https://www.google.co.jp/)

・強調

・斜体…アスタリスク、もしくはアンダースコア1個で文字列を囲みます。  
これは *イタリック* です  
これは _イタリック_ です  
・太字…アスタリスク、もしくはアンダースコア2個で文字列を囲みます。  
これは **ボールド** です  
これは __ボールド__ です  
・斜体+太字…アスタリスクもしくはアンダースコア3個で文字列を囲みます。  
これは ***イタリック&ボールド*** です  
これは ___イタリック&ボールド___ です

・打消し

・取り消し線…チルダ~2個で文字列を囲みます  
　これは ~~取り消し~~ です。

・Images画像…リンク表記の先頭の!で画像と認識されます。  
　　![alt](画像URL)

・Table表...-と|を使ってtableを作成します。

| TH1 | TH2 |
----|----
| TD1 | TD3 |
| TD2 | TD4 |
　
| 左揃え | 中央揃え | 右揃え |
|:---|:---:|---:|
|1 |2 |3 |
|4 |5 |6 |

## Git
コードなどの変更履歴を記録・管理するためのバージョン管理ツール。**どのファイルが、どのタイミングで、どんな変更が加えられたか管理できる。**

- リポジトリ…プロジェクトの履歴を保存する場所。  
- コミット…変更履歴を保存する操作。または履歴自体。  
    - コミットメッセージ…変更時に変更をわかりやすくするため書き込めるメッセージ。

**GitHub**とは  
Gitのリポジトリをインターネット上で共有・保存することができるサービス。類似サービスにGitLab。自分のPC内にあるリポジトリがローカルリポジトリ、GitHub等にあるリポジトリをリモートリポジトリという。

- ローカルリポジトリの操作
1. ファイル変更
1. コミット対象を選ぶ（ステージング）
1. コミット（コミットメッセージと共に、ステージされた変更を履歴に登録）

- ローカルリポジトリとリモートリポジトリの連携
4. リモートに共有（プッシュ）→GitHub  
プッシュとは反対にリモートリポジトリの履歴をローカルリポジトリに反映するための操作をプルという。

## Flutter
Googleが開発した **オープンソースのフレームワーク（枠組み、キット）** の一つ。一つのソースで複数のプラットフォームに対応できる。Andoroidとの相性が良い

## Dart
Flutterによる開発で使用されるプログラミング言語。Flutter同様、Googleが中心になって開発された言語。元々はJavaが使いにくいという人たちの不満から作られた。

### Dart入門
- 順次処理…記載された命令を上から順に処理すること。
- 繰り返し処理…同じ処理を繰り返し実行する処理のこと　例：while,for
- 分岐処理…条件によって実行する処理が変わる処理のこと 例:if, switch

プログラムが扱うデータのことを**値**といいます。
値の種類のことを**型**といいます。
- intなど（整数）
- doubleなど(実数)
- String（文字列）
- bool(真偽値)

| 演算 | 意味 |
----|----
| A+B | 足し算 |
| A-B | 引き算 |
| A*B | 掛け算 |
| A/B | 割り算 |
| A%B | AをBで割った余り |
| A~/B | AをBで割った整数値 |

| テキスト演算 | 意味 |
----|----
| テキスト + テキスト | 足し算 |
| テキスト * 整数 | 掛け算 |

| 比較演算子 | 結果 |
----|----
| A == B | AとBが等しいときtrue、それ以外はfalse |
| A != B | AとBが等しくないときtrue、それ以外はfalse |
| A < B | AがBより小さいときtrue、それ以外はfalse |
| A <= B | AがB以下のときtrue、それ以外はfalse |
| A > B | AがBより大きいときtrue、それ以外はfalse |
| A >= B | AがB以上のときtrue、それ以外はfalse |

printで観察してみよう。
``` c
void main() {
print(1000 > 999999);
}
```

| 演算 | 意味 |
----|----
| A += B | A = A + B |
| A -= B | A = A - B |
| A *= B | A = A * B |
| A /= B | A = A / B |

| 演算 | 意味 |
----|----
| A++、++A | A = A + 1 |
| A--、--A | A = A - 1 |

#### Tips. ++を付ける位置  
A++と++Aは、どちらを使用しても、Aに代入される値は一緒です。ただ、実は、微妙な違いがあります。それは「式の値」です.A++はAの値に1を足していきますが、++Aは1にAを足していきます。

## Chapter1
- flutter doctor  
Flutter開発に必要なツール類をチェックし、開発の準備が整っているか判定してくれるコマンド
- flutter create プロジェクト名  
Flutterプロジェクトを作成するコマンド

## Chapter2
Flutterによるプログラムの基礎を学び、基本のコードをかけるようになる。  
**教科書p50を必ず確認**。  

**通常の関数の実装**
``` c
void main() {
  int answer = calc(1, 2, 3);
  print(answer);
}

int calc(int a, int b, int c) {
  return a + b + c;
}
```
↑引数が多くなればなるほど、どの引数がどの役割かわかりづらくなる
``` c
void main() {
  int answer = calc(1, 2);
  print(answer);
}
```
↑呼び出し時に引数が足りなければエラーとなる。

**名前付き引数による実装（P.379～）**
``` c
void main() {
  int answer = calc(1, b:2);
  print(answer);
}

int calc(int a, {int b = 5, int c = 10}) {
  return a + b + c;
}
```
「calc(1, b:2);」で関数を呼び出すときに引数を指定してあげている。「{int b = 5, int c = 10}」で呼び出し時に指定していないものはデフォルトの値になる。  
「基本的には」1つの引数には1つの値を渡し、1つの関数からは1つの値が返ってくる。**それぞれの処理で、どんな値を渡すのか、どんな値が返ってくるのかを意識することが重要**

**P51**
``` c
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      home: Text(
        'Hello, Flutter World!!',
        style: TextStyle(fontSize:32.0),
      ),
    );
  }
}
```

アプリケーションの中に部品を入れていく、マトリョシカのような構造で開発していく。ここで部品のことを**ウィジェット**、構造のことを**ウィジェットツリー**という。  
ウィジェットは次の二つに分けられる
- StatelessWidget　ステート（状態）を持たない
- StatefulWidget　ステート（状態）を持つ

いずれかを**継承**してオリジナルのウィジェットを作っていく（P391参考）。すでに面倒くさい部分は実装されているので、必要なメソッド（関数）を上書きするだけでよい。

構造の始まりとなるウィジェットはmain関数によって呼び出される
``` c
void main() {
  runApp(ウィジェット);
}
```
**※Dartを実行したとき、main関数が最初に呼ばれる。**

オリジナルのウィジェットを作るときは以下のように作成する。
``` c
class クラス名 extends StatelessWidget {

  @override
  Widget build(BuildContext context) {
    return ウィジェット;
  }
}
```
オリジナルのウィジェットを作るときは**extends、@override**を活用  
buildメソッド..ウィジェットを生成するときに呼び出されるメソッド

実は、Flutterではすでに以下のように作成された便利なウィジェットが多数存在する。  
- **class クラス名 extends StatelessWidget {略}**  
- **class クラス名 extends StatefullWidget {略}**

ちなみにMaterialAppはこんなクラスで  
- **class MaterialApp extends StatefullWidget {略}**

以下のような値などをコンストラクタで受け取ることができるようになっています。  
- title ・・・ 文字列
- home ・・・ ウィジェット

**P.55を必ず読んでおくこと。コンストラクタはP.386**

同様に文字を表示するための「Text」というウィジェットもある  
- class Text extends StatelessWidget {略}  
　　　　　　　　↓
- Text( ‘表示する文字', style: TextStyle(略),)

**P51のサンプルコードを改めて確認**

#### Flutter Studio
ブラウザ上でFlutterのUIを作れる便利なサイト　→　[FlutterStudio](https://flutterstudio.app/)

**TextStyle**..テキストのスタイルを指定するために用意されているクラス。様々な調整が可能。以下のコードはP78より
``` c
Text (
  "Hello Flutter!",
  style: TextStyle(
    fontSize:32.0,
    color: const Color(0xff000000),
    fontWeight: FontWeight.w700,
    fontFamily: "Roboto"
  ),
),
```
- FontSize...文字のサイズ
- fontFamily...フォント
- fontWeight...文字の太さ。w100～w900、あるいはboldという定数で指定。

**Color**...色を指定するクラス（Textstyle以外でもよく使う）  
Color(0x  00  00  00  00)  
　　　　| A | R | G | B |　　←16進数で各値が設定されている  
Color(0xffff0304)　←→　Color.fromARGB(255, 255, 3, 4)  
　　　　　　同じ色で設定される

Center...childで指定したWidgetを上下中央揃えで表示する。画面サイズを変えても常に中央揃えになる。
``` c
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: Text('App Name'),
    ),
    body:
    Center(
      child:
      Text(
        "Hello Flutter!",
        style: TextStyle(fontSize:32.0,
          color: const Color(0xff000000),
          fontWeight: FontWeight.w700,
          fontFamily: "Roboto"),
      ),
    ),
  );
}
```

**Container**...Centerよりも細かく位置の調整をする場合に使用。  
- EdgeInsets...周囲の余白幅を設定するためのクラス
  - 個別に設定　EdgeInsets.fromLTRB(左,上,右,下)...それぞれの余白幅を数値で指定
  - シンメトリック　const EdgeInsets.symmetric（横,縦)...横（左右）と縦（上下）にそれぞれ同じ値を設定します。　　
- Alignment...配置場所を設定するためのクラス

P87～89をよく読んでおく。
``` c
Container(
  child:
  Text(
    "Hello Flutter!",
    style: TextStyle(fontSize:32.0,
      color: const Color(0xff000000),
      fontWeight: FontWeight.w700,
      fontFamily: "Roboto"),
  ),
  padding: const EdgeInsets.all(10.0),
  alignment: Alignment.bottomCenter,
),
```

**Column**...複数のウィジェット縦に並べて表示する。P90～P95をよく確認。
``` c
Column(
  mainAxisAlignment: MainAxisAlignment.start,
  mainAxisSize: MainAxisSize.max,
  crossAxisAlignment: CrossAxisAlignment.center,
  children: <Widget>[
    Text(略),
    Text(略),
    Text(略)
  ]
),
```
- **mainAxisAlignment: MainAxisAlignment.start,**　上下の位置（column）
- **crossAxisAlignment: CrossAxisAlignment.center**　左右の位置(Row)

## Chapter3
**TextButton**...文字が表示されているボタン　※ほかのボタンの構造も同様  
P99コード↓
``` c
TextButton(
  onPressed: buttonPressed,
  child: Padding(
    padding: EdgeInsets.all(10.0),
    child: Text(
      "Push me!",
      style: TextStyle(略),
    )
  )
)
```
- onpressed..ボタンが押されたときに実行されるメソッド
- child..ボタン内に表示するウィジェット

**P98～107をよく読んでおく**  

カスケード記法..（厳密には）式の値を元のオブジェクトにしたまま操作を行う記法。同一のオブジェクトに対して複数の操作を行うことができる。  
↪janken..suffle

#### 教科書で紹介されている入力のためのUI
- **TextField**..自由に文字を入力させたいときに使う、文字を入力することのできるウィジェット。あくまで、文字を入力できるだけなので**入力された値を保持しているわけではない**。  
例）：アンケート自由入力欄
  - **onChanged**..値が変更されるたびに呼ばれるイベント。適切に活用すれば非常に便利なものになる。　　※TextField以外にも
- **Checkbox,Switch**..要素に該当するかどうかチェックさせたいときに使う、ONとOFFの切り替えなどができるウィジェット。  
例）：複数選択可能な質問、利用規約同意など
- **Radio,Dropdown,(PopupMenuButton)**..複数の要素から一つだけ選ばせたいとき  
例）：満足度選択など
- **Slider**..特定の値の範囲で数値を入力させたいとき  
例）：年齢入力など

NULLとは、値が入っていない状態のこと（0とは違う）
　　　　　　　　　　　　　　　
- 利用者:ファミチキください
  - セブン:そもそも取り扱っていない（存在していない、値が入っていない）
  - ファミマ:在庫がない（いまはない、0）

　　　　　　　　　　　　　　　
- showDialog..一時的にdialogを表示するメソッド（P133にコード）
- AlertDialog..アラート表示をすることができるdialog

アロー関数..無名関数を簡単に書くことのできる記法(P382)  
アラートにはボタンを追加したり、ユーザーに入力させたりすることもできる(P134～P138を確認)

## Chapter4
- **AppBar**..タイトル表以外にも複数のウィジェットを内包させることができる　　
bottomは、PreferredSizeクラス（高さを決めるクラス）を受け取るので注意
- **BottomNavigation**..画面下部に表示させるバー。主にアイコンや文字の表示（P145にコード）  
  - ポイント..onTapで設定する関数は全itemで共通。itemごとに動きを変える場合は引数のint型の値を使用。  
  ※引数にはクリックされた要素のindex(0～)が渡される。
- **ListView**..多数の項目を並べるためのウィジェット。各項目はListTileという専用のウィジェットを使うと便利で、選択されているかどうかやクリックや長押しのイベントも設定可能  
※P148～P153を確認

**「情報の整理」**  
アプリケーションを作っていくと「情報の整理」に悩むことになります。  
**たくさんある情報をどうやってアプリのデザインに落とし込むのか**

解決策
- 1画面の領域を大きくする　→　スクロールを可能にすることで画面の領域を広げる(P154)
- 画面を増やす　→　画面表示を切り替えることで画面を増やしている。

**Navigator**..LIFO(スタック)式で、画面遷移を実現するための機能（クラス）。一番上にある画面が表示される。(p158～参照)

**MaterialPageRoute**..Routeクラスの孫クラス
- Pushの時の動き
  1. 画面
  1. MaterialPageRouteに変換
  1. Navigatorに保存
- Popの時の動き
  1. Navigatorから取得
  1. MaterialPageRouteを取得
  1. 画面

※表示間のデータの受け渡しについてはP162~165をよく読んでおくこと  

**routes**..アドレスを事前に決めておくことで、毎回Routeクラスを書かないための設定値。処理がよりシンプルになる。
``` c
initialRoute: '/',
routes: {
  '/': (context) => FirstScreen(),
  '/second': (context) => SecondScreen('Second'),
  '/third': (context) => ThirdScreen('Third'),
},
```
``` c
Navigator.pushNamed(context, '/Second');
```

- **TabBar**..Tabの一覧を表示するウィジェット  
  - **Tab**..一つ一つのタブ
- **TabBarView**..Tabの一覧を表示するウィジェット
- **TabController**..TabBarとTabBarViewを連携させるための仕組み  
タブの表示を下にするにはどうしたらいいでしょうか?(~P178を確認)
- **Drawer**.. ≡アイコンのように画面外からリストが表示されるようなUI(~P180を確認)









