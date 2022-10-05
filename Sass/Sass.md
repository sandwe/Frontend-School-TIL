# Sass

## **Sass(Syntactically Awesome Stylesheets)나 SCSS 쓰는 이유**

- 스타일시트가 점점 더 커지고 복잡해지면 유지보수가 어렵다.
- Sass안에 있는 변수, 네이스팅, 믹스인, 가져오기, 상속, 내장기능 등 css에는 없는 편의 기능들이 있다.
- 코드 재사용이 가능하다.

<br>

## **Sass란**

Sass는 CSS로 컴파일 되는 스타일 시트 확장 언어이며 CSS 전처리기의 하나이다. 브라우저가 Sass를 직접 로딩하는 것이 아니라 개발은 Sass를 기반으로 한 후, CSS로 익스포트하는 과정을 거친다.

- 브라우저가 Sass파일을 직접 읽지 못하기 때문에 일반 CSS로 컴파일해야 합니다.
- 웹업계에서 실제 많이 사용하는 전처리기입니다.

<br>

### Sass 기술방식 2가지

- **.sass 방식**과 **.scss 방식** → 다른 파일 확장자를 사용합니다.
- 일반적으로 CSS와 좀 더 유사한 중괄호를 사용하는 SCSS를 사용한다.

```scss
//SCSS
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```

```sass
//Sass
$font-stack: Helvetica, sans-serif
$primary-color : #333

body
	font: 100% $font-stack
	color: $primary-color
```

> ❓ 실무에서는 node 환경으로 Sass 구축 후 cli 환경에서 컴파일 되도록 명령어를 사용해야 한다.

<br>

## 중첩(Nesting)

- 중첩을 사용해 HTML의 계층 방식과 동일하게 CSS를 중첩시켜 작성할 수 있다. 따라서, CSS 구조화 되어 가독성이 높아지며 유지보수가 편리해진다.

**선택자 nesting**

```html
<!--HTML-->

<nav>
  <!--nav안에 ul이 중첩되어 있고-->
  <ul>
    <!--ul안에 세가지 li가 중첩되어 있다.-->
    <li>one</li>
    <li>two</li>
    <li>three</li>
    <li>four</li>
  </ul>
</nav>
```

```scss
//Scss
//Scss에서도 HTML처럼 계층구조로 스타일을 적용할 수 있다.
nav {
  background: #c39bd3;
  padding: 10px;
  height: 50px;
  ul {
    display: flex;
    list-style: none;
    justify-content: flex-end;
    li {
      color: white;
      margin-right: 10px;
    }
  }
}
```

**속성 nesting**

```scss
//Scss
.add-icon {
  background : {
    image: url("./assets/arrow-right-solid.svg");
    position: center center;
    repeat: no-repeat;
    size: 14px 14px;
  }
}
```

```css
/*CSS*/
.add-icon {
  background-image: url("./assets/arrow-right-solid.svg");
  background-position: center center;
  background-repeat: no-repeat;
  background-size: 14px 14px;
}
```

<br>

### **중첩을 사용하는 이유?**

기존 CSS는 부모에게 상속된 자식 요소에게 스타일을 적용하려고 할 때마다 **최상위 선택자를 반복 선언해야 한다.** 하지만 중첩을 사용하면 최상위 선택자를 한번만 선언하여도 자식 선택자에게 스타일을 적용할 수 있게 되어 코드 반복을 줄일 수 있다.

```css
/*CSS*/

.info-list div {
  display: flex;
  font-size: 14px;
  color: #4f4f4f;
}

.info-list div dt {
  font-weight: 700;
  margin-right: 7px;
}
/*기존 CSS : info-list에 있는 자식과 자손에게 스타일을 적용하려고 할때마다 
부모 선택자를 적어준다*/
```

```scss
//Scss

.info-list {
  div {
    display: flex;
    font-size: 14px;
    color: #4f4f4f;
    dt {
      font-weight: 700;
      margin-right: 7px;
    }
  }
}
// 중첩을 사용하여 부모선택자를 한번만 사용한다.
// 그리고 코드를 봤을 때 info-list div tag안에 dt가 들어있음을 한눈에 알아볼 수 있다
```

