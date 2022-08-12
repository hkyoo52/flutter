## State
* UI가 변경되도록 영향을 미치는 데이터
* App 수준과 Widget 수준의 데이터가 있다.

## Stateless widget
* State가 변하지 않는 widget


## Tree 종류

![image](https://user-images.githubusercontent.com/63588046/184268960-22102112-de4c-4eac-8726-1491daea11a6.png)

#### Widget tree
* 우리가 만드는 tree
* 설계도(어떤 순서로, 어떤 모양으로 그릴 건지)

#### Element tree
* widget tree 기반으로 생성
* widget tree와 1대1 대응
* 위치정보를 저장함. 그래서 widget tree가 변경되어도 변화 X
* 즉 변경된 부분만 바꿈!!!

#### Render tree
* 앱 상으로 보여줌


## Stateful widget 사용법
* Stateless widget을 만든다.
* Stateful로 바꾼다.
* 변경되는 부분을 setState(() { 내용 } ); 로 감싼다.

```dart
setState(() {
    counter++;
    print('$counter');
  });
```
