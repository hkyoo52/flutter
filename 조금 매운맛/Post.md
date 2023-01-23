```dart
import 'package:http/http.dart' as http;

_postRequest() async {
    String url = 'http://example.com/login';

    http.Response response = await http.post(
        url,
        headers: <String, String> {
            'Content-Type': 'application/x-www-form-urlencoded',
        },
        // 보낼 값
        body: <String, String> {
            'user_id': 'user_id_value',
            'user_pwd': 'user_pwd_value'
        },
    );
}

```