⚠️ 하지만 지나친 중첩된 코드는 삼가하는 것을 권장한다. 너무 깊이 중첩되면 코드를 보기가 어렵고, 컴파일 했을 경우 불필요한 선택자를 선택할 수 있다.

<br>

### ampersand (앰퍼샌드, &)

`&`는 상위에 있는 부모 선택자를 가리킨다.

1. `&`을 이용하여 after, hover 등의 가상요소, 가상클래스, class나 id 셀렉터 등을 참조할 수 있다.

```scss
//Scss
.box {
  &:focus {
  } // 가상선택자
  &:hover {
  }
  &:active {
  }
  &:first-child {
  }
  &:nth-child(2) {
  }
  &::after {
  } // 가상요소
  &::before {
  }
}
```

```css
/*CSS*/
.box:focus {
} /* 가상선택자 */
.box:hover {
}
.box:active {
}
.box:frist-child {
}
.box:nth-child(2) {
}
.box::after {
} /* 가상요소 */
.box::before {
}
```

2. 아래 예시와 같이 **공통 클래스명**을 가진 선택자들을 중첩시킬 수 있다.

```scss
//Scss
.box {
  &-yellow {
    background: #ff6347;
  }
  &-red {
    background: #ffd700;
  }
  &-green {
    background: #9acd32;
  }
}
//.box라는 이름이 같기 때문에 &를 사용해 중첩구조로 만들 수 있다
```

```css
/*CSS*/
.box-yellow {
  background: #ff6347;
}
.box-red {
  background: #ffd700;
}
.box-green {
  background: #9acd32;
}
```

<br>

### @at-root

- 선택자 앞에 `@at-root` 키워드를 사용하면 중첩에서 벗어난다.
- `중첩된 선택자`에게만 사용 가능하다.

```scss
//Scss
.article {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 10px;
  .article-content {
    font-size: 14px;
    opacity: 0.7;
    @at-root i {
      opacity: 0.5;
    }
  }
}
```

```css
/*CSS*/
.article {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 10px;
}
.article .article-content {
  font-size: 14px;
  opacity: 0.7;
}
/*중첩을 빠져나온 것을 확인할 수 있다.*/
i {
  opacity: 0.5;
}
```

<br>

## 변수

### **변수 생성하기**

변수를 만들 때는 `$` 기호를 사용해 스타일을 적용할 값(색상, 폰트 사이즈, 이미지url)을 지정한다.

```scss
//**$변수 : 값**
$bgColor: #fff;
```

css 전체에 걸쳐 반복되는 값들을 정의하면 편하게 스타일링을 할 수 있다.

```scss
//색상
$red: #ee4444;
$black: #222;
$bg-color: #3e5e9e;
$link-color: red;
$p-color: #282a36;

//폰트사이즈
$font-p: 13px;
$font-h1: 28px;

//폰트
$base-font: "Noto Sans KR", sans-serif;

body {
  background-color: $bg-color;
  font-size: $font-p;
  font-family: $base-font;
}

h1 {
  font-size: $font-h1;
  color: $black;
}

p {
  font-size: $font-p;
  color: $black;
}

a {
  color: $link-color;
}
```

<br>

### **변수 type**

- type ⇒ numbers, strings, color, booleans, lists, null이 있다.
- number : 1, .82, 20px, 2em 등
- string: "./images/a.png", bold, left, uppercase 등
- color : green, #FFF, rgba(255,0,0,.5) 등
- boolean : true, false
- null
- lists

  ```scss
  //sass 공식문서
  $font-size : 10px 12px 16px; //폰트사이즈 리스트
  $image-file : photo_01, photo_02, photo_03 //이미지 파일명 리스트

  //아래와 같은 형태로 사용(순회도 가능) - ruby sass
  nth(10px 12px 16px, 2); // 12px
  nth([line1, line2, line3], -1); // line3
  ```

