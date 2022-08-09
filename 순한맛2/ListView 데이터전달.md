![image](https://user-images.githubusercontent.com/63588046/183609052-1410e145-bebe-4a44-a00d-b0be33b08162.png)

```python

class _MyPageState extends State<MyPage> {

  static List<String> animalName = ['Bear','Camel','Deer','Fox','Kangaroo','Koala','Lion','Tiger'];
  static List<String> animalImagePath = ['image/img1.jpg','image/img2.jpg','image/img3.jpg','image/img4.jpg','image/img5.jpg','image/img6.jpg','image/img7.jpg','image/img8.jpg'];
  static List<String> animalLocation = ['Bear','Camel','Deer','Fox','Kangaroo','Koala','Lion','Tiger'];

  final List<Animal> animalData = List.generate(animalLocation.length, (index) =>
      Animal(animalName[index],animalLocation[index],animalImagePath[index])); //Animal은 import 해야됨, //오름차순으로 데이터를 전달

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('ListView'),
      ),
      body: ListView.builder(
          itemCount: animalData.length,
          itemBuilder: (context, index){
            return Card(
              child: ListTile(
                title: Text(
                  animalData[index].name
                ),
                leading: SizedBox(      // 이미지 넣기
                  height: 50,
                  width: 50,
                  child: Image.asset(animalData[index].imgPath),
                ),
              ),
            );
          }),
    );
  }
}
```

![image](https://user-images.githubusercontent.com/63588046/183647356-ea77e62b-c2a6-4274-8568-12bc23a384e6.png)

```python
# animal_page.dart
import 'package:flutter/material.dart';

import 'model.dart';

class AnimalPage extends StatelessWidget {
  const AnimalPage({Key? key, required this.animal}) : super(key: key); // animal이라는 변수를 받아야함(그래서 아래에 final Animal animal 만듬) // 그리고 animal은 null값 못가지므로 꼭 required를 앞에 붙여야함!!

  final Animal animal;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(animal.name),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            //Image.asset(animal.imgPath), // 너무 이미지가 크게 나옴 -> SizedBox 사용
            SizedBox(
              height: 200,
              width: 200,
              child: Image.asset(animal.imgPath),
            ),
            SizedBox(
              height: 20,
            ),
            Text(
              'It lives in ' + animal.location,
              style: TextStyle(
                fontSize: 18
              ),
            )

          ],
        ),
      ),
    );
  }
}
```

## 좋아요 버튼
* ... 작동이 안됨...??ㅠㅠ
