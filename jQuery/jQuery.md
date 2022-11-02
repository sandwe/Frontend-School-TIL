# jQuery

## 자주 사용하는 것

1.

```jsx
// $(".main-cont").hide();
$("h2").click(function () {
  alert("클릭!");
});
$("h2").css("color", "red");
$(".main-cont").text("hello world!!!");
$(".main-cont").html("<strong>hello strong</strong>");
```

2.

```html
<input id="one" type="text" />
<input id="two" type="text" />
<p id="three">helo</p>
<button id="four">클릭해!</button>
```

```jsx
$("#four").click(function () {
  let value = $("#one").val();
  $("#one").val("");
  $("#three").text(value);
});
```

3. 자바스크립트를 jQuery처럼 사용하기

```html
<h1 class="one">hello world</h1>
<script>
  // 자바스크립트를 제이쿼리처럼 사용하기
  function $(선택자) {
    return document.querySelector(선택자);
  }
  console.log($(".one"));
</script>
```

4.

```html
<div class="wrapper">
  <h1 class="title">TITLE</h1>
  <ul class="items">
    <li class="items">item 1</li>
    <li class="items">item 2</li>
  </ul>
</div>
<div class="class1">hello world1</div>
<div class="class2">hello world2</div>
<div class="class3">hello world3</div>
<div class="class4">hello world4</div>
<div class="class5">hello world5</div>
<div class="class6">hello world6</div>
<div class="class7">hello world7</div>
<div class="class8">hello world8</div>
<div class="class9">hello world9</div>
<div class="class10">hello world10</div>
```

```jsx
// js에서도 동일하게 할 수 있다.
// const one = document.getElementById("one");
// const mother = one.parentNode;
// 부모 생성
// const mother = document.getElementById("mother");
// const every = mother.childNodes;
// const one = mother.firstChild;
// const three = mother.lastChild;
// css에서는 부모 요소를 선택할 수 없다.

console.log($("div").children());
console.log($("div").children()[0]);
console.log($("div").children()[1]);
console.log($("h1").parent());

// $("div").first().text("안녕하세요!");
// $("div").last().text("안녕하세요!");
```

5. 요소에 클래스 토글하기 → JavaScript에도 이미 있다.

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title></title>
    <script src="https://code.jquery.com/jquery-3.5.0.js"></script>
    <style>
      .blue {
        color: blue;
      }
    </style>
  </head>
  <body>
    <h1>hello world</h1>
    <h1 class="blue">hello world</h1>
    <p>hello world</p>
    <p>hello world</p>
    <p id="one" class="blue">hello world</p>
    <script>
      $("p").append("!!");
      $("p").prepend("!!");
      $("#one").remove();
      $("h1, h2, p").toggleClass("blue");
    </script>
  </body>
</html>
```
