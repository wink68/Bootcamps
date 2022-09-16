## 4. Git 원격 저장소
### 1) 원격 저장소 받아오기
* 인터넷이나 네트워크 어딘가에 있는 저장소   

   * ex> 호스팅 서비스 (깃허브, 깃랩) 
<br>

### (1) Git 원격 저장소 받아오기
* 명령어 __```Git clone```__   

   * 기존의 git repository를 복사하는 기능   

   * 원격 repository도 복사 가능

<br>

#### (1-1) 새로운 폴더 생성 & 저장소 지정
* 현재 위치한 폴더에서 __```git clone```__ 을 하면 하위 폴더가 생성됨

* 현재 폴더를 저장소로 쓰고 싶다면 __```git clone```__ 의 마지막에 콤마(.)를 찍어주면 된다

<br>

### (2-1) url로 받아오기
* 원격 저장소에서 __```clone```__ 버튼을 클릭   

* SSH와 HTTPS 중 __```Clone with HTTPS```__ 옵션으로 clone   

* __```Git clone```__ 뒤에 원격 저장소의 주소url을 넣어준다

   * 내 컴퓨터에 사본 저장 완료

 ```
   $ git clone https://gitlab.com/alwys/myproject.git
 ```

<br>

### (2-2) 원격저장소 연결
```
  $ git remote add origin 주소
```

<br>

### (3) 저장소 주소
```
  $ git remote add origin https://gitlab.com/group/project     ( 웹호스트 서비스 / 그룹명 / 프로젝트명 )
```

<br>

### (4-1) 원격 저장소 확인
* 명령어 __```git remote```__

```
  $ git remote
    origin
```

<br>

### (4-2) 원격 저장소 한번에 살펴보기
* 명령어 __```git remote show origin```__

<br>

### (5) 원격 저장소 이름 변경
* 명령어 __```git remote rename 원래이름 새로운 이름```__

```
  $ git remote rename origin git_test
```

<br>

### (6) 원격 저장소 삭제
* 명령어 __```git remote rm 저장소 이름```__

```
  $ git remote rm git_test
```

<br>
<hr>

### 2) 원격 저장소 동기화

<br>
<hr>

### 3) Origin이란?
