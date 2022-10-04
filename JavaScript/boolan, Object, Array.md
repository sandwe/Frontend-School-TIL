# JavaScript 자료형

### let, const, var

- const: 참조 변경 불가
- let: 변경 가능
- var: ES5까지 유일했던 변수 선언 키워드, 더 이상 사용하지 않는 것이 좋다.

**const로 대부분의 값을 표현하라**

코드 리뷰하는 동안 해당 변수가 변경될지 신경쓸 필요가 없다.

```jsx
const rate = 0.1;
const total = 10000;

// 1000줄의 코드

return rate * total; // 1000
```

```jsx
let rate = 0.1;
let total = 10000;

// 1000줄의 코드, 무슨 일이 일어났을지 모름

return rate * total;
```

<br>

## bool

### true로 판별되는 값

- `“ “`
- `“abc”`
- `123`, `-123`
- `Infinity` - 비교 시 많이 사용(최대값, 최소값, 값의 정렬 시 사용)
- **`[]`**
- `{}`

### false로 판별되는 값

- `“”`(빈 문자열)
- `0`
- `NaN`
- `undefined`
- `null` - 비어있는 것을 명시하기 위해 사용

<br>

## 비교 연산자 `===`

- 다른 언어에는 없는 연산자
- JS에서 `==` 로 비교하면 타입이 같지 않아도 같은 값이면 true가 나온다.
- **type까지 고려**해 비교하기 위해 `===` 를 사용한다.
- 견고한 코딩을 위해 `===` 를 권장한다.

<br>

## 논리 연산자 `&&, ||, !, !!`

- `!!` : 다른 타입의 값을 boolean 타입으로 변환

### 단락 평가

- ex) 회원가입 여부

```JavaScript
회원가입여부 = !!(username && pw);
회원가입여부 = !(!username || !pw); // 드모르간의 법칙, 코드를 줄일 때 사용된다.
회원가입여부 = !!pw && !!username;
```

<br>

## 암묵적 형변환

### 숫자로 형변환 `+`

```JavaScript
+false; // 0
+"100" + 10; // 110
```

- 종종 사용된다.

### 문자로 형변환

```jsx
1 + ""; // '1'
```

> 암묵적 형변환은 의도를 파악하기 어려우므로 많이 사용하지 않는 것이 좋다.

<br>

## 할당 연산자

```JavaScript
let a = 10;
a = a + 10; // =가 우선순위가 낮아 덧셈 연산 후 할당된다.
// a += 10;
console.log(a); // 20
```

<br>

## Object

### 특정 프로퍼티 값 읽기

- 대괄호 표기법안에서는 문자열을 **따옴표**로 묶어야 한다.

```jsx
let newUser = {
  id: "abc",
  pw: "1234", //  실제로는 해시 생성해서 pw 관리, https://www.convertstring.com/ko/Hash/MD5
  name: "aaaa",
  email: "abcd@gmail.com",
  active: true, // 휴면계정 관리
};

console.log(newUser["id"]);
console.log(newUser.id);
```

<br>

### 함수에도 프로퍼티를 추가할 수 있다.

```jsx
function sum(x, y) {
  return x + y;
}
console.log(sum);
console.log(typeof sum);

sum.value = "abc"; // 함수에도 프로퍼티 키, 값을 넣어서 사용할 수 있다.
console.dir(sum);
```

<br>

### 객체의 key, value 뽑아내기

```JavaScript
// key와 value만 뽑아내기
console.log(Object.keys(newUser)); // 키만
console.log(Object.values(newUser)); // 값만
console.log(Object.entries(newUser)); // 키와 값 둘다
```

**Map을 사용하면 메서드로 바로 사용 가능하다.**

```JavaScript
const newUser = new Map();

newUser.keys();
newUser.values();
```

**Object.keys랑 Object.prototype.tostring() 처럼 prototype 붙고 안붙고의 차이는 뭘까?**

<br>

### 스프레드(Spread) 문법

- 객체의 값을 변경해본다.

```JavaScript
let newUser = {
  id: "abc",
  pw: "1234", //  실제로는 해시 생성해서 pw 관리, https://www.convertstring.com/ko/Hash/MD5
  name: "aaaa",
  email: "abcd@gmail.com",
  active: true, // 휴면계정 관리
};

let userInfoUpdate = {
  name: "cat",
  email: "abc@naver.com",
};

newUser["name"] = userInfoUpdate["name"];
newUser["email"] = userInfoUpdate["email"];
```

- **스프레드 문법**을 사용하여 값을 변경해본다.

```jsx
newUser = {...newUser, ...userInfoUpdate};
```

**객체를 복사해 복사한 객체의 값을 변경하고 싶을 때는?**

- 아래에서는 기존 객체와 복사한 객체 둘다 값이 변경되는 문제가 발생한다.

```JavaScript
let newUser2 = newUser;
newUser2["id"] = "helloworld";
console.log(newUser);
console.log(newUser2);
```

- **스프레드 문법**을 사용하면 원본을 건드리지 않고 복사된 객체의 값을 변경할 수 있다.

```jsx
let newUser2 = {...newUser};
newUser2["id"] = "helloworld";
console.log(newUser);
console.log(newUser2);
```

<br>

## Array

### 배열 선언 방법

```jsx
let 과일 = ["사과", "수박", "복숭아", "딸기", "바나나"];
let 과일 = new Array(5);
let 과일 = new Array("사과", "수박", "복숭아", "딸기", "바나나");
```

<br>

### 원본 배열 수정 없이 값을 수정하고 싶은 경우

- 스프레드 문법을 사용해 새로운 객체를 만들고, 새로운 객체를 수정한다.

```JavaScript
let x = [10, 20, 30, 40];
console.log([...x].pop()); // 40
console.log(x); // [10, 20, 30, 40]

let y = [...x];
y.pop();
console.log(y); // [10, 20, 30]
```

```JavaScript
let data = [10, 20, 30];
console.log(data.length); // 3
let data2 = new Array(5);
console.log(data2); // [empty x 5]
let data3 = new Array("사과", "수박", "복숭아", "딸기", "바나나");
console.log(data3); // ['사과', '수박', '복숭아', '딸기', '바나나']
```

<br>

### Array 메서드

**`splice()`**

- 배열의 기존 요소를 삭제 또는 교체하거나 새 요소를 추가하여 배열의 내용을 변경한다.

```JavaScript
// 아이템 삭제
data3.splice(3, 1);
console.log(data3); // ['사과', '수박', '복숭아', '바나나']

// 아이템 추가
data3.splice(3, 0, "한라봉");

// 아이템 삭제 후 추가
data3.splice(3, 1, "제주감귤");
console.log(data3); // ['사과', '수박', '복숭아', '제주감귤']

data3.splice(3, 0, ["포도", "체리"]);
console.log(data3);
```