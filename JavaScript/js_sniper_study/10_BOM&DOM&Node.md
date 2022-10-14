# BOM & DOM & Node

## 1. BOM

- 웹 브라우저의 다양한 기능을 객체처럼 다루는 모델

### window 객체

- Global Context(전역 공간)이자 브라우저 창을 나타내는 객체
- 전역 변수나 전역 함수의 경우 window의 프로퍼티처럼 작동한다.
- 중요 프로퍼티: InnerWidth, InnerHeight, screenX, screenY, scrollBy(), scrollTo()

```JavaScript
var testValue = 'hahah';
function testFunc() {
  console.log('hahaha');
}
window.testFunc();
window.testvalue;
```

**innerwidth, innerHeight**

```js
window.innerWidth;
window.innerHeight;
```

**screenX, screenY**

- `screenX` : 화면 왼쪽 끝과의 거리
- `screenY` : 화면 위쪽 끝과의 거리

**scrollBy(), scrollTo()**

- `scrollBy`: 현재 위치에서 값만큼 스크롤 이동
- `scrollTo`: 절대좌표 (0,0)에서 값만큼 스크롤 이동

<br>

### screen 객체

- 사용자 환경의 디스플레이 정보를 나타내는 객체

**screen.availWidth**

- 모니터의 높이에서 웹 브라우저가 사용 가능한 넓이

**screen.width**

- 모니터의 위에서 아래까지의 넓이

**screen.availHeight**

- 모니터의 높이에서 웹 브라우저가 사용 가능한 높이

**screen.height**

- 모니터의 위에서 아래까지의 높이

**orientation**

- 화면의 angle

<br>

### locatation 객체

- 사용자가 보고 있는 페이지의 URL을 다루는 객체

**location.href**

- 현재 주소가 찍힌다.
- `location.href = 이동할 주소`: 이동할 주소로 이동해준다.

**location.reload()**

- 현재 페이지를 즉시 새로고침한다.

**location.replace()**

- 현재 페이지를 명시한 주소로 아예 교체한다. 이전 기록도 삭제된다.
- `location.replace("교체할 페이지");`
-

<br>

### navigator 객체

- 웹 브라우저 및 브라우저 환경정보를 가지는 객체

**navigator.userAgent**

- 브라우저가 어떤 환경에서 구동되고 있는지가 저장되어 있다.
- 사용자가 어떤 기기로 해당 브라우저를 접속하고 있는지 알 수 있다.

<br>

## 2. DOM

> Document Object Model
> 자바스크립트 Node 객체의 계층화된 트리

### document 노드

- 웹 페이지마다 존재하는 객체
- 웹 페이지 안의 모든 컨텐츠를 다루는 **시작점**
