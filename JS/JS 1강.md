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
    
    // body 맨 끝에 넣어줌
    <script>
        document.getElementById('one').innerHTML =
        'hi world'
    </script>
</body>
```
<br>

