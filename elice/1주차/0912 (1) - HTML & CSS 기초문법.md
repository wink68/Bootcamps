## 1. 웹 사이트의 정보와 디자인   
### 1). 웹을 구성하는 요소   
#### 0) 프로그래밍이란?
* 컴퓨터와 소통하는 방법을 의미   

* 웹 개발을 하기 위한 언어로 브라우저와 소통

   * HTML: 웹 사이트에 정보를 표시할 때 or 웹 사이트의 구조를 설계할 때 사용   

   * CSS: 웹 사이트에 디자인을 입힐 때 사용 (스타일링)   

   * JavaScript: 웹 사이트에 동적인 효과를 부여하고자 할 때   

<br>

#### (1) 고려 사항
* 웹 표준

   * 웹 사이트를 작성할 때 따라야 하는 공식 표준이나 기술 규격

* 웹 접근성

   * 장애의 여부와 상관 없이 모두가 웹 사이트를 이용할 수 있게 하는 방식

* 크로스 브라우징

   * 모든 브라우저 또는 기기에서 사이트가 제대로 작동하도록 하는 기법   

<br>
<hr>

### 2) HTML 주요 태그 살펴보기   
#### (1-1) HTML   
* HTML이란

   * Hyper Text Markup Language   

      * Hyper Text = 'Text를 뛰어넘는다' = 순차적 접근을 뛰어넘는다 (다른 페이지로 쉽게 이동, 링크 or 북마크)   

      <br>

   * 웹 사이트에서 눈에 보이는 정보나 특정 구역을 설정할 때 사용하는 언어   

<br>

* 구성 요소   
```<태그 속성 = "속성값"> 내용 </태그>```
<br>

#### (1-2) Markup
* HTML의 M   

* 문서를 구조적으로 표시하기 위한 것   

<br>

#### (1-3) HTML 주석
```
<!-- 내용 -- >
```

<br>

#### (1-4) Self-Closing Tag
* 종료 태그가 없는 태그   

* 기본형

   * <태그 속성 = "속성값" />
   
   * ★ __```엔딩 슬래시```__ 로 종료를 나타냄 (선택 사항) ★   

<br>

__ex>__
```
   <img />  <meta />  <link />  <br />  <col />  <hr />
```

<br>
<br>

#### (1-5) 코딩 컨벤션 (Coding Convention)   
* 코드 규칙

   * 단축이 가능한 코드를 한 줄에 쓸 것인가, 선택 사항을 넣을 것인가 등

<br>

#### (1-6) ★ 개발자 도구 (F12, Ctrl+Shift+C) ★
* Elements - <body>의 코드 클릭 - Styles에서 체크박스를 조정해 속성 체크 가능   

<br>
<br>
<hr>

#### (2) HTML 5 기본 구조
```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title> 문서 제목 </title>
    </head>

    <body>
        <h1 style="color:navy"> 문서 내용 </h1>
    </body>
</html>
```
  
* __head__ : head는 요약 정보 (노출 X)   

   * __"UTF-8"__: 모든 문자코드를 (깨짐없이) 잘 출력하도록 하기 위해   

   * __title__: 브라우저 상단 탭 제목   
<br>

* __body__: 실제 웹 사이트에서 보여지는 정보   

   * __style__: style은 속성, color는 속성값, 속성값은 세미콜론으로 구분   
<br>

* __태그__: 열린태그와 닫힌태그 사이의 모든 것이 컨텐츠

   * ```<h1></h1>```

<br>
<hr>

#### (3) HTML 기본 태그   
#### ① ```<img> 태그```   
* 기본형
```
<body>
   <img src="이미지 파일 경로" alt="출력하지 못했을 경우 텍스트 내용">
</body>
```

* 닫힌 태그 X   

* src속성 : 파일 경로

* alt속성
    * 웹사이트가 이미지를 출력하지 못했을 경우, 텍스트 정보로 대체

    * 시각 장애인분들에게 정보 전달
<br>

#### ② ```<h> 태그```
* 제목이나 부제목 표현 (head)   

* 폰트 사이즈: h1 ~ h6   

   * h1은 가장 중요한 정보를 담으며, 한 번만 사용됨   

<br>

#### ③ ```<p> 태그```   
* 본문 내용 표현 (paragraph)   

__ex>__
```
<p>Nice to meet you</p>
```

<br>

