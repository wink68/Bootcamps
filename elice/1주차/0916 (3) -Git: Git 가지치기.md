## 3. Git 가지 치기
## 1) Git Branch
* 독립적으로 어떤 작업을 진행하기 위한 개념

* 각각의 Branch는 다른 Branch의 영향을 받지 X

<br>

### (1) Git Branch 종류
* __메인 branch__: 배포할 수 있는 수준의 안정적인 branch

* __토픽 branch__: 기능 추가나 버그 수정과 같은 단위 작업을 위한 branch

<br>

### (2) Git Branch 생성
* 명령어 __```git branch 이름```__

   * HEAD → master: master 브랜치는 첫 git 저장소를 만들 때 자동으로 생성되는 branch

   * HEAD는 현재 가리키고 있는 branch를 의미

<br>

### (3) Git Branch 확인
* 명령어 __```git branch```__

```
  $ git branch
    like_feature
  * master
```

<br>

### (4) Git Branch 이름 변경
* 명령어 __```git chekckout 변경할 이름```__

```
  $ git checkout like_feature
  Switched to branch 'like_feature'
```

* ```checkout```은 branch를 전환하는데 사용 가능

   * ```git log```로 확인한 __snapshot__ 을 넘나들 때도 사용 가능

   * snapshot의 hash값을 이용하여 __과거의 파일 내용__  을 확인할 수 있음

```
   git checkout <snapshot hash>  // 16진수로 이루어진 hash
```

__ex>__
```
  $ git log --pretty=oneline
  e4abb6f... (HEAD -> master) this is master
  d97d387... another snapshot
  
  $ git checkout d97d38
  ...
  HEAD is now at d97d38 another snapshot
  
  $ git log --pretty=oneline
  e4abb6f... (master) this is master
  d97d387... (HEAD) another snapshot     // HEAD가 바뀜
```

<br>
<hr>

## 2-1) fast forward 병합 방식
* ```git checkout like_feature```로 branch위치 이동

   * like_feature에 새로운 정보를 넣어 commit

   * like_feature에서 새로운 checkpoint를 만듦

* ```merge``` → __새로운 내용만 master에 병합되는 방식__   

   * ```branch → master로 병합```

<br>

<img src="https://user-images.githubusercontent.com/108077414/190641998-fa920d07-f73c-4cf1-96a8-9fd7b4e43ed9.jpg" alt="branch" width="500" />

<br>

## 2-2) 갈라지는 branch
### (1) commit graph 확인
* 명령어 __```git log --graph --all```__

   * commit graph 확인 가능

<br>

### (2) 병합merge
```
  $ git checkout master
  switched to branch 'master'
  
  $ git merge like_feature
  [main 2019-07-31T08:58:15.648Z] update#setState idle
  Merge made by the 'recursive' strategy
    checkout.text | 2 +-
    1 file changed, 1 insertion(+), 1 deletion(-)
```
<br>

<img src="https://user-images.githubusercontent.com/108077414/190641536-66aa0cbc-cae6-4fc3-beda-e257553541e6.jpg" alt="branch" width="500" />

<br>
<hr>

## 3) Merge
### (1) 병합
* 명령어 __```git merge 통합할 브랜치```__

   * ```master``` Branch로 통합   

```
  $ git checkout masster
  $ git merge like_feature  // master로 통합
```

<br>

* 명령어 __```git branch --merged```__

   * merge된 branch를 볼 수 있음

__ex>__
```
  $ git branch --merged
    like_feature
  * master
```

<br>

### (2) branch 삭제
* 명령어 __```git branch -d 브랜치 이름```__

   * 사용을 마친 branch 삭제

```
  $ git branch -d like_feature
  
  $ git log --graph --pretty=oneline --all
```

<br>
<hr>

## 4) conflict 해결
### (1) Merge 충돌 해결
* Merge한 두 브랜치에서 __같은 파일을 변경했을 때__ 충돌이 발생   

```
  // 두 브랜치를 각각 다르게 수정한 상황
  $ git merge like_feature
  
  Auto-merging comment.js
  CONFLICT (content) : Merge conflict in comment.js
  Automatic merge failed; fix conflicts and then commit the result.
```
<br>

* __```git status```__ 명령어로 어느 파일에서 충돌이 발생했는지 확인

* 수정 완료 후 __```git add```__ , __```git commit```__ 과정을 거쳐 다시 merge 해준다

<br>

### (2) Merge 충돌 방지
* __```master```__ branch의 변화를 지속적으로 가져와서 충돌이 발생하는 부분을 제거   
