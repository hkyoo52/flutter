## main.dart

* 간단한 정보만 사용

```dart
import 'package:flutter/material.dart';

import 'login_app/login.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Login app',
      theme: ThemeData(primarySwatch: Colors.grey),
      home: LogIn(),
    );
  }
}
```

## login.dart
* 반복을 제외한 부분을 사용
* body는 기니깐 따로 뺌
```dart
import 'package:flutter/material.dart';
import 'package:flutter_project/my_button/my_button.dart';


class LogIn extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.blue,
        title: Text(
          'Sign In',
          style: TextStyle(color: Colors.white),
        ),
        centerTitle: true,
        elevation: 0.2,
      ),
      body: _buildButton(),
    );
  }

  // widget 타입으로 바꾸기!!
  // 앞에 _ 붙이는 거는 접근 관리자 기능!! -> 이 파일에서만 사용 가능
  Widget _buildButton() {
    return Padding(
      padding: EdgeInsets.all(16.0),
      child: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: <Widget>[

          SizedBox(
            height: 10.0,
          ),
            MyButton(image: Image.asset('image/glogo.png'),
              text: Text(
              'Login with Facebook',
              style: TextStyle(color: Colors.black, fontSize: 15.0),
            ),
              color: Colors.white,
              radius: 4.0,
                onPressed: (){},
            ),
          SizedBox(height: 10,),
          MyButton(image: Image.asset('image/flogo.png'),
            text: Text(
              'Login with Facebook',
              style: TextStyle(color: Colors.white, fontSize: 15.0),
            ),
            color: Colors.blue,
            radius: 4.0,
            onPressed: (){},
          ),
          SizedBox(height: 10,),
          MyButton(image: Image.asset('image/glogo.png'),
            text: Text(
              'Login with Facebook',
              style: TextStyle(color: Colors.white, fontSize: 15.0),
            ),
            color: Colors.green,
            radius: 4.0,
            onPressed: (){},
          ),
        ],
      ),
    );
  }
}
```

## my_button.dart
* button 부분을 여러개 만드니깐 동일한 부분은 하나로 만듬

```dart
import 'package:flutter/material.dart';

class MyButton extends StatelessWidget {

  MyButton({required this.image, required this.text, required this.color, required this.radius, required this.onPressed});

  final Widget image;
  final Widget text;
  final Color color;
  final double radius;
  final VoidCallback onPressed;

  @override
  Widget build(BuildContext context) {
    return ButtonTheme(
      height: 50.0,
      child: RaisedButton(
        child: Row(
          mainAxisAlignment: MainAxisAlignment.spaceEvenly,
          children: <Widget>[
            image,
            text,
            Opacity(
              opacity: 0.0,
              child: image,
            ),
          ],
        ),
        color: color,
        onPressed: onPressed,
      ),
      shape: RoundedRectangleBorder(
        borderRadius: BorderRadius.all(
          Radius.circular(radius),
        ),
      ),
    );
  }
}
```