#### ④ ```<ul> 태그```   
* 순서가 없는 리스트 (unordered list) <=> __```<ol> 태그```__      

* 메뉴 버튼: __```<li>```__   

__ex>__
```
<ul>
   <li>메뉴1</li>
   <li>메뉴2</li>
</ul>
```

<br>
<hr>

#### ⑤ ```<a> 태그```
* 링크 형성   

   * 웹페이지나 사이트에 연결하는 태그

* 기본형   
```
<a href="링크" target="웹페이지를 연결하는 방식">링크 텍스트</a>
  
// href (hypertext reference) : 텍스트나 이미지를 링크에 연결
```

* __```_self```__: 새 탭에서 생성   

* __```_blank```__: 새 창에서 생성   

* __```width=""```__: 폭 길이 지정   

* __```height=""```__: 높이 지정

<br>

__ex1>__
```
<body>
   <a href="https://academy.elice.io/" target="_blank">엘리스</a>    /* 글자 "엘리스"에 링크 걸기 */
   <img src="elice_logo.png" alt="엘리스 회사 로고" width="200px">    /* 이미지 생성 */
</body>
```

<br>

__ex2>__: 이미지에 링크 걸기   
```
  <a href="https://academy.elice.io/" target="_blank">
      <img src="elice_logo.png" alt="엘리스 회사 로고">
  </a>
```

<br>

__ex3>__: 회사 메인 로고
```
<h1>
   <a>
      <img>
   </a>
</h1>
```

<br>

__ex4>__: 리스트 (링크)   
* 링크가 미정일 경우 __```#```__ 을 넣어준다   

```
<ul>
   <li>
      <a href="#">메뉴1</a>
   </li>
   <li>
      <a href="#">메뉴2</a>
   </li>
</ul>
```

<br>
<br>

#### ◆ 하이퍼링크 CSS
* __```a:link```__

   * 방문한 적 없는 기본 링크

* __```a:visited```__

   * 방문한 링크

* __```a:hover```__

   * 마우스를 가져다뒀을 때

* __```a:active```__

   * 링크를 클릭했을 때

__CSS >__
```
a:link {
   color: red;
   text-decoration: none;
}

a:visited {
   color: blue;
   text-decoration: none;
}

a:hovor {
   color: hotpink;
   text-decoration: underline;
}

a:active {
   background-color: blue;
   text-decoration: underline;
}
```

<br>
<hr>

#### ⑥ ```<br> 태그```   
* 줄바꿈(엔터) 태그

   * Break(쪼개다)의 약자

__ex>__
```
  <p>
      내용 <br>
      내용
  </p>
  <span>내용<br>내용</span>
```

<br>

#### ⑦ ```<form> 태그```
* form 생성 태그

   * 로그인, 회원가입 등에 사용

   * input, button 태그를 사용

__ex>__
```
  <form action="/examples/media/action_target.php">
     이름 : <input type="text" name="st_name"><br>
     학번 : <input type="text" name="st_id"><br>
     학과 : <input type="text" name="department"><br>
     <input type="submit">
  </form>
```

<br>

#### ⑧ ```<iframe> 태그```
* 외부 페이지 삽입 태그

__ex>__
```
  <iframe src="https://academy.elice.io/explore" width="300" height="300"></iframe>
```

<br>

#### ⑨ ```<strong> 태그```
* 중요한 내용 강조 태그

__ex>__
```
  <p><strong>주의!</strong> 이번 역은 승강장 사이와의 간격이 넓으니 주의하시기 바랍니다!</p>
```

<br>

#### ⑩ ```<i> 태그```   
* Italic의 약자
  
* 기울임 태그
  
__ex>__
```
  <p><i>타이타닉호</i></p>
```

<br>
<hr>

### 3) 공간을 만들 때 사용하는 태그   
* HTML 태그 구성 요소

   * 목차 + 본문 * 부록      
<br>

#### (1: 목차) __```<header>```__ , __```<nav>```__ 태그   
* __```<header>```__: 웹사이트의 머리글을 담는 공간   

* __```<nav>```__: 메뉴버튼을 담는 공간 (navigation)   

   * ```<ul>, <li>, <a>```와 함께 사용   
   
__ex>__
```
<header>
   <img scr="링크" alt="텍스트">
   <nav>
      <ul>
         <li><a>홈</a></li>
         <li><a>전체 목록</a></li>
      </ul>
   </nav>
</header>
```

