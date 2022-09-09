# Git, GitHub, Terminal 명령어

> 22.09.01

<br>

## 깃허브 기본 명령어

### help 명령어

```bash
$ git help -a : 상세히 명령어들 살펴보기
$ git 명령어 -h : 명령어 옵션 보기
$ git help 명령어 : web에서 해당 명령어 상세보기
```

<br>

### 현재 경로의 디렉토리를 git 저장소로 설정 및 초기화

```bash
$ git init
```

```Text
💡 이때, 한 폴더에는 하나의 .git(로컬 저장소)만을 가진다. 그렇지 않을 경우 충돌이 발생할 수 있다.
```

<br>

### 파일 생성(touch), 추가(add), 커밋(commit)

```bash
$ touch README.md
$ git status # Untracked files 확인
$ git add README.md # 변경한 파일 목록 중 stage에 올릴 파일을 선택해 올릴 때
$ git add . # 변경한 파일 모두를 stage에 올릴 때
$ git commit -m "first commit"
```

<br>

### GitHub 저장소에 무시할 파일 설정 - `.gitignore`

1. `.gitignore` 자동 생성기 활용

- 어떤 스택을 사용하여 프로젝트를 할 때, 해당 스택을 검색해 생성하면 무시할 파일 목록이 저절로 생성되어 간편하다.<br>
  [gitignore.io](https://www.toptal.com/developers/gitignore)

<br>

## 터미널 명령어

- `mkdir`: 폴더 생성
- `cd test`: test 폴더 이동
- `touch test.html` : test.html 파일 생성
- `vi test.html`: 문서 편집기로 test.html 열기, 실무에서는 vim을 많이 사용
- `:wq` 작업한 내용 저장 및 종료
- `cat test.html` 파일을 순서대로 읽어 출력

<br>

## DNS 관리- 도메인과 IP 연결

- A 레코드 관리: 호스트 IP를 등록
- 도메인 별칭 관리(CNAME): 도메인 주소를 또 다른 도메인 주소(별명)로 매핑할 수 있다.
  ||||
  |---|---|---|
  |A|naver.com|192.0.2.255|
  |CNAME|www.naver.com|naver.com|
- 유저가 별칭 도메인 주소(www.naver.com)를 요청하여도 매핑된 메인 도메인 주소(naver.com)를 통해 IP 주소를 얻을 수 있다.
