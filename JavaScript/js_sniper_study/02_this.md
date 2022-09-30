# this

## this 란?

- 함수를 호출하는 객체
- 함수를 재사용하기에 유용하다.
- this를 사용해 함수를 호출함으로써 글로벌 함수를 여러 객체에서 재사용하기가 편해진다.

  ```JavaScript
  function menuGlobal() {
  console.log('오늘 저녁은 ' + this.name);
  }

  var myDinner = {
  name: '김치찌개',
  menu: menuGlobal
  }

  myDinner.menu(); // 오늘 저녁은 김치찌개

  var yourDinner = {
  name: '된장찌개',
  menu: menuGlobal
  }

  yourDinner.menu(); // 오늘 저녁은 된장찌개
  ```

<br>

## this 제어하는 함수

> 일반적으로 this 값은 자동으로 할당되지만, 상황에 따라 제어할 수 있어야 한다.

### 1. call()

- this의 값을 바꾸거나 함수 실행 시 사용할 인수를 전달한다.

```JavaScript
function menuGlobal(item) {
  console.log('오늘 저녁은 ' + item + this.name);
}

var myDinner = {
  name: '김치찌개'
};

var yourDinner = {
  name: '된짱찌개'
};

// myDiner 객체를 실행하고, '묵은지'라는 인자값을 함수에 전달한다.
menuGlobal.call(myDinner, '묵은지'); // 오늘 저녁은 묵은지김치찌개
menuGlobal.call(yourDinner, '차돌');

```

<br>

### 2. apply()

- 함수 실행 시 인수를 배열로 묶어 전달한다.

```JavaScript
function menuGlobal(item1, item2) {
  [item1, item2].forEach(function(el) {
    console.log('오늘 저녁은 ' + el + this.name);
  }, this); // forEach문 안에서 this를 전달받기 위해 this를 선언해야 한다.
}

var myDinner = {
  name: '김치찌개'
};

var yourDinner = {
  name: '된짱찌개'
};

menuGlobal.apply(myDinner, ['묵은지', '차돌']);
menuGlobal.apply(yourDinner, ['두부', '애호박']);

```

> 📓 call()과 apply()의 차이
>
> call: 함수에 인수를 하나 하나 전달한다.  
> apply: 전달할 인수를 배열로 묶어 한번에 전달한다. 따라서, 호출할 객체와 배열 총 2개의 인수만 필요하다.

<br>

### 3. bind()

- ES5에서 추가됨
- this 값을 어디서 사용하든 호출 객체가 바뀌지 않게 고정시킨다.

```JavaScript
function menuGlobal(item) {
  console.log('오늘 저녁은 ' + item + this.name);
}

var myDinner = {
  name: '김치찌개'
};

var yourDinner = {
  name: '된짱찌개'
};

// menuGlobal 함수가 바라보는 객체가 myDinner로 고정된 새로운 함수가 변수에 할당된다.
var menuGlobalForMe = menuGlobal.bind(myDinner);
var menuGlobalForYou = menuGlobal.bind(yourDinner);

menuGlobalForMe('묵은지'); // 오늘 저녁은 묵은지김치찌개
menuGlobalForMe('삼겹살'); // 오늘 저녁은 삼겹살된장찌개

// myDinner 객체에 키와 메서드 추가
myDinner.menuMine = menuGlobalForYou;
myDinner.menuMine('묵은지');
```

<br>

## 화살표 함수에서의 this

- 화살표 함수에서의 this는 일반적인 this처럼 함수를 호출한 객체를 할당하지 않고, **바로 상위 스코프의 this를 할당**한다.

```JavaScript
function menuGlobal(item1, item2) {
  // forEach문의 상위 스코프의 this는 myDinner
  // 화살표 함수를 사용함으로써 전역 객체를 바라보던 this를 상위 스코프를 바라보도록 바꾼다.
  [item1, item2].forEach((el) => {
    console.log('오늘 저녁은 ' + el + this.name);
  });
}

var myDinner = {
  name: '김치찌개'
};

var yourDinner = {
  name: '된짱찌개'
};

menuGlobal.apply(myDinner, ['묵은지', '차돌']);
```
