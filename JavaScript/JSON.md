# JSON

## JSON이란?

- 자바스크립트에서 객체를 표현하는 형식으로 데이터를 표현한 것
- 다른 방식에 비해 가볍고 자바스크립트와 호환성이 높아 많이 사용된다.
- 쉽게 말해 **텍스트로 표현된 정보의 덩어리!**

### JSON 기본 형태

```JSON
{
  "squadName": "슈퍼히어로",
  "members": [
    {
      "name": "아이언맨",
      "age": 29,
      "본명": "토니 스타크"
    },
    {
      "name": "헐크",
      "age": 39,
      "본명": "부르스 배너"
    }
  ]
}
```

### 같은 데이터를 가지는 JSON과 xml 비교

- xml
  xml 형태도 많이 쓰인다.

```XML
<?xml version="1.0" encoding="UTF-8" ?>
<root>
  <squadName>슈퍼히어로</squadName>
  <members>
    <name>아이언맨</name>
    <age>29</age>
		<본명>토니 스타크</본명>
	</members>
	<members>
	  <name>헐크</name>
	  <age>39</age>
		<본명>부르스 배너</본명>
	</members>
</root>
```

<br>

## JSON 응용

### JSON을 활용한 테이블 만들기

```HTML
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title></title>
    <style>
      table,
      thead,
      tbody,
      tr,
      th,
      td {
        border: solid 1px black;
        border-collapse: collapse;
      }
    </style>
  </head>
  <body>
    <button onclick="renderTable(userData)">회원정보 로딩</button>
    <table style="width: 100%" id="infoTable">
      <thead>
        <th onclick="sort('_id')" style="width: 15%">id</th>
        <th onclick="sort('index')" style="width: 15%">index</th>
        <th onclick="sort('guid')" style="width: 15%">guid</th>
        <th onclick="sort('age')" style="width: 15%">age</th>
        <th onclick="sort('name')" style="width: 15%">name</th>
        <th onclick="sort('gender')" style="width: 15%">gender</th>
      </thead>
      <tbody id="tableBody"></tbody>
    </table>
    <script>
      let userData = [
        {
          _id: "6346555b442cea576e37249c",
          index: 0,
          guid: "5b398a4f-86b4-411b-aabc-3adb96659fdd",
          age: 37,
          name: "Marshall Booker",
          gender: "male",
        },
        {
          _id: "6346555bf0204a1ee03b4151",
          index: 1,
          guid: "f8eaa1a3-91c6-42bf-ac43-a622dc6e5750",
          age: 26,
          name: "Millicent Berry",
          gender: "female",
        },
        {
          _id: "6346555b4aeca9e1506038b0",
          index: 2,
          guid: "e3b74bf7-7e6b-427e-93ab-a0b40b4a813c",
          age: 30,
          name: "House Williams",
          gender: "male",
        },
        {
          _id: "6346555b0a1e5fc2884ed06f",
          index: 3,
          guid: "407e62c9-172d-4e64-84a5-77dabfe36dbc",
          age: 20,
          name: "Hobbs Bartlett",
          gender: "male",
        },
        {
          _id: "6346555bbc08e6272c2e1ee2",
          index: 4,
          guid: "c237c8bc-dd6f-46eb-851e-16450c9493c7",
          age: 39,
          name: "Hancock Macdonald",
          gender: "male",
        },
        {
          _id: "6346555bf2fb2fc3c4673d9c",
          index: 5,
          guid: "a9144fc5-a490-4aee-9abe-b2c8ab6db6a1",
          age: 27,
          name: "Mercedes Lynch",
          gender: "female",
        },
        {
          _id: "6346555b9c9e72828bcd25de",
          index: 6,
          guid: "b4d4b22f-2421-4821-bcf2-31b5719667df",
          age: 28,
          name: "Dorthy Haney",
          gender: "female",
        },
      ];

      var click = true;

      function sort(key) {
        if (click) {
          click = false;
          let sortedData = userData.sort((a, b) => (a[key] < b[key] ? -1 : a[key] > b[key] ? 1 : 0));
          renderTable(sortedData);
        } else {
          click = true;
          let sortedData = userData.sort((a, b) => (a[key] > b[key] ? -1 : a[key] < b[key] ? 1 : 0));
          renderTable(sortedData);
        }
      }

      function renderTable(userData) {
        // console.log(userData[0]);
        let tableBodayData = [];

        for (const user of userData) {
          tableBodayData.push(`
            <tr>
              <td>${user._id}</td>
              <td>${user.index}</td>
              <td>${user.guid}</td>
              <td>${user.age}</td>
              <td>${user.name}</td>
              <td>${user.gender}</td>
            </tr>
          `);
        }
        console.log(tableBodayData.join(""));
        document.querySelector("#infoTable > tbody").innerHTML = tableBodayData.join("");
      }
    </script>
  </body>
</html>
```
