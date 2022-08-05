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











