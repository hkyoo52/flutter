## weather API
* openwether 사이트 들어가기
* API - current api - doc - How to make an API call
* 우리가 넣을 검색창에 API call 넣기
* 홈페이지에서 내정보에 API key 넣기

```dart
const apiKey = 'b2a769dd9206a9a735f9ffd0d18e141a';

// latitude, apiKey 등 변수 const!!!로 저장하고 사용
Network network = Network('https://api.openweathermap.org/data/2.5/weather?lat=$latitude3&lon=$longitude3&appid=$apiKey');
```

## 데이터 전달받는법!!
* 생성자를 통해서 데이터를 받음!!
* 그 후 메서드를 통해서 받은 데이터를 변형해서 사용한다!!
```dart
class WeatherScreen extends StatefulWidget {
  WeatherScreen({this.parseWeather});
  final parseWeather;

  @override
  State<WeatherScreen> createState() => _WeatherScreenState();
}

class _WeatherScreenState extends State<WeatherScreen> {

  String? cityName;
  double? temp;

  @override
  void initState() {
    // TODO: implement initState
    super.initState();
    updateData(widget.parseWeather);
  }

  void updateData(dynamic weatherData){
    temp = weatherData['main']['temp'];
    cityName = weatherData['name'];
  }
```

* 그 아래부터는 자유롭게 temp랑 cityName 사용!!