<br>

#### (2: 본문) __```<main>```__ , __```<article>```__ 태그   
* __```<main>```__: 본문 영역   

   * __```role="main"```__: main의 역할을 나타내기 위해 필수 입력   

* __```<article>```__: 주요 내용 (텍스트, 이미지)   

__ex>__
```
<main role="main">
   <article>
      <h#></h#>
   </article>
</main>
```

<br>

#### (3: 부록) __```<footer>```__ 태그   
  
__ex>__
```
<footer>
   <div>
      <p>주소: </p>
      <p>이메일: </p>
   </div>
   <div>
      <p>사업자등록정보: </p>
      <p>통신판매업신고번호: </p>
   </div>
</footer>
```

<br>

#### (4) __```<div>```__ 태그   
* 임의의 공간(레이아웃)을 만들 때   
  
* Block 태그

   * 가로 한 줄 전체 영역을 사용함   

* Division(분할)의 약자

<br>

#### (5) __```<span>```__ 태그   
* Inline 태그

   * 세로가 아닌, 가로로 쌓임

__ex>__
```
   <span>hello1</span>
   <span>hello2</span>
   <span>hello3</span>      // hello1 hello2 hello3
```

<br>
<hr>

### 4) HTML의 두 가지 성격   
#### (1) Block 요소와 Inline 요소

#### ① Block 요소
* y축 정렬 형태로 출력 (줄바꿈 현상)

   * ```<h>, <p>, <div>, <header>, <ul>, <ol>, <form>, <table>, <fieldset>, <address>, <blockquote>``` 등

* width, height 공간 크기 설정 가능   

* 상하 배치 작업 가능   

__ex>__
```
<p>내용1</p>
<p>내용2</p>
<p>내용3</p>
```

#### ② Inline 요소   
* x축 정렬 형태로 출력 (한 줄 출력)   

* 공간을 만들 수 없음

* 상하 배치 작업 불가   

__ex>__
```
<a>내용1</a>
<a>내용2</a>
<a>내용3</a>

// 출력
내용1 내용2 내용3
```

<br>
<hr>

### 5) CSS 주요 속성 살펴보기   
### (1) CSS란?
* Cascading Style Sheet   

* 정보(HTML)와 디자인(CSS)의 분리   

* 문서의 레이아웃(배치)과 스타일(디자인) 정의   

<br>

### (2) CSS 구성 요소
* 구성요소
   * 선택자: 디자인을 적용할 HTML 영역

   * 속성: 어떤 디자인을 적용할지 정의

   * 속성값: 어떤 역할을 수행할지 구체적으로 명령, 세미콜론(;) 필수 입력

* 기본형:   
```
선택자 { 속성 : 속성값; }
```

<br>

__ex>__
```
h1 {
  font-size: 20px;           // 폰트 사이즈
  font-family: sans-serif;   // 글꼴
  color: blue;               // 폰트 색깔
  background-color: yellow;  // 배경색
  text-align: center;        // 텍스트 정렬
}
```

<br>

### (3) ★ 적용 방법 ★
* 적용 우선순위 : __```인라인 > 내부 > 외부```__

<br>

#### ① Inline Style Sheet (인라인)   
* 태그 안에 직접 style 적용   

* 기본형: __```<태그 style="속성: 속성값;"></태그>```__
<br>

__ex>__
```
<h1 style="color: red;"> coding 101 </h1>
```

<br>

#### ② Internal Style Sheet (내부)   
* <head>의 <style> 태그 안에 넣기

__ex>__
```
<head>
<style>
    h1 { background-color: yellow; }
</style>
</head>
```

<br>

#### ③ External Style Sheet (외부)   
* 기본형   

   * __```<link rel="css파일의 성격" href="css파일">```__

      * ```<link rel="stylesheet" href="파일명.css" />```   
      <br>

   * rel 속성 (css파일의 성격) : http://tcpschool.com/html-tag-attrs/link-rel   
<br>

* html, css 각각의 문서 안에서 따로 관리

   * 가독성이 높고 유지보수가 쉬움

__ex>__
```
<head>
    <link rel="stylesheet" href="style.css">
</head>
```

<br>
<hr>

### 6) ★ CSS 선택자 ★
#### (1) 선택자 (Selector) 종류 
* head 안의 style 안에 작성   

