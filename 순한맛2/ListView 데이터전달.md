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