- maps

  ```scss
  //sass 공식문서
  $font-weights: ("regular": 400, "medium": 500, "bold": 700); //글자 굵기 리스트

  //아래와 같은 형태로 사용 - ruby sass
  map-get($font-weights, "medium"); // 500
  map-get($font-weights, "extra-bold"); // null
  ```

<br>

### Lists, Maps

**Lists**

- 리스트는 순서가 있는 값으로, 값마다 인덱스를 가지고 있다.
- lists의 요소들은 쉼표`,` , 공백 또는 일관성이 있는 `/`로 구분하여 생성하고, 다른 타입의 변수들과 다르게 특수 괄호를 사용하지 않아도 lists로 인식한다.
- 빈 lists를 만들 때나 lists에 들어있는 값이 하나일 때는 `[ ]` 나 `( )` 를 사용한다.

lists에 들어있는 값의 index는 0부터 시작하지 않고 1부터 시작합니다.

```scss
$sizes: 40px, 50px, 80px;
$valid-sides: top, bottom, left, right;
```

**lists 관련 내장함수**

`append(list,value,[separator])`, `index(list,value)`, `nth(list, n)` 등

- `append(list,value,[separator])` : lists의 값을 추가하는 함수
- `index(list,value)` : lists의 값에 대한 인덱스를 리턴하는 함수
- `nth(list, n)` : lists의 인덱스에 해당하는 값을 리턴하는 함수

**예시**

`nth()`를 사용해서 lists의 인덱스에 해당하는 값을 불러옵니다.

```scss
// Scss
$valid-sides: left, center, right;

.screen-box {
  text-align: nth($valid-sides, 1);
}
```

```css
/*CSS*/
.screen-box {
  text-align: left;
}
```

**Maps**

maps는 `( )` 괄호 안에 키:값의 형태로 저장하여 사용합니다. 키와 값을 정의할 때, 키는 고유해야 하지만 키에 해당하는 값은 중복이 가능합니다. 변수를 각각 선언하는 대신, 관련 있는 변수들을 한번에 모아 maps로 만들어서 사용할 수 있습니다.

**map관련 내장함수**

`map-get(map,key)`, `map-keys(map)`, `map-values(map)` 등이 있습니다.

- `map-get(map,key)` : 키에 해당하는 값을 값을 리턴하는 함수
- `map-keys(map)` : map에 들어있는 키(key) 전부를 리턴하는 함수
- `map-values(map)` : map에 들어있는 값(value) 전부를 리턴하는 함수

**예시**

`map-get`을 사용하여 map안의 키에 해당되는 값을 불러온다.

```scss
// Scss
$font-sizes: ("h1": 45px, "h2": 19px, "p": 16px);

section {
	h2 {
		font-size : map-get($font-sizes, "h2");// 19px
	}
}
map-get($font-size, "h3");// null
```

```css
/*CSS*/
section h2 {
  font-size: 19px;
}
```

※ lists와 maps 뿐만 아니라 string이나 number같은 타입들도 function을 가지고 있다.

