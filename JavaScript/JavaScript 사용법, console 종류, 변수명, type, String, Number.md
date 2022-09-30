## JavaScript 사용 방식

### 1. 인라인 방식

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title></title>
  </head>
  <body>
    <button onclick="document.write('hello world')">helo</button>
  </body>
</html>
```

### 2. 외부 방식

```html
<body>
  <p id="one"></p>
  <script src="002.js"></script>
</body>
```

### 3. 내부 방식

```html
<body>
  <p id="one"></p>
  <script>
    document.getElementById("one").innerHTML = "hello <strong>world</strong>";
  </script>
</body>
```

<br>

## console 종류

```JavaScript
console.log("hello"); // 콘솔창에 출력

let data = {
  one: 1,
  two: 2,
  three: 3,
};

console.dir(data); // 객체의 데이터를 확인

console.info("hello world"); // 정보가 되는 메시지를 콘솔에 출력

// 그룹을 만들 수 있다.
console.group("팀원");
console.log("호준");
console.log("유정");
console.log("혜연");
console.group("two");
console.log("태수");
console.log("슬기");
console.groupEnd();
console.log("end");
console.groupEnd();

console.table(data); // 데이터를 테이블로 보여준다.
console.error("정신차렷"); // 에러 메세지를 나타낸다.
console.warn("실행은 한다만, 경고는 읽어봐"); // 경고 메세지를 나타낸다.
```

<br>

## 변수로 사용 가능한 것

```JavaScript
let x = 10;
let y = 100;
x = 15;
console.log(x + y);

// 한글
let 한글변수명 = 100;
console.log(한글변수명 + 한글변수명);

// 특수문자
let $__$ = 548;
let _ = 100; // 반복문 돌 때 의미 없는 변수에 사용
let π = 100;

// 변수명으로 안되는 것
// let 10 = 100; // 숫자
// let 1a = 100; // 숫자가 가장 먼저 앞에 오는 것
```

- 이외에도 예약어로 지정된 키워드(let, const, var, if, else 등)는 변수명으로 지정할 수 없다.

<br>

## JavaScript의 type

`typeof 피연산자` : 피연산자의 자료형을 나타낸다.

```JavaScript
console.log(typeof "hello world"); // string
console.log(typeof 100); // number
console.log(typeof NaN); // number
console.log(typeof true); // boolean
console.log(typeof undefined); // undefined
console.log(typeof Symbol()); // symbol
console.log(typeof null); // object
console.log(typeof []); // object
console.log(typeof {}); // object
console.log(typeof function () {}); // function
console.log(typeof /정규표현식/gi); // object

console.log(10 + 10); // 20
console.log("10" + 10); // 1010
console.log("10" + "10"); // 1010
console.log(10 + "10"); // 1010

// 형변환은 형태를 변경하는, 타입을 변경하는 것을 의미
console.log(Number("10") + Number("10")); // 권장하지 않습니다.
console.log(parseInt("10") + parseInt("10")); // parseInt()를 권장
console.log(String(10) + String(10));
```

**type을 확인하는 이유?**

- 실무에서 보통 변수로 값을 사용하고, 변수의 타입을 확인하기 위해 많이 사용한다.

<br>

### 문자열(String)

```JavaScript
let txt = "ABCDEFGHIJK";
let txt2 = '"hello world"'; // 이스케이프 문자(\), \ 다음 문자가 특수 문자임을 알려준다.
let txt3 = "a\nb\ncde"; // 개행
let txt4 = "a\tb\tcde"; // 탭
let txt5 = "10";
let txt6 = "10.1abc";

console.log(txt + txt); // ABCDEFGHIJKABCDEFGHIJK
console.log(txt[0]); // A
console.log(txt[4] + txt[5] + txt[6]); // EFG
console.log(txt2); // 'hello world'

console.log(parseFloat(txt6));

console.log(typeof txt);
console.log(txt.length);

// 문자열에서 인자로 주어진 문자가 위치하는 인덱스를 반환
console.log(txt.indexOf("B")); // 인자에 정규 표현식이 허락되지 않는다.
console.log(txt.search("F")); // 인자에 정규 표현식이 허용된다.

