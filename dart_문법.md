* '', "" 둘다 가능
* ; 붙임
* var : 함수내의 변수
* dynamic : 함수 정의때 사용하는 변수

```python
void main(){
  var a = 10    # public
  var _b = 'HI'     # private
  

Myprint(dynamic c){

}
```

* int, double 사용할 필요 X => num으로 표현

* final 은 동적으로 저장
* const는 바로 저장...??     => final 사용하자

* List타입 -> var items = ['a','b','c'];   
* List 안에 list 넣기 -> [... items, 5, 6];
* Set타입 -> var itemSet = {1, 2, 3};
* map타입 -> var itemMap = {'key1':1,'key2':2,'key3':3};


#### method
```python
void main(){
  something('name', age=10);        # age는 option 값이므로 age=10으로 쓴다.
  
}
void something(String name, {int age}) {       # () 안에 {String name}은 name 변수를 option으로 넣는다.


}


```

* 타입 체크 : a is int -> a는 int?, a is! int -> a는 none int?
* 행변환 
```python
var a=10
b= a as double      # b는 a의 double로 저장
```

* Future 중간에 넣는 코드 -> 비동기 처리 **수정**
```python
void main(){
  print('시작')
  ~~~~~~~~~~~~~~~~~~~~~
  print('끝')
}?

~~~~~~~~~~~~~~~~~~~~~~~
```


## Stream
* 바꿀 부분만 정하기
* 최적화에 좋음


## 클래스
* 객체 : 만들어야 할 대상
* class : 객체를 만들 틀
* 인스턴스 : 클래스를 통해 만들어진 대상
```python
class AutoMobile{
  String carMaker = 'Ford';
  int price = 3000;
  String color = 'red';
  int wheelNumber = 4;
}

class NewCar{
  String carMaker2 = 'Ford';
  int price2 = 3000;
  int wheelNumber2 = 4;
  
  void autoPark(){
    print('자동 주차 가능합니다.');
  }
}
void main(){
  AutoMobile a1 =AutoMobile();
  print(a1.carMaker);
  
  NewCar n1 = NewCar();
  n1.autoPark();
}
```

## 생성자
```python
class Person{
  String name;
  
  Person({String name}){   # 생성자, {} 안에 넣으면 써도 되고 안써도 된다는 의미
    this.name = name
  }
}

void main(){
  Person p1 = new Person()  # Class 인스턴스 이름 = new 생성자
  Person p2 = new Person(age=50)
  print(p1.age)     # 결과 : null
  print(p2.age)     # 결과 : 50

}

```

## 생성자2
```dart
class MyButton extends StatelessWidget {

  // required는 무조건 
  MyButton({required this.image, required this.text, required this.color, required this.radius, required this.onPressed});

  final Widget image;
  final Widget text;
  final Color color;
  final double radius;
  final VoidCallback onPressed;
```


## Collection Generic
* Collection : 데이터들을 모아서 가지고 있는 자료구조
    * fixed-length list : 리스트 크기 고정
    * growable list : 리스트 크기 변경 가능
* Generic : Collection이 가지고 있는 데이터들의 데이터 타입 지정
 
```python


void main(){
  //var number = new List(5); // fixed list
  // List<Stirng> number = new List();  // 리스트 타입 고정 -> 제네릭 기법
  List<int> number = List(); // growable list
  
  // list는 add함수로 데이터 추가
  number.add(2);
  number.add(3);
  number.add(7);
  number.addAll([2,5,6]);
  print(number);
}
```



## const vs final
* const : 컴파일 할때부터 상수 -> 변수 초기화할때부터 고정되어 있음
* final : 런타임때 상수 -> 초기화할때는 고정 X 


## null safety
* 모든 변수는 null이 될 수 없다. non-nullable 변수에는 null 값을 할당할 수 없다.
* non-nullable 변수를 위한 null check가 필요 없다. (num == null  이런거 X)
* Class 내의 변수는 반드시 선언과 동시에 초기화를 시켜야 함 (int name; 은 안됨!!, int name = 5;)
* 반드시 null이 안되는 경우 뒤에 ! 붙여!!  



#### 에러
```dart
String? name; // null값이 올 수 있다.

String nameChange(String name) {   -> 근데 여기서 String name에 name은 null 이면 안된다!! 그래서 에러
  this.name = name;
  return name.toUpperCase();
}
```

