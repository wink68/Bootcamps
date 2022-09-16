## 1. Git이란?   
## 1) Git을 사용하는 이유   
* 효율적인 협업

   * 다른 개발자가 원본을 수정하면, 다른 개발자가 자신의 원본을 찾을 수 없음

   * 코드 병합을 자동으로 할 수 있다
   <br>

* 쉬운 버전 관리

   * 스냅샷 형태로 저장
   
      * 여러 버전을 하나의 파일로 관리 가능

      * 손쉽게 다른 버전으로 이동 가능

<br>

## 2) Git의 특징
### (1) 가지 치기와 병합 가능
<img src="https://user-images.githubusercontent.com/108077414/190574430-16d363fa-72a5-4d5b-bfe9-80e246519c8e.png" alt="Git branching" width="400px" />

<br>

### (2) 가볍고 빠르다   
* 대부분 작업이 서버와의 통신 없이 로컬에서 진행된다   

   * 이와 달리, SVN의 모든 코드는 중앙서버에 있음   

* 다른 사람과 코드를 공유할 때만 중앙 서비스에 접속하면 된다   

<br>

### (3) 분산 작업
* 각 사용자들은 모든 코드를 가지고 있어 개발을 분산 작업을 할 수 있음

   * 통합 관리자는 코드 통합만 담당

<br>

### (4) 데이터 보장
* 모든 파일은 체크섬이라는 과정을 거친다

   * 체크섬은 16진수 문자열(commit ID)로 이루어져있음

   * commit ID가 같으면 누가 어느 파일을 작업했는지 기록이 남음 → 버전 관리하기 좋음

<br>

### (5) 준비 영역 (Staging area)
* Git 영역

   * 작업 영역 (WorkingDirectory), 준비영역 (Staging Area), 저장소 (Repository)   
<br>

* 수정된 코드를 repository에 저장하기 전 검토하는 단계   

   * git add로 파일 선택
   
   * 실제로 저장소에 파일 반영

<img src="https://user-images.githubusercontent.com/108077414/190575900-81fe948a-faca-4385-b4d3-24542cef0022.png" alt="staging area" width="400px" />

<br>

### (6) 오픈 소스
* 누구나 프로젝트에 기여할 수 있음

<br>

### (7) Git 호스팅 서비스 (원격 저장소)
* GitHub

* Bitbucket (빗버캣)

* GitLab

<br>
<hr>

## 3) Git 초기 설정
* __```Git Bash```__ 라는 프로그램에 접속   
<br>

### (1) Git 버전 확인
```
$ git version
```
<br>

### (2) 사용자 정보 설정
* 프로젝트마다 다른 사용자 정보를 지정하고싶을 때, ```--global```을 빼고 실행   

```
$ git config --global user.name "이름"
$ git config --global user.email 이메일
```

<br>

### (3) 설정한 정보 확인
```
$ git config --list
```

<br>

### (4) 오류 메시지
* ```git config user.name "이름"```이라고 입력하면, ```fatal: not in a git directory```라는 메시지가 나옴

* git 저장소가 시작되지 않은 상태에서는 반드시 ```--global```을 입력해야 한다

<br>
<hr>

## 4) Git 저장소 생성
* __```Git init```__ 명령어   
   * Git을 사용할 프로젝트 폴더로 이동후 git init 명령어 실행   

   * 기존의 디렉토리를 git repository로 설정

* Git 저장소가 초기화 되었다는 메시지

   * ```Initialized empty Git repository in 주소```
<br>

* ```ls -al```: 모든 파일 출력   

   * 프로젝트 디렉토리에 ```.git``` 디렉토리가 생성되며 저장소 생성이 완료

<br>

### (1) 새 저장소 생성
* __```ls```__ : 현재 파일 확인

* __```git init 새 저장소 이름```__ : 새 저장소 생성

* __```cd 디렉토리명```__ : 디렉토리로 이동

   * ```cd mydir```

   * ```git init hello``` : hello라는 새 저장소 생성

<br>
<hr>

## 5) Git 명령어 총정리
* ```git version``` : git 버전 확인

* ```git init``` : git 새 저장소 생성

* ```git config --global user.name "이름"``` : 이름 수정

* ```git config --global user.email "email"``` : 이메일 수정

* ```git config --list``` : git 설정 확인
