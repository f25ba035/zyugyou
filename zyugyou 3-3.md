# アラートとダイアログ
### showDialog関数について
アラートやダイアログなどのいわば通知のようなものを画面に表示させるUIです。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
  static var _message = 'ok.';

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

            Padding(
              padding: EdgeInsets.all(10.0),
              child: ElevatedButton(
                onPressed:buttonPressed,
              child: Text(
                  "tap me!",
                  style: TextStyle(fontSize:32.0,
                    color: const Color(0xff000000),
                    fontWeight: FontWeight.w400,
                    fontFamily: "Roboto"),
                )
              )
            ),
          ],
        ),
      ),
    );
  }

  void buttonPressed(){
    showDialog(
        context: context,
        builder: (BuildContext context) => AlertDialog(
          title: Text("Hello!"),
          content: Text("This is sample."),
        )
    );
  }
}
```
実行するとボタンが表示されます。クリックすると画面に「Hello!」と書かれたアラートが表示されます。

### アラートにボタンを追加
いくつかのボタンを表示しクリックしたボタンに応じて処理を行うという処理でよく用いられます。ソースコードは以下の通りです。
``` c
void buttonPressed(){
  showDialog(
    context: context,
    builder: (BuildContext context) => AlertDialog(
      title: Text("Hello!"),
      content: const Text("This is sample."),
      actions: <Widget>[
        TextButton(
            child: const Text('Cancel'),
            onPressed: () => Navigator.pop<String>(context, 'Cancel')
        ),
        TextButton(
            child: const Text('OK'),
            onPressed: () => Navigator.pop<String>(context, 'OK')
        )
      ],
    ),
  ).then<void>((value) => resultAlert(value));
}

void resultAlert(String value) {
  setState((){
    _message = 'selected: $value';
  });
}
```
実行するとボタンが表示され、クリックすると画面にアラートが表示されます。するとメッセージの下に「Cancel」「OK」というボタンが表示されます。これらのボタンをクリックするとアラートが消え「selected: ○○」と表示されます。

### SimpleDialogについて
ダイアログにはユーザーに入力してもらうものもあります。複数の項目から1つを選ぶような入力は簡単に作成できるクラスが「SimpleDialog」です。ソースコードは以下の通りです。
``` c
void buttonPressed(){
  showDialog(
    context: context,
    builder: (BuildContext context) => SimpleDialog(
      title: const Text('Select assignment'),
      children: <Widget>[
        SimpleDialogOption(
          onPressed: () => Navigator.pop<String>(context, 'One'),
          child: const Text('One'),
        ),
        SimpleDialogOption(
          onPressed: () => Navigator.pop<String>(context, 'Two'),
          child: const Text('Two'),
        ),
        SimpleDialogOption(
          onPressed: () => Navigator.pop<String>(context, 'Three'),
          child: const Text('Three'),
        ),
      ],
    ),
  ).then<void>((value) => resultAlert(value));
}
```
実行すると「One」「Two」「Three」という項目を持ったダイアログが現れる。ここから項目を選択すると選択した項目がメッセージに表示される。