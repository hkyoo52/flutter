## BuildContext
* widget tree에서 현재 widget의 위치를 알 수 있는 정보
* BuildContext는 위치 정보를 알려줌, 이때 context를 물려받음
* Build Context는 stateless나 state 빌드 메서드에 의해서 리턴 된 위젯의 부모가 된다.

## Scaffold.of(context) 메서드
* 현재 주어진 context에서 위로 올라가면서 가장 가까운 Scaffold를 찾아서 반환하라

* 기존 방법하면 에러가 발생

![image](https://user-images.githubusercontent.com/63588046/183271569-0bfd34b1-d561-4684-9e82-a6a3ed2eab3e.png)

* 그래서!!!

![image](https://user-images.githubusercontent.com/63588046/183271587-cf37dd6c-3e06-44a9-9ca5-db58d489a6ad.png)


![image](https://user-images.githubusercontent.com/63588046/183238520-60576772-c4fe-467b-af67-603d7eebb63c.png)


```python
class MyPage extends StatelessWidget {
  const MyPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: Text('Snack Bar'),
          centerTitle: true,
        ),
        body: Builder(    // 만약 Builder를 만들지 않으면 아래에 Scaffold는 Mypage있으므로 그부분 context를 찾게 된다 -> 원하는 위치 X 그래서 builder를 생성해서 위치를 builder로 두고 거기 있는 flatbar를 찾아서 적용한다.
          builder: (BuildContext ctx) {
            return Center(
              child: FlatButton(
                //입체감 없이 flat하게 그려짐
                child: Text(
                  'Show me',
                  style: TextStyle(color: Colors.white),
                ),
                color: Colors.red,
                onPressed: () {
                  Scaffold.of(ctx)
                      .showSnackBar(SnackBar(content: Text('Hello')));
                },
              ),
            );
          },
        ));
  }
}

```


## 빌더 없이 snack bar 만들기
![image](https://user-images.githubusercontent.com/63588046/183271538-15f7d7e0-615f-43ec-95fa-789ce1dbecc0.png)

* 궁금증... scaffold를 사용하면 context가 바뀌나???
```python
class MySnackBar extends StatelessWidget {
  const MySnackBar({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Center(
      child: RaisedButton(
        child: Text('Show me'),
        onPressed: (){
          Scaffold.of(context)
              .showSnackBar(SnackBar(
                content: Text('Hello',
                textAlign: TextAlign.center,
                style: TextStyle(),
                ),
                backgroundColor: Colors.teal,
                duration: Duration(milliseconds: 1000),  //메세지 전송 시간
                )
                );
        },
      ),
    );
  }
}
```

## 토스트 메세지 구현하기  -> 근데 왜 안되지??
* pubsec.yaml 에서 cupertino_icon 아래에 fluttertoast: ^8.0.9 붙여넣기 (버전은 바뀔 수 있음...https://pub.dev/packages/fluttertoast)
* 상단에 pub get 클릭

```python 
# main.dart
import 'package:fluttertoast/fluttertoast.dart';


class MyPage extends StatelessWidget {
  const MyPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Toast Message'),
        centerTitle: true,
      ),
      body: Center(
        child: ElevatedButton(
          child: Text('Toast'),
          onPressed: () {
            flutterToast();
          },
          style: ButtonStyle(
            backgroundColor: MaterialStateProperty.all(
                Colors.red), //ElevatedButton 에서 버튼 색 바꾸기
          ),
        ),
      ),
    );
  }
}


void flutterToast() {
  // 토스트 메시지를 출력하기 위한 함수 생성
  Fluttertoast.showToast(
      msg: 'Flutter 토스트 메시지', // 토스트 메시지 내용
      gravity: ToastGravity.BOTTOM,
      backgroundColor: Colors.redAccent, // 배경색 빨강색
      fontSize: 20.0,
      textColor: Colors.black, // 폰트 하얀색
      toastLength: Toast.LENGTH_SHORT // 토스트 메시지 지속시간 짧게
  );
}
```