[Sass String Functions](https://www.w3schools.com/sass/sass_functions_string.php)

<br>

### 변수의 Scope(변수의 유효범위)

**지역변수**

- 변수를 선언한 자기자신을 감싸는 중괄호 { } 안에서 사용된다. 이보다 하위 단계에 있는 중괄호에서도 사용할 수 있다.

```scss
.info {
  $line-normal: 1.34; // 지역변수
  font-size: 15px;
  line-height: $line-normal;
  text-align: right;
  span {
    line-height: $line-normal;
  }
}
```

**전역변수**

- 파일 가장 윗부분에 정의하여 파일 내에 어디서든지 사용가능한 변수이다.
- 전역변수를 파일로 만들어서 사용하는 경우, 메인 scss파일(ex. style.scss 파일)에서 전역변수파일을 다른 파일들보다 윗부분에 위치시킨다.

```scss
//Scss
$font-p: 15px; // 전역변수

.main-box {
  p {
    font-size: $font-p;
  }
  a {
    font-size: $font-p;
    color: blue;
    text-decoration: none;
  }
}
```

```css
/*CSS*/
.main-box p {
  font-size: 15px;
}

.main-box a {
  font-size: 15px;
  color: blue;
  text-decoration: none;
}
```

- `!global`을 사용하여 local 변수를 global 변수로 만들어 사용할 수도 있다.

```jsx
$mycolor: #ffffff !global;
```

[Variables](https://sass-lang.com/documentation/variables)

<br>

### Operator

**비교연산자 (숫자형)**

<aside>
💡 debug는 VSC Extension에서는 작동하지 않는다.

</aside>

1️⃣ **< , <=, >, >=**

```scss
// Sass 공식문서
@debug 100 > 50; // true
@debug 10px < 17px; // true
@debug 96px >= 1in; // true
@debug 1000ms <= 1s; // true
```

```scss
// $size: 1920px;
$size: 1080px;

.responsive {
  @if $size >= 1920px {
    width: 200px;
    height: 200px;
    background-color: green;
  } @else if $size >= 1080px {
    width: 100px;
    height: 100px;
    background-color: blue;
  }
  // @if $size < 1920px and $size >= 1080px {
  //     width: 150px;
  //     height: 150px;
  //     background-color: green;
  // }
}
```

⚠️ERROR : 비교하거나 연산하는 값의 단위가 일치하지 않으면 에러가 발생한다. 그러나, 단위가 없는 숫자와 일반 숫자와 비교하는 경우에는 에러가 발생하지 않는다. (그렇지 않은 경우도 있음)

```scss
//Sass 공식문서

@debug 100px > 10s;
// Error: Incompatible units px and s

@debug 100 > 50px; // true
@debug 10px < 17; // true
// Not Error
```

2️⃣ **==, != (모든 타입)**

변수의 타입에 따라 `true`, `false`결과가 약간씩 다릅니다.( `==` 의 연산자의 경우를 말합니다. `!=` 연산자는 반대의 값을 반환합니다.)

- 색상, 숫자, 문자열: 값과 단위가 동일한 경우, 값의 단위를 서로 변환했을 때 일치하는 경우 `true`를 반환
- 맵: 키와 값이 모두 동일한 경우/ 리스트: 들어있는 값들이 모두 동일한 경우 `true`를 반환
- boolean: `true == true`, `false == false`,`null == null` 처럼 각자 자신과 비교할 때만 `true` 반환

```scss
//Sass 공식문서

// 숫자
@debug 1px == 1px; // true
@debug 1px != 1em; // true
@debug 1 != 1px; // true
@debug 96px == 1in; // true

// 문자
@debug "Poppins" == Poppins; // true
@debug "Open Sans" != "Roboto"; // true

// 색상
@debug rgba(53, 187, 169, 1) == #35bba9; // true
@debug rgba(179, 115, 153, 0.5) != rgba(179, 115, 153, 0.8); // true

// 리스트
@debug (5px 7px 10px) != (5px, 7px, 10px); // true
@debug (5px 7px 10px) != [5px 7px 10px]; // true
@debug (5px 7px 10px) == (5px 7px 10px); // true
```

**산술연산자 (숫자나 색)**

- `a + b` : a 와 b의 값을 더합니다.
- `a - b` : a 에서 b의 값을 뺍니다.
- `a * b` : a와 b의 값을 곱합니다.
- `a / b` : a를 b로 나눕니다.
  - 괄호로 묶지 않으면 문자열로 반환된다.
- `a % b` : a 에서 b를 나눈 나머지 값을 구합니다.

⚠️ERROR : 비교하거나 연산하는 값의 단위가 동일하지 않으면 에러 발생한다.

```scss
//Sass 공식문서
@debug 100px + 10s;
// Error: Incompatible units px and s.
```

**String의** `a + b`

앞서 말했던 `+` 연산자에서 a와 b가 모두 문자열이라면 문자열 `a`, `b` 를 합쳐서 새로운 문자열로 반환한다.

만약 a나 b중 하나만 문자열이라 하더라도 문자열이 아닌 값은 문자열로 변환하여 두 값을 합친 문자열로 반환한다.

```scss
//Sass 공식문서
@debug "Helvetica" + " Neue"; // "Helvetica Neue"
@debug sans- + serif; // sans-serif
@debug sans - serif; // sans-serif

@debug "Elapsed time: " + 10s; // "Elapsed time: 10s";
@debug true + " is a boolean value"; // "true is a boolean value";
```

```scss
// Scss
.status-bar {
  font-family: "Noto Sans KR", sans- + serif;
}

td {
  &::after {
    content: "Heades" + " up!"; // 문자열 더하기
  }
}
```

```css
/*CSS*/
.status-bar {
  font-family: "Noto Sans KR", sans-serif;
}

td::after {
  content: "Heades up!";
}
```

### **논리연산자 (불리언 타입)**

```scss
// Sass 공식문서
@debug not true; // false
@debug not false; // true

@debug true and true; // true
@debug true and false; // false

@debug true or false; // true
@debug false or false; // false
```

<br>

## Mixin

- Mixin은 **코드를 재사용**하기 위해 만들어진 기능이다.
- 선택자들 사이에서 반복되고 있는 코드들은 mixin을 사용해 줄일 수 있다. 중복되는 코드는 mixin으로 만들어 놓고 원하는 선택자 블럭에 mixin을 include한다.

<br>

### Mixin 사용하기

```scss
@mixin 이름(매개변수) {
  //생성
  // 중복되는 코드 작성
}

//사용
스타일하고자 하는 요소 {
  @include 이름(인수);
}

// 매개변수가 없어도 mixin 사용할 수 있다.
@mixin text-style {
}
a {
  @include text-style;
}
```

- 앞에 `@Mixin`을 쓰고 이름을 정해준 후, 중괄호 `{ }` 안에 중복되는 코드를 넣는다.
- `@include`를 사용하여 스타일 하고자 하는 요소에 포함한다.
- mixin은 파일을 만들어서 import하여 사용하거나, mixin을 사용할 파일 내에서 선언 후 사용할 수 있다. 이때, **여러 개의 mixin을 만들어 사용**한다면 `_mixins.scss` 파일을 만들어서 관리한다.

```css
.card {
  display: flex;
  justify-content: center;
  align-items: center;
  background: gray;
}

.aside {
  display: flex;
  justify-content: center;
  align-items: center;
  background: white;
}
/*.card와 .aside 클래스 선택자의 적용한 스타일이 겹침*/
```

```scss
// scss를 사용

@mixin center-xy {
  display: flex;
  justify-content: center;
  align-items: center;
}

.card {
  @include center-xy; // 정의한 center-xy mixin을 사용하여 코드 한줄이면 끝!
}

.aside {
  @include center-xy;
}
```

> ⚠️ 반복하는 모든 코드를 하나의 mixin에 몰아넣어서 사용하는 것은 좋지 않다. 위에 코드처럼 서로 연관 있는 스타일 속성끼리 묶어서 만들어야 좀 더 사용성이 높은 mixin을 만들 수 있다.

<br>

### Arguments

> ❓ 파선아실
>
> 파라미터 - 선언할 때  
> 아규먼트(arguments, 인자) - 실제 값

<br>

**1) 인수(Arguments)**

mixin 이름 뒤에 인수를 넣어서 사용할 수 있으며, 일반 언어와 마찬가지로 매개변수와 인수의 개수가 같아야 한다. mixin의 매개변수에 들어가는 인자들의 값에 따라 형태는 같지만 스타일이 조금씩 달라지므로 능동적으로 스타일 적용이 가능하다.

```scss
@mixin image-style($url, $size, $repeat, $positionX, $positionY) {
  background-image: url($url);
  background-size: $size;
  background-repeat: $repeat;
  background-position: $positionX $positionY;
}
//background관련 스타일 코드가 들어있다.
//mixin의 인수에 따라 조금씩 다른 스타일링이 가능하다.

.profile {
  @include image-style("./assets/user.jpg", cover, no-repeat, center, center);
}

.box-one {
  @include image-style("/images/poster1.svg", cover, no-repeat, 40%, 50%);
}
```

```css
.profile {
  background-image: url("./assets/user.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center center;
}

.box-one {
  background-image: url(url("/images/poster1.svg"));
  background-size: cover;
  background-repeat: no-repeat;
  background-position: 40% 50%;
}
```

**2) 기본값 설정**

