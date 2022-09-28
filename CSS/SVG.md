# SVG

## SVG란?

확장 가능한 벡터 그래픽(scalable vector graphics)으로 XML 기반의 2차원 그래픽이다. HTML 태그의 집합으로 이루어져 있어 CSS와 JavaScript로 컨트롤이 가능하다.

<br>

### SVG의 장점

- 아무리 확대를 해도 이미지가 깨지지 않는다.
- 이미지의 크기를 키워도 용량이 늘어나지 않는다.

<br>

### SVG의 단점

- **코드로 이루어진 이미지**이기 때문에 복잡한 이미지일수록 파일 사이즈가 커진다.
- 단순한 모양일수록 효율이 좋다. 복잡한 이미지를 굳이 SVG로 표현하고자 하면 오히려 용량이 너무 거대해져 역효과가 날 수 있다. 그렇기 때문에 주로 **단순한 아이콘, 로고, 도형** 등을 구현할 때 많이 사용한다.

<br>

## HTML에 SVG를 적용하는 여러가지 방법들

### 내부 요소 조작이 필요하지 않을 때 사용하는 방법

**1. img 태그로 사용하기**

src="" 속성값으로 svg 파일을 연결합니다.

- svg는 벡터값(좌표값)으로 이루어져 있어서 넓이, 높이 값을 설정해야 나타난다.

```html
<img src="frog.svg" alt="" />
```

**2. css background로 사용하기**

`background-image` 속성값으로 svg 파일을 연결한다.

```css
.cont-svg {
  width: 100vw;
  height: 100vh;
  background: url(frog.svg) no-repeat 0 0;
  background-size: contain;
}
```

<br>

### 내부 요소를 조작해야 할 때 사용하는 방법

**3. 인라인으로 구현하기**

svg 파일의 코드를 그대로 html 코드 안에서 사용한다.

```html
<svg width="624" height="465" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="m446.529 308.502 79.386-37.479c-37.824-34.863-111.48-58.521-196.146-58.521-123.264 0-223.191 50.142-223.191 112.002 0 61.857 99.927 112.002 223.191 112.002 94.674 0 175.575-29.586 208.011-71.334l-91.251-56.67Z" fill="#00A249" />

  .. 중략 ...

  <path d="M383 129c0 16.016-13.208 29-29.5 29S324 145.016 324 129s13.208-29 29.5-29 29.5 12.984 29.5 29Z" stroke="#000" />
  <ellipse class="eye-right" cx="353.5" cy="129" rx="12.5" ry="12" fill="#000" />
</svg>
```

**4. Object 태그 사용하기**

아래처럼 object 태그로 사용하면 내부 요소에 접근할 수 있다.

```html
<object data="./image.svg" type="image/svg+xml"></object>
```

<br>

### 참고 사이트

- svg 이미지 최적화  
  https://jakearchibald.github.io/svgomg/
- png -> svg 변환  
  https://convertio.co/kr/png-svg/
