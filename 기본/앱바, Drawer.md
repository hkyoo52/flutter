## Class와 Widget의 연관성
* Class : 객체가 가져야 하는 속성, 기능을 정의한 내용
* 객체 : 클래스가 정의된 후 메모리상에 할당된것
* 인스턴스 : 클래스 기반으로 생성 됨


## 매뉴칸, 장바구나 칸, 쇼핑칸 만들기
![image](https://user-images.githubusercontent.com/63588046/183236867-c5878313-b4af-41f0-8a5e-6f21c23218b2.png)


```
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title : 'Appbar',
      theme: ThemeData(
        primarySwatch: Colors.red
      ),
    home : MyPage(),
    );
  }
}

class MyPage extends StatelessWidget {
  const MyPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title : Text('Appbar icon menu'),
        centerTitle: true,
        elevation: 0.0,
        leading:          // 위젯이나 아이콘의 위치를 왼쪽에서 생성
          IconButton(
            icon : Icon(Icons.menu),  // menu 위젯 생성
            onPressed: (){    // 클릭 가능한 위젯, 클릭시 이벤트 정의함
              print('menu button is clicked');
            },
          ),
        actions: [        // 위젯이나 아이콘 오른쪽에 생성성
         IconButton(
            icon : Icon(Icons.shopping_cart),  // menu 위젯 생성
            onPressed: (){    // 클릭 가능한 위젯
              print('shopping cart button is clicked');
            },
          ),
          IconButton(
            icon : Icon(Icons.search),  // menu 위젯 생성
            onPressed: (){    // 클릭 가능한 위젯
              print('Search button is clicked');
            },
          ),
        ],
      ),
    );
  }
}

```


## 매뉴바 클릭시 띄워지기
![image](https://user-images.githubusercontent.com/63588046/183236815-49626de9-fa19-4940-a43c-bbaa442109cb.png)

* 매뉴바 만드는거 삭제
* Draw 추가 (아래가 방법)
```python
      ~~~
      drawer: Drawer(
        child : ListView(
          padding: EdgeInsets.zero,
          children: [
            UserAccountsDrawerHeader(
                currentAccountPicture: CircleAvatar(
                  backgroundImage: AssetImage('assets/flutter.jpg'),   // 이미지 
                  backgroundColor: Colors.white,
                ),
                onDetailsPressed: (){     // 새로운 창을 열 수 있는 화살표 새성
                  print('arrow is clicked');
                },
                decoration: BoxDecoration(   // 박스 부분 변경하기
                  color: Colors.red[200],
                  borderRadius: BorderRadius.only(    // 박스 아래부분 둥글게 만들기
                    bottomLeft: Radius.circular(40.0),
                    bottomRight: Radius.circular(40.0)
                  )
                ),
                accountName: Text('flutter'),
                accountEmail: Text('flutter@naver.com')),

          ],
        ),
      ),
```

## 매뉴바 클릭시 띄워지는 곳 아래에 리스트 뷰 만들기
![image](https://user-images.githubusercontent.com/63588046/183236713-76f4ef66-5a6e-4632-b743-983fd68d539d.png)

```python
      drawer: Drawer(
        child : ListView(
          padding: EdgeInsets.zero,
          children: [
            UserAccountsDrawerHeader(
                currentAccountPicture:        // 왼쪽 끝에 이미지
                  CircleAvatar(
                    backgroundImage: AssetImage('assets/flutter.jpg'),
                    backgroundColor: Colors.white,
                  ),
                otherAccountsPictures: [         // 오른쪽 끝에 이미지
                  CircleAvatar(
                    backgroundImage: AssetImage('assets/pikachu.png'),
                    backgroundColor: Colors.white,
                  ),
                  CircleAvatar(
                    backgroundImage: AssetImage('assets/pikachu.png'),
                    backgroundColor: Colors.white,
                  ),
                ],
                onDetailsPressed: (){     // 새로운 창을 열 수 있는 화살표 새성
                  print('arrow is clicked');
                },
                decoration: BoxDecoration(
                  color: Colors.red[200],
                  borderRadius: BorderRadius.only(
                    bottomLeft: Radius.circular(40.0),
                    bottomRight: Radius.circular(40.0)
                  )
                ),
                accountName: Text('flutter'),
                accountEmail: Text('flutter@naver.com')),
            ListTile(
              leading: Icon(Icons.home,   // 왼쪽에 아이콘 생성
              color: Colors.grey[850],),
              title: Text('Home'),
              onTap: (){                      // 클릭시 소리가 나면서 살짝 그림자가 지다가 없어지게 하는 기능
                print('Home is clicked');
              },
              trailing: Icon(Icons.add),   // 오른쪽에 아이콘 생성
            ),
            ListTile(
              leading: Icon(Icons.settings,   // 왼쪽에 아이콘 생성
                color: Colors.grey[850],),
              title: Text('Setting'),
              onTap: (){                      // 클릭시 소리가 나면서 살짝 그림자가 지다가 없어지게 하는 기능
                print('Setting is clicked');
              },
              trailing: Icon(Icons.add),   // 오른쪽에 아이콘 생성
            ),
            ListTile(
              leading: Icon(Icons.question_answer,   // 왼쪽에 아이콘 생성
                color: Colors.grey[850],),
              title: Text('Q&A'),
              onTap: (){                      // 클릭시 소리가 나면서 살짝 그림자가 지다가 없어지게 하는 기능
                print('Q&A is clicked');
              },
              trailing: Icon(Icons.add),   // 오른쪽에 아이콘 생성
            )
          ],
```
