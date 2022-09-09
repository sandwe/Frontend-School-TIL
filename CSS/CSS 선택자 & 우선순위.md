# CSS 선택자

> 22.09.08

<br>

## 전체 선택자 (Universal Selector)

- 모든 HTML 요소에 접근한다.
- 문서 전체의 공통 기본 스타일을 지정할 때 사용하기도 한다.

```CSS
* {
  /* 스타일 속성 */
}
```

<br>

## 타입 선택자 (Type Selector)

- 스타일을 적용하려는 태그의 이름을 사용한다.
- 해당 태그의 이름에 해당하는 모든 태그에 속성을 적용한다.

```CSS
p {
  /* 스티알 지정 */
}
```

<br>

## 아이디 선택자 (ID Selector)

- 페이지 내 id 속성을 적용한 요소를 유일하게 식별할 때 사용한다. 같은 페이지 안에 id 값은 **유일**해야 한다.
- <a> 태그의 href 속성과 연결하여 현재 페이지에서 어떤 구역으로 이동하는 [해시 링크](https://github.com/sandwe/Frontend-School-TIL/blob/main/HTML/Text-level%20semantics%20%26%20Embedded%20content.md)를 만들 수 있다.

```CSS
#id값 {
  /* 스타일 속성 */
}
```

<br>

## 클래스 선택자 (Class Selector)

- class는 페이지 내 여러 개 일 수 있다.
- clsss는 하나의 태그에 여러개 적용할 수 있다.
- CSS뿐만 아니라 JavaScript에서도 활용할 수 있는 속성이다.
-

```HTML
<h1 class="one two">hello world"</h1>
<h2 class="one">hello world2</h2>
```

```CSS
.one {
  /* one이라는 클래스 값을 갖는 요소에 적용되는 스타일 속성 */
}
```

<br>

## 선택자 목록 (Selector List)

- ,로 다양한 선택자를 연결하여 ,로 이어진 선택자들과 일치하는 요소를 선택한다.

```CSS
h1, h2, h3, h4, h5, h6 {color: red;}
```

<br>

## 자손 선택자 (Descendant Selector)

- 앞의 선택자의 **하위 요소** 중 뒤의 선택자에 해당하는 모든 요소에 스타일을 적용한다.

```CSS
/* div 요소의 하위 요소 중 p 요소에 스타일을 적용 */
div p {
  color: red;
}
```

<br>

## 인접 형제 선택자 (Adjacent sibling combinator)

- 앞의 선택자의 **바로 다음 형제 요소 하나**를 선택해 스타일을 적용한다.

```HTML
<h1 class="one">hello world</h1>
<h2>hello</h2>
<h2>hi</h2>
```

```CSS
/* one이라는 클래스의 바로 다음 형제 요소인 hello에 빨간색 스타일을 적용한다.
.one + h2 {
  color: red;
}
```

<br>

## 자식 선택자 (Child combinator)

- 뒤의 선택자가 앞의 선택자의 자식 (바로 밑) 요소이면 스타일을 적용한다.

```CSS
h1 > p {
  /* h1요소의 자식 요소인 p 요소에 스타일 적용 */
}
```

<br>

# 선택자 우선순위

> CSS를 적용하는 우선 순위가 있다. 선택자 우선순위에는 다음의 3가지 원칙이 있다.

<br>

## 1. 후자 우선 원칙

- 동일한 선택자가 연속으로 사용되면 나중에 작성한 스타일이 우선된다.

```CSS
/* p 요소에는 후자 우선 원칙에 의해 color의 속성값이 green으로 적용된다. */
p {
  color: red;
  font-size: 20px;
}

p {
  color: green;
}
```

<br>

## 2. Specificity (명시도, 구체성)의 원칙

- 구체적으로 작성된 선택자의 스타일이 우선 적용된다.
- 아래의 예시는 후자 우선 원칙에 의하여 color의 속성값이 green이 될 것 같지만 결과는 그렇지 않다.  
  `p.color-red`가 더 구체적으로 작성되었기에 color의 속성값은 red가 적용된다.
- 스타일 적용시 우선순위: id > class > 태그 type

```HTML
<p class="color-red">hello world</p>
```

```CSS
p.color-red {
  color: red;
  font-size: 20px;
}

p {
  color: green;
}
```

<br>

## 3. 중요성의 원칙

- 다른 속성보다 더 우선적으로 적용되어야 할 속성이 있다면 !important를 속성값 다음에 추가한다.
- !important는 인라인 스타일을 덮어써야 하는 등의 불가피한 상황이 나리아면 사용하지 않는 것이 좋다.

```CSS
p {
  color: red !important;
}
```

<br>

### 어떤 선택자가 더 구체적인가를 판단하기 위한 지표 - 가중치

- 점수
  |inline-style|1000점|
  |id 선택자|100점|
  |class, 가상클래스, 속성선택자|10점|
  |타입, 가상요소 선택자|1점|
  |전체 선택자|0점|
  |!important|9999999999점|

- 가중치 점수가 높은 스타일을 적용한다.
- 점수가 같다면 가장 마지막에 작성된 스타일을 적용한다.(후자 우선 원칙)
