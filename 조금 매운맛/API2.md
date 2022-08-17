## weather API
* openwether 사이트 들어가기
* API - current api - doc - How to make an API call
* 우리가 넣을 검색창에 API call 넣기
* 홈페이지에서 내정보에 API key 넣기

```dart
const apiKey = 'b2a769dd9206a9a735f9ffd0d18e141a';

Network network = Network('https://api.openweathermap.org/data/2.5/weather?lat=$latitude3&lon=$longitude3&appid=$apiKey');
```
