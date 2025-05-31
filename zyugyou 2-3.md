# 2-3 ウィジェットの基本レイアウト
画面のレイアウトを作成するにあたり、「Flutter Studio」というWebサイトを活用していきます。これは必要なウィジェットをドラッグ＆ドロップして配置しながら作成し、レイアウトを可視化したものです。作成した後、画面下にある「Source code」を押せば、そのレイアウトのソースコードをコピーすることができます。アクセスするには以下のアドレスにアクセスしてください。　　

[Flutterstudio](https://flutterstudio.app/)

※作成時の注意  
　現在のFlutterのverと、このサイトのソースコードはverが違うため一部Flutterでは使えない記述があります。修正する場合は「Chat gtp」等を活用し修正してください。

[Chatgtp](https://openai.com/ja-JP/chatgpt/overview/)

### Textを配置
「Flutter Studio」の左側の「Basic」のジャンルから「Text」アイコンをドラッグ＆ドロップして配置します。これを細かく設定するには右側に出てきたプロパティを使います。ここでは表示するテキスト、テキストのフォント、フォントのサイズ、幅、テキストのカラー等を設定できる。ソースコードは以下のようになります。
``` c
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}
class MyApp extends StatelessWidget {

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Generated App',
      theme: ThemeData(
        primarySwatch: Colors.blue,
        primaryColor: const Color(0xff2196f3),
        canvasColor: const Color(0xffafafa),
      ),
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatefulWidget {
  MyHomePage({Key? key}) : super(key: key);
  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        appBar: AppBar(
          title: Text('App Name'),
          ),
        body:
          Text(
          "Hello Flutter!",
            style: TextStyle(fontSize:32.0,
            color: const Color(0xff000000),
            fontWeight: FontWeight.w700,
            fontFamily: "Roboto"),
          ),
      );
    }
}
```
実行すると「Flutter Studio」の画面のようにアプリが表示され白い背景に先ほど設定したテキストが表示されます。

### テーマの指定
「Flutter Studio」の背景をクリックするとテーマを設定するためのプロパティが表示される。ここではテーマの基本的な色や標準のテキストの色、アクセントカラーなどを細かく設定できます。ソースコードは以下の通りです。
``` c
class MyApp extends StatelessWidget {

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Generated App',
      theme: ThemeData(
        primarySwatch: Colors.pink,
        primaryColor: const Color(0xffe91e63),
        canvasColor: const Color(0xfffafafa),
      ),
      home: MyHomePage(),
    );
  }
}
```
実行すると「Flutter Studio」の画面のようにアプリケーションバーが色付きで表示されるようになります。

### Centerによる中央揃え
「Flutter Studio」の左側の「Layout」から「Center」をドラッグ＆ドロップします。更にこの中にウィジェットを配置するとすべて中央に配置されるようになります。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
  @override
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
}
```
実行すると「Hello Flutter!」のテキストが中央に配置されるようになります。

### Contanierクラスについて
「Flutter Studio」の左側の「Layout」から「Container」をドラッグ＆ドロップで配置します。これはコンテナの名の通りほかのウィジェットを格納できます。配置した後右側にプロパティが表示され、ここでは「Container」のテーマの色や配置場所、表示サイズ余白幅などが設定できます。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('App Name'),
      ),
      body:
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
    );
  }
}
```
これを実行すると「Hello Flutter！」が中央下に表示されます。

### Alignmentについて
先ほどのContanierの中に記述している「Alignment」クラスでテキストなどの表示位置を細かく設定して配置できます。ソースコードは以下の通りです。
``` c
alignment: const Alignment(0.5, -0.5),
```