기본값을 설정하여 매개변수에 값이 들어오지 않을 때 기본으로 설정한 값을 사용할 수 있다.

```scss
// 위에 코드를 가져와서 기본값을 설정해주었다.
@mixin image-style($ul, $size, $repeat, $positionX: 50%, $positionY: 50%) {
  background-image: url($ul);
  background-size: $size;
  background-repeat: $repeat;
  background-position: $positionX $positionY;
}

.profile {
  @include image-style("./assets/user.jpg", cover, no-repeat);
}
// profile과 .box-one은 서로 관계가 없지만, 코드가 중복되기때문에 mixin을 만들어서
// 각 요소에서 사용합니다.
```

```css
.profile {
  background-image: url("./assets/user.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  background-position: 50% 50%;
}
```

- 값을 비우거나(null) 값을 아예 안줘도 된다.

```scss
@mixin pri-button_($width: 100px, $height: 50px, $radius: 10px) {
  width: $width;
  height: $height;
  border-radius: $radius;
  background-color: aqua;
}

// 값 비우기
.btn__ {
  @include pri-button_(100px, null, 20px);
}

// 중앙값 주지 않기
.btn__ {
  @include pri-button_(100px, $radius: 20px);
}
```

<br>

### Content

`@content`를 사용하면 원하는 부분에 스타일을 추가하여 전달할 수 있다.

