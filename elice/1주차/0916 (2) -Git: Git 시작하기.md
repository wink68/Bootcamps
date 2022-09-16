## 2. Git 시작하기
## 1) Git 파일 생성
### (1) 파일의 상태 라이프 사이클
* ```Untracked```: Working Directory에 있을 때

* ```Modified```: 수정

* ```Staged```: git add로 추가하면 Staging Area로 이동

* ```Unmodified```: commit을 하면 unmodified 상태가 됨
<br>

<img src="https://user-images.githubusercontent.com/108077414/190606257-0643831b-80ec-47e4-b325-613ddc930c37.png" alt="git lifecycle" width="700px" />

<br>

### (2) 준비 영역으로 보내기
* 명령어 __```git add 파일명```__

   * staging area로 이동

```
  $ git add comment.js
```

* 여러 파일을 보내야 할 때: 현재 폴더의 모든 파일 보내기
```
  $ git add .
```

<br>

### (3) Staging 상태 확인
* 명령어 __```git status```__

   * staging area의 파일의 상태 (변경 사항)를 확인

```
  $ git status
  
  On branch master
  Changes to be committed:
     (use "git reset HEAD <file>..." to unstage)
     
        modified:    comment.js
```

<br>
<hr>

## 2) Git 저장소
### (1) Git 저장소 반영
* 명령어 __```git commit```__

   * staging area의 모든 파일을 .git 저장소에 저장

* __```-m "메시지"```__

```
$ git commit -m "Initial comment"
```

<br>

### (2) commit 메시지 수정
* 명령어 __```git commit --amend```__

   * 텍스트 편집기 실행 → 수정하고 저장

<br>

### (3) git 저장소 반영 내역 확인
* 명령어 __```git log```__

```
  $ git log
  commit 숫자로된 commit ID
  Author: 
  Date: 
  
     메시지
```

<br>

### (4) git history
* commit된 내용
```
commit ID

Commit size
파일 Tree
Parent
Author
Commiter

메시지
```

<br>
<hr>

## 3) Git 관리 상태 확인
### (1) 변경사항 비교
* 명령어 __```git diff```__
```
  $ git diff
  
  -#let
  +#trysome
```

<br>

### (2) log 옵션들
* 명령어 __```git log -p -n```__

   * ```-p, --patch```

      * commit의 수정 결과를 비교해주는 diff와 같은 역할

   * ```-n```
   
      * 상위 n개의 commit만 보여줌

<br>

* 명령어 __```git clog --stat```__

   * ```--stat```
