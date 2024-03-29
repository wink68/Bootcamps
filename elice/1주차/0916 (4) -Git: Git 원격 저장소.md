## 4. Git 원격 저장소
### 1) 원격 저장소 받아오기
* 인터넷이나 네트워크 어딘가에 있는 저장소   

   * ex> 호스팅 서비스 (깃허브, 깃랩) 
<br>

#### (1) Git 원격 저장소 받아오기
* 명령어 __```Git clone```__   

   * 기존의 git repository를 복사하는 기능   

   * 원격 repository도 복사 가능

<br>

#### (1-1) 새로운 폴더 생성 & 저장소 지정
* 현재 위치한 폴더에서 __```git clone```__ 을 하면 하위 폴더가 생성됨

* 현재 폴더를 저장소로 쓰고 싶다면 __```git clone```__ 의 마지막에 콤마(.)를 찍어주면 된다

<br>

#### (2-1) url로 받아오기
* 원격 저장소에서 __```clone```__ 버튼을 클릭   

* SSH와 HTTPS 중 __```Clone with HTTPS```__ 옵션으로 clone   

* __```Git clone```__ 뒤에 원격 저장소의 주소url을 넣어준다

   * 내 컴퓨터에 사본 저장 완료

 ```
   $ git clone https://gitlab.com/alwys/myproject.git
 ```

<br>

#### (3-1) 원격저장소를 로컬 저장소와 연결
* origin이 기본값 (default)   

```
  $ git remote add origin(저장이름) 주소
```

__ex>__
```
  $ git remote add origin https://gitlab.com/group/project     ( 웹호스트 서비스 / 그룹명 / 프로젝트명 )
```

<br>

#### (3-2) 원격 저장소 확인
* 명령어 __```git remote```__

```
  $ git remote
    origin
```

<br>

#### (3-3) 원격 저장소의 이름과 주소 살펴보기
* 명령어 __```git remote -v```__   

__ex>__
```
  $ git remote -v
  
  origin https://gitlab.com/group/project (fetch)
  origin https://gitlab.com/group/project (push)
```

<br>

#### (3-4) 원격 저장소 한번에 살펴보기
* 명령어 __```git remote show origin```__

<br>

#### (4) 원격 저장소 이름 변경
* 명령어 __```git remote rename 원래이름 새로운 이름```__

```
  $ git remote rename origin git_test
```

<br>

#### (5) 원격 저장소 삭제
* 명령어 __```git remote rm 저장소 이름```__

```
  $ git remote rm git_test
```

<br>
<hr>

### 2) 원격 저장소 동기화
* 명령어 __```Pull```__

   * 원격 저장소에서 데이터 가져오기 + 병합(merge)

* 명령어 __```Fetch```__

   * 원격 저장소에서 데이터 가져오기

#### (1) 저장소 갱신 - Pull
* 원격 저장소에서 데이터를 가져와 __로컬 데이터와 병합__   
```
  $ git log --all
  
  commit f7b775d (HEAD -> master, origin/master)  // 두 브랜치가 병합되어 하나의 체크포인트를 가리키고 있음
```

<br>

#### (2) 저장소 갱신 - Fetch
* __```git log```__ 명령어로 변경된 파일을 확인하고 Merge 해줘야 함   

   * commit 메시지로 업데이트 된 부분을 확인할 수 있음

__ex>__
```
  $ git log origin/master
  
     Update README.md    // commit 메시지
```

<br>

#### (3) 저장소 발행 - Push
* 로컬 저장소에서 작업한 내용 → 원격 저장소 보내기

   * 다른 사람이 먼저 push한 상태에서 push 불가능

   * 다른 사람이 작업한 것을 먼저 merge 해줘야 함

```
  $ git push origin master
```

<br>
<hr>

### 3) Origin이란?
* 원격 저장소에 저장되는 기본 이름
