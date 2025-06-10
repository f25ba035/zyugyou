# 入力のためのUI
### TextFieldについて
これはテキストを入力するUIウィジェットです。「FlutterStudio」では「Input」の中にアイコンがあります。配置するとプロパティが表示され、フォント名、カラーパレット、大きさ、幅等が設定できます。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
  static var _message = 'ok.';
  static final _controller = TextEditingController();

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
            Padding(
              padding: EdgeInsets.all(10.0),
              child: TextField(
                controller: _controller,
                style: TextStyle(
                  fontSize: 28.0,
                  color: const Color(0xffFF0000),
                  fontWeight: FontWeight.w400,
                  fontFamily: "Roboto"),
              ),
            ),
            ElevatedButton(
                child: Text(
                  "Push me!",
                  style: TextStyle(
                    fontSize: 32.0,
                    color: const Color(0xff000000),
                    fontWeight: FontWeight.w400,
                    fontFamily: "Roboto"),
                ),
                onPressed: buttonPressed),
          ],
        ),
      ),
    );
  }

  void buttonPressed() {
    setState(() {
      _message = 'you said: ' + _controller.text;
    });
  }
}
```
実行するとテキストを入力するフィールドとボタンが表示されます。テキストを入力してボタンをクリックすると上に「you said:○○」とでます。

### onChangedイベントの利用
これはテキストが修正されると発生するイベントです。これを利用するとテキストを編集している間、リアルタイムに入力値を利用した処理を行わせることができます。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
  static var _message = 'ok.';
  static final _controller = TextEditingController();

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
            Padding(
              padding: EdgeInsets.all(10.0),
              child: TextField(
                onChanged: textChanged,
                controller: _controller,
                style: TextStyle(
                  fontSize: 28.0,
                  color: const Color(0xffFF0000),
                  fontWeight: FontWeight.w400,
                  fontFamily: "Roboto"),
              ),
            ),
          ],
        ),
      ),
    );
  }

  void textChanged(String val){
    setState((){
      _message = val.toUpperCase();
    });
  }
}
```
実行するとテキストを入力するごとにリアルタイムで大文字に変換されたテキストが入力フィールドに表示されます。削除するときもリアルタイムに消えていきます。

### Checkboxについて
これはONかOFFか等の二者択一を迫るときに使います。「FlutterStudio」の「Input」の中にあります。配置するとプロパティが表示され、Top,Bottom,Left,RightといったPaddingの値が設定できます。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
  static var _message = 'ok.';
  static var _checked = false;

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
            Padding(
              padding: EdgeInsets.all(10.0),
              child: Row(
                  mainAxisAlignment: MainAxisAlignment.start,
                  mainAxisSize: MainAxisSize.max,
                  crossAxisAlignment: CrossAxisAlignment.end,
                  children: <Widget>[
                    Checkbox(
                      value:_checked,
                      onChanged: checkChanged,
                    ),
                    Text(
                      "Checkbox",
                      style: TextStyle(fontSize:28.0,
                          fontWeight: FontWeight.w400,
                          fontFamily: "Roboto"),
                    )
                  ]
              )
            ),
          ],
        ),
      ),
    );
  }

  void checkChanged(bool? value){
    setState(() {
      _checked = value!;
      _message = value ? 'checked!' : 'not checked...';
    });
  }

}
```
実行するとチェックボックスが1つだけ表示されてチェック部分をクリックするとチェックがついたり消えたりします。同時に上に「checked!」「not checked...」といったテキストが表示されます。

### Switchについて
Checkboxと似たものに「Switch」があります。これもクリックしてONかOFFか等の二者択一を迫るときに使います。FlutterStudioでは「Input」の中にあり、配置するとプロパティが表示されます。ここでは「Switch」とは関連性のないテキストのフォント名、色、大きさ、幅が表示されます。ソースコードは以下の通りです。
``` c
Switch(
  value:_checked,
  onChanged: checkChanged,
),
```
実行すると「Switch」が表示されます。これをクリックするとcheckChangedメソッドが呼び出され現在の状態がテキストに表示されます。

### Radioについて
複数の項目から1つを選ぶものがラジオボタンです。Flutter Studioでは「Input」「Radio」がそれに当たります。配置してみると「Radio」にはプロパティがありません。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
  static var _message = 'ok.';
  static var _selected = 'A';

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

            Padding(
              padding: EdgeInsets.all(10.0),
            ),

            Row(
                mainAxisAlignment: MainAxisAlignment.start,
                mainAxisSize: MainAxisSize.max,
                crossAxisAlignment: CrossAxisAlignment.center,
                children: <Widget>[

                  Radio<String>(
                    value: 'A',
                    groupValue: _selected,
                    onChanged: checkChanged,
                  ),
                  Text(
                    "radio A",
                    style: TextStyle(fontSize:28.0,
                      fontWeight: FontWeight.w400,
                      fontFamily: "Roboto"),
                  )
                ]
            ),

            Row(
                mainAxisAlignment: MainAxisAlignment.start,
                mainAxisSize: MainAxisSize.max,
                crossAxisAlignment: CrossAxisAlignment.center,
                children: <Widget>[

                  Radio<String>(
                    value: 'B',
                    groupValue: _selected,
                    onChanged: checkChanged,
                  ),
                  Text(
                    "radio B",
                    style: TextStyle(fontSize:28.0,
                      fontWeight: FontWeight.w400,
                      fontFamily: "Roboto"),
                  )
                ]
            ),
          ],
        ),
      ),
    );
  }

  void checkChanged(String? value){
    setState(() {
      _selected = value ?? 'nodata';
      _message = 'select: $_selected';
    });
  }
}
```
実行すると二つのラジオボタンが表示されます。ボタンをクリックすると上に「select:○○」と表示されます。