let regExp = /CD/;
console.log(txt.search(regExp));

//-------------------------------

let txt7 = "abcAHelloBC";
let txt8 = "paullab CEO leehojun CEO";
let regExp2 = /[A-Z]/g;
console.log(txt7.search(regExp2));

// slice(시작인덱스, 종료인덱스) : 시작인덱스부터 (종료인덱스 - 1)까지 반환합니다.
console.log(txt8.slice(1, 3));
console.log(txt8.slice(3, 1)); // 작동 x.
console.log(txt8.slice(2));

// substring(시작인덱스, 종료인덱스) : 시작인덱스부터 (종료인덱스 - 1)까지 반환합니다.
console.log(txt8.substring(1, 3));
console.log(txt8.substring(3, 1)); // 작동 o.
console.log(txt8.substring(2));

// substr(시작위치, 길이) : 시작인덱스부터 길이만큼 반환
// https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/substr
// 명세에서 사라질 수도 있음
console.log(txt8.substr(8, 3));
console.log(txt8.substr(txt8.indexOf("C"), 3));

// replace()
console.log(txt8.replace("CEO", "CTO"));
console.log(txt8.replace(/"CEO"/g, "CTO"));
console.log(txt8.replace(/CEO/g, "CTO"));
console.log(txt8.replaceAll("CEO", "CTO"));

// 대문자, 소문자로 바꾸기
console.log(txt7.toUpperCase());
console.log(txt8.toLowerCase());

// includes() : 인자로 들어간 값이 문자열에 포함되는지 여부를 boolean 값으로 반환
console.log(txt7.includes("H"));
console.log(txt7.includes("E"));

// split()
console.log(txt8.split(" "));
console.log("010-1234-5678".split("-"));

//trim() : 문자열 앞뒤의 공백을 제거한다.
console.log("      abc"); //       abc
console.log("      abc".trim()); // abc
console.log("abc     ".trim()); // abc
console.log("      a b c".trim()); // a b c
```

indexOf()가 배열에서 요소를 못찾으면 -1을 반환한다.

[Array.prototype.indexOf() - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)

```JavaScript
if (txt.indexOf("z") === -1 {
	// 배열에서 요소를 찾지 못했을 때 처리
}
```

> 정규표현식
>
> [RegExr: Learn, Build, & Test RegEx](https://regexr.com/5nvc2)

<br>

## Number

```JavaScript
let n1 = 10000;
let n2 = 10.123123;
let n3 = 31;
let n4 = 1001;
let n5 = 1111; // 무시

let s1 = "1000000000";
let s2 = "1,000,000,000";
console.log(parseInt(n1));
console.log(parseInt(n2));
console.log(parseInt(n3, 2));
console.log(parseInt(n4, 2)); // 뒤에 있는 숫자: 진수
console.log(parseInt(n4, 8));
console.log(parseInt(n5, 2));
console.log(n2.toFixed(3));

console.log("-------");
console.log(Number(true));
console.log(Number(false));
console.log(Number(""));
console.log(Number(" "));

console.log("-------");
console.log(Number("hello"));
console.log(Number("10 20"));
console.log(Number("10     "));
console.log(Number("     10"));
console.log(Number("     10     "));

if (" ") {
  console.log("hello world! - 1"); // hello world! - 1
}

if ("") {
  console.log("hello world! - 2"); // undefined
}

// ---------- Math -----------
console.log(Math.PI);
console.log(Math.max(10, 20, 30, 1, 200, 3));
console.log(Math.min(10, 20, 30, 1, 200, 3));

let data = [10, 20, 30, 40];
console.log(Math.max(data)); // NaN
console.log(Math.max(...data)); // 40

console.log(Math.round(4.7));
console.log(Math.round(4.4));

// ceil(올림)이나 floor(내림)
console.log(Math.floor(Math.random() * 50 + 1));

console.log(Math.sqrt(64)); // 8
console.log(Math.pow(2, 3)); // 8
console.log(Math.pow(2, 4));
```
