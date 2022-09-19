# Grid

<br>

## grid 컨테이너에 사용하는 속성

### 1. grid-template-columns

- 열방향 트랙의 사이즈를 결정한다.
- fr: 분수, 일부, 비율을 의미한다.

```css
grid-template-columns: 1fr 1fr 1fr; /* fr: fraction(분수, 일부, 비율) */
grid-template-columns: 1fr 1fr 1fr 1fr;
grid-template-columns: 5% 10% 15% 70%;
grid-template-columns: 100px 200px;
grid-template-columns: 1fr 2fr 1fr;
grid-template-columns: repeat(3, 1fr);
```

<br>

### 2. grid-template-rows

- 행방향 트랙의 사이즈를 결정한다.
- CSS **repeat(반복 횟수, 트랙에 세팅할 값)** 함수를 사용해 트랙의 사이즈 값을 쉽게 설정할 수 있다.

<br>

### 3. CSS 함수

1. `minmax(최솟값, 최댓값)` 함수: 최소와 최대 사이의 범위를 설정하는 함수이다.
2. `repeat(반복 횟수, 반복할 트랙 세팅 값)` 함수: 트랙의 사이즈를 쉽게 설정하는 함수이다.

   `auto-fill` & `auto-fit`: repeat 함수 사용 시 반복 횟수를 고정하지 않고, 컨테이너의 넓이에 따라 가능한 많은 grid 아이템을 배치할 때 사용한다.

   ```css
   .container{
   	display:grid;
   	grid-template-columns: repeat(3, minmax(50px, 150px));
   	grid-template-columns: repeat(auto-fill, minmax(50px, auto)); /* 가용공간 채울 수 있어도 채우지 않는다 */
   	grid-template-columns: repeat(auto-fit, minmax(50px, auto)); /* 가용 공간을 채울 수 있으면 채운다. *
   }
   ```

3. `gap`: 셀과 셀 사이의 간격을 설정한다. **IE 지원 x**

<br>

s## grid 아이템에 사용하는 속성

### 1. grid-column-start, grid-column-end

- 열방향 트랙에서 grid 아이템의 시작/끝 위치를 지정한다.

### 2. grid-row-start, grid-row-end

- 행방향 트랙에서 grid 아이템의 시작/끝 위치를 지정한다.

### 3. grid-area

- grid-row-start, grid-column-start, grid-row-end, grid-column-end의 값을 한번에 설정할 수 있다.
- 각각의 값들은 grid-line 번호를 의미한다.
- `span` 태그를 사용해서도 영역을 채울 수 있다.

```css
.item {
  /* grid-column-start : 1;
	grid-column-end : 3;
	grid-row-start : 1;
	grid-row-end : 3; */

  grid-area: 1 / 1 / 3 / 3;

  grid-area: 1 / 1 / span 2 / span 2;
}
```

### 4. grid-template-areas와 grid-area 속성

- `grid-area` 속성을 통해 영역의 이름을 짓고, `grid-template-areas` 속성을 통해 해당 영역의 범위를 직관적으로 표현할 수 있다.

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>template areas</title>
    <style>
      body {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        /* 
                    3. 간격은 맞춰 주는 것이 좋습니다. 
                    4. main 넓이를 많이 주어야 할 때에는 아래처럼 구성할 수 있습니다.
                */
        grid-template-areas:
          ".       .       .       time"
          "header  header  header  header"
          "aside-a main    main    aside-b"
          "footer  footer  footer  footer";
      }

      header {
        grid-area: header;
        background-color: pink;
      }

      main {
        grid-area: main;
        background-color: royalblue;
      }

      .aside-a {
        grid-area: aside-a;
        background-color: lightgreen;
      }

      .aside-b {
        grid-area: aside-b;
        background-color: lightgreen;
      }

      footer {
        grid-area: footer;
        background-color: aquamarine;
      }

      p {
        grid-area: time;
        background-color: blueviolet;
      }
    </style>
  </head>
  <body>
    <!-- 
            - 위치 상으로 맨 위로 올라가는 것이 맞지 않을까요? 
						- aside는 웹 접근성을 고려하여 main 아래로 마크업하는 것이 적절함.
        -->
    <p>현재시간 :<time>22-09-19</time></p>
    <header>header</header>
    <main>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Error repellat
      earum iure id natus, consectetur, aut a adipisci, suscipit dolore in quam
      commodi recusandae magni excepturi sapiente quasi optio accusantium?
    </main>
    <aside class="aside-a">aside</aside>
    <aside class="aside-b">aside</aside>
    <footer>footer</footer>
  </body>
</html>
```
