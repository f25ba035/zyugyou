# タブビューとドロワー
### TabBarとTabBarView
タブのUIを作るのに用意されているウィジェットが「TabBar」と「TabBarView」です。Flutter Studioでは「Material」内にアイコンが用意されています。まず「TabBar」をドラッグ＆ドロップで配置、続けて「TabBarView」もドラッグ＆ドロップで配置します。これでタブの基本的な構成ができます。一応プロパティが表示されますが、AlignmentとSize関係のものが3つ表示されるだけなのでタブ特有の設定はソースコードから行うことになります。ソースコードは以下の通りです。
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
        canvasColor: const Color(0xfffafafa),
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

class _MyHomePageState extends State<MyHomePage>
    with SingleTickerProviderStateMixin {

  static const List<Tab> tabs = <Tab>[
    Tab(text: 'One'),
    Tab(text: 'Two'),
    Tab(text: 'Three'),
  ];

  late TabController _tabController;

  @override
  void initState() {
    super.initState();
    _tabController = TabController(
        vsync: this,
        length: tabs.length
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('My App'),
        bottom: TabBar(
          controller: _tabController,
          tabs: tabs,
        ),
      ),

      body: TabBarView(
        controller: _tabController,
        children: tabs.map((Tab tab) {
          return createTab(tab);
        }).toList(),
      ),
    );
  }

  Widget createTab(Tab tab) {
    return Center(
        child: Text(
          'This is "${tab.text}" Tab.',
          style: const TextStyle(
            fontSize: 32.0,
            color: Colors.blue,
          ),
        )
    );
  }
}
```
実行するとAppBarにタブを切り替えるためのリンクが表示され、クリックすると下に表示されるコンテンツが左右にスクロールして切り替わります。

### 画面下部にタブバーを表示する
先ほどはAppBarのbottomにTabBarを追加して表示していたが、これでは下に表示することができません。AppBarではScaffoldのbottomNavigationBarにTabBarを組み込めば画面下部に配置できます。ソースコードは以下の通りです。
``` c
static const List<Tab> tabs = <Tab>[
  Tab(text: 'One', icon: Icon(Icons.star)),
  Tab(text: 'Two', icon: Icon(Icons.info)),
  Tab(text: 'Three', icon: Icon(Icons.home)),
];
```
下部に表示する場合、テキストだけでなくアイコンも表示するとより自然な切り替えボタンになります。icon引数にIconインスタンスを用意することでアイコンを表示できます。　　
タブバーの表示を変更するために_MyHomePageStateクラスのbuildメソッドを修正することで行えます。ソースコードは以下の通りです。
``` c
@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: Text('My App'),
    ),
    bottomNavigationBar:Container(
      color: Colors.blue,
      child:TabBar(
        controller: _tabController,
        tabs: tabs,
      ),
    ),
    body: TabBarView(
      controller: _tabController,
      children: tabs.map((Tab tab) {
        return createTab(tab);
      }).toList(),
    ),
  );
}
```
実行するとタブバーが画面下部に表示されるようになります。タブのリンクにアイコンも付いたことでより使いやすく、わかりやすくなりました。

### Drawer(ドロワー)について
ドロワーとは、左上や右上に「≣」のアイコンをクリックすると、画面の左または右側からリストが表示されるというUIのことです。このUIはFlutterのScaffoldに組み込んで使うことができます。Scaffoldのdrawerに「Drawer」というウィジェットを組み込んで作成することができます。ソースコードは以下の通りです。
``` c
class _MyHomePageState extends State<MyHomePage> {
  static var _items = <Widget>[];
  static var _message = 'ok.';
  static var _tapped = 0;

  @override
  void initState() {
    super.initState();
    for (var i = 0; i < 5; i++) {
      var item = ListTile(
          leading: const Icon(Icons.android),
          title: Text('No, $i'),
          onTap: (){
            _tapped = i;
            tapItem();
          }
      );
      _items.add(item);
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Flutter App'),
      ),
      body: Center(
        child: Text(
          _message,
          style: const TextStyle(
            fontSize: 32.0,
          ),
        ),
      ),
      drawer: Drawer(
        child: ListView(
          shrinkWrap: true,
          padding: const EdgeInsets.all(20.0),
          children: _items,
        ),
      ),
    );
  }

  void tapItem() {
    Navigator.pop(context);
    setState((){
      _message = 'tapped:[$_tapped]';
    });
  }
}
```
実行すると画面の左上に「≣」アイコンが表示されるようになります。クリックすると左側からリストが表示されます。ここから項目をクリックするとドロワーが消え、「tapped:[○○]」というメッセージが表示されます。