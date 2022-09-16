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

### (2-1) 준비 영역으로 보내기
* 명령어 __```git add 파일명```__

   * staging area로 이동

```
  $ git add comment.js README.py
```

* 여러 파일을 보내야 할 때: 현재 폴더의 모든 파일 보내기
```
  $ git add .
```

<br>

### (2-2) 준비 영역 reset
* 명령어 __```git reset```__

   * staging area를 reset 해준다

   * staging area가 비워진다

<br>

### (3) Staging 상태 확인
* 명령어 __```git status 파일명.확장자```__

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

   * unmodified 상태가 됨

* __```-m "메시지"```__

```
$ git commit -m "Initial comment"
```

<br>

### (2) commit 메시지 수정
* 명령어 __```git commit --amend```__

   * 텍스트 편집기 실행 → 수정하고 저장

   * 끝에 __```-m "수정할 메시지"```__ 를 붙여주면 수정 가능   

   * 저장: ```ctrl X + Y + enter```

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

   * commit된 파일 중 변경된 사항을 비교
   
```
  $ git diff
  
  -#let
  +#trysome
```

<br>

### (2) log 옵션들
* 명령어 __```git log -p -n```__

   * ```-p, --patch```

      * 각 commit의 수정 결과를 비교해주는 diff와 같은 역할

   * ```-n```
   
      * 상위 n개의 commit만 보여줌

<br>

* 명령어 __```git log --stat```__

   * ```--stat```

      * 어떤 파일이 commit에서 수정되고 변경되었는지, 파일 내 라인이 추가되거나 삭제되었는지 확인

<br>

* 명령어 __```git log --pretty=oneline```__

   * ```--pretty=oneline```

      * 각 commit을 한 줄로 출력

<br>

* 명령어 __★ ```git log --graph``` ★__

   * ```--graph```

      * commit간의 연결된 관계를 아스키 그래프로 출력

      * branch에서 유용하게 쓰임

<br>

* 명령어 __```git log --S 특정 텍스트```__

   * ```--S```

      * 추가되거나 제거된 내용 중 특정 텍스트가 포함되어 있는지 검사

