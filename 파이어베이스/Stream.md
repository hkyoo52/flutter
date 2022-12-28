## Stream
* 변동되는 데이터 값 불러오기


```dart
// 연습용
class ~~ StatefulWidget{
  ~~~
}  
class _ ~~  {
  final int price = 2000;
  
  @override
  Widget build(BuildContext context){
    return scaffold(
      appBar: AppBar(){
        title: Text("~"),
      },
      body: StreamBuilder<int>(
        initialData: price,  // 최초의 값으로 쓸 것
        stream : addStreamValue(),  // 새로운 데이터를 받을때마다 snapshot에 저장
        builder: (context, snapshot){ 
          final priceNumber = snapshot.data.toString(); // 받은 데이터를 string을 변형
          return Center(
            child: Text(
              priceNumber,
            )
          )
        }
      )
    ):
  }
  
  Stream<int> addStreamValue(){
    return Stream<intperiodic(
      Duration(seconds: 1),
        (count) => price + count
    );
  }
}


```

### 파이어베이스 데이터베이스 사용하기
![image](https://user-images.githubusercontent.com/63588046/209837861-f188bb17-6896-409f-8b14-ea4f27fbffe0.png)

* 데이터 베이스 만들기 클릭, 테스트 모드에서 시작
* 쭉쭉 진행
* 폴더 생성  Ex. chat
* 문서 생성 - 받을 데이터 유형 선택 Ex. 자동완성
* 폴더 생성  Ex. message
* 문서 생성 - 필드 이름, 받을 데이터 유형 선택  Ex. 자동완성, 필드 이름을 text로 했음..



```dart
import 'package: ~~ firestore~~'

body: StreamBuilder(
  stream : FirebaseFirestore.intance.collection(서버 이름 & 서버에 저장된 파일위치.snapshots()),   // snapshots은 바뀌는 데이터 불러옴
          builder: (BuildContext context, AsyncSnapshot<QuerySnapshot<Map<String, dynamic>>> snapshot) { // 최신식 데이터 불러오기
      if(snapshot.connectionState == ConnectionState.waiting){
        return Center(
          child: CircularProgressIndicator(),
        );
      }

      final docs = snapshot.data!.docs;   // 전체 데이터
      return ListView.builder(
        itemCount: docs.length,    // 데이터 개수
        itemBuilder: (context, index) {  index는 앞에 itemCount 개수만큼 보여줌
          return Container(
            padding: EdgeInsets.all(8.0),
            child: Text(
              docs[index]['text'],  // text는 저장한 필드 이름임
              style: TextStyle(fontSize: 20.0),
            ),
          );
        },
      );
    },
    )

```
