# 4-1 複雑な構造のウィジェット
### AppBarについて
AppBarはtitleにTextを用意してタイトルの表示を行う目的で使ってきました。AppBarには他にも重要なプロパティがあります。
- title　タイトル表示部分。通常はテキストを使用。
- leading 左端に表示される。通常はアイコンやボタンに使用。
- actions タイトルの右側に表示される。ボタン・アイコンなどのリストを用意。
- bottom 上記の下に追加表示される部分。PreferredSizeインスタンスを用意。

これらを理解したうえでAppBarをカスタマイズしてみました。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
  static var _message = 'ok';
  static var _stars = '☆☆☆☆☆';
  static var _star = 0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('My App'),
        leading: BackButton(
          color: Colors.white,
        ),

        actions: <Widget>[
          IconButton(
            icon: Icon(Icons.android),
            tooltip: 'add star...',
            onPressed: iconPressedA,
          ),
          IconButton(
            icon: Icon(Icons.favorite),
            tooltip: 'subtract star...',
            onPressed: iconPressedB,
          ),
        ],

        bottom: PreferredSize(
          preferredSize: const Size.fromHeight(30.0),
          child: Center(
            child: Text(_stars,
              style: TextStyle(
                fontSize: 22.0,
                color:Colors.white,
              ),
            ),
          ),
        ),
      ),

      body: Center(
          child: Text(
            _message,
            style: const TextStyle(
              fontSize: 28.0,
            ),
          )
      ),
    );
  }

  void iconPressedA() {
    _message = 'tap "android".';
    _star++;
    update();
  }
  void iconPressedB() {
    _message = 'tap "favorite".';
    _star--;
    update();
  }

  void update() {
    _star = _star < 0 ? 0 : _star > 5 ? 5 : _star;
    setState(() {
      _stars = '★★★★★☆☆☆☆☆'.substring(5 - _star, 5 - _star + 5) ;
      _message = _message + '[$_star]';
    });
  }
}
```
実行するとAppBarの左側に1つ、右側に2つアイコンが表示されます。右側のアイコン二つは、クリックすると「tap: "アイコン名".[星数]」といった形でメッセージが表示され、bottomの星の数が変化します。

### BottomNavigationBarについて
これはAppBarのように画面上部だけでなく、下部にもバーを表示することができるようになるものです。このBottomNavgationBarには、BottomNavigationBarItemというウィジェットを組み込むことでアイコンを表示しクリックして操作できるようになります。Flutter Studioにもこれは用意されていて、「Material」ジャンルを選択すると、そこに「BottomNavigationBar」,「BottomNavigationBarItem」のアイコンがあります。これをドラッグ＆ドロップして配置すると項目が追加され、プロパティ欄にアイコンとタイトルを設定する表示が追加されます。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
  static var _message = 'ok';
  static var _index = 0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('My App'),
      ),
      body: Center(
        child: Text(
          _message,
          style: const TextStyle(
            fontSize: 28.0,
          ),
        )
      ),
      bottomNavigationBar: BottomNavigationBar(
        currentIndex: _index,
        backgroundColor: Colors.lightBlueAccent,
        items: <BottomNavigationBarItem>[
          BottomNavigationBarItem(
            label: 'Android',
            icon: Icon(Icons.android,color: Colors.black, size: 50),
          ),
          BottomNavigationBarItem(
            label: 'Favorite',
            icon: Icon(Icons.favorite,color: Colors.red, size: 50),
          ),
          BottomNavigationBarItem(
            label: 'Home',
            icon: Icon(Icons.home,color: Colors.white, size: 50),
          ),
        ],
        onTap: tapBottomIcon,
      ),
    );
  }

  void tapBottomIcon(int value) {
    var items = ['Android', 'Heart', 'Home'];
    setState(() {
      _index = value;
      _message = 'you tapped: "' + items[_index] + '".';
    });
  }
}
```
実行すると下部に3つのアイコンが表示されたバーが出てきます。これがBottomNavigationBarです。アイコンをクリックすると、そのアイコンが選択され「you tapped: ○○」と表示されます。

