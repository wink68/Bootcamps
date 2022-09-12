## 2. 웹사이트 레이아웃에 영향을 미치는 요소
### 1) 박스 모델
* 콘텐츠 영역 < 패딩(padding) < 박스 테두리(border) < 마진(margin)

#### (1) margin과 padding의 차이
* __margin-left__

   * border 바깥쪽에서 왼쪽에 여백을 만듦   

* __padding-left__

   * border 안쪽에서 왼쪽에 여백을 만듦
   
   * 여백이 공간 크기에 포함됨
   
<br>

#### (2) margin과 padding 작성법
* top right bottom left순

   * 12시 시계방향
   
__ex>__
```
<style>
   div { margin: 100px 0 0 100px; }
</style>
```

<br>