#### 고치는점
```dart
String? name;

String nameChange(String? name) {   
  this.name = name;
  if(name == null){
    return 'need a name';
  }
  else{
    return name.toUpperCase();
  }
}
```

#### late 사용하기
```dart
class Person {
  late String name;
  
  String printname(String name){
    this.name = name;
    return name
  }
}

void main() {
  Person p = Person();
  print(p.printname('hi'))
}
```

#### null을 가지면 안되는 경우 required 추가
```dart
void main() {
  print(add(a: 5, b:6));
}

int add({required int a, required int b}) {
  int sum = a + b;
  return sum;
}
```


## Future
```dart
import 'dart:io';  // 네트워크와 연동

void main(){
  showData();
}

void showData(){
  startTask();
  accessData();
  fetchData();
}

void startTask() {
  String info1 = '요청수행 시작';
  print(info1);
}

void accessData() {
  Duration time = Duration(seconds: 3);     // time = 3초
  if(time.inSeconds>2){
    Future.delayed(time, (){                // time에 delay가 있으면 다른 코드 먼저 실행하고 time초 이후에 실행해라
      String info2 = '데이터 처리 완료';
      print(info2);
    });
  }
  else{
    sleep(time);
    String info2 = '데이터 가져왔습니다';
    print(info2);
  }
}

void fetchData() {
  String info3 = '잔액은 8500만원 입니다.';
  print(info3);
}
```

## async
* await 메서드를 가짐
* 이 부분이 끝나야 다음 부분 진행하게 만듬
```dart
import 'dart:io';  // 네트워크와 연동

void main(){
  showData();
}

void showData() async{
  startTask();
  String account = await accessData();
  fetchData(account);
}

void startTask() {
  String info1 = '요청수행 시작';
  print(info1);
}

Future <String> accessData() async{
  String account;

  Duration time = Duration(seconds: 3);
  if(time.inSeconds>2){
    await Future.delayed(time, (){
      account = '8500만원';
      print(account);

      return account;
    });
  }
  else {
    String info2 = '데이터 가져왔습니다';
    print(info2);
  }
  return '';
}

void fetchData(String account) {
  String info3 = '잔액은 $account 입니다.';
  print(info3);
}
```
메
## cascade notation
* 아래 2개는 동일함
```dart
Person p1 = new Person();
p1.age= 20;
p1.name='James';
p1.show();
```
```dart
Person p1 = new Person();
p1..name='Jamie'..setA(30)..show();   // 이 방식이 cascade notation
```

## generate
```dart
// 1부터 45까지 생성 ... [1,2,3,,,,,,45]
var test = List<int>.generate(45, (i) => i+1);
print(test);
```

## shuffle
* 리스트 내에 있는거 섞기
```dart
List<int>.generate(45, (i) => i+1)..shuffle()
```

## 리스트 index하기 -> sublist
```dart
List<int>.generate(45, (i) => i+1).sublist(0,6);
```


## 반복문
```dart
void main(){
  
  List<String> rainbow = ['빨','주','노','초','파','남','보'];
  
  for(int i = 0; i<rainbow.length; i++){
    print(rainbow[i]);
  }
}
```

```dart
void main(){
  
  List<String> rainbow = ['빨','주','노','초','파','남','보'];
  
  for(String x in rainbow){
    print(x);
  }
}
```

#### 로또번호 예제
```dart
import 'dart:math';

void main(){
  List lotto =  Lottonum();
  List my = Mynum();
  int num=0;
  for(int i in lotto){
    for(int j in my){
      if(i==j){
        num++;
        print('당첨번호 : $i');
        break;
      }
    }
  }
  print('총 당첨 개수 : $num');
}


List Lottonum(){
  var random = Random();
  List<int> LottoList = [];
  var num;
  
  for(int i=0; i<6; i++){
    num = random.nextInt(45)+1;
    LottoList.add(num);
  }
  return LottoList;
}

List Mynum(){
  var random = Random();
  List<int> MyList = [];
  var num;
  
  for(int i=0; i<6; i++){
    num = random.nextInt(45)+1;
    MyList.add(num);
  }
  return MyList;
}

```


## 삼항연산자
```dart
value2 = value ? 100 : 200;
```



