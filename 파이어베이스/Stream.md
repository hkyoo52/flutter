## Stream
* 변동되는 데이터 값 불러오기

```dart
body: StreamBuilder(
  stream : 서버 이름 & 서버에 저장된 파일위치.snapshots(),   // snapshots은 바뀌는 데이터 불러옴
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
              docs[index]['text'],
              style: TextStyle(fontSize: 20.0),
            ),
          );
        },
      );
    },
    )

```
