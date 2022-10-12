# this

- 최신의 코드를 사용할 수 있는 **엄격모드와 비엄격 모드**에서 동작의 차이가 발생한다.

> 📓 어떤 버전에서는 `use strict` 를 사용하고, 어떤 버전에서는 `use strict` 를 사용하지 않는 것은 일관성에 맞지 않다.

<br>

## this란?

- **자신을 호출한 객체에 따라 this가 동적으로 결정된다**

```JavaScript
function a() {
  console.log(this);
}

// 함수 a는 전역 객체 window의 메서드이다.
a();
// window.a();
```

```JavaScript
let test = {
  one: 1,
  two: 2,
  three: function () {
    console.log(this);
  },
};

test.three();
let test2 = test.three;
test2(); // test2는 전역 객체 window의 메서드이다.
```

```JavaScript
// this 가 클릭한 버튼을 가리킨다.
<body>
    <button id="btn1">클릭1</button>
    <button id="btn2">클릭2</button>

    <script>
      let test1 = {
        one: 1,
        two: 2,
        three: function () {
          console.log(this);
        },
      };
      let test2 = test1.three;

      let btn1 = document.getElementById("btn1");
      btn1.addEventListener("click", test1.three);
      let btn2 = document.getElementById("btn2");
      btn2.addEventListener("click", test2);
    </script>
  </body>
```

- 전역 변수인 name의 값 'Hero'를 가리킨다.

```JavaScript
function sayName() {
  console.log(this.name);
}

var name = "Hero";

let peter = {
  name: "Peter Parker",
  sayName: sayName,
};

let bruce = {
  name: "Bruce Wayne",
  sayName: sayName,
};

sayName(); // Hero
```

```JavaScript
// 함수 안의 함수를 호출했을 때도 this는 모두 전역 객체를 가리킨다.

function a() {
  console.log(this);
  function b() {
    console.log(this);
  }
  b();
}
a();
```

<br>

### this 사용 예시

```JavaScript
let 호텔 = [
  {
    이름: "하나호텔1",
    방의개수: 50,
    예약자수: 25,
    남은방의개수: function () {
      return this.방의개수 - this.예약자수;
    },
  },
  {
    이름: "하나호텔2",
    방의개수: 40,
    예약자수: 25,
    남은방의개수: function () {
      return this.방의개수 - this.예약자수;
    },
  },
  {
    이름: "하나호텔3",
    방의개수: 30,
    예약자수: 25,
    남은방의개수: function () {
      return this.방의개수 - this.예약자수;
    },
  },
  {
    이름: "하나호텔",
    방의개수: 25,
    예약자수: 25,
    남은방의개수: function () {
      return this.방의개수 - this.예약자수;
    },
  },
];

// 호텔[0]["방의개수"] - 호텔[0]["예약자수"];
호텔[0]["남은방의개수"]();
```

<br>

### this 값을 사용자의 의도대로 조작하기

- `apply(), call(), bind()`를 사용하면 this를 조작하거나 고정할 수 잇따.

`call()` 메서드

특정한 object나 다른 변수에서 사용한 것을 가져와 재사용하기 위해서

```JavaScript
var peter = {
  name: "Peter Parker",
  sayName: function () {
    console.log(this.name);
  },
};

var bruce = {
  name: "Bruce Wayne",
};
peter.sayName.call(bruce); // Bruce Wayne

// peter.sayName.call(bruce) 의 결과는 무엇이 될지 생각해 봅시다.
```

다음과 같이 인자를 전달할 수 있다.

```JavaScript
var peter = {
  name: "Peter Parker",
  sayName: function (감탄사) {
    console.log(this.name + 감탄사);
  },
};

var bruce = {
  name: "Bruce Wayne",
};
peter.sayName.call(bruce, "!");
```

`apply()` 메서드

- `call()`과 동작은 동일하고, 인자를 배열로 전달한다.

```JavaScript
var peter = {
  name: "Peter Parker",
  sayName: function (is, is2) {
    console.log(this.name + " is " + is + " or " + is2);
  },
};

var bruce = {
  name: "Bruce Wayne",
};

peter.sayName.apply(bruce, ["batman", "richman"]);

/* peter.sayName.apply(bruce, ['batman', 'richman']) 의 결과가 무엇이 될지 생각해보고
apply 를 call로 바꾸어 호출했을 때와 비교해 봅시다. */
```

`bind()` 메서드

- `this` 가 고정된 새로운 함수를 반환한다.

```JavaScript
function sayName(){
  console.log(this.name);
}

var bruce = {
  name: 'bruce',
  sayName : sayName
}

var peter = {
  name : 'peter',
  sayName : sayName.bind(bruce)
}

peter.sayName();
bruce.sayName();

```
