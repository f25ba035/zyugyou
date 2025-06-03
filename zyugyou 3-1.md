# ボタンウィジェット
### TextButtonについて
最も基本的なボタンで、特にUIの外観などを持たない平面のボタンです。「Flutter Studio」では「Material」の中にある「FlatButton」というのがこれに当たります。配置するとプロパティが表示されここではボタンのサイズや幅ではなく、ボタンのテキストのサイズ、幅が設定できます。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
  static var _message = 'ok.';
  static var _janken = <String>['グー', 'チョキ', 'パー'];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('App Name'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.start,
          mainAxisSize: MainAxisSize.max,
          crossAxisAlignment: CrossAxisAlignment.stretch,
          children: <Widget>[
            Padding(
              padding: EdgeInsets.all(20.0),
              child: Text(
                _message,
                style: TextStyle(
                  fontSize: 32.0,
                  fontWeight: FontWeight.w400,
                  fontFamily: "Roboto"),
              ),
            ),
            TextButton(
              onPressed: buttonPressed,
              child: Padding(
                padding: EdgeInsets.all(10.0),
                child: Text(
                  "Push me!",
                  style: TextStyle(
                    fontSize: 32.0,
                    color: const Color(0xff000000),
                    fontWeight: FontWeight.w400,
                    fontFamily: "Roboto"),
                )
              )
            )
          ]
        ),
      ),
    );
  }

  void buttonPressed() {
    setState(() {
      _message = (_janken..shuffle()).first;
    });
  }
}
```
これを実行すると「Push me!」というボタンが表示され、このボタンを押すと「グー」「チョキ」「パー」からランダムに表示されます。

### アイコンを表示する
「TextButton」にはTextが内蔵されているためTextを表示できています。ということは代わりに別のものを組み込めば、ほかのものを表示できるというわけです。ここではアイコンを組み込みます。ソースコードは以下の通りです。
``` c
TextButton(
  onPressed:buttonPressed,
  child: Padding(
    padding: EdgeInsets.all(10.0),
    child:Icon (
      Icons.android,
      size: 50.0,
    )
  )
)
```
これを実行すると先ほどの「Push me!」というテキストがandroidのアイコンに代わっています。動作は特に変わっていません。

### buttonPressedメソッドについて
クリックしたときの処理について「onPressed:buttonPressed」とメソッドを設定しています。ソースコードは以下の通りです。
``` c
void buttonPressed(){
  setState((){
    _message = (_janken..shuffle()).first;
  });
}
```

### Paddingについて
実は先ほどから「TextButton」の中に新しいクラスが使われていました。それが「Padding」です。これはTextの周りの余白を表示するためのコンテナです。このボタンと同じような働きをするものに「ElevatedButton」というものがあります。これは少し立体的に表示されます。「FlutterStudio」では「Material」内に「RaisedButton」がそれに当たります。プロパティには、フォント、カラーパレット、大きさ、幅を設定できます。ソースコードは以下の通りです。
``` c
ElevatedButton(
  onPressed:buttonPressed,
  child: Padding(
    padding: EdgeInsets.all(10.0),
    child:Icon (
      Icons.android,
      size: 50.0,
    )
  )
)
```
実行するとタイトルバー部分と同じ色をしたボタンが表示されます。周囲には影が付き立体的に見えるようになっています。

### IconButtonについて
このボタンは「FlutterStudio」の「Material2」に用意されています。配置するとプロパティにカラーパレットとアイコンの種類、大きさを設定できるものが表示されます。ソースコードは以下の通りです。
``` c
IconButton(
  icon: const Icon(Icons.insert_emoticon),
  iconSize: 100.0,
  color: Colors.red,
  onPressed:buttonPressed,
)
```
これを実行すると赤い笑顔のアイコンが表示され、クリックすると先ほどと同様にじゃんけんの手がランダムに生成されます。

### FloatingActionButtonについて
これはアイコンを表示するボタンで既に使用しています。「Scaffold」の「floatingActionButton」にインスタンスを設定することで画面の右下にボタンが追加されています。これは先ほどの「IconButton」のように使うことができます。「FloatingActionButton」を組み込んでみましょう。ソースコードは以下の通りです。
``` c
FloatingActionButton(
  child: Icon(Icons.android),
  onPressed: buttonPressed
),
```
これを実行するとテキストの下に「FloatingActionButton」のアイコンが表示されます。動作は問題ないですがこのボタンはあくまでも右下に表示するボタンなので、同じデザインのボタンがあると混乱しやすいのであまり推奨はできません。ですがボタンとしても使えることは知識として大事です。

### RawMaterialButtonについて
このボタンはテーマの設定などに応じて自動的に表示の色などが調整される機能の影響を受けないようにするボタンです。なので自身で使用するボタンをすべて設定して使用します。ソースコードは以下の通りです。
``` c
RawMaterialButton(
  fillColor: Colors.white,
  elevation: 10.0,
  padding: EdgeInsets.all(10.0),
  child: Text(
      "Push me!",
      style: TextStyle(fontSize:32.0,
      color: const Color(0xff000000),
      fontWeight: FontWeight.w400,
      fontFamily: "Roboto"),
    ),
  onPressed: buttonPressed
),
```
実行すると横長の白いボタンが表示されます。やや立体的に見えると思います。これはこのボタンの様々な値を細かく設定することで、より細かく設定できます。