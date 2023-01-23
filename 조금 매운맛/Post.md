```dart
import 'package:http/http.dart' as http;

_postRequest() async {
    String url = 'http://example.com/login';
    
    // body에 들어갈 변수 정의
    final map = jsonEncode({
        'user_id': 'user_id_value',
        'user_pwd': 'user_pwd_value',
  });
  
    http.Response response = await http.post(
        url,
        // 헤더가 없으면 안보내도 됨!!
        headers: <String, String> {
            'Content-Type': 'application/x-www-form-urlencoded',
        },
        // 보낼 값
        body: map,
    );
}

```
