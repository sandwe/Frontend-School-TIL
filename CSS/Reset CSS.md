# RESET CSS & Vendor Prefix

> 22.09.08

<br>

## 브라우저마다 다른 요소의 스타일

> 브라우저마다 요소의 기본 스타일이 다르고, 모든 브라우저에 똑같은 웹디자인을 구현하기 위해 각각의 브라우제 다른 스타일을 부여하는 것은 매우 비효율적이다. 따라서 다음의 스타일 초기화 방법을 사용한다.

<br>

### 에릭 마이어의 reset CSS

- 브라우저의 모든 기본 스타일 속성을 초기화 시킨다.
- 따라서 모든 스타일을 처음부터 구현할 수 있다.
- 2011년 이후로 업데이트 중단

```CSS
/* http://meyerweb.com/eric/tools/css/reset/
   v2.0 | 20110126
   License: none (public domain)
*/

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed,
figure, figcaption, footer, header, hgroup,
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure,
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}
```

<br>

### normalize.css

- 각각의 브라우저 스타일마다 추가적인 스타일을 덧붙여 **어떤 브라우저에서든 일관되게 보이도록** 만드는 파일
- [Normalize.css](https://necolas.github.io/normalize.css/)
- https://github.com/necolas/normalize.css

### CSS Remedy

- 만약 CSSWG에서 CSS를 제작하는 사람들의 입장이라면, 어떤식으로 브라우저에게 기본 스타일을 주게 될까 라는 생각에서 출발한 차세대 CSS reset 프로젝트입
- https://github.com/jensimmons/cssremedy

## Vendor Prefix (벤더 프리픽스)

> 아직 비표준이거나 실험적인 CSS 속성을 특정 브라우저에서 실행할 수 있도록 CSS 속성 앞에 브라우저 제조사 만의 접두어(prefix)를 붙이는 문법

- CSS 코드를 vendor prefix를 추가한 코드로 바꿔주는 사이트
  [Autoprefixer CSS online](https://autoprefixer.github.io/)
- 보통 VS code 확장 프로그램으로 Autoprefixer를 많이 사용한다.
