## Ⅰ. 자바스크립트 (Javascript)   
## 1. 강의 자료
https://www.notion.so/JS-22-6-8723b46e0cde4d90b020b689e5cb9f0a#6d71826efcd24cbfbecd00ea8092f8ee

<br>

### 0) 개발자 도구
* __ctrl + shit + i__   
<br>

### 1) 삽입 위치
* 기본 태그: __```<script> </script>```__   

* 보통 body의 맨 끝   

__ex>__
```
<body>
    <h1>hellow world</h1>
    <p id="one">hello world</p>
    <p>hello world</p>
    <p>hello world</p>
    <p>hello world</p>
    <p>hello world</p>
    
    <script> // body 맨 끝에 넣어줌
        document.getElementById('one').innerHTML =
        'hi world'
    </script>
</body>
```
<br>
<hr>

### 2)  JavaScript를 출력하는 4가지 방법
* ```ctrl+shift+i```를 누르고 Console에서 테스트 가능   
<br>

#### (1) 문서 내 요소를 선택하여 출력
* innerHTML   
```
document.getElementById('one').innerHTML =
        'hi world'            // 화면에 hi world 출력
```
<br>

#### (2) 문서 내 직접 출력
* write   
```
document.write('js hello!!')  // 화면에 js hello!! 출력
```
<br>

#### (3) 사용자 인터렉션 
* alert   
```
alert('hello')    // hello라는 알람창이 뜸
```

* confirm   
```
confirm('hello')  // 알람에서 확인 누르면 true, 취소 누르면 false 반환
```
<br>

#### (4) 콘솔에 찍는 방법
* 웹 화면이 아니라, 콘솔 화면에 출력   

* conole.log
```
console.log('hello')  // 콘솔에 hello 출력
```

<br>
<hr>

### 3) 코드 구조   
#### (1) ~문
* 문(statement)은 세미콜론으로 구분   

* 문 → 값, 연산자, 키워드, 명령어, 표현식 등
<br>

#### (2) 주석
```
//    1줄 주석
/**/  여러 줄 주석
```