```scss
// mixin 정의
@mixin sample {
  display: flex;
  justify-content: center;
  align-items: center;
  @content;
}
```

```scss
// 사용하는 곳에서
a {
  @include sample {
    color: white; // smaple의 스타일도 가지면서 새로운 스타일 추가
  }
}
```

- 다음 2개는 동일하게 적용된다.

```scss
@mixin one {
  width: 100px;
  height: 100px;
  color: white;
  @content;
}

// include 안에 쓰는 경우
a {
  @include one {
    background-color: black;
  }
}

@mixin two {
  width: 100px;
  height: 100px;
  color: white;
}

// include 밖에 쓰는 경우
button {
  @include two;
  background-color: black;
}
```

<br>

### 실무에서 사용하는 mixin

```scss
$url: "./assets/img/";

@mixin thumb($total, $img, $type) {
  @for $i from 1 through $total {
    li:nth-child(#{$i}) .thumb {
      background-image: url(#{$url} + #{$img} + #{$i} + '.' + #{$type});
    }
  }
}

@include thumb(5, "background", "png");

@mixin circleBase {
  display: block;
  border-radius: 50%;
  -ms-border-radius: 50%;
  -webkit-border-radius: 50%;
}

@mixin circle($size, $color: null) {
  // $size: unitCheck($size);
  @include circleBase;
  width: $size;
  height: $size;
  background-color: $color;
}

.profile {
  @include circle(100px, red);
}
```

<br>

### 문자열 처리 예제

```SCSS
// @function sigma($number){
//     $result: 0;

//     @for $i from 1 to $number {
//         $result: #{$result + $i}; // 문자열로 처리(#이 들어간 공간을 통째로 문자열로 처리)
//     }

//     @return $result;
// }

// .one {
//     width: sigma(11) + px;
//     // width: 12345678910px;
// }

@function sigma($number){
    $result: 0;

    @for $i from 1 to $number {
        $result: #{$result} + $i;
    }

    @return $result;
}

.one {
    width: sigma(11) + px;
    // width: 012345678910px;
}
```
