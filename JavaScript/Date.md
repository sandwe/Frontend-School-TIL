# 내장 객체 Date

> 날짜 및 시간과 관련된 메서드를 제공해준다.

## Date 객체 생성 및 Date 객체 메서드

```js
let d = new Date();
d; // Thu Oct 13 2022 15:26:33 GMT+0900 (한국 표준시)
d.getDate(); // 13
d.getMonth(); // 9, 월은 0부터 시작한다.
d.getDay(); // 4 (목), 일요일부터 0으로 시작한다.
d.getHours();
d.getMinutes();
d.getSeconds();
d.getFullYear():
```

- 요일 뽑기

```js
let d = new Date();

switch (d.getDay()) {
  case 0:
    console.log("일요일");
    break;
  case 1:
    console.log("월요일");
    break;
  case 2:
    console.log("화요일");
    break;
  case 3:
    console.log("수요일");
    break;
  case 4:
    console.log("목요일");
    break;
  case 5:
    console.log("금요일");
    break;
  case 6:
    console.log("토요일");
    break;
    defalut: console.log("날짜의 양식이 잘못되었습니다.");
    break;
}
```

- UTC와 today의 지정 로캘 KST와의 차이는 **-9시간**이다.

```js
today = new Date();
today.getTimezoneOffset() / 60;
```

<br>

### 인수로 값을 넣어 날짜 지정하기

```js
// 2023년 1월
new Date(2023, 0);
new Date(2023, 0, 20, 5);
new Date("2023/1/20/10:00");
```

```js
today.toString(); // -> Fri Jul 24 2020 12:30:00 GMT+0900 (대한민국 표준시)
today.toTimeString(); // -> 12:30:00 GMT+0900 (대한민국 표준시)

today = new Date("2023/1/20/10:00:00");
today.toString();
today.toISOString();
today.toISOString().slice(0, 10);
today.toISOString().slice(0, 10).replace(/-/g, "");

//http://www.w3bai.com/ko/tags/ref_language_codes.html#gsc.tab=0
//http://www.w3bai.com/ko/tags/ref_country_codes.html#gsc.tab=0
today.toLocaleString("ko-KR"); // -> 2020. 7. 24. 오후 12:30:00
today.toLocaleString("en-US"); // -> 7/24/2020, 12:30:00 PM
today.toLocaleString("ja-JP"); // -> 2020/7/24 12:30:00

const dayNames = ["(일요일)", "(월요일)", "(화요일)", "(수요일)", "(목요일)", "(금요일)", "(토요일)"];
// getDay 메서드는 해당 요일(0 ~ 6)을 나타내는 정수를 반환한다.
const day = dayNames[today.getDay()];

const year = today.getFullYear();
const month = today.getMonth() + 1;
const date = today.getDate();
let hour = today.getHours();
let minute = today.getMinutes();
let second = today.getSeconds();
const ampm = hour >= 12 ? "PM" : "AM";
```
