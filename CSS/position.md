# position

## position 속성값

- 문서 상의 요소를 배치하는 방법을 지정해준다.

<br>

### static

- 기본값, 일반적인 html 구조에 맞게 배치한다.

### relative

- 자기 자신이 있던 자리를 기준으로 top, right, bottom, left 값에 따라 위치한다.
- **다른 요소들의 레이아웃에 영향을 주지 않는다.**

### absolute

- static 값을 제외한 position 속성값을 가진 가장 가까운 부모 요소를 기준으로 위치한다.
- 만약 조상 요소에 position 속성이 하나도 없다면 <html> 기준으로 위치를 잡는다.
- 다른 요소들이 absolute가 적용된 요소를 알아보지 못한다.

### fixed

- 뷰포트를 기준으로 한쪽 화면에 붙은 것처럼 보이게 할 때 사용한다.
- 페이지가 스크롤되어도 노출되어야 할 중요 정보(ex. 네비게이션)에 많이 적용한다.

### sticky

- 조상 요소에 scroll이 적용되어 있을 때, 가장 가까운 부모 요소의 콘텐츠 영역에 달라붙는다.

<br>

### z-index

- static을 제외한 position 속성 값으로 요소들의 위치를 움직이다 보면 요소끼리 겹치게 된다.
- 어떤 요소를 더 위에 올라오게 나타내고 싶을 때 숫자를 적용한다.
- 부모 요소가 z-index 값을 높여서 자식 요소 앞으로 나올 수 없다. 자식 요소의 z-index 값을 낮춰 부모 요소 뒤로 가는 것은 가능하다.
- 자식 요소는 부모 요소에 종속적이므로 다른 조상 요소들과의 z-index를 비교할 수 없다..
- 부모 요소가 다른 형제 요소들을 못이기면 자식 요소는 절대 조상 요소들을 z-index값으로 이길 수 없다.
- 형제 요쇼의 z-index 값이 동일하면 html의 구조 순으로 요소가 보이게 된다.
- 실무에서는 박스들이 엄청나게 많아서 보통 계산의 편리를 위해 10단위로 z-index 값을 적용한다.

> 📓 z-index를 미루어 보아 웹은 2D 세상 같지만 z축도 포함한 3D 세상이다!. 그래서 z-index로 위로 올라오는 요소를 정할 수 있다!
