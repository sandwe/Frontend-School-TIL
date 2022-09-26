# 미디어 쿼리

## 미디어 쿼리란?

- 특정 조건(단말기의 유형, 화면 해상도, 뷰포트 너비 등)에서 특정 스타일만 적용되도록 만들어주는 기능
- 대응하는 브레이크 포인트와 UI 시안 갯수는 회사별, 프로젝트별로 달라진다.

> 📓 기기별 해상도와 브레이크 포인트
>
> - IOS 기기별 해상도 : [https://www.ios-resolution.com/](https://www.ios-resolution.com/)
> - Android 디바이스 브레이크 포인트 : [https://developer.android.com/guide/topics/large-screens/support-different-screen-sizes](https://developer.android.com/guide/topics/large-screens/support-different-screen-sizes)

<br>

### 예제

```css
/* 1000px 이하, 1000px일 때까지 다음의 스타일이 적용된다 */
@media screen and (max-width: 1000px) {
  body {
    background-color: green;
  }
}
```

<br>

## 미디어쿼리 유형

### `all`

- 모든 장치를 대상으로 한다.

### `print`

- 인쇄 결과물 및 출력 미리보기 화면에 표시하는 경우에 사용한다.

```html
<abbr title="world wide web consortium">w3c</abbr>
```

가상요소 안에 title 속성의 fullname 값을 넣어서 출력 시 종이에 포함될 수 있도록 한다.

```css
@media print {
  abbr::after {
    /* attr() : css 속성 함수입니다. */
    content: " (" attr(title) ")";
  }
}
```

### `screen`

- **모니터나 스크린이 있는 디바이스**를 의미한다.

<br>

## 미디어 쿼리 조건

### `webkit-device-pixel-ratio`

- 1px에 속성값으로 입력된 숫자만큼의 화소가 들어갈 때 특정 스타일을 적용한다.

### `webkit-min-device-pixel-ratio, webkit-max-device-pixel-ratio`

- 출력 장치의 최소, 최대 픽셀 비율
- css의 1px 안에 들어가는 디바이스의 스크린 픽셀의 숫자를 속성값으로 한다.

### `min-width, max-width`

- 스크롤바를 포함한 뷰포트의 최소, 최대 넓이

### `orientation`

- 뷰포트의 방향

[orientation - CSS&colon; Cascading Style Sheets | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/orientation)

```css
@media screen and (orientation: portrait) {
  /* 세로모드 */
}

@media screen and (orientation: landscape) {
  /* 가로모드 */
}
```

<br>

## 논리연산자

- `and` : 조건을 모두 만족하는 경우에만 스타일 적용
- `not` : 조건을 반전하는 경우 스타일 적용
- `,` : **조건중 하나**라도 만족하는 경우 스타일 적용
- `only` : 미디어 쿼리를 지원 하는 브라우저에서만 작동하게 한다.
  - (미디어 쿼리 css3 버젼은 IE9 부터 지원하지만 사실 미디어 쿼리 자체는 이미 IE6부터 지원한다. 하지만 이땐 아직 논리 연산자를 지원하지 않기 때문에 논리연산자를 무시하고 스타일을 반영하는 오류를 미연에 방지하고자 only 키워드가 탄생하게 된다.)

```css
body {
  background: black;
}

@media screen and (min-width: 481px) and (max-width: 1280px) {
  body {
    background: red;
  }
}

@media screen and (max-width: 480px) {
  body {
    background: green;
  }
}

@media not screen and (orientation: landscape) {
  /* not은 항상 @media 뒤에 옵니다. 기본값은 portrait */
  body {
    background: pink;
  }
}

@media screen and (-webkit-device-pixel-ratio: 2) {
  body {
    background: royalblue;
  }
}
```

<br>

**기기의 픽셀 비율을 알아내는 방법**

1. BOM api 이용 (window.devicePixelRatio) - **화면 확대하면 비율이 달라진다.**
2. [https://johankj.github.io/devicePixelRatio/](https://johankj.github.io/devicePixelRatio/)

**각 기기별 사이즈와 중단점(break point) 정리**

[Material Design](https://material.io/design/layout/responsive-layout-grid.html#columns-gutters-and-margins)

> ❓ 보통 미디어 쿼리를 사용할 요소들은 CSS를 한번에 묶어서 적용시킨다.