<br>

#### ① Type(타입) 선택자
* HTML 태그   

__ex>__
```
// h2 = 타입 선택자

<style>
   h2 { color: red; }
</style>
```

<br>
<br>

#### ② Class(클래스) 선택자
* 태그에 대한 별명   

   * 콤마(.)Class명   

__ex>__
```
// <h2 class="coding"> 내용 </h2>

<style>
   .coding { color: red; }
</style>
```

<br>
<br>

#### ③ ID(아이디)
* 태그의 이름

   * 샵(#)ID명   
   
   * ID는 클래스보다 더 큰 공간을 의미 = __아이디가 클래스보다 CSS 선택자 우선순위가 높다__   

__ex>__
```
// <h2 id="coding"> 내용 </h2>

<style>
   #coding { color: green; }
</style>
```

<br>
<br>

#### ④ 속성 선택자 (Attribute Selectors)
* __```[속성이름 = "속성값"]```__   

* 해당 속성의 속성값까지 일치하는 모든 요소에 적용   

__ex>__
```
  a[title] {
     color: purple;
  }
  
  a[href="https://swtrack.elice.io/"] {
     color: green;
  }
  
  [title="first h2"] {
     background: black;
     color: yellow;
  }

```

<br>
<hr>

### 6-1) 선택자 응용
#### (1) 태그 사이 콤마 (,)   
* 여러 태그에 css를 적용하고자 할 때   
   
__ex>__
```
<style>
   html, body {
      margin:0; 
      padding:0;
      }
</style>
```

<br>

#### (2) 태그와 클래스 결합
* 점(.)으로 태그와 클라스 연결   

__ex>__
```
   h1.header { color: blue; }
   h2.header { color: green; }
```

<br>

#### (3) 복합 선택자 조합   
* 자식 선택자 (>)

   * ```nav > ul```   

* 후손 선택자 (공백)

   * ```nav li```

* 일반 형제 선택자

   * ```li ~ li```   

* 인접 형제 선택자

   * ```.li1 + .li2```   

__HTML >__
```
<nav>
  <ul>
     <li class="li1">홈</li>
     <li class="li2">로그인</li>
     <li class="li3">회원가입</li>
     <li class="li4">게시판</li>
     <li class="li5">질의응답</li>
  </ul>
  </nav>
```
   
__CSS >__
```
.li1 { color : red; }

ul li { color : green; }         /* 부모 자식 관계 */
ul > .li4 { color : orange; }    /* 직속 부모 자식 관계 */

.li1 + .li2 { color : yellow; }  /* 인접 형제 관계 */
.li1 ~ .li5 { color : blue; }    /* 일반 형제 관계 */
```

<img src="https://user-images.githubusercontent.com/108077414/190550268-9c5196b4-0737-4131-bd62-42316d3a6200.jpg" alt="복합 선택자 조합" width="300px" />

<br>
<br>

#### (4) 별 표시 태그 (*)   
* 모든 태그에 적용하고자 할 때   
   
__ex>__   
```
<style>
   * {
      margin:0; 
      padding:0;
      }
</style>
```

<br>
<hr>

### 7) 부모 자식 관계
* 부모 자식 관계
  
   * ```<header>와 <h1><p>```
  
   * 부모의 css속성을 상속받을 수 있다
  
   * 자식 속성이 우선
  
* 형제 관계
  
   * ```<h1>과 <p>```

__ex1>__
```
<style>
   header { color: red; }
   h1 { color: blue; }      // 자식 속성이 우선이여서 부모 red속성을 상속받지 X
   p { color: green; }
</style>
```
  
__ex2>__
```
<style>
   header { color: red; }
   header h1 { color: blue; }    // 어느 부모인지 정하면 그 부모의 자식에게만 적용
   header p { color: green; }
</style>
```

<br>
<hr>

### 8) 캐스케이딩
#### (1) 의미
* CSS의 우선순위   

* 우선순위를 결정하는 요소

   * 순서, 디테일, 선택자
   

#### ① 순서
* 나중에 적용한 속성값 우선

__ex>__
```
p { color: red; }
p { color: blue; }
```

#### ② 디테일
* 더 구체적으로 작성된 선택자 우선

__ex>__: 부모 명시
```
header p { color: red; }
p { color: blue; }
```

#### ★ ③ 선택자 ★
* style > id > class > type 순   

__ex>__
```
// 1등(핑크)
<h3 style="color: pink" id="color" class="color"> color </h3>

// css 문서
#color { color: blue; }  2등
.color { color: red; }   3등
h3 { color: green; }     4등
```
<br>

### ★ (2) CSS 적용 우선순위 ★
* ① 속성값 뒤에 __```!important```__

* ② 태그 인라인(inline) style 속성 지정

* ③ 아이디 선택자 __```#id```__

* ④ 클래스 선택자__```.class```__ , __```:추상클래스 (ex :hover)```__

* ⑤ 태그 선택자

* ⑥ 상위 객체에 의해 __```상속된 속성```__

<br>

◆ 선택자 우선순위 점수 매기기   
* https://iridescent-zeal.tistory.com/90

<br>
<hr>

### 9) CSS 주요 속성
#### (1) width, height
* __```width```__: 넓이 설정   

* __```height```__: 높이 설정

__ex>__
```
<p class = "paragraph"> 프로그래밍을 배워봐요! </p>

.paragraph { width: 500px; height: 500px; }
```

<br>

#### (2) font
* __```font-family```__

   * 여러 폰트를 순서대로 작성 가능
   
   * __```sans-serif```__ : 모든 브라우저에서 지원하기에 마지막 디폴트값

* __```font-style```__

   * 폰트 스타일: ```normal / italic(이텔릭체) / oblique(기울임꼴)```   

* __```font-weight```__

   * 100 ~ 900 사이 숫자, 100 단위

* __```text-align```__

   * 폰트 정렬 (left / right / center / justify)   

```
.paragraph {
   font-size: 50px;                  // 글자 크기
   font-family: Arial, sans-serif;   // 글꼴
   font-style: italic;               // 글자 기울기
   font-weight: bold;                // 글자 굵기
}
```

<br>

#### (3) border (테두리)
* __```border-style```__   

   * __```solid```__: 실선
   
   * __```dotted```__: 점선

* ★ 띄어쓰기로 한 줄 작성 가능 ★

```
.paragraph {
   border-style: solid;
   border-width: 10px    // 테두리 굵기
   border-color: red;
}
```
```
.paragraph {
   border: solid 10px red;
}
```

<br>

#### (4) background (특정 영역 배경)
* __```background-color```__

   * 배경색 지정

<br>

* __```background-image```__

   * 배경 이미지 지정, 상대경로, 절대경로, url 사용 가능   

<br>

* __```background-repeat```__

   * x축으로 반복: ```repeat-x```
   * y축으로 반복: ```repeat-y```
   * 반복하지 않음: ```no-repeat```

<br>

* __```background-position```__: 이미지 위치   

   * ```top, bottom, center, left, right, px, %```

   * ex> 오른쪽 위 : ```right top```

<br>

__ex>__
```
.paragraph {
  background-color: yellow;
  background-image: url(이미지 경로.확장명);   /* no-repeat를 쓰지 않으면 배경에 이미지로 꽉 채워짐 */
  background-repeat: no-repeat
  background-position: left;
}
```
<br>

* ★ 띄어쓰기로 한 줄 작성 가능 ★
```
.paragraph {
  background: yello url(이미지 경로) no-repeat left;
}
```

<br>
<hr>

### 10) 사이즈 (size) 단위   
| 단위 | 설명 | 예시 |
| -- | -- | -- |
| px | 픽셀 (절대 크기) |  |
| % | 퍼센트 (상대 크기) |  |
| em | 현재 스타일이 지정된 요소의 font-size 기준 | 1.2em : 현재 폰트의 1.2배 |
| rem (root em) | 최상위 최상위 요소의 font-size 기준 | 1.2rem : 최상위 폰트의 1.2배 |
| vh (vertical height) | 뷰포트 높이값의 100분의 1 단위 | 1vh = 9px, 브라우저 높이값이 900px일 때 |
| vw (vertical width) | 뷰포트 넓이값의 100분의 1 단위 | 1vw = 9px, 브라우저 넓이값이 900px일 때 |
| vmin (vertical min) | 뷰포트의 최소값 | 1vmin = 7px, 브라우저 크기: 넓이 1100px, 높이 700px일 때 |
| vmax (vertical max) | 뷰포트의 최대값 | 1vmax = 11px, 브라우저 크기: 넓이 1100px, 높이 700px일 때 |




