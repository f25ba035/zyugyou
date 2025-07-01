# 4-2 ナビゲーションとルーティング
### 表示切替とナビゲーション
アプリは一つの画面だけで完結するのではなく、いくつかの画面を切り替えることで捜査をしているアプリがほとんどです。これはナビゲーション機能を使うことで解決します。これは「Navigator」というクラスで用意されています。これは以下のような働きをします。
- 移動先のウィジェットを追加すると、そのウィジェットに表示を切り替える。
- 保管されたウィジェットを取り出すと、そのウィジェットに表示を戻す。

上記のことからわかる通り、「Navigator」はコレクション的な機能と表示の切り替えが一体化したものです。ここでは「push」と「pop」が使われており、pushは現在の表示をデータに保管し、起動先に表示を切り替える働きをします。popは最後に表示した移動元を取り出し、そこに表示を戻します。ソースコードは以下の通りです。
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
      home: FirstScreen(),
    );
  }
}

// １つ目のスクリーン
class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Home'),
      ),
      body: Center(
        child: Container(
          child: const Text('Home Screen',
              style: const TextStyle(fontSize: 32.0)),
        ),
      ),
      bottomNavigationBar: BottomNavigationBar(
        currentIndex: 1,
        items: <BottomNavigationBarItem>[
          const BottomNavigationBarItem(
            label: 'Home',
            icon: const Icon(Icons.home, size:32),
          ),
          const BottomNavigationBarItem(
            label: 'next',
            icon: const Icon(Icons.navigate_next, size:32),
          ),
        ],
        onTap: (int value) {
          if (value == 1)
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context)=>SecondScreen()),
            );
        },
      ),
    );
  }
}

// ２つ目のスクリーン
class SecondScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Next"),
      ),
      body: Center(
        child: const Text('Next Screen',
            style:const TextStyle(fontSize: 32.0)),
      ),
      bottomNavigationBar: BottomNavigationBar(
        currentIndex: 0,
        items: <BottomNavigationBarItem>[
          const BottomNavigationBarItem(
            label: 'prev',
            icon: const Icon(Icons.navigate_before, size:32),
          ),
          const BottomNavigationBarItem(
            label: '?',
            icon: const Icon(Icons.android, size:32),
          ),
        ],
        onTap: (int value) {
          if (value == 0) Navigator.pop(context);
        },
      ),
    );
  }
}
```
これを実行すると「HomeScreen」と表示された画面が出てきます。下にはナビゲーションバーがあり、「home」「next」というアイコンがあります。nextをクリックすると画面が切り替わり、「NextScreen」と表示されたウィジェットに変わります。このとき左下の「prev」をクリックすると、元の画面に戻ります。(左上に表示される←をクリックでも戻れる)

### 表示間の値の受け渡し
複数の表示を切り替えながら操作するには、必要な値を受け渡す必要があります。これをするには最初の画面で必要な値を用意し、次の画面に移動する際に値を引数に指定してインスタンスを作れば簡単に作ることができます。ソースコードは以下の通りです。
``` c
class FirstScreen extends StatefulWidget {
  FirstScreen({Key? key}) : super(key: key); // コンストラクタ

  @override
  _FirstScreenState createState() => _FirstScreenState();
}

class _FirstScreenState extends State<FirstScreen> {
  static final _controller = TextEditingController();
  static var _input = '';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Home'),
      ),
      body: Column(
        children: <Widget>[
          const Text('Home Screen',
          style: const TextStyle(fontSize: 32.0)),
          Padding(
            padding: const EdgeInsets.all(20.0),
            child: TextField(
                controller: _controller,
                style: const TextStyle(fontSize: 28.0),
                onChanged: changeField,
              ),
          ),
        ],
      ),
      bottomNavigationBar: BottomNavigationBar(
        currentIndex: 1,
        items: <BottomNavigationBarItem>[
          const BottomNavigationBarItem(
            label: 'Home',
            icon: const Icon(Icons.home),
          ),
          const BottomNavigationBarItem(
            label: 'next',
            icon: const Icon(Icons.navigate_next),
          ),
        ],
        onTap: (int value) {
          if (value == 1) {
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context) => SecondScreen(_input)),
            );
        }
      },
    ),
    );
  }

  void changeField(String val) => _input = val;
}

class SecondScreen extends StatelessWidget {
  final String _value;

  SecondScreen(this._value);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Next"),
      ),
      body: Center(
        child: Text(
          'you typed: "$_value".',
          style: const TextStyle(fontSize: 32.0),
        ),
      ),
      bottomNavigationBar: BottomNavigationBar(
        currentIndex: 0,
        items: <BottomNavigationBarItem>[
          BottomNavigationBarItem(
            label: 'prev',
            icon: const Icon(Icons.navigate_before),
          ),
          BottomNavigationBarItem(
            label: '?',
            icon: const Icon(Icons.android),
          ),
        ],
        onTap: (int value) {
          if (value == 0) Navigator.pop(context);
        },
      ),
    );
  }
}
```
実行すると入力できるフィールドが出てきます。テキストを書いて右下のアイコンをクリックすると、「Second Screen」に移動、「you typed:"○○".」と表示される。

### routesによるルーティング
あらかじめルートと表示するウィジェットの関係を定義しておき、ルートの値を設定することで指定のウィジェットが表示される仕組みをつくるもの。このような場合に使われるのがStateless Widgetに用意できる「routes」というプロパティです。ソースコードは以下の通りです。
``` c
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
      initialRoute: '/',
      routes: {
        '/': (context) => FirstScreen(),
        '/second': (context) => SecondScreen('Second'),
        '/third': (context) => SecondScreen('Third'),
      },
    );
  }
}

class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Home'),
      ),
      body: Center(
        child:const Text('Home Screen',
          style: const TextStyle(fontSize: 32.0),
        ),
      ),
      bottomNavigationBar: BottomNavigationBar(
        currentIndex: 1,
        items: <BottomNavigationBarItem>[
          BottomNavigationBarItem(
            label: 'Home',
            icon: const Icon(Icons.home),
          ),
          BottomNavigationBarItem(
            label: 'next',
            icon: const Icon(Icons.navigate_next),
          ),
        ],
        onTap: (int value) {
          if (value == 1)
            Navigator.pushNamed(context, '/second');
        },
      ),
    );
  }
}

class SecondScreen extends StatelessWidget {
  final String _value;
  SecondScreen(this._value);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text("Next"),
      ),
      body: Center(
        child: Text(
          '$_value Screen',
          style: const TextStyle(fontSize: 32.0),
        ),
      ),
      bottomNavigationBar: BottomNavigationBar(
        currentIndex: 0,
        items: <BottomNavigationBarItem>[
          BottomNavigationBarItem(
            label: 'prev',
            icon: const Icon(Icons.navigate_before),
          ),
          BottomNavigationBarItem(
            label: '?',
            icon: const Icon(Icons.android),
          ),
        ],
        onTap: (int value) {
          if (value == 0) Navigator.pop(context);
          if (value == 1)
            Navigator.pushNamed(context, '/third');
        },
      ),
    );
  }
}
```
実行したら右下のアイコンをクリックすると、「FirstScreen」から「SecondScreen」、「ThirdScreen」へと変わっていきます。