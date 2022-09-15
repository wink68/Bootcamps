## 2. 웹사이트 레이아웃에 영향을 미치는 요소
### 1) 박스 모델
* 콘텐츠 영역 < 패딩(padding) < 박스 테두리(border) < 마진(margin)
<br>

#### (1) margin과 padding의 차이
* __margin-left__

   * border 바깥쪽에서 왼쪽에 여백을 만듦   

* __padding-left__

   * border 안쪽에서 왼쪽에 여백을 만듦
   
   * 여백이 공간 크기에 포함됨
   
<br>

#### (2) margin과 padding 작성법
* __★ ```top right bottom left 순``` ★__   

   * 12시 시계방향
   
__ex>__
```
<style>
   div { margin: 100px 0 0 100px; }
</style>
```

<br>
<hr>

### 2) Block 요소와 Inline 요소
* Block 요소

   * weight, height 가능

   * ```<header>, <div>, <h>, <p>```   

* Inline 요소

   * ★ weight, height 불가능 ★

   * ```<a>, <span>```
  
   * ★ margin-top, margin-bottom 적용 불가 ★

<br>
<hr>

### 3-1) 마진 병합 현상 (형제지간)
* 두 마진이 겹치는 현상

* 큰 값과 작은 값 중 큰 값으로 사용 (150px + 100px = 150px)   

__ex>__
```
<div class="box1">Hello World</div>
<div class="box2">Hello World</div>

/ css문서
.box1 { margin-bottom: 150px; }  // 150px 적용
.box2 { margin-top: 100px; }
```

<br>

### 3-2) 마진 병합 현상 (부모 자식간)
* 자식 <article>에 마진을 주면, 부모인 <main>에도 영향을 미침   

   * 자식에게만 적용하고플 때: __```position: absolute;```__   
   
__ex>__
```
<main rol="main">
   <article>
   </article>
</main>


// css 문서
article {
   width: 200px;
   height: 200px;
   margin-top: 100px;    /* 부모, 자식 모두 위에 100px 빈 공간이 생김 */
```

<br>
<hr>

### 4) 레이아웃에 영향을 미치는 속성
### ① display
* Block과 Inline 요소의 성격을 바꿀 때 사용

   * inline-block을 사용하면 두 요소의 성격을 모두 가짐

__ex1>__
```
// css 문서
p { display: inline; }
a { display: block; }
a { display: inline-block; }
```

<br>

__ex2>__
```
<head>
  <style>
    p {
      width: 300px;
      height: 300px;
      background-color: pink;
      display: inline         // block을 inline으로 바꿈
    }
    
    a {
      width: 300px;
      height: 300px;
      background-color: yellow;
      display: block         // inline을 block으로 바꿈 → 폭, 높이 적용
    }
  </style>
</head>
  
  
<body>

   <p>Block Element</p>   // block 요소
   <p>Block Element</p>
   <p>Block Element</p>
   
   <a href="#">Inline Element</a>  // inline
   <a href="#">Inline Element</a>
   <a href="#">Inline Element</a>

</body>
```

<br>
<hr>

### ② float
* object를 왼쪽/오른쪽에서부터 정렬하고자 할 때

* float을 지정하려는 부모의 width값이 float을 지정한 지점의 width값 이상이어야 함

   * 작을 경우, 레이아웃이 틀어질 수 있음

__ex>__
```
<div class = "left">Hello World</div>
<div class = "right">Hello World</div>

// css문서
.left { float: left; }
.right { float: right; }
```

<br>

__ex>__: float이 적용되지 않은 검정색이 float가 적용된 빨강, 초록, 핑크 뒤로 가게 된다
<img src="https://user-images.githubusercontent.com/108077414/190482092-c4d3f0b8-e734-420c-90c2-cff9589c1bb8.jpg" width="80%" alt="float example">

<br>

### ③ clear
* float의 단점: 뒤에 생성된 레이아웃을 밑에 겹치게 배치

   * clear로 float을 꺼줌

* float에 대한 속성을 제어하고자 할 때
  
   * float값이 마지막으로 사용한 다음 태그에 clear 적용

   * left, right, both

__ex>__
```
<header></header>
  <aside class="left">Hello World</aside>
  <main></main>
  <aside class="right">Hello World</aside>
  <footer></footer>

// css 문서
footer { clear: both; }
```

<br>

### ④ 공백 제거
* 공백이 생기는 이유

   * html과 body 태그가 태생적으로 margin값과 padding값을 가지므로 초기화 필요

   * 별(*)로 초기화
<br>

__ex>__: 방법1
```
<style>
   html, body {
      margin: 0;
      padding: 0;
   }
</style>
```
__ex>__: 방법2 (모든 html 태그)
```
<style>
   * {
      margin: 0;
      padding: 0;
   }
</style>
```
