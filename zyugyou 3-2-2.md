### DropdownButtonについて
ラジオボタンのように複数の項目から1つを選ぶようなUIとして「DropdownButton」があります。クリックするとメニューが現れ、そこから項目を選んで表示されるというものです。Flutter　studioでは「Material2」のなかに「DropdownButton」というアイコンがあります。これをドラッグ&ドロップすると、テキストの表示に関するプロパティが表示されます。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
  static var _message = 'ok.';
  static var _selected = 'One';

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

            DropdownButton<String>(
              onChanged: popupSelected,
              value: _selected,
              style: TextStyle(color:Colors.black,
                fontSize:28.0,
                fontWeight: FontWeight.w400,
                fontFamily: 'Roboto'),

              items: <DropdownMenuItem<String>>[
                const DropdownMenuItem<String>(value: 'One',
                  child: const Text('One')),
                const DropdownMenuItem<String>(value: 'Two',
                  child: const Text('Two')),
                const DropdownMenuItem<String>(value: 'Three',
                  child: const Text('Three')),
              ],
            ),
          ],
        ),
      ),
    );
  }

  void popupSelected(String? value){
    setState(() {
      _selected = value ?? 'not selected...';
      _message = 'select: $_selected';
    });
  }
}
```
実行すると「DropdownButton」のある画面が表示されます。これをクリックするとそこに三つの項目が出てきます。どれか一つを選ぶと項目名が「select:○○」というように表示されます。

### PopupMenuButton
「DropdownButton」と似たようなものに「PopupMenuButton」があります。これはその名の通りポップアップメニューを呼び出すための専用ボタンです。ソースコードは以下の通りです。
``` c
Align(alignment: Alignment.centerRight,
  child: PopupMenuButton(
    onSelected: (String value)=> popupSelected(value),
    itemBuilder: (BuildContext context) =>
    <PopupMenuEntry<String>>[
      const PopupMenuItem( child: const Text("One"), value: "One",),
      const PopupMenuItem( child: const Text("Two"), value: "Two",),
      const PopupMenuItem( child: const Text("Three"), value: "Three",),
    ],
  ),
),
```
実行すると画面に「…」の縦版が表示されます。これをクリックするとメニューがポップアップして現れます。ここからメニュー項目を選ぶと、選んだメニューの値がメッセージとして画面に表示されます。

### Slider
数値をアナログに入力するときによく使われるのが「スライダー」です。線上の点をドラッグして動かし、それを左右（または上下）に動かすことで値を設定するウィジェットです。Flutter Studioの「Input」の中に「Slider」というアイコンで表示されています。これをドラッグ＆ドロップして配置すると上下左右の余白を設定するプロパティが表示されます。本来はもっと多くのことを設定するのですが、独自のプロパティは表示できないようです。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
  static var _message = 'ok.';
  static var _value = 0.0;

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

            Slider(
              onChanged: sliderChanged,
              min: 0.0,
              max: 100.0,
              divisions: 20,
              value:_value,
            ),
          ],
        ),
      ),
    );
  }

  void sliderChanged(double value){
    setState(() {
      _value = value.floorToDouble();
      _message = 'set value: $_value';
    });
  }
}
```
実行すると横長のスライダーが表示されます。これをドラッグして動かすと5刻みで0~100の中で値が表示されます。