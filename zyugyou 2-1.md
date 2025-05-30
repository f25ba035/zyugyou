# 2-1 プロジェクトの構成　　
Flutterプロジェクトを作成すると多数のファイル、フォルダが生成される。実際に編集するDartのスクリプトが入っているのは「lib」フォルダで、「main.dart」というファイルが入っている。　　

### main.dartのソースコード　　
```　c
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
これはデフォルトのmain.dartスクリプトファイルを少し書き換えたもの。実行すると真っ黒の背景に「Hello, Flutter World!!」と表示される。  

### アプリ画面とウィジェットツリー
Flutterでは画面表示が「**ウィジェット**」と呼ばれる部品で構成されている。アプリのボタンやレイアウトだけを設定するものなど様々なウィジェットがある。アプリはそうしたウィジェットの回想のような組み合わせでできており、これを「**ウィジェットツリー**」という。　　

### アプリの構造
1. アプリケーションはmain関数として定義する。このmain関数では、runAppでウィジェットのインスタンスを実行する。
1.  runApp関数では、StatelessWidget継承クラスのインスタンスを引数に指定。これがアプリの本体のUIとなる。
1. StatelessWidget継承クラスにはbuildメソッドを用意する。ここでマテリアルデザインのアプリクラスであるMaterialAppインスタンスをreturnする。
1. MaterialAppの引数homeに、実際にアプリ内に表示するウィジェットを設定する。

### ScaffordとAppBar  
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
      home: Scaffold(
        appBar: AppBar(
          title: Text('Hello Flutter!'),
        ),
        body: Text(
          'Hello Flutter World!!',
          style: TextStyle(fontSize:32.0),
        ),
      ),
    );
  }
}
```
これを実行すると上部にアプリケーションバーが表示され、「Hello Flutter!」というタイトルが表示される。その下には「Hello Flutter World!!」というテキストが表示される。

Scaffoldはプログラムの土台のようなもので今回はAppBarとBodyのウィジェットを追加させることで、使えるようにしている。　　
AppBarはアプリケーションバーを設定するための値を指定するためのものです。  
bodyはアプリケーションバーの下の空白エリアを全体の表示を担当しています。