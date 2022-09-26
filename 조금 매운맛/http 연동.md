## 설치하기
* yaml에 설치
* import 'package:http/http.dart' as http;
* android-app-src-main-AndroidMainfest에 <uses-permission android:name="android.permission.INTERNET" />

## url에 있는 값 불러오기
```dart 
import 'package:http/http.dart' as http;
import 'dart:convert';

void initState() {
    // TODO: implement initState
    super.initState();
    fetchData();
  }

  void fetchData() async{
    http.Response response = await http.get('https://samples.openweathermap.org/data/2.5/weather?q=London&appid=b1b15e88fa797225412429c1c50c122a1');

    if(response.statusCode == 200){
      String jsonData = response.body;
      var myJson = jsonDecode(jsonData)['weather'][0]['description'];
      print(myJson);

      var wind = jsonDecode(jsonData)['wind']['speed'];
      print(wind);

      var id = jsonDecode(jsonData)['id'];
      print(id);
    }
  }
```
