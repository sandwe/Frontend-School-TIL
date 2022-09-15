# Text

<br>

## line-height

- 글자 라인의 높이를 지정해 텍스트 라인과 라인 사이의 간격을 설정

<br>

### line-height 속성값

1. normal

- 기본 값
- 폰트의 font-family에 따른 글자의 기본 높이로, 사용하는 font-family에 따라 기본 line-height 값이 달라진다.

<br>

2. number

- 숫자로 값을 설정한다.
- `line-height: 1;`은 글자의 위아래 half-leading, 즉 leading area를 제거해 font-size와 같은 크기를 갖는다.
- line-height를 주는 가장 일반적인 방법

3. px, em, %

- px: 고정된 픽셀 값으로, 유연하지 않아 잘 사용하지 않는다.
- em: 부모 요소의 font-size의 배수 단위의 값을 적용
- %: 요소 자신의 font size를 기준으로 값 설정

<br>

## letter-spacing

- 한 글자 사이의 간격 조정

<br>

## text-align

- 블록 레벨 요소 안에 있는 텍스트를 정렬한다.
- 속성값: left, right, center, justify

<br>

### 텍스트 가로, 세로 정렬 둘다 하는 방법

- text-align 속성을 적용하면서 padding이나 margin 속성을 추가한다.

```CSS
.text_center{
  text-align: center;
  padding: 10px 0px;
}
```

<br>

## vertical-align

- 인라인 요소의 수직 정렬을 맞추기 위해 사용한다.
- `<img>`요소의 바깥쪽 공백을 없애기 위해 자주 사용한다.

> 📓 img 요소의 하단 공백이 생기는 이유?
>
> - `<img>`는 인라인 요소이고 따라서 baseline을 기준으로 위치하게 되어 아래에 공백이 생긴다.
>
> 📓 img 요소의 공백을 없애는 방법?
>
> 1. img 요소를 `display: block` 처리 (img가 블록 레벨 요소로 변하는 것 유의)
> 2. vertical-align 속성값 적용

<br>

### 속성값

초기값은 baseline이고, 가장 자주 사용하는 속성값은 top, bottom이다.

- top: 글씨 가장 상단의 위치를 라인의 상단으로 정렬한다.
- bottom: 글씨 가장 하단의 위치를 라인의 하단으로 정렬한다.
- 이외에도 sub, super, text-top, text-bottom, middle 이 있다.

<br>

## text-indent

- 텍스트 라인의 텍스트 시작하기 전 즉, 들여쓰기를 설정한다.

<br>

## text-overflow

- 넘치는 콘텐츠를 어떻게 사용자에게 보여줄지를 설정한다.

### 말줄임('...')

- 한 줄을 말줄임 하기 위해 `text-overflow: ellipsis`과 `overflow: hidden;`, `white-space:nowrap;`를 함께 사용한다.
