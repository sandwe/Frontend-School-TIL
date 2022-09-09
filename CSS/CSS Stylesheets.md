# CSS를 적용하는 방법

> 22.09.07

## 1. 인라인 방식

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <h1 style="color: red">
      인라인 스타일은 마크업을 해치므로 권장하지 않는다.
    </h1>
  </body>
</html>
```

<br>

## 2. 외부 스타일 시트

- 마크업과 CSS를 분리한다.

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link rel="stylesheet" href="002.css" />
  </head>
  <body>
    <h1>마크업과 CSS를 분리할 수 있어 좋다.</h1>
  </body>
</html>
```

## 3. 내부 스타일 시트

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      h1 {
        color: blue;
      }
    </style>
  </head>
  <body>
    <!-- 외부 css가 없다. 파일 1개만 수정하면 된다. -->
    <h1>hello world</h1>
  </body>
</html>
```

## 4. 다중 스타일 시트

- CSS 파일 안에 다른 CSS 파일을 포함한다.

```CSS
/* @font-face : 디바이스에 없는 폰트를 다운받아 적용할 때 사용합니다. */
@font-face {
  font-family: "RixInooAriDuriR";
  src: url("https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_2207-01@1.0/RixInooAriDuriR.woff2")
    format("woff2");
  font-weight: normal;
  font-style: normal;
}

h1 {
  border: 1px solid black;
  font-family: "RixInooAriDuriR";
}
```
