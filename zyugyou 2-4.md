# 複数ウィジェットの配置
### Columnを使う
このウィジェットは複数のウィジェットを縦に並べて配置できるウィジェットです。配置すると右側にプロパティが表示されます。このプロパティでは「Column」の配置場所、「Column」の中に配置したウィジェットの配置場所、ウィジェットのサイズなどを設定できます。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('App Name'),
      ),
      body:
      Column(
          mainAxisAlignment: MainAxisAlignment.start,
          mainAxisSize: MainAxisSize.max,
          crossAxisAlignment: CrossAxisAlignment.center,
          children: <Widget>[
            Text(
              "One",
              style: TextStyle(fontSize:32.0,
                  color: const Color(0xff000000),
                  fontWeight: FontWeight.w700,
                  fontFamily: "Roboto"),
            ),
            Text(
              "Two",
              style: TextStyle(fontSize:32.0,
                  color: const Color(0xff000000),
                  fontWeight: FontWeight.w700,
                  fontFamily: "Roboto"),
            ),
            Text(
              "Three",
              style: TextStyle(fontSize:32.0,
                  color: const Color(0xff000000),
                  fontWeight: FontWeight.w700,
                  fontFamily: "Roboto"),
            )
          ]
      ),
    );
  }
}
```
これを実行すると「One」「Two」「Three」のテキストが縦に整列して配置されます。

### Rowを使う
「Row」は「Column」の横に並べるバージョンです。「Column」と同様に、「Row」の配置場所、「Row」の中に配置したウィジェットの配置場所、ウィジェットのサイズなどを設定できます。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        appBar: AppBar(
          title: Text('App Name'),
        ),
        body:
          Row(
            mainAxisAlignment: MainAxisAlignment.center,
            mainAxisSize: MainAxisSize.max,
            crossAxisAlignment: CrossAxisAlignment.center,
            children: <Widget>[
              Text(
              "One",
                style: TextStyle(fontSize:32.0,
                color: const Color(0xff000000),
                fontWeight: FontWeight.w400,
                fontFamily: "Roboto"),
              ),
              Text(
              "Two",
                style: TextStyle(fontSize:32.0,
                color: const Color(0xff000000),
                fontWeight: FontWeight.w400,
                fontFamily: "Roboto"),
              ),
              Text(
              "Three",
                style: TextStyle(fontSize:32.0,
                color: const Color(0xff000000),
                fontWeight: FontWeight.w400,
                fontFamily: "Roboto"),
              )
            ]
          ),
      );
    }
    void fabPressed() {}

}
```
これを実行すると「One」「Two」「Three」のテキストが横に整列して配置されます。