# 속성 선택자, 가상 클래스 선택자, 가상 요소 선택자

## 속성 선택자 (Attribute Selector)

```CSS
/* <div> 요소이면서 class라는 속성을 갖는 요소 선택 */
div[class] {
  font-size: 10px;
}
/* <a> 요소이면서 href라는 속성을 갖는 요소 선택 */
a[href] {
  font-size: 10px;
}
/* <a> 요소이면서 href 속성값이 'https://www.paullab.co.kr 인 요소 선택 */
a[href="https://www.paullab.co.kr"]
{
  font-size: 32px;
}
/* <div>요소이면서 class의 속성값 중 변수 "weniv"를 완전한 단어로 포함하는 요소 선택 */
div[class~="weniv"] {
  color: red;
}
/* <a>요소이면서 href의 속성값이 http로 시작하는 요소 선택 */
a[href^="http"] {
  color: black;
}
/* <a>요소이면서 href의 속성값이 kr로 끝나는 요소 선택 */
a[href$="kr"] {
  color: black;
}
/* <a>요소이면서 href의 속성값이 변수 'weniv'를 포함하는 요소 선택 */
a[href*="weniv"] {
  color: black;
}
/* <a>요소이면서 href의 속성값이 변수 'http'이거나 'http'로 시작하면서 뒤에 바로 '-'(하이픈)이 있는 요소 선택 */
a[href|="http"]{
    color: black;
}
```

[Attribute selectors - CSS: Cascading Style Sheets | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors)

## 가상 클래스 선택자 (Pseudo class selector)

- 실제 html 문서에는 존재하지 않는 클래스이지만 마치 클래스가 존재하는 것처럼 동작한다.

```CSS
div:first-child {

}

div:last-child {

}

div: nth-child(3) {

}

div:nth-child(odd) {

}

div:nth-child(even) {

}
/* n=0, 1, 2, ... */
div:nth-child(n) {

}
div:nth-child(3n+1) {

}
/* 방문한적 있는 링크 선택, 개인정보 보호 위해 제한적으로 사용되어야 함 */
a:visited {

}
```

> 📓 `:first-child`와 `:last-child`를 쓰는 경우는?  
> 페이지의 첫 요소나 마지막 요소에 **여백**을 줄때 많이 사용한다.

<br>

`:hover`

- 사용자가 마우스를 요소 위에 올렸을 때 적용된다.
- 모바일 기기에서는 사용자의 손가락 호버 시점을 모르므로 호버가 적용되기 힘들다.

`:active`

- 사용자가 버튼을 누르고 있거나 링크를 클릭할 때 적용된다.

`:focus`

- 요소가 포커스될 때 적용된다.
- 클릭 가능한 요소, 폼 컨트롤(input, select 등)에 사용

`:checked`

- 선택하거나 토글된 상태인 라디오, 체크박스, 옵션 요소를 선택

<br>

## 가상 요소 선택자

`::before`

- 가상 요소 선택자를 적용할 요소의 맨 첫 번째 자식으로 HTML 문서에는 없는 가상요소를 생성한다.

`::after`

- 요소의 맨 마지막 자식으로 HTML 문서에 없는 가상요소를 생성한다.

> 📓 가상 요소 선택자에 width나 height를 적용하기 위해서는?
>
> 가상 요소 선택자는 인라인 요소이다. 따라서 `display: inline-block` 속성을 적용하여 width, height를 지정할 수 있다.

> 📓 어떤 것을 가상 요소 선택자로 적용해야 할까?
>
> CSS로 생성한 콘텐츠는 DOM이 포함하지 않고, 접근성 트리에도 들어가지 않는다. 스크린 리더가 읽어야하는 콘텐츠는 css 로 생성하는 것보다 문서에 포함하는 것이 좋다.

> ✅ 가상 클래스 선택자: 클래스가 없는데 있는 것처럼 처리 (:이 1개)  
> ✅ 가상 요소 선택자: 요소가 없는데 있는 것 처럼 처리 (:이 2개)

<br>

## Combinator

### **일반 형제([General sibling](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Combinators#general_sibling_combinator))** 콤비네이터

- 일반 형제 콤비네이터는 선택자 사이에 `~` 를 사용하여 나타낸다.
- `~`의 앞 요소 이후에 나오는 뒷 요소에 해당하는 모든 요소들을 선택한다.

```CSS
h1 ~ ul {
  color:red;
}
```