### ListViewについて
このListViewはスマートフォンのシステム設定などで多数の項目を並べて表示しているインターフェースなどでよく見られます。FlutterStudioでは「Scrolling」とおいうジャンルに入っています。ドラッグ＆ドロップで配置すると上下左右のスペースを調整するプロパティが表示されます。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
  static var _message = 'ok.';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('My App'),
      ),

      body: Column(
        children: <Widget>[
          Text(
            _message,
            style: TextStyle(
              fontSize: 32.0,
            ),
          ),

          ListView(
            shrinkWrap: true,
            padding: const EdgeInsets.all(20.0),

            children: <Widget>[

              Text('First item',
                style: TextStyle(fontSize: 24.0),
              ),
              Text('Second item',
                style: TextStyle(fontSize: 24.0),
              ),
              Text('Third item',
                style: TextStyle(fontSize: 24.0),
              ),
            ],
          ),
        ],
      ),
    );
  }
}
```
これを実行するとコード内のListViewで入力した「First item」「Second item」「Third item」縦に並んで表示されます。他にもListViewの中には「shrinkWrap」という追加された項目に応じて、大きさを自動調整してくれる設定が入っています。

### ListTileで項目を用意する
ListViewを表示された項目をクリックして操作する本来の使い方をするならListViewに用意されている専用ウィジェット、「ListTile」を使いましょう。ここでは以下のようなことが設定できます。

| 設定 | 内容 |
----|----
| leading | 項目の左端に表示するアイコン。Iconインスタンスで設定 |
| title | 項目に表示する内容。 |
| selected | その項目の選択状態。trueなら選択されている。 |
| onTap | クリックされた際のイベント処理。 |
| onLongPress | ロングクリックされた際のイベント処理。 |

ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
  static var _message = 'ok.';
  static var _index = 0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(

      appBar: AppBar(
        title: Text('My App'),
      ),

      body: Column(
        children: <Widget>[
          Text(
            _message,
            style: TextStyle(
              fontSize: 32.0,
            ),
          ),
          ListView(
            shrinkWrap: true,
            padding: const EdgeInsets.all(20.0),
            children: <Widget>[

              ListTile(
                leading: const Icon(Icons.android, size:32),
                title: const Text('first item',
                  style: TextStyle(fontSize: 28)),
                selected: _index == 1,
                onTap: () {
                  _index = 1;
                  tapTile();
                },
              ),

              ListTile(
                leading: const Icon(Icons.favorite, size:32),
                title: const Text('second item',
                  style: TextStyle(fontSize: 28)),
                selected: _index == 2,
                onTap: () {
                  _index = 2;
                  tapTile();
                },
              ),

              ListTile(
                leading: const Icon(Icons.home, size:32),
                title: const Text('third item',
                  style: TextStyle(fontSize: 28)),
                selected: _index == 3,
                onTap: () {
                  _index = 3;
                  tapTile();
                },
              ),
            ],
          ),
        ],
      ),
    );
  }

  void tapTile() {
    setState(() {
      _message = 'you tapped: No, $_index.';
    });

  }
}
```
実行すると先ほどの分にアイコンが追加されたリストが出現し、クリックするとその項目が選択されクリックした項目の番号が「you tapped: No.○○」と表示されます。

### SingleChildScrollViewについて
ListViewを使っていると項目が増えすぎて表示しきれないということが起きてしまいます。こうした場合に使われるのが「SingleChldScrollView」というものです。これは1つのウィジェットを内部にもてるコンテナでそのウィジェットの幅に応じて自動的にスクロール表示できます。FlutterStudioでは「Scrolling」ジャンルに用意されています。ドラッグ＆ドロップで配置すると、上下左右の設定と「Vertical」「Horizontal」というスクロール方向切り替えボタンが表示されます。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {

 @override
 Widget build(BuildContext context) {
   return Scaffold(

     appBar: AppBar(
       title: Text('My App'),
     ),

     body: SingleChildScrollView(
       child: Column(
           mainAxisSize: MainAxisSize.min,
           mainAxisAlignment: MainAxisAlignment.spaceAround,
           children: <Widget>[
             Container(
               color: Colors.blue,
               height: 120.0,
               child: const Center(
                 child: Text('One',
               style: const TextStyle(fontSize: 32.0)),
               ),
             ),
             Container(
               color:Colors.white,
               height: 120.0,
               child: const Center(
                 child: Text('Two',
               style: const TextStyle(fontSize: 32.0)),
               ),
             ),
             Container(
               color: Colors.blue,
               height: 120.0,
               child: const Center(
                 child: Text('Three',
               style: const TextStyle(fontSize: 32.0)),
               ),
             ),
             Container(
               color:Colors.white,
               height: 120.0,
               child: const Center(
                 child: Text('Four',
               style: const TextStyle(fontSize: 32.0)),
               ),
             ),
             Container(
               color: Colors.blue,
               height: 120.0,
               child: const Center(
                 child: Text('Five',
               style: const TextStyle(fontSize: 32.0)),
               ),
             ),
           ],
         ),
       ),
   );
 }

}
```
実行すると青と白の背景に四角い項目が5つ表示されます。全部表示しきれない場合は、マウスで上下にドラッグするとスクロールすることで見れるようになっています。