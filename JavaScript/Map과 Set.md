# Map과 Set

- **IE 10 이하**에서 사용 못한다. (바벨을 사용하면 사용 가능하지만 프로젝트에 따라 바벨을 사용하지 않을 수도 있다.)
- IE에서 지원하지 않는 것을 지원하게 해주는 폴리필

[폴리필](https://ko.javascript.info/polyfills)

<br>

## Map(맵)

- Object 자료형을 업데이트하는 것은 힘들다.
- **키-값 쌍**을 가지는 객체 자료형으로 Object 자료형의 단점을 해결하기 위해 만들어졌다.

```JavaScript
let m = new Map();
m.set("하나", 1).set("둘", 2).set("셋", 3).set("넷", 4);

console.log(m); // Map(4) {'하나' => 1, '둘' => 2, '셋' => 3, '넷' => 4}
m.set(true, "트루");
console.log(m.get(true));

m.set([1, 2], "리얼리?");
console.log(m.get([1, 2])); // undefined, 이렇게는 호출 불가능
// 각 객체가 다른 주소값을 가지기 때문이다.
```

- Map에 해당하는 key 값이 있는지 확인 - `has()`

```JavaScript
m.has("하나"); // true
```

- Map에 값을 제거하기 - `delete()`

```JavaScript
m.delete("하나");
m.has("하나"); // false
```

- Map 크기 구하기 - `size`

```jsx
m.size; // 5
```

<br>

### Map이 아닌 자료형을 Map으로 만들기

```JavaScript
// Map - Object 간의 형변환
let 맵 = new Map(Object.entries({one: 1, two: 2}));
let 오브젝트 = Object.fromEntries(m);
```

```JavaScript
let data1 = new Map(Object.entries({one: 1, two: 2}));
let data2 = new Map([
  ["one", 1],
  ["two", 2],
]);

let data3 = new Map({one: 1, two: 2}); // X
let data4 = new Map("hello world"); // X
let data5 = new Map([10, 20, 30, 40]); // X
```

<br>

## Set(셋)

- 모든 타입의 값을 저장하는 객체 자료형
- 이때 객체 안의 값은 **중복을 허용하지 않는다.**

```JavaScript
let s = new Set("abcdeeeeeeeee");
console.log(s);
console.log(s.size); // 5

// Set에 값을 추가하기
s.add("f");
console.log(s);

// Set을 순환하기
for (var variable of s) {
  console.log(variable);
}

// 값이 배열인 경우
let ss = new Set("abcdeeeeeeeee".split(""));
console.log(ss);

// Set의 값을 제거하기
ss.delete("b");

// Set의 값을 확인하기
console.log(ss.has("a"));

// Set의 모든 값을 제거하기
ss.clear;
console.log(ss);


```

`Set` 사용하여 교집합, 합집합, 차집합 구하기

```JavaScript
let a = new Set("abc");
let b = new Set("cde");
// 교집합
let cro = [...a].filter((value) => b.has(value));
// 합집합
let union = new Set([...a].concat(...b));
// 차집합
let dif = new Set([...a].filter((x) => !b.has(x)));
let dif2 = [...a].filter((x) => !b.has(x));
